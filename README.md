# Snoop's Garry's Mod Lua Guide

## General Information 
- You don't have to take everything here as true or source.
- This is how I view glua and this is how I think everyone should get started with it.
- Our [discord](https://discord.gg/ZPxpb7KFct). 
- If you need help with anything contact us in the discord server.

## Getting Started - WIKI
- PLEASE for the love of god always use the [wiki](https://wiki.facepunch.com/gmod)

## Getting Started - IDE
- What is an IDE? integrated development environment or (IDE) is a building applications that combines common developer tools into a single graphical user interface.
- What would I reccomend. ( [Visual Stuido Code](https://code.visualstudio.com), [Sublime Text](https://www.sublimetext.com) )
- Once you install either IDE you will need to setup your addon.
- Create a base folder. ex: stoopy_<addon_name>
- Next we will setup the directorys inside the addon folder.
  
  `lua/autorun/sh_<addon_name>.lua`
  `lua/autorun/server/sv_<name>.lua`
  `lua/autorun/client/cl_<name>.lua`
- This is the simplest way to setup an addon.

## Getting Started - sh_.lua
- The prefix "sh" stands for shared this means both client and server can be used here.
- Code example. I used a meta table bc im lazy
```lua
local pMeta = FindMetaTable("Player")

function pMeta:getName()
  return pMeta:Name() or ""
end 

function pMeta:getSteamID()
  return pMeta:SteamID() or ""
end

```

## Getting Started - sv_.lua
- The prefix "sv" stands for server this means serverside so clientside code wont work here.
  `LocalPlayer() wont work here`
- Code example. I used a meta table bc im lazy
```lua
function ServerSide(p, v)
    if !IsValid(p) then return end 
    if v == "" then return end 
    local a = tostring(v) 
    if a < 1 then return end 
    return a  
end 

```

## Getting Started - cl_.lua

- The prefix "cl" stands for client this means clientside or frontend code.
- Don't put severside code here.
```lua
concommand.Add("example", function(self) 
    // This is poop ui code but it is used as an example for clientside code/
    local frame = vgui.Create("DFrame")
    frame:SetSize(600, 550)
    frame:Center()
    frame:MakePopup()
    frame:SetTitle("Snoopy's Guide")
end)

```

