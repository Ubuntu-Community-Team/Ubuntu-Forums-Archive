---
title: "Radeon card not performing well"
date: 2011-05-12
forum: Multimedia Software
---

### Post by Fabled One on 2011-05-12
Hello all, I have a Radeon HD 5830 card and it just doesn't seem to be working to it's full potential. I've tried TF2 and SC2 through the latest stable release of Wine, but the frame rates are horrible.

Also, when I run fgl_glxgears, I only get 800fps. (If I reboot the computer and run fgl_glxgears as soon as I log in, I get at least 3000fps for a few seconds. Then it's back to 800)

I've tried reinstalling the driver several times.

Why is the performance so low?

Here's my setup:
XFX Radeon 5830
Ubuntu 11.04 (fresh install and updated)
11.5 ATI driver from AMD's site. Here is fglrxinfo output:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 5800 Series  
OpenGL version string: 4.1.10750 Compatibility Profile Context

```

xorg.conf
```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "UseFastTLS" "1"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

### Post by ghostborg on 2011-05-12
I'm not sure if this is what you mean, but for me I was running an on-board HD3200 and had to un-check Sync To VBlank in the OpenGL settings in Compiz Config Settings Manager.
I think I also had to enable Tear free in the ATI catalyst
settings.

---

### Post by Fabled One on 2011-05-12
Well, I don't have Compiz installed and when I enable Tear free in the ATI catalyst, it just limits my fps to my screens refresh rate. (Also, I can't even seem to disable it now :( )

But you reminded me about the motherboard's onboard graphics. My mobo has a built-in 4250.  Maybe that's interfering with my 5830?

Has anyone ever had conflicts with onboard VS dedicated graphics cards?

---

### Post by handy on 2011-05-13
Can you disable the on-board GPU via the machines BIOS?

---

### Post by Fabled One on 2011-05-13
> **handy said:**
> Can you disable the on-board GPU via the machines BIOS?

I just tried that now. There is no difference.  I assume it was using the dedicated card all along. But I still don't see why it's working so poorly.

---

### Post by Naike on 2011-05-13
I had to switch to Kubuntu because GNOME would lag horribly with my 5870.
Like when I move my window or so it would be choppy, or scrolling in firefox.
I tried to tweak stuff in the compiz settings (like the opengl thing) but nothing worked. I ended up getting Kubuntu.

---

### Post by Fabled One on 2011-05-13
> **Naike said:**
> I had to switch to Kubuntu because GNOME would lag horribly with my 5870.
Like when I move my window or so it would be choppy, or scrolling in firefox.
I tried to tweak stuff in the compiz settings (like the opengl thing) but nothing worked. I ended up getting Kubuntu.

Other than low fps in games and fgl_glxgears, regular use seems fine.

The only regular-use problem I have is that videos in VLC and even the fgl_glxgears always show through windows that overlap it.

I don't want to try another install just yet. I really feel like there is a simple setting that I missed, I just have no idea what it is.

---

### Post by Fabled One on 2011-05-22
I tried installing the KDE desktop, but there is no improvement at all.

Is anyone else experiencing terrible performance with ATI cards?

---

### Post by Fabled One on 2011-05-24
I have attached an image of the ATI related packages according to synaptic.

Is this what I need, or do I have too much or not enough? Are any of these packages conflicting with each other?

---

### Post by Fabled One on 2011-06-09
Am I the only one having this problem?

---

### Post by face_mcgace on 2011-08-11
Yes, I'm having these same terrible problems. My card is a Radeon HD 5670 1gb and on all low settings im only getting 10-22 FPS which is terrible (I know my card isn't THAT good, but it should be pumping out more fps than 10 on all low, in windows I was pulling 40 FPS on Ultra settings).

As far as I have gotten, there isn't really a straight answer but maybe I can help you out a bit. On the WineHQ [http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882) there are some tips, most notably:

"Regedit video performance tweaks" where you change settings in the registry (if you need help setting this up feel free to ask).

Also, from what I can tell, it's not the ATI graphic cards that have problems but the ability for Ubuntu to correctly manage the CPU (if you have more than one core, I have a quad-core) and this set boosted my FPS from 10 to 30-ish (still $hit but better than nothing:

the main issue with SC2 is probably the fact that when it runs on multiple core it doesn't fully utilize all the cores, yielding to poor performance. 
We don't know yet if this is an issue in wine implementation of some API or Linux scheduler or something else. 

If in my previous post I suggested to force the CPU speed to MAX in order to overcome this issue, now I have a possibly better solution. 

Basically on multi core CPUs you have to set the 'affinity' of the SC2.exe process to one core only (i.e. even if the game is multithreaded you run all threads on one core). 

I don't know if there's a better way to to this, so I've created a simple utility to setup affinity of processes. 
You can grab it here: 
mynzb.youlink.org/affinity/affinity.cpp 
and a script to use it (once SC2 gets executed start the script and it'll be run only on core 1 - the second core) 
mynzb.youlink.org/affinity/sc2.sh 

In order to use both, first you have to 
- compile affinity: g++ -O2 -o affinity affinity.cpp 
- copy sc2.sh in the same directory 
- execute StarCraft II 
- once SC2 is running, within an open terminal go the sc2.sh directory and type ./sc2.sh ; you should see out put on the terminal itself "Setting SC2 (a number here) affinity to CPU 1" (**Originally posted by Ema**)

Hope that helps, if you find anyway to really fix this keep us informed :) (would love to play on low with at least 60 FPS)

---

### Post by fqowehf on 2011-08-11
They you can kiss the Hard Drive goodbye and get another SATA HDD

---

### Post by sodainmate15 on 2012-01-21
> **Fabled One said:**
> 
Also, when I run fgl_glxgears, I only get 800fps. (If I reboot the computer and run fgl_glxgears as soon as I log in, I get at least 3000fps for a few seconds. Then it's back to 800)


I see the same issue with my Radeon HD 6770. Looks like it's running normally for a while, before something gets initialized and slows it down. I've been digging into it for a few days now, but no luck.

```
~$ fgl_glxgears 
Using GLX_SGIX_pbuffer
11327 frames in 5.0 seconds = 2265.400 FPS
12161 frames in 5.0 seconds = 2432.200 FPS
11760 frames in 5.0 seconds = 2352.000 FPS
11478 frames in 5.0 seconds = 2295.600 FPS
5799 frames in 5.0 seconds = 1159.800 FPS
3451 frames in 5.0 seconds = 690.200 FPS
3390 frames in 5.0 seconds = 678.000 FPS
3450 frames in 5.0 seconds = 690.000 FPS
3443 frames in 5.0 seconds = 688.600 FPS
3367 frames in 5.0 seconds = 673.400 FPS
3496 frames in 5.0 seconds = 699.200 FPS
3375 frames in 5.0 seconds = 675.000 FPS
c3358 frames in 5.0 seconds = 671.600 FPS
```

---

### Post by silverhaze06 on 2012-01-21
I had the same problems until I followed this thread. [http://ubuntuforums.org/showthread.php?t=1857911]("http://ubuntuforums.org/showthread.php?t=1857911")

So I would recommend giving it a shot.

---

