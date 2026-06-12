---
title: "ATI Radeon Xpress 1100 IGP - Horrible performance !"
date: 2008-06-24
forum: Multimedia Software
---

### Post by JohoTehAzn on 2008-06-24
Hello all,

I recently installed Ubuntu 8.04 from scratch, and installed the ATI proprietary driver from "Hardware Drivers" under Administration.  I'm running into several problems.

Firstly, although I have Visual Effects set to "Extra" and everything runs smoothly, I'm having pretty poor performance in fullscreen.  YouTube videos and VLC Player flicker in fullscreen, but are fine windowed.

Secondly, I seem to get these "spikes" of poor graphics performance.  Running Diablo II: Lord of Destruction on WINE (which I previously did under Feisty and Gutsy with no problems), I average approximately 60-70 FPS which is very smooth, but every minute or two, the framerate plunges down to 10-20 FPS with 15+ skip.  VLC Player (and all of the other video players) gives me this same problems--I'll be watching a video and the video lag spikes are to the point where I have to pause said video and wait; this happens anywhere from every five minutes to every minute.  Both of these problems happen in fullscreen and windowed mode.

Lastly, every time I have a YouTube video playing and close the tab, it crashes FireFox completely.  This gets extremely irritating, especially when I'm in the middle of a download.

I previously had Ubuntu 8.04 installed on this very same machine, and all of these problems were existent.  Reformatting and re-installing has not solved any of my issues.

