---
title: "Youtube Video in Full Screen is not Fullscreen, kinda Widescreen"
date: 2011-02-08
forum: Multimedia Software
---

### Post by DarkSideKlyde on 2011-02-08
So I am about 8 hours into my first non-dual-boot Ubuntu (finally!) install and I have just about everything set up the way I want it, save this one issue... I have Adobe Flash 10.1 installed (from Adobe's website) and my flash video playback works works fine, and continues to work when switching to full screen. This isn't the freeze issue. It just doesn't go full screen. The video remains the same size and the controls stretch across the screen, creating a "widescreen" look. There is no change to the video size whatsoever. I have an integrated Intel 945 GMA graphics card. I have never had this problem in XP or in Lucid 10.04. I haven't installed any other drivers, just the ones that came with the Ubuntu installation. I have tried disabling Hardware Acceleration and tried the "freeze fix" to override GPU validation as follows:


[LIST=1]
[*]sudo mkdir /etc/adobe
[*]echo "OverrideGPUValidation=true" >~/mms.cfg
[*]sudo mv ~/mms.cfg /etc/adobe/
[/LIST]

I have also tried a different browser (Epiphany). I am running Firefox v.3.6.13. The same problem occurred in Epiphany.

Any insight into this little problem of mine? Your help would be much appreciated. Thanks in advance.


As a side note when I run a duel screen monitor (15" Dell 1024x768, my netbook rez is 1024x600) with Firefox running on the Dell Monitor and I hit the full screen button, it sends the video to the netbook screen, still in the "widescreen" mode. I would be happy to have the full screen thing fixed, even if this other thing doesn't get fixed, lol.

DarksideKlyde

EDIT: Ok, so after some more testing I have found that the full screen works just fine when disconnected from the Dell monitor. Plug in the monitor and I get the weird widescreen mode. No clue, but if any one knows what to do to fix it, I'd be grateful. Thanks

---

### Post by Shanttu on 2011-02-10
Same problem here. Disabling the secondary display worked for me as well. Many youtube-vids works well on full screen, even though the secondary screen is attached. Thank you for the tip.
Any solutions welcome =).

---

### Post by DarkSideKlyde on 2011-02-17
I am no longer using dual screens and full-screen video works fine with just my netbook monitor. However, This is still something that needs fixing???

---

### Post by fireworksshow on 2011-03-30
Having the same problem here, still no fix for this? It's really getting annoying.

---

### Post by alexandroid on 2011-04-17
I have the same problem on Dell Studio 15 with dual monitors. Video on the secondary monitor does not stretch (controls do).

When viewing video on main laptop screen, image stretches to the same size as it does on the secondary monitor, but appears offset from the middle.

Laptop resolution is 1280x800, secondary monitor is running 1680x1050.

It appears that image is being stretched to fit the laptop screen resolution, when viewed on any - the picture size is roughly 1260 pixels wide. So it is not enough to fill fullscreen on the monitor, but because of the offset, it is also not viewable on the main laptop screen when secondary monitor is connected.

Any ideas what piece of the software could be a source of the problem? I cannot use "direct video youtube links" solution because I need subtitles and they are provided by youtube flash player...

Ubuntu 10.10 x64, Intel X3100. Desktop effects are off.

Thanks,
Alex

---

### Post by calamari on 2012-03-06
I realize this thread is old, but this continues to be a problem in Kubuntu 11.10 x86_64. I have an external CRT at 1280x960. My laptop screen is 1366x768. Setup is:

```
xrandr --output HDMI1 --off --output LVDS1 --mode 1366x768 --pos 1280x192 --rotate normal --output DP1 --off --output VGA1 --mode 1280x960 --pos 0x0 --rotate normal
```

---

### Post by fmmarzoa on 2012-05-10
Same problem here.

---

### Post by Gaygerbil on 2012-05-24
I'm also having this problem with Flash 11.2.202.235 on Lubuntu 11.10, graphics card is onboard Nvidia Geforce 6100SE n430. I'm only using one monitor, it will go fullscreen but not stretch the image to be actual fullscreen, it's very annoying.

Any help would greatly be appreciated.

---

### Post by denisk on 2012-06-02
Same issue with Kubuntu 12.04 x64.  I have very same hardware/software dual monitor configurations at home and at work.  At home everything works fine. At work videos just don't stretch properly in fullscreen.

---

### Post by Gaygerbil on 2012-06-27
Just an update for me, I recently bought a 22in monitor to replace my CRT monitor to deal with smallish fullscreen I've had with flash. 

All of a sudden videos are scaling right, I wonder if Flash was scaling to 16:9 for me, cuz that seems to be the problem. It's apparent though that the graphics card (for me at least) was not the problem but the way the image was being scaled to my monitor.

---

### Post by Justitia on 2012-08-27
Bumping this thread. I am experiencing this problem using dual monitors (laptop and external) and Ubuntu 12.04.  It's immensely frustrating and I was wondering if anyone had found a fix or work around?

Edit: Just noticed that this is only a problem with Flash.  I am using Youtube's trial HTML5 version and the videos in HTML5 work just fine in full screen, but not the Flash videos.

Edit #2: Ok, a work around that works for me.  Go to [www.youtube/html5](www.youtube/html5) and choose to do the trial HTML5 version.  Now when you want to watch a video in fullscreen right click on it and choose the "pop out" option.  This gives you a popped out version in HMTL5 which you can then set to full screen.  I've tried this with several flash videos and it seems to work.  It's annoying but better than nothing.

---

