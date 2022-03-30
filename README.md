# animated BF icons
Do anything you want with it
just credit

also i got it from 
https://youtu.be/3sXiP_xxZLY

```lua
function onCreate()
	if boyfriendName == 'bf' then
		makeAnimatedLuaSprite('animatedBFicon', 'icons/icon_bf', getProperty('iconP1.x'), getProperty('iconP1.y'))
		addAnimationByPrefix('animatedBFicon', 'normal', 'normal0', 24, true)
		addAnimationByPrefix('animatedBFicon', 'losing', 'defeat', 24, true)
		addAnimationByPrefix('animatedBFicon', 'winning', 'winning', 24, true) --in case you want a winning animation
		setScrollFactor('animatedBFicon', 0, 0)
		setObjectCamera('animatedBFicon', 'other') -- either is under the health bar or nothing
		addLuaSprite('animatedBFicon', true)
		objectPlayAnimation('animatedBFicon', 'normal', false)
	end
end

function onUpdate(elapsed)
	if boyfriendName == 'bf' then
		setProperty('iconP1.alpha', 0)
		if getProperty('healthBar.percent') < 20 then
			objectPlayAnimation('animatedBFicon', 'losing', false)
		elseif getProperty('healthBar.percent') > 80 then
			objectPlayAnimation('animatedBFicon', 'winning', false)
		else
			objectPlayAnimation('animatedBFicon', 'normal', false)
		end
	end
	setProperty('camOther.zoom', getProperty('camHUD.zoom'))
	setProperty('animatedBFicon.x', getProperty('iconP1.x'))
	setProperty('animatedBFicon.angle', getProperty('iconP1.angle'))
	setProperty('animatedBFicon.y', getProperty('iconP1.y') + 0)
	setProperty('animatedBFicon.scale.x', getProperty('iconP1.scale.x'))
	setProperty('animatedBFicon.scale.y', getProperty('iconP1.scale.y'))
end
