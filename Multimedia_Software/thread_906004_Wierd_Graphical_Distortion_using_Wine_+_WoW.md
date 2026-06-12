---
title: "Wierd Graphical Distortion using Wine + WoW"
date: 2008-08-30
forum: Multimedia Software
---

### Post by baddelini on 2008-08-30
So I've run through about every guide I can find on the subject (All fresh installations each time) and I still don't know whats going on with this.

When I try to run wow in Wine on my ATI Radeon 2600 512mb PCI-E card, I get distortion like the picture below:

[IMG]http://i142.photobucket.com/albums/r92/baddelini/noname.jpg[/IMG]

This happens right when wow starts up.  I maintain a clear view of my mouse strangely enough, and I can get back to a normal view by restarting X.

Has anyone had a similar problem they were able to fix? If so, how?  I'm desperate here, please help!



[I]Edit: Solved the problem.

So I actually got mine working on an ATI Radeon 2600 512mb PCIE, it required a fresh installation though.  Basically I did a fresh install, enabled the 3d drivers that came with Ubuntu, and then updated.

Installed Wine, blah blah... I had a windows installation of WoW on another HD so I used that and added the following lines at the end of Config.wtf (after deleting the account folder and everything in it).

SET ffxGlow "0"
SET M2UseShaders "0"
SET gxApi "opengl"

And wow booted up and played the movies and I had a clear picture, no gfx distortion or common other wine/wow problems.

I hope this works for you!

Here's a paste of my WTF config file.[/I]

```
SET locale "enUS"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET coresDetected "1"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1440x900"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET pixelShaders "1"
SET movie "0"
SET expansionMovie "0"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET farclip "477"
SET particleDensity "1.000000"
SET spellEffectLevel "4"
SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET M2UseShaders "0"
SET gxCursor "0"
SET textureFilteringMode "0"
SET Gamma "1.000000"
SET lastCharacterIndex "1"
SET readTOS "1"
SET readEULA "1"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET lod "1"
SET groundEffectDist "70"
SET weatherDensity "0"
SET cameraPitchMoveSpeed "90"
SET cameraPitchSmoothSpeed "45"
SET realmName "Hyjal"
SET gameTip "1"
SET uiScale "0.63999998569489"
SET useUiScale "1"
SET shadowLOD "0"
```

---

