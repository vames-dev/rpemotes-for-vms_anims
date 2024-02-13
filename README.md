# RPEmotes for vms_anims
Prepared list of animations from [TayMcKenzieNZ](https://forum.cfx.re/u/taymckenzienz/summary) RPEmotes resource for vms_anims.

The above animations are not configured by me, only converted animation loading table.

## **How can you use it?**
1. Go to ***`vms_anims/config/animations.lua`***.
2. Copy the animations from the ***`animations.lua`*** file from this github.
3. Paste the new animations into ***`vms_anims/config/animations.lua`*** in the appropriate place.
4. Keep in mind that a large part of the animations from RPEmotes have custom props created by creators, in order for them all to work properly, you need to stream the files, for that go to [**archive RPEmotes github**](https://github.com/MLGCrisis/rpemotes/tree/master).
5. Download the entire stream folder from the above given github.
6. Upload the entire stream folder to your vms_anims.
7. Start the server and enjoy the new animations.

## **Konwerter animacji:**
Below is an animation converter for RPEmotes, if you want to use it, you can do so by copying the code below and pasting it on [Online Lua Compiler](https://www.tutorialspoint.com/execute_lua_online.php) and then pasting the list of your animations into ***`AnimationsList`***, then press **Execute**, the last step will be to copy the printed animations list from the right console.
```lua
Config = {Languages={['']={}},MenuLanguage=''}
function dump(o)
    if type(o) == 'table' then
        local s = '{\n'
        for k, v in pairs(o) do
            if type(k) ~= 'number' then
                k = k
            end
            s = s..'    '..(type(k) ~= 'number' and '   '..k..' = ' or '').. dump(v) .. ',\n'
        end
        return s .. '}'
    else
        return tostring(o)
    end
end


local AnimationsList = {

}

local vmsTable = {}

for _, animation in pairs(AnimationsList) do
    local animId = #vmsTable + 1
    vmsTable[animId] = {}
    vmsTable[animId].Category = '"'.."CHANGE IT"..'"'
    vmsTable[animId].Label = '"'..animation[3]..'"'
    if type(animation[4]) == 'string' then
        vmsTable[animId].SubTitle = '"/e '..animation[4]..'"'
    end
    if animation.AnimationOptions.PtfxAsset and animation.AnimationOptions.PtfxName then
        vmsTable[animId].particles = {}
        vmsTable[animId].particles.asset = '"'..animation.AnimationOptions.PtfxAsset..'"'
        vmsTable[animId].particles.name = '"'..animation.AnimationOptions.PtfxName..'"'
        vmsTable[animId].particles.placement = animation.AnimationOptions.PtfxPlacement
        vmsTable[animId].particles.rgb = {1.0, 1.0, 1.0}
    end
    if animation.AnimationOptions.Prop and animation.AnimationOptions.PropBone and animation.AnimationOptions.PropPlacement then
        vmsTable[animId].props = {}
        vmsTable[animId].props.prop = '"'..animation.AnimationOptions.Prop..'"'
        vmsTable[animId].props.propBone = animation.AnimationOptions.PropBone
        vmsTable[animId].props.propPlacement = animation.AnimationOptions.PropPlacement
    end
    vmsTable[animId].AnimDict = '"'..animation[1]..'"'
    vmsTable[animId].Anim = '"'..animation[2]..'"'
end

print(dump(vmsTable))
```

* We do not support the installation of animation to vms_anims, in case of problems check our documentation to verify the correct animation tables.
