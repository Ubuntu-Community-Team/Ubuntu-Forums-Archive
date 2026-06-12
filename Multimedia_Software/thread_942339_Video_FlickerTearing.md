---
title: "Video Flicker/Tearing"
date: 2008-10-09
forum: Multimedia Software
---

### Post by L815 on 2008-10-09
I have an Intel gm965 video card in my laptop. When I play videos full screen, or just large in general, there are tears when there is a lot of movement in the video.

This is related to Ubuntu since the video play in Windows is fine.

Anyone know a solution to this? 
I've tried a few but none of them work :/

---

### Post by lovinglinux on 2008-10-09
I don't know if the issue I'm experiencing is the same as you, because I couldn't find a word in English to describe it. But since the effect is more visible when there is a lot of movement I guess it should be the same. Here is not drastic, but is kind of annoying. The effect is kind of a horizontal line, like if a line in the screen is misplaced. sometimes it fills the entire video width, sometimes is confined to a small area, sometimes multiple areas.

I don't know how to solve it, but I decided to bump the thread and follow the discussion. I hope someone can help us.

BTW, my graphics card is a nVidia 7300GT.

---

### Post by L815 on 2008-10-09
That's the same exact problem. I read around while searching for a solution that it might have to do with the refresh rate of the video. 

It's really annoying trying to watch flash and videos like that.
Since it is a problem with or without compiz, I can't just disable compiz :p

If they get this fixed, I'm sure I can finally go over 100%

---

### Post by medic2000 on 2008-10-09
In ccsm change the automatic refresh rate detector to manual and enter 60Hz. Also in ccsm activate the SynctoVBlank. I hope they will work.

---

### Post by lovinglinux on 2008-10-09
> **medic2000 said:**
> In ccsm change the automatic refresh rate detector to manual and enter 60Hz. Also in ccsm activate the SynctoVBlank. I hope they will work.

Unfortunately, they don't.

---

### Post by testbenchdude on 2008-10-09
I am having the same problem, and it's going to make me have to resort to Windows again. I have this problem with any kind of video, through VLC or Totem; streaming via Flash, or watching downloaded avi and DVDs. The video plays fine in a small windowed screen but when I increase the size to half my screen or full screen, everything becomes horrendously choppy.

It's not my hardware because this laptop played any kind of video just fine full screen with Windows. I do not have desktop effects turned on and I am not using Compiz or any other eye candy. I have the latest ATI driver for my card and I'm using the latest Flash 10 install on Ubuntu Hardy 64.

This just flat out sucks. I'm tired of googling "x random problem ubuntu"--I've been doing that for three days straight now! Many thanks to everyone here who has already helped me with the problems I've had, but I'm done. Guess I'll try it again in a few years. ;(

---

### Post by testbenchdude on 2008-10-10
Aaaaaaand a partial retraction is in order here. I stumbled upon the idea that maybe my video driver might share some of the blame since everything seemed to be affected video-wise. In my internet meanderings I came across a program called Envy which is a front end for simple installation/removal of video drivers. I installed it, then uninstalled my ATI driver. Rebooted, then reinstalled the ATI driver via Envy, and rebooted.

Hoorah! Full screen DVD playback in VLC is Silky Smooth! Flash still bites but it *is* better than it was. Everything seems a little snappier too, from dragging windows around on the desktop to firing up something like the Synaptic Package Manager (screen used to stutter as the root password prompt came up). I must have mucked around too much and corrupted my display driver or something because this is much more akin to what I'd expect an OS to behave on modern hardware.

My suspicions were almost outright confirmed as I surfed around during the driver reinstallation--even with the crappy default resolution, web pages seemed much more responsive. So if you've been hitting your head against the wall like I have been, why not do a reinstall of your video drivers? I for one was pleasantly surprised. Now then, if only they could figure a way to get Flash to play without chop in full screen...

Holding off on switching back to Windows... for now.  Cheers~

Envy:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Thanks, Alberto!!!

---

