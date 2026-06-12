---
title: "full screen video problem"
date: 2008-07-21
forum: Multimedia Software
---

### Post by Alaxandar on 2008-07-21
When I click on any videos on the internet to full screen it shows for a sec then just disappears and goes back the the little screen. Thanks in advance

---

### Post by rowell on 2008-07-25
I'm currently having the same problem in Hardy Heron 32 with Firefox 3.0.1.  Fullscreen flash worked as recently as three days ago, and the only change that I can think of between now and then is updating my system to Firefox 3.0.1 from 3.0.  I will try downgrading firefox to see if this solves the problem.

---

### Post by Bender2k14 on 2008-07-27
I also have this problem.

Just as above, this was not always a problem for me.  I do not know what has changed.

---

### Post by rowell on 2008-07-27
I don't really know a good way to revert to the last ff3, but I was able to 'fix' the problem by turning off visual effects (System->Preferences->Appearance-Visual Effects->None).  So this is a problem with how ff and compiz play together.  How recent was the last compiz upgrade?

---

### Post by Bender2k14 on 2008-07-27
> **rowell said:**
> ...I was able to 'fix' the problem by turning off visual effects (System->Preferences->Appearance-Visual Effects->None).

This also worked for me.  I am going to look for Ubuntu/Compiz bugs on this issue.

---

### Post by Bender2k14 on 2008-07-27
I did not find any bug reports that matched this issue (though there were some similar ones), so I open a new bug:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/252352](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/252352)

---

### Post by skajoeska on 2008-07-28
I have a similar problem. Whenever I click full screen in youtube (no problem with google video, break, or daily motion), it goes fullscreen, but things like my gnome-panel clock, download helper icon, and awn icons seem like they are trying to come through. The video plays but the clock, etc. flicker in and out over the video. Whenever I hit escape it returns to the small video, but the last frame from the fullscreen picture covers everything else until I click on the browser.

Disabling compiz fusion fixes the problem. All was working with compiz fusion 5 hours ago. I might have upgraded to ff 3.0.1 in that time.

below is two screenshots of my desktop after i try and go fullscreen then hit escape.

sorry if this is the completely wrong thread, but it's the closest thing I could find to my problem.

---

### Post by rowell on 2008-07-29
This morning I got a new firefox update, and now videos from hulu.com, youtube.com, and dailymotion.com will maximize to fullscreen correctly.

---

### Post by rowell on 2008-07-29
Looks like I spoke too soon.  The problem has returned.  I'm not sure why it went away, as I hadn't changed the compiz settings this morning.

---

### Post by palomar on 2008-08-03
Same problem here. Hope there will be a fix soon...

---

### Post by mustard675 on 2008-11-03
same problem and i recently installed visual effects.. will try and disable

any updates from compiz?

---

### Post by ogromano on 2009-02-07
Bump....

Same issue but I've noticed that if you right click on a video and select the settings from the context menu, then close the settings... and then click on the maximize button, it WILL maximize correctly.

Don't know who to blame anymore, FF, compiz or plugins for FF! Anyone any more ideas??

Thanx

 - Ogro -

---

### Post by redroad55 on 2009-02-07
It's possible that the plugin you are using in firefox is not set as your default player..so when updates happen you lose your settings. 
this will give you your default list:
> gksudo gedit /etc/gnome/defaults.list..

Here is some examples for vlc for dvd player but the idea is the same for others.
> Press Ctrl+f and search for "x-content/video", then change the "totem.desktop" entries to "vlc.desktop". Close and save. Next, navigate to "Places > Computer > Edit > Preferences > Media > DVD Video", and make sure VLC is selected, then test whether automatic launch and playback with VLC works for you by inserting a DVD. If playback doesn't work properly, navigate to "Video > Deinterlace" within VLC and select mode "Blend". If that still doesn't solve your issue, or you just want more features enabled upon launch (such as fullscreen upon launch), follow the intructions in the next paragraph.

Right-click on "Applications" in the top panel and select "Edit Menus" to open the default menu editor. Navigate down to "Sound & Video" in the left pane and click on it to show all those applications in the pane to the right. Scroll down the list of applications displayed until you see "VLC media player", right-click on it, then click on "Properties" in the context menu to open "Launcher Properties", and change the launch command from "wxvlc %F" to:

vlc --volume 512 %m

or to have DVD playback automatically launch in fullscreen:

vlc --volume 512 --fullscreen %m

Close the VLC properties dialog and exit the menu editor.

Note: Remember to enable deinterlacing in "VLC > Video > Deinterlace" if you see any artifacts during playback, or if playback doesn't work correctly (the same is true with some AVI files also). To exit and enter fullscreen in VLC, just press the "f" key.


this example is for 8.04...Maybe this helps someone here ..Best to you

---

### Post by ogromano on 2009-02-07
Hi again...

Was racking my brain trying to figure this one out and in some post someone suggested uninstalling and reinstalling the flash plugin, so I went to synaptic and did a quick search and saw that there were two options for plugins one installed and the other one wasn't installed. ](*,)
In order to make sure, I went to Adobe's website and found out that the one that was installed wasn't the right one, so I uninstalled it and installed the newest version 10.0.15.3. And magically, my problem dissapeared. :p

I remember installing this non-free version when I installed ubuntu about 7 months ago following some other thread telling me what I should or shouldn't install to get stuff working. And it did, back then. Problem was that the non-free version was probably not getting updated anymore since they came out with a new one or something of the sort.

I hope this fixes your issues as well. I will report back if for some reason it stops working again.

- Ogro -

---

### Post by ryuukage on 2010-07-12
I have the same problem.  Sometimes after clicking on full screen it'll go fullscreen for a second then go back to the normal page.  When this happens if I click on the firefox button on the panel it brings it up full screen.  It's a quick workaround for me.

---

### Post by arijit_bosco on 2011-08-01
Thanks, this was helpful to me too.

---

