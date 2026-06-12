---
title: "Frustrating video problem with Nvidia"
date: 2010-11-23
forum: Multimedia Software
---

### Post by sonicb00m on 2010-11-23
I have tried several Nvidia cards and drivers and even different monitors but I cannot fix this issue.

The video playback for any video file (but mostly HD videos) is just not perfect.

About a quarter of the way down from the top of the screen I always get this slight line during motion of a video that kind of distorts to the right creating what seems like some horizontal sync issue.

It's like the picture is slightly pushed over for a small area.

This happens on all HD videos regardless of screen resolution or monitor that I try.

It happens in all video players ....mplayer, vlc, xbmc, totem....

I have resorted to using Windows 7 as my OS for my media player :( but i really want to use Ubuntu but cannot get perfect video playback.

I have tried with both 32bit and 64bit 10.10 but it doesn't make  difference.

---

### Post by sonicb00m on 2010-11-24
Can anyone confirm if what I am experiencing is normal? 

Does anyone else get absolutely perfect video playback at 720p/1080p with Nvidia cards?

---

### Post by xc3RnbFO8P on 2010-11-24
Did you install **libvdpau1**
I got these lines but I dont see them when I watch the video, only in screenshots.
Here is a screenshot of a full HD video:

[[img]http://ompldr.org/tNmFqMA[/img]](http://ompldr.org/vNmFqMA)

---

### Post by sonicb00m on 2010-11-24
Yes that is enabled and in XBMC it even shows that it is in use during playback.

The video is perfect other than during motion where i get this jittering effect in that area of the screen.

---

### Post by amauk on 2010-11-24
This is called video tearing, and is caused by the graphics card pushing out frames at a different rate than your monitor can display them

Try enabling "sync to blank" in the nvidia-settings program
also, if you use compiz, enable sync to blank in there as well (under the general > display in the compizconfig-settings-manager)

Annoyingly, I can't fix my tearing, as it's caused by my monitor and outside of any software's control

I've got a graphics card with DVI only connectors, going via one of those DVI-VGA adapters, going into an analogue input flatscreen monitor

Refresh rate ends up as a non-integer (60.02 Hz)
so I get tearing and no way to fix it

---

### Post by sonicb00m on 2010-11-24
I set that sync in all the places I could find it and it looks like that has totally solved the problem.

Thanks a lot!

---

### Post by isahlos on 2010-12-04
I had the exact same problem, didn't help to enable sync to black in the nvidia preferences. However, running sudo apt-get install compizconfig-settings-manager and change the refresh rate to 60hz worked for me!

---

### Post by stephenmoore on 2010-12-06
I am running a GeForce 8400GS card with a dual core machine (2.8GHz) and 2 GB RAM and get lusy HD playback... stuttering and slow speed.  The monitor shows 100% CPU usage but only 360MB of RAM used!  I think we have some serious issues here with system utilization!

---

### Post by gradinaruvasile on 2010-12-06
> **sonicb00m said:**
> I have tried several Nvidia cards and drivers and even different monitors but I cannot fix this issue.

The video playback for any video file (but mostly HD videos) is just not perfect.

About a quarter of the way down from the top of the screen I always get this slight line during motion of a video that kind of distorts to the right creating what seems like some horizontal sync issue.

It's like the picture is slightly pushed over for a small area.

This happens on all HD videos regardless of screen resolution or monitor that I try.

It happens in all video players ....mplayer, vlc, xbmc, totem....

I have resorted to using Windows 7 as my OS for my media player :( but i really want to use Ubuntu but cannot get perfect video playback.

I have tried with both 32bit and 64bit 10.10 but it doesn't make  difference.

I have perfect HD playback. Using Debian and the nvidia drivers installed from the scripts fron nvidias site.

For HD playback on nvidia Linux you must have:

1. A card that knows VDPAU hardware decoding - h264 and some other compressions supported (8xxx series and up, excluding certain high end gtx cards, look up on wikipedia).
8400gs is the lowest one that does this, but some of its versions might not have VDPAU support (older chips).

[http://en.wikipedia.org/wiki/Nvidia_PureVideo#Table_of_PureVideo_.28HD.29_GPUs](http://en.wikipedia.org/wiki/Nvidia_PureVideo#Table_of_PureVideo_.28HD.29_GPUs)

Feature set C is recommended, it supports the most image formats and compressions.

2. A driver that enables VDPAU (the nvidia-provider .run driver has all functions, including vdpau), you have to install the libvdpau package if you use the stock driver. I is recommended to use the latest available driver because they typically have many vdpau-related enhancements.

3. A video player that supports VDPAU - i found smplayer to be the best. Totem (AKA Movie Player) and Vlc DO NOT support VDPAU currently.

Also, mplayer (or any other) has to be built with vdpau support. In the Debian repos this is standard, i dont know how it is in Ubuntu any more, maybe some PPA is required.
And you have to explicitly tell the program to use VDPAU (the default is typically xv output).

Problems i encountered: sometimes i had the tearing effect - i disabled xorgs composite extension from xorg.conf and i had perfect VDPAU playback (and no desktop effects, but i dont have compiz installed anyway).

Now it seems to work even with the composite extension (i reinstalled because of a hdd failure).

---

### Post by shreepads on 2010-12-06
> **stephenmoore said:**
> I am running a GeForce 8400GS card with a dual core machine (2.8GHz) and 2 GB RAM and get lusy HD playback... stuttering and slow speed.  The monitor shows 100% CPU usage but only 360MB of RAM used!  I think we have some serious issues here with system utilization!


Stephen I had similar problems and have posted a slightly detailed how-to here:

[http://ubuntuforums.org/showthread.php?t=1637794](http://ubuntuforums.org/showthread.php?t=1637794)

The above is for Hardy but at the top there are links for other versions...

---

### Post by marcus.2009 on 2010-12-06
ok...i'm at a loss....i have just changed over to 10.04 lts...and i am now getting a double vision on my screen...

i get rid of it by changing my resolution but only for a little while and then it comes back...and something besides me is not stable hahaahaha....

definetely a screen to ubuntu setting error...but help me.. i'm not wise enough it seems to rersolve this by myself

---

### Post by Tomei Ningen on 2010-12-23
To report a small success story

I have a Dell XPS 14 laptop (i7 740qm) with Nvidia GeForce GT 425M (4GB Video RAM). I noticed that I have tearing problems when playing video on the external monitor, but the laptop's built-in LCD has no such problem. After reading a lot of threads in this group, I finally found a combination that works:

Ubuntu 10.10 2.6.35-24-generic
nvidia driver version: 260.19.29
Compiz off
In nvidia settings app, choose OpenGL Settings -> Sync to VBlank
Disable the built-in LCD and use the external monitor as the only display
In VLC, choose Tools -> Preferences -> Video -> Output = "GLX Video Output (XCB)"
In Smplayer, choose Options -> Preferences -> General -> Video -> Output driver = "gl_nosw"

This seems to work fine with an external 1280x1024 monitor.

I am going to buy the Dell U2711 monitor with 2560x1440 resolution. I hope this solution would work there as well, or else it would be a $1000 mistake .... I think I will need to bring my laptop to a local Fry's and test on their 27 inch Apple Cinema Display with the same resolution just to be 100% sure.

---

### Post by gradinaruvasile on 2010-12-23
Have you tried using VDAPU output (hardware decoding)? That should use v-sync.

---

### Post by Tomei Ningen on 2010-12-25
> **gradinaruvasile said:**
> Have you tried using VDAPU output (hardware decoding)? That should use v-sync.

Thanks [gradinaruvasile]("http://ubuntuforums.org/member.php?u=589640")! VDPAU does the trick. I selected this output option in smplayer and the tearing is completely gone, even in TwinView mode (both laptop and external monitors are enabled simultaneously).

- TN

---