### Post by CazperII on 2008-10-16
> **lovinglinux said:**
> I don't know if the issue I'm experiencing is the same as you, because I couldn't find a word in English to describe it. But since the effect is more visible when there is a lot of movement I guess it should be the same. Here is not drastic, but is kind of annoying. The effect is kind of a horizontal line, like if a line in the screen is misplaced. sometimes it fills the entire video width, sometimes is confined to a small area, sometimes multiple areas.

I don't know how to solve it, but I decided to bump the thread and follow the discussion. I hope someone can help us.

BTW, my graphics card is a nVidia 7300GT.

I had the exact same thing until the recent kernel updates with nvidia-glx update (2.6.24-21). Then I started playing around with some settings. I changed the following:

In System -> Settings -> Advanced Desktop Settings (=ccsm) -> general options -> Dipslay settings:

detect refresh rate OFF
set refresh rate to 200
sync to vblank OFF
detect outputs OFF

in System -> Preferences -> Nvidia X Server Settings (=nvidia-settings) -> X server Xvideo settings:

Both sync to vblank OFF


After this reboot (not sure if it's really needed)

start a movie with the command:

```

mplayer -vo xv movie_with_tearing.avi

```

Or just use something like SMPlayer with the output driver set to xv

These steps resolved my video tearing problem. I also have a Geforce 7300.

Hope this helps!

---

### Post by lovinglinux on 2008-10-16
> **CazperII said:**
> I had the exact same thing until the recent kernel updates with nvidia-glx update (2.6.24-21). Then I started playing around with some settings. I changed the following:

In System -> Settings -> Advanced Desktop Settings (=ccsm) -> general options -> Dipslay settings:

detect refresh rate OFF
set refresh rate to 200
sync to vblank OFF
detect outputs OFF

in System -> Preferences -> Nvidia X Server Settings (=nvidia-settings) -> X server Xvideo settings:

Both sync to vblank OFF


After this reboot (not sure if it's really needed)

start a movie with the command:

```

mplayer -vo xv movie_with_tearing.avi

```

Or just use something like SMPlayer with the output driver set to xv

These steps resolved my video tearing problem. I also have a Geforce 7300.

Hope this helps!

Thank you. It helps, but not entirely. I was afraid to raise the refresh rate to 200, so I'm using 75. Is it safe to use 200 with a LCD monitor?

---

### Post by BMWDriver on 2008-10-17
Refresh rate of an LCD is not measured in Hz, but in microseconds. So 60Hz will not affect video playback. Refresh rates really only concern CRT monitors (the big fat monitors of old). However, the 60Hz is there because LCD screens must co-exist with CRT in the market of today; see it as a compromise. So don't go to 200, it may not do good to the LCD.

The video playback has to do with the graphics drivers enabling the video card chip to kick in and give you that nice playback.

For example, I had to give a configuring command to my ATI card to enable 2D video acceleration. And first I had to install the ATI drivers properly, which required a lot of searching.

So, you'll have to find the drivers for your card and find instructions on how to enable 2D acceleration in order to take advantage of your respective video cards capabilities. But, it may also be that there is a solution for the default drivers installed by Ubuntu (GLX, Mesa...)

As far as ATI goes, this site was great : [http://wiki.cchtml.com/]("http://wiki.cchtml.com/")

---

### Post by CazperII on 2008-10-17
The refresh rate in CCSM has nothing to do with the refresh rate of the monitor whether it be a CRT or LCD. The refresh rate in CCSM is the OpenGL refresh rate in Compiz. It does NOT change the Xorg frequency.

---

### Post by lovinglinux on 2008-11-02
Today I tested Mandriva 2009 live CD with gnome-mplayer and the videos are perfect on my system, even with compiz enabled. No tearing. I don't want to use another distro, but I want to fix this issue on Ubuntu. Any idea why this is happening with Ubuntu and not Mandriva?

---

### Post by GZ Expat on 2008-11-02
I didn't have this problem with 8.04, but am now having this when I upgraded to 8.10.  Odd.  I use VLC and I have tried a variety of settings in VLC, along with changing my screen resolution to 60hz...a bit better, but not resolved.

---

### Post by marcelofontenele on 2008-11-02
medic2000 tip works real great here. Change from 50Hz to 75Hz and i can watch dvds perfectly now! Thanks

---

### Post by caish5 on 2008-11-02
I just installed intrepid and now have this problem with integrated intel graphics. It was ok in hardy so i'm a bit lost as to how ti fix it.

---

### Post by szale9001 on 2008-11-02
I have integrated intel graphics as well (945G/GM). From what I could find, and this is the best way I can explain it, in Hardy when you have xvideo selected (in any player...vlc,totem whatever), video would run through the hardware only, it wasn't composited. Thats why when I would move the video player around or 3d flip through open windows, the video was never part of the effects and you would see blue or whatever. It was like compiz didnt even know the video existed. Now in Intrepid for whatever reason (maybe the new X version), the video is ALWAYS composited. Even if I change my default video settings to xvideo, it is still composited. So I get really bad tearing while watching videos. I have tried everything and there doesnt seem to be a fix. The 2.5 intel linux driver released was *supposed* to fix this issue but it fell through. I guess the only workaround possible is the find a way to "uncomposite" video, if thats even possible with intrepid.

---

### Post by jimminy_cricket on 2008-11-02
Possibly relevant, possibly not.  Haven't tested it yet but this thread: [http://ubuntuforums.org/showthread.php?t=964912&page=2](http://ubuntuforums.org/showthread.php?t=964912&page=2) may work for some.

---

### Post by caish5 on 2008-11-04
No help there with the intel graphics. This is a serious regression i'm gonna go look for a bug report.

---

### Post by lovinglinux on 2008-11-09
I finally solved the problem on my machine by enabling "Unredirect Fullscreen Windows" under CCSM General options:popcorn:

---

### Post by fyo on 2008-11-11
> **lovinglinux said:**
> Thank you. It helps, but not entirely. I was afraid to raise the refresh rate to 200, so I'm using 75. Is it safe to use 200 with a LCD monitor?

For users with NVIDIA cards, using nvidia-settings and CompizConfigSettingsManager to ENABLE vsync should do the trick.

Raising the refresh rate will only simulate the effect and might be a stop-gap solution for users who are unable to properly enable vsync (which may require setting it in both the driver and ccsm).

Note that vsync appears twice in nvidia-settings. Once for OpenGL and once for XVIDEO. Enable them both.

---

### Post by caish5 on 2008-11-12
There is a workaround at...
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/278318](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/278318)

If you install the debs linked there and add
        Option "TexturedVideo" "false"
to your xorg.conf inthe device section, there is no more tearing.

---

### Post by lovinglinux on 2008-11-12
> **lovinglinux said:**
> I finally solved the problem on my machine by enabling "Unredirect Fullscreen Windows" under CCSM General options:popcorn:

The fix above wasn't very stable. Sometimes it worked, sometimes not.

Now it seems to be solved by setting the Device in gstreamer-settings to "NV05 Video Blitter".

---

### Post by guardian_de on 2008-11-15
I have the same problem with tearing on my Mac Mini with integrated Intel 945GM graphics chipset too. I'm not running Compiz so it's not related to compositing. And it's obviously an Intrepid regression as I didn't have problems under Hardy.

Any solutions yet?

---

### Post by Berduchwal on 2008-11-15
I am having the same issue on Mobile Intel Graphics Media Accelerator X3100 in addition to video after upgrade games no longer work.

I have to say this is bit rubbish as it was working very well both for video and games - it does not surprise me why Windows is still dominating player as even people that already use Ubuntu run into such basic issues after system upgrade..

---

### Post by Kellobyte on 2008-11-15
I have a laptop with a ati x1400 video card.
All the movies worked fine in 8.04
All the movies work fine in 8.10 when im in fullscreen.
But when its just large non-fullscreen i get the vertical flickering.
Is there an ATI user out there who has fixed this.

Also i've never used "Envy" can anyone else vouch for it?

---

### Post by L815 on 2008-11-15
The bug was listed under launchpad 2 days ago (intel video tearing). It had been assigned to someone with high priority.

Today, I don't see it there. Maybe it has been fixed?

---

### Post by Berduchwal on 2008-11-15
Envy did not do any good for me as I needed to reconfigure graphic after I tried it. So would not recommend!

I also tried: > There is a workaround at...
[https://bugs.launchpad.net/ubuntu/+s...el/+bug/278318](https://bugs.launchpad.net/ubuntu/+s...el/+bug/278318)

If you install the debs linked there and add
Option "TexturedVideo" "false"
to your xorg.conf inthe device section, there is no more tearing.

No difference

---

### Post by clevercasey on 2008-11-17
I am also having this issue with video on 8.10 with an Intel 945gm none of the fixes offered so far in this thread have done anything for me yet.

---

### Post by Kellobyte on 2008-11-18
FOUND FIX!!!!!!
run in terminal
gstreamer-properties
select video tab
change plugin to "x window system (no XV)"

---

### Post by Berduchwal on 2008-11-18
Thanks!
this was good advise but only reduced the effect by 50-60% it is still present.

---

### Post by lovinglinux on 2009-06-20
Are you still having this issue on Jaunty? I don't have it anymore. ;)

It seems that they fixed this on Jaunty and new threads about this issue stopped being posted as regular as it was. Jaunty most common issue seems to be flash choppiness, but this is subject for [another thread](http://ubuntuforums.org/showthread.php?t=1146943).

---

### Post by micdhack on 2010-05-01
Did anybody had any updates about the issue.
I have lucid installed and the problem still persists. I have an nvidia card but i don't think it matters what kind of card you have.
Its compiz's problem and so far whatever i tried from this thread it didnt work.

---

### Post by cmx on 2010-05-19
> **micdhack said:**
> Did anybody had any updates about the issue.
I have lucid installed and the problem still persists. I have an nvidia card but i don't think it matters what kind of card you have.
Its compiz's problem and so far whatever i tried from this thread it didnt work.
i solve that using tips from this thread.
so,you need to do next things:
1.go to nvidia control panel and check **sync to vblank** in both Xserver XVideo settings and OpenGl settings
2.in preferenses=>compizconfig setings manager=>general options check "sycn to vblank" too

it works in karmic,post about lynx.
good luck.

*sorry no nedd for cheking "unredirect fullscreen' in ccsm*

---

### Post by dracumere on 2010-12-04
Oki kinda late to reply to this thread but ....it seems to work m8s.

---

### Post by jleemcmahan on 2010-12-31
My flash videos flicker (MSNBC.com in particular), and I cannot figure out what to do to fix it. I have tried the above steps. I have a GeForce 9500GT card, plugged into an M4A78LT-M LE motherboard, with an AMD Athlon II X2 (2.9ghz), with 2 GB DDR3. I have the nVidia driver installed, and I installed Compizconfig.

When I turn on Sync to Vblank in the nvidia control GUI, I observe no change at all. When I turn it on in Compizconfig, video becomes choppy and the sound doesn't sync correctly---AND the flickering remains. I am considering formatting and installing XP Pro; I hate Flash video in general, but this an HT/media PC. Without solid handling of flash video it might as well be made of cheese.

EDIT: Oh, one more thing. This problem is evident only when the video is being viewed fullscreen. The flicker doesn't occur when the video is played back at its native resolution. The syncing problems which are observed when I activate sync to vblank, however, occur in both native and fullscreen playback.

---

### Post by jleemcmahan on 2010-12-31
Okay, I went [here]("http://www.webgapps.org/flash/optimization"), and I overrode GPU validation, and now fullscreen performance is excellent. This is with all the sync to vblank boxes UNchecked. However, now the native playback is choppy. Lucky for me, that doesn't matter given that I always watch in fullscreen on this PC.

That's that.

---

