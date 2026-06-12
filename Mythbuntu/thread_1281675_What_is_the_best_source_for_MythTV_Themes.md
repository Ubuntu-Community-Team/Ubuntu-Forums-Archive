---
title: "What is the best source for MythTV Themes?"
date: 2009-10-03
forum: Mythbuntu
---

### Post by NinjaNumberNine on 2009-10-03
What is the most complete collection of MythTV Themes available? I wish they had one that had the WMC effects such as thumbnail scrolling left and right, fully animated scrolling and zooming effects, and maybe even some sound effects. So, free to all opinions, what's the best place to look for themes? I looked at their on-site themes but I would need someone to tell me how to install tar packages before I could install them... Wouldn't it be nice if all the packages out there had a .deb extension available? 

Anyway thanks for advice,


NinjaNumberNine

---

### Post by Lepy on 2009-10-03
You will have to wait for .22 to be released or help test it out if you want to experience a more metadata friendly theme akin to wmc or xbmc.

Since I assume you are using 9.04 you can either download trunk from the automatic daily builds [(link)](http://www.mythbuntu.org/auto-builds) or upgrade to 9.10 (either through update-manager -d or the beta iso from the mythubuntu site) which comes with .22 by default.

If you choose to do this, make sure to backup your database, that is if you have an extensive amount of recordings you wish to keep. Also, keep in mind that you may run into bugs or instability. While I have found .22 to work ok right now, use at your own risk!

---

### Post by NinjaNumberNine on 2009-10-03
You mean there aren't any more themes available for the current version? I am using Jaunty.

---

### Post by Lepy on 2009-10-03
All of the standard themes for .21 on jaunty should be accessible for download (and should be installed by default) through the Theme tab in the Mythbuntu Control Center and changeable in the settings option of the frontend.

Extra themes for .21 may be found [here](http://www.mythtv.org/wiki/Category:Themes)

However, the effects/metadata (and possibly sounds?) that you requested are being implemented in .22 through the use of the newly written MythUI: [Example 1](http://www.mythtv.org/wiki/MythUI_Demo_Theme), [Example 2](http://www.mythtv.org/wiki/Theme_Terra)

To use MythUI, you must upgrade to Myth .22 through the Mythubuntu auto-builds or update to 9.10 which comes with .22 by default.

---

### Post by NinjaNumberNine on 2009-10-03
Thanks for the information. I use Kubuntu, though... Is there any way to update from there?

---