I have an Acer Aspire 5100-5728.  My graphics card is an ATI Radeon Xpress 1100 IGP.  Included with the laptop was Windows Vista Home Premium, which was fine with graphics (but gave me terrible networking problems to the point where I couldn't even connect to the internet).  I tried two different installations of XP, and neither of them wanted to work at all, so Linux is my last and only hope.

Any help would be greatly appreciated.

---

### Post by Canis familiaris on 2008-06-25
Disable Compiz (i.e. Desktop Effects) and see wheter all works.

Maybe this link will help.
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I think you can use ATI driver for ATI 1100IGP. This link will help.
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

This link may help too
[https://wiki.ubuntu.com/X/RadeonXpress](https://wiki.ubuntu.com/X/RadeonXpress)

---

### Post by JohoTehAzn on 2008-06-27
Thank you very much.  I am currently using the open source ATI driver and as of now, everything is smooth.

However, I wish to enable direct rendering; under the third link, it tells me to add software sources, and then "update your mesa packages"; how do I go about doing so?  I know how to add software sources, but I am unfamiliar with the latter.

---

### Post by MonGol on 2008-06-27
After you have added the software sources you start Synaptic and press the "reload" button. By pressing "mark all upgrades" and "apply" Synaptic will install all available upgrades - maybe the Mesa packages are upgraded too. You can check this by searching for "mesa" and scrolling down to "libgl2-mesa-dri" or "libgl2-mesa-glx". If they are marked as an upgrade everything should work as expected after applying.

---

### Post by JohoTehAzn on 2008-06-27
Okay, another update.

I have yet to enable direct rendering, but I'm still getting the same performance issues in terms of "spikes" of low framerate in games.  Videos, however, seem to be fine at the time being.

Is there a possibility that direct rendering may help this issue?

---

### Post by JohoTehAzn on 2008-06-27
Well, another update.

Direct rendering is now enabled, and the performance has increased noticeably.  Unfortunately, the issue of "spikes" of low framerate still exists in Diablo II; I will try to test it out in other games.

Could this be an issue with WINE?  I've never had any problem of this sort in the past with previous versions of WINE and Ubuntu.

---

### Post by JohoTehAzn on 2008-06-28
Hmmm.  Streaming videos (YouTube) and WINE are the only ones giving me problems right now in terms of "spikes" of low framerate.  Video files are fine.

Any thoughts?  :(

---

### Post by |{urse on 2008-06-28
everything you will ever need to get your annoying ati card/chipset running (fairly well) with ubuntu is here. If you are using gutsy (change Hardy to Gutsy in the link)

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

I really do feel for you, I had the same problem for a while.

[http://ubuntuforums.org/showthread.php?t=780455](http://ubuntuforums.org/showthread.php?t=780455)

don't use any of those xorg.conf's, just lettin u know how frustrated i got lol.

---

### Post by James_the_dude on 2008-06-28
I am having the exact same issues with my ATI Radeon Xpress 1150 video card. I have been researching this problem for a while now and I cannot find any real solution. I've tried messing around with interlacing settings, something to do thing "-Xv" or video output settings, disabling desktop effects does not change anything, various alterations to my xorg.conf file don't help either. Essentially there are two options:

1. Use the open source driver. You probably won't be able to enjoy any useful desktop effects (even as basic as transparency) and you probably won't be able to enjoy anything which is three dimensional, but your *DVDs* will look great.

2. Use the non-free fglrx driver. Enjoy desktop effects, and 3d capabilities, and get headaches, maybe even seizures due to the horrendous quality of any video you try to watch.

On the positive side, it would seem that a lot of people are experiencing this exact same problem, so there is a slim possibility that ATI may consider doing something about it.

---

### Post by JohoTehAzn on 2008-06-28
I have tried each possible solution offered in this topic.

The only one thing that varies from "solution" to "solution" is the quality of video.

Both the proprietary and open-source drivers give me absolutely horrid performance in WINE, and the games I'm playing (Diablo II, RollerCoaster Tycoon 1, The Sims 1) don't even require that much in terms of hardware performance; they ran smoothly back in Gutsy and Feisty and Edgy, and gave me no problems in terms of hardware performance.

Additionally, desktop effects have no effect whatsoever on performance.  I can have them enabled or disabled, and I will still continue getting these "spikes" of laggy framerate.  Quite frankly, I don't care one bit about desktop effects if the basic functions of a graphics card cannot be fulfilled.

---

### Post by |{urse on 2008-06-28
to fix your "crappy video while composite is enabled" run this,

```
gstreamer-properties
``` 

click the tab entitled 'video'

select "X Window System (no Xv)" then click close.

It's all well and good to configure xorg to not use Xv but if gstreamer still is then you're going to get that horrendous flicker.

---

### Post by |{urse on 2008-06-28
also.. for the flickering during 3d games. Turn off desktop effects or if you're lazy like me. Make custom "shortcuts" (theyre really just scripts) to switch from no composited wm back to composited after you've finished playing the game. 

Example

> #!/bin/bash
metacity --replace &
sleep 2
/usr/local/games/etqw.demo/etqw &&
sleep 2
compiz --replace &

yep it just turns off desktop effects before the game starts and reenables them when the game exits.


Oh and I just remembered this, If you have a fairly beefy system but youre stuck with integrated garbage for gfx, try installing the real-time kernel, I've had a lot of luck getting performance boosts in gaming/multimedia that way. it's in the repos ^^

---

### Post by JohoTehAzn on 2008-06-29
I have all my games set to the lowest graphics settings possible, and turning off desktop effects does not affect game speed in any way.

---

### Post by Melcar on 2008-06-29
Running games in Wine with an ATI chip is simply a no no.  You will either get bad performance or serious graphical glitches.  This is true for both the proprietary and open source driver, the latter being just too slow (in most cases it's up to 50% slower) and not having full openGL capabilities (which is really important for Wine).

Video flickering happens with windowed apps. while composition managers are one; running them fullscreen sort off alleviates this.  The newest driver (8.6) allows you to play accelerated videos and play games without flickering with Compiz on (as long as they're in fullscreen mode).  If you really want to play around with Compiz and be able to use Xv/openGL, you're going to need to install the latest ATI driver (the one from the drivers manager in Hardy is an older version and lacks a few fixes).

---

### Post by jaytothepeah on 2008-07-01
> **Melcar said:**
> Running games in Wine with an ATI chip is simply a no no.  You will either get bad performance or serious graphical glitches.  This is true for both the proprietary and open source driver, the latter being just too slow (in most cases it's up to 50% slower) and not having full openGL capabilities (which is really important for Wine).

Video flickering happens with windowed apps. while composition managers are one; running them fullscreen sort off alleviates this.  The newest driver (8.6) allows you to play accelerated videos and play games without flickering with Compiz on (as long as they're in fullscreen mode).  If you really want to play around with Compiz and be able to use Xv/openGL, you're going to need to install the latest ATI driver (the one from the drivers manager in Hardy is an older version and lacks a few fixes).

I have the exact same laptop. acer aspire 5100.

I have zero compiz issues and I don't play windows games in wine and I have never had any video problems, but I am not able to get my second monitor to display a second desktop.

---

