---
title: "using  different media player  in unbuntu hardy"
date: 2008-11-12
forum: Multimedia Software
---

### Post by avout on 2008-11-12
I am a new user of Ubuntu. I wanted to try out different media players to play DVDs. Seems Totem is the default. Even if I try opening DVD with 'open with' it still will only open with Totem(only choice given). I have looked for a resolution for this problem there does not seem to be one. I saw posts advocating deleting current media player, using symbolic links etc.. I would like to be able to use 'open with' to be able to choose media player I want to use.

---

### Post by mc4man on 2008-11-12
You haven't mentioned what ver. of ubuntu your using.

In both 8.04 and 8.10 all apps that are available as 'auto run' (default) choices will show up in the r. click on dvd icon 'open with' menu.

In 8.10 this has been made a bit easier (except for apps that need a custom command
Go to home folder -> edit -> preferences -> media -> DVD Video. Chose your app from the 'open with other application' option.

In 8.04 that option in ..media... doesn't exist, a little work is needed to get apps to appear in the dvd video dropdown.

If you have a specific app in mind let me know and I'll link you to an exact step by, do it once and you'll get the idea how to set up any app for dvd's, cd's, ect.

What you can do for now is go to places -> computer and right click on the dvd icon there. In this case the 'open with other application' is available. 
This won't usually add the app to the r. click 'open with' but will start it on a one time basis. ( and show you if a 'custom launch command' is needed

---

### Post by avout on 2008-11-13
I tried going tp places right click etc. . Now nether of Totem or Mplayer works. I saw my DVD rive is set  to open with Mplayer after doing this. I set the Drive back to Totem but still having a problem.

---

### Post by mc4man on 2008-11-13
Mplayer is not suited to auto run a dvd, it needs a 'custom' launch command.

Are you using 8.04 (hardy) or 8.10 (intrepid


what media players do you have installed?

for instance see screen for some players that will successfull auto run dvds. Note xine and mplayer needed 'custom' commands, hence the name changes. Smplayer, vlc and totem-xine work fine as is

---

### Post by ITAndrew on 2008-11-13
Also, I do believe you will need libdvdcss2 (for Totem) to play encrypted DVDs (most retail DVDs). The explanation can be found at Medibuntu's repository located at [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

VLC is generally what I use which can play DVDs straight from install.

---

### Post by SuperSonic4 on 2008-11-13
> **mc4man said:**
> You haven't mentioned what ver. of ubuntu your using.


> **mc4man said:**
> 
Are you using 8.04 (hardy) or 8.10 (intrepid)


The OP put hardy in the title ;)

> gksudo gedit /etc/gnome/defaults.list

Press Ctrl+f and search for "x-content/video", then change the "totem.desktop" entries to "vlc.desktop". Close and save. Next, navigate to Places > Computer > Edit > Preferences > Media > DVD Video, and make sure VLC is selected, then test whether automatic launch and playback with VLC works for you by inserting a DVD. If playback doesn't work properly, navigate to Video > Deinterlace within VLC and select mode "Blend". If that still doesn't solve your issue, or you just want more features enabled upon launch (such as fullscreen upon launch), follow the intructions in the next paragraph.

Right-click on "Applications" in the top panel and select "Edit Menus" to open the default menu editor. Navigate down to "Sound & Video" in the left pane and click on it to show all those applications in the pane to the right. Scroll down the list of applications displayed until you see "VLC media player", right-click on it, then click on "Properties" in the context menu to open "Launcher Properties", and change the launch command from "wxvlc %F" to:

source: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

I always use VLC or SMplayer or occasionally Dragonplayer

---

### Post by avout on 2008-11-13
I had loaded down ibdvdcss2, Totem and Mplayer were both working. I should have thought of this before - I was able to play an un-encrypted DVD, so it looks like something happened to the codecs. Thanks all I do not want to waste anymore of your time with this

---

