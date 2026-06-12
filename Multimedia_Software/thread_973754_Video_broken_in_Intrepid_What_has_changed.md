---
title: "Video broken in Intrepid? What has changed?"
date: 2008-11-07
forum: Multimedia Software
---

### Post by Open-SuSe-A-Me on 2008-11-07
hello

i have an integrated intel 965 graphics card and video will not play right as it did in hardy. this is true with or without compiz enabled and even with compiz completely uninstalled. the video flickers/tears like crazy.

most of the fixes on the forums talk about not using compiz. i thought the intel drivers were supposed to be very linux friendly and video works flawlessly on hardy right out of the box. there must be something terribly wrong here.

i have found one temporary fix - alt+F2 gstreamer-properties and selecting "Video Overlay". this makes video play fine in Totem but i hate totem and while this setting is on my screen will flicker alot. VLC and Mplayer flicker on every video output setting. i also notice slight flickering when a gksu prompt opens for example.  maybe the new "auto-xorg" isnt configuring my card properly.

i really like the improvements in intrepid (ubuntu now works with my laptop brightness buttons) and i would like not to downgrade back to hardy.

any help would be great - thanks.

---

### Post by Open-SuSe-A-Me on 2008-11-07
bumpity bump

---

### Post by Open-SuSe-A-Me on 2008-11-07
also i have installed kubuntu 8.10 and i have the same issue

---

### Post by Peter09 on 2008-11-07
Post the output of the code below so that we can see which driver is active.
```
lshw -C display
```

---

### Post by Open-SuSe-A-Me on 2008-11-07
ok this is what i get -

*-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

---

### Post by Peter09 on 2008-11-07
The only success I have had in this one is to boot into recovery mode and do an xfix.

This has occasionally worked.

---

### Post by Open-SuSe-A-Me on 2008-11-07
do you mean the whole

sudo dpkg-reconfigure xserver-xorg thing?

if you dont could you tell me how to do an xfix?

---

### Post by Peter09 on 2008-11-07
Hit the ESC key at the Grub prompt. Use the`arrow keys to move down one line to the recovery kernel. Hit ENTER.

When the menu comes up select xfix.

---

### Post by Peter09 on 2008-11-07
Also check if you have a driver waiting to be enabled.

System->Admin->Hardware and DRivers

---

### Post by dabl on 2008-11-07
As said in the 8.10 release notes, there is a new X.org version:

[http://www.ubuntu.net/getubuntu/releasenotes/810](http://www.ubuntu.net/getubuntu/releasenotes/810)

The old utility dpkg-reconfigure xserver-xorg no longer adjusts the display, only the input devices.

---

### Post by Open-SuSe-A-Me on 2008-11-07
thanks for the help, but the xfix did not work.

the only things in the driver manager are 2 atheros wireless drivers, which are disabled in favor of the compiled madwifi drivers.

i think im just going to use a different distro for awhile.

---

### Post by TropheusJon on 2008-11-07
I'm having the same problem, trying to play avi and mkv files.  The videos keep on blinking with cpu at about 50%.

Hopefully this can be solved soon.  Any suggestions to play the files at this point?  Right now I have to play them on windows.

---

### Post by Open-SuSe-A-Me on 2008-11-07
Dabl - 

I don't understand what you mean.  Ubuntu has always been that good ol' faithful distro, when opensuse would be in RPM hell, or when Debian was so confusing and took 25 googles just to get one thing working, or when Fedora made it difficult to install codecs, ubuntu was there for me.  now i cant even watch videos. is this new Xorg special or something?

---

### Post by TropheusJon on 2008-11-07
Just wondering if anyone is having this problem or had it and solved it.

Thanks!

---

### Post by TropheusJon on 2008-11-08
Bump

---

### Post by javierrivera on 2008-11-10
> **TropheusJon said:**
> Just wondering if anyone is having this problem or had it and solved it.

Thanks!
I'm having it with an ATI card.

The only workaround that I know is disabling compiz or disabling the card video aceleration (ALT+F2, type gstreamer-properties, in the video tab select the No Xv option).

---

### Post by DavidMIRV on 2008-12-04
I am having this same problem myself, I've tried just about everything. The only *fix* is to use the radeon/raedonHD drivers in which you have no OpenGL or 3D acceleration. 

Anybody got a real fix for this yet?

---

### Post by Rasheeke on 2008-12-05
I've got an Intel card and I'm having issues with google earth showing characters (lat. and long.).

Probably some more problems I don't know about too.

---

### Post by jama999 on 2008-12-18
> **javierrivera said:**
> I'm having it with an ATI card.

The only workaround that I know is disabling compiz or disabling the card video aceleration (ALT+F2, type gstreamer-properties, in the video tab select the No Xv option).

Bump - Also having this problem on an Intel GMA - switching the card acceleration off as mentioned above makes all videos unwatchable - even low bandwidth one lose 50% of their frames and processor is <40% while playing.

Anyone got any updates to this?

Cheers

J

---

### Post by JohnRory1971 on 2009-01-06
> 
i have an integrated intel 965 graphics card and video will not play right as it did in hardy. this is true with or without compiz enabled and even with compiz completely uninstalled. the video flickers/tears like crazy.

Has this one been solved because I have Intel integrated GM965/GL960 graphics card as well and am having the same problem? I'm thinking of changing from 8.10 to 8.4 in hope that I won't have this problem

---

### Post by Open-SuSe-A-Me on 2009-01-08
> **JohnRory1971 said:**
> Has this one been solved because I have Intel integrated GM965/GL960 graphics card as well and am having the same problem? I'm thinking of changing from 8.10 to 8.4 in hope that I won't have this problem

Hello again i will share my progress with this issue.  The reason why the tearing occurs is because the new Intel driver uses "Textured Video" which does not work properly with this card.  

I went through the process of patching the driver to force it to use Overlay Video which removes the tearing, but introduces a more serious problem.  About 20% of the time when a video is opened in any player, the screen will turn one (random) color and freeze.  The only way to get it back is to do a hard reboot.  I have tested this on Ubuntu, Arch, and Opensuse all with the same result.  There is also a bug about this on launchpad >>> [https://bugs.launchpad.net/ubuntu/intrepid/+source/xserver-xorg-video-intel/+bug/278318](https://bugs.launchpad.net/ubuntu/intrepid/+source/xserver-xorg-video-intel/+bug/278318)

So i recommend Hardy 8.04 for now if you have this video card.  Hardy works great.

---

### Post by canoe529 on 2009-01-09
I upgraded from kubuntu Hardy to kubuntu Intrepid and have not really been happy. KDE pukes artifacts all over the screen, and 3D is very slow, despite claiming to have DRI enabled. I don't play flash videos very much, though, so I haven't really seen the problem you're talking about. I can watch things on youtube with no problem.
I'm hoping that there is some relief in site with the Intel 965 drivers. Supposedly a new graphics memory manager has been released by Intel which will be included in the next kernel release. I don't know if that will address the textured video problem, but maybe it will make 3D usable. As it is, I can't play any games or run flightgear on my laptop because of it. I know that this doesn't address your problem, but I figured that sharing information about the 965 problems and solutions isn't a bad idea. Good luck with your issues, I hope they get fixed for you. For anyone in general: Stick with Hardy if you have the Intel 965 graphics chip. I will probably end up downgrading to Hardy when I get the chance, right now I'm too busy.

---

