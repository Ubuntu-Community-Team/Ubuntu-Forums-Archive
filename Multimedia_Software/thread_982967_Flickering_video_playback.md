---
title: "Flickering video playback"
date: 2008-11-15
forum: Multimedia Software
---

### Post by EpidemikE on 2008-11-15
Hey, I am having an issue on my HP NC6400 running 8.10 x64. What happens, is playing videos from any of the media players (VLC, gxine, Totem) the video playback flickers. I am not sure when this started but I know this wasn't happening before I upgraded to 8.10

Does anyone have any suggestions?

EDIT:
I just started playing with Compiz and when I change the Windows manager to Metacity I dont have any issues

---

### Post by linux32_user on 2008-11-15
> **EpidemikE said:**
> Hey, I am having an issue on my HP NC6400 running 8.10 x64. What happens, is playing videos from any of the media players (VLC, gxine, Totem) the video playback flickers. I am not sure when this started but I know this wasn't happening before I upgraded to 8.10

Does anyone have any suggestions?

EDIT:
I just started playing with Compiz and when I change the Windows manager to Metacity I dont have any issues

May be the vertical synchronization is disabled from the graphics drivers, I am new to linux and can only tell that it is most probably a VSYNC issue. The video will look cutting or tearing effects. VSYNC is the synchronization of bringing down the frame rate of the video to monitor refresh rate level like 60 fps or 75 fps. If you turn VSYNC to 'ON' the video will no longer flicker.

---

### Post by Zootropo on 2008-11-15
Try using x11 to play the video.

---

### Post by EpidemikE on 2008-11-15
Guys,

I am not sure on how to change the vsync options

I also  am not sure on how to play via x11, can you guys elaborate on tis?

---

### Post by Izek on 2008-11-15
> **EpidemikE said:**
> I also  am not sure on how to play via x11, can you guys elaborate on tis?

type gstreamer-properties in terminal (Applications > Accessories in Ubuntu) and go to the video tab. Under **Default Output**, choose X Window System (no Xv).

If this doesn't fix the issue, then I'm out of ideas, since the second X Window System (X11/xv/shm) option causes my totem to fail.

---

### Post by apollyon0810 on 2008-11-15
It worked for me!  I've been looking for this solution for a while.  BTW, I'm using Mobility Radeon HD 2400.

---

### Post by EpidemikE on 2008-11-15
I tried what Izek suggested and still I get the same thing upon playback.

Weird thing is that the test video plays fine. I did an upgrade from 8.04 to 8.10 and I've had some bugs so I think I may do a clean install and that more than definitely will clear up any bugs

EDIT:
I just tried it again with Totem and it works. I still have the same issue with VLC and gxine. Oh well, clean install...away!!

---

### Post by Dubbayoo on 2008-11-15
> **Izek said:**
> type gstreamer-properties in terminal (Applications > Accessories in Ubuntu) and go to the video tab. Under **Default Output**, choose X Window System (no Xv).


This worked for me. Radeon HD 4850.

---

### Post by zager on 2008-11-17
> **Izek said:**
> type gstreamer-properties in terminal (Applications > Accessories in Ubuntu) and go to the video tab. Under **Default Output**, choose X Window System (no Xv).

This didn't worked for me. Testing video is fine, but other videos are flickering in VLC, Mplayer and native player in Ubuntu 8.10.

I have: HP nc6400 with ATI graphic card.

---

### Post by EpidemikE on 2008-11-18
I did a clean install and I am not sure if I could define the problem as getting worse but it did. Now instead of flickering I get no video and just audio. I used the Compiz Fusion icon to change the window manager to metacity and video playback resumed.

Ugh, I wonder if this is an issue with my video card. ATi has been known to have issues with Linux support...

Thoughts, suggestions, comments?

EDIT:

OK i delved into it a bit more and I found that the fglrx drivers weren't activated. I tried to activate them but it wouldn't let me. So I went to synaptic and did a search and installed the drivers. I activated them for the card and rebooted, afterwards I experienced the same flickering upon video playback. Yeah, not cool.

---

### Post by kdreimiller on 2008-11-18
i have an ati radeon 3100 and adjusting the video output to x11 worked for me as well.  vlc stopped flickering but i cant get totem to stop since i cant find the higher level preferences with totem.

---

### Post by EpidemikE on 2008-11-19
I have a radeon x1250/1300, can you post on how to make the x11 changes or the ones that you made?

---

### Post by powerwatt on 2008-11-19
Izeks post work fine for video. However for graphics they seem to be flickering. Stuff such as Google Earth for example.

Anyone have any other tips?

---

### Post by Izek on 2008-11-19
> **powerwatt said:**
> Izeks post work fine for video. However for graphics they seem to be flickering. Stuff such as Google Earth for example.

Anyone have any other tips?

If you're using compiz, it may be the problem, or if you're using certain open-source drivers.

IE: [http://forum.compiz-fusion.org/showthread.php?t=3367](http://forum.compiz-fusion.org/showthread.php?t=3367)

---

### Post by Tilex on 2008-12-02
Hi guys,

I'm on Kubuntu 8.10 with ATI 3450.  

How do we disable compiz (I don't know if it's installed), or how to we change to X11 output?

I've got the video playback as well as Google Earth flickering problem.

Thanks!

---

### Post by Tilex on 2008-12-02
> How do we disable compiz (I don't know if it's installed), or how to we change to X11 output?

I finally simply removed compiz packet(s) this way:

```
sudo apt-get remove compiz*
```

Now movies are playing just fine and Google Earth is very smooth.

**I've a question: how can we get visual effects if compiz is removed?  Is there another program handling the job?

---

### Post by mrthumb on 2008-12-15
Hi All, 
Had exactly the same problem after an 8.04 to 8.10 upgrade. Doing the gstreamer-preferences bit worked fine for Totem. But not VLC.

Went into VLC tools>preferences>video and selected from the Output pull down "X11 video output".  All smooth & fine once more.

I'm using the FGLRX drivers with an ATI Radeon X1300.

---

### Post by kdreimiller on 2008-12-18
update:
I edited my xorg.conf file to include this:
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
and it works beautifully now.  i only need to turn off compiz when i go to fullscreen.  totem looks great - so much better placy on totem than vlc.  whereas before i did this totem was ALWAYS choppy.

im using an ati radeon 3100 btw

im wondering what other tweaks i can do to my card to maybe get better performance now?

---

### Post by Linux Lurker on 2008-12-19
> **Tilex said:**
> I finally simply removed compiz packet(s) this way:

```
sudo apt-get remove compiz*
```

Now movies are playing just fine and Google Earth is very smooth.

**I've a question: how can we get visual effects if compiz is removed?  Is there another program handling the job?


While reading this thread, I decided to see if desktop effects were the cause of my flickering as well.  So, instead of completely uninstalling compiz, I went to the following area in Kubuntu 8.10:
System Settings | Desktop | Desktop Effects | "General Tab" |
UNcheck "Enable desktop effects".
Video now plays fine.  I'll experiment later to see if I can have effects and flicker-free video too.
==========
Ok... same area.  REenable desktop effects (checkmark)
Advanced options button
Left compositing type unchanged "OpenGL"
Tried each of the three options in drop down box "OpenGL mode" - the other two had WEIRD effects on my screen, so I let it revert back to the original setting.
Texture filter - changed from "bilinear" to "trilinear (best quality)
Played a movie... all looked good.
Changed texture filter back to original "bilinear" and tried again...  Video STILL looks good???
After playing with the above options, I returned all to previous settings.  Now video plays fine.
I dunno... but it's currently working fine.  When before I had heavy flickering with video playback.

---

### Post by h4ppycl0wn on 2008-12-29
For Kubuntu; I repeated Linux Lurkers step of switching the texture filter at System Settings -> Desktop -> Advanced Options from bilinear to trilinear and at first thought "hooray, its solved the problem for me. "

Actually I noticed that for some reason deskptop effects (compiz) had become disabled. I restarted compiz and the problem returned. 

So, disabling desktop effects (System Settings -> Desktop -> Enable Desktop Effects) is one solution.

With desktop effects enabled I also tried switching the video out driver to x11 with mplayer. This worked fine but I couldn't fullscreen unless I enabled the -zoom option ( to enable software scaling). So... finally, completed command line for mplayer to have non-flickering playback:

mplayer -vo x11 -zoom <filename>

You could also add these options to the bottom of /etc/mplayer/mplayer.conf :
vo=x11
zoom=yes
... so that they are used as default for all users.

I am using ATI Radeon HD4650 in brand new build Kubuntu 8.10. Desktop effects (I.e. compiz) is enabled. No idea why playing with this filter would solve the problem but it does.

---

### Post by laplace/d on 2008-12-30
none of those options worked for me... since i use VLC i did it straight from there:

Tools > Preferences:

check the "All" option at the bottom left corner.
expand Video, click on Output modules (without expanding).
go to the right where it says Video output module and then save.

that worked fine for me.

source: [http://www.ubuntugeek.com/fix-for-video-playback-problem-in-compiz-fusion.html](http://www.ubuntugeek.com/fix-for-video-playback-problem-in-compiz-fusion.html)

i use an ATI 3200 on an hp pavilion dv5 laptop.

---

### Post by zika on 2008-12-30
for ubuntu intrepid:
```
System->Preferences->Multimedia Systems Selector->Video->Plugin->X Window System (No XV)
```above makes X11 without Xv default.

(for flash right clik on video and choose X11 ...)

that made my flicker go away ... ;) (ATI Radeon HD 3650 with newest driver from ATI (10. dec. 2008.))

---

### Post by Douglas Cartland on 2009-04-08
> **EpidemikE said:**
> 
EDIT:
I just started playing with Compiz and when I change the Windows manager to Metacity I dont have any issues

I have the exact same problem, and same workaround. My graphics card is a Radeon HD 2600XT. Flickering also happen for graphics applications such as emulators, wine and computer games as well, but never for flash videos, they always seem to work fine.

---

