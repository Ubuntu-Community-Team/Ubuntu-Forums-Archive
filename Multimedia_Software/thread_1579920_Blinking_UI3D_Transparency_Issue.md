---
title: "Blinking UI/3D Transparency Issue"
date: 2010-09-22
forum: Multimedia Software
---

### Post by Serja Daeva on 2010-09-22
I've been trying to use Google to solve this one, but at this point I'm stumped and the people on #Radeon haven't been able to help me, so I thought I'd try here, see if many anyone had a solution or knew if one was being worked on.

I've got a system with the following specs:

Acer Aspire 5672WLMi
Intel Core Duo T2300 1.66 GHz ( Dual-Core )
2 GB DDR II SDRAM
ATI Mobility Radeon X1400 128 MB
Ubuntu 10.04 LTS

I'm using the R300 drivers that I got from the two following respositories:

[xorg-edgers fresh X crack]("https://launchpad.net/~xorg-edgers/+archive/ppa")
[Radeon gallium - mesa testing]("https://launchpad.net/~xorg-edgers/+archive/radeon")

3D rendering does work. The issue I am having is that with certain games there is a blinking effect that will occur either at some points or the entire time. The two games I have tried and seen this in are Lord of the Rings Online and EVE Online.

Lord of the Rings Online only seems to be affected by the issue part of the time. The UI will blink in and out for a few seconds then stabilize, typically when I am interacting with a dialog box that has transparency, such as the chat pane or quest dialogs. Sometimes it also happens when I am using the mouse to move or look.

With EVE Online the flashing UI is continual, though it may stabilize in parts when certain windows are open, but for the most part the UI is flashing in and out, all though I can still interact with it, assuming I can figure out where to put my cursor.

[IMG]http://i56.tinypic.com/1z4dh00.jpg[/IMG]

[IMG]http://i54.tinypic.com/1y5vf9.jpg[/IMG]

It's hard to capture the UI when it isn't flashed out because the transparent panes blink in and out so rapidly, but I hope the screenshot gives some indicator as to the problem.

I also get the message "The kernel rejected CS, see dmesg for more information". I'm running 2.6.32-24-generic, which was the latest offered to me when Ubuntu updated, but I'm unsure if that is the kernel it is talking about.

That's all the debugging info I have so far. If anyone can tell me where to look for more, or what I might try to troubleshoot this, I'd be more than happy to attempt it.

EDIT:

I updated to the v2.6.36-rc5-maverick kernel and now EVE Online works without blinking, but LotRO crashes to desktop with no error log. Erk. Trying to see if I can resolve that. >.>

---

### Post by Ghost|BTFH on 2010-09-23
Suggestion - I've seen issues like this before where people are playing 3D intensive games with compiz running on the desktop.  If you have the fancy effects turned on, turn them off.

System - Preferences - Appearance

Visual Effects tab - click on the None box.

If this doesn't resolve the issue, or the effects are not turned on at all, then I would consider the drivers to be the source of the problem.  As I'm not an expert with ATi in ubuntu, I would suggest doing a search for best drivers for your setup.

Hope this helps.

Cheers,
Ghost|BTFH

---

### Post by Dimath on 2010-11-08
Serja Daeva,

The fact that you managed to run LOTRO with Radeon Gallium (without fglrx) is just amazing. I'm trying to do the same and I would really appreciate if you could help me here.

Following the same guide, I added two repositories:
```

deb http://ppa.launchpad.net/xorg-edgers/radeon/ubuntu maverick main 
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu maverick main

```
and then I did
```

sudo apt-get update
sudo apt-get upgrade
sudo reboot

```

What am I missing? Do I need to install/configure anything else?

When I start the game I just always have a black screen with the error on background: "Hardware textures compression support was not detected. This video card feature is required to run the game. [129]"[/B]

My system is almost the same as yours:
```

Acer Aspire 5670
ATI Mobility Radeon X1400 128 MB
Ubuntu 10.10 Maverick
2.6.35-22-generic kernel

```

```

glxinfo | grep OpenGL
OpenGL vendor string: X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on RV515
OpenGL version string: 2.1 Mesa 7.10-devel
OpenGL shading language version string: 1.20
OpenGL extensions:

```

Please, help! Thanks a lot in advance!!

---

### Post by Serja Daeva on 2010-11-09
I recall getting the same error when I first tried to launch the game. If I recall correctly you need to use a script called Winetricks to get the Direct X 9 package installed, which will allow the graphics to decompress.

Also, LOTRO didn't run in the RC5 of Maverick for me. I have to run it using the older Lucid kernel. It might run with the released version, but I'm using 10.04 LTS right now and likely won't upgrade from that for a while. I haven't updated my Gallium drivers in a bit, so I can't say for sure whether they run better or worse when at the latest, though I do tend to try and keep them up to date.

I hope that solves your problem. If not, let me know and I'll boot over into Ubuntu and poke at my settings some more instead of trying to recall them from memory. XD

- Serja

P.S. EVE ran much cleaner (ie, without phasing) in the RC5 Maverick kernel, but then LOTRO didn't run. I'm sincerely hoping I'm not going to have to play musical kernels just to run various programs, but that's the life of a world that refuses to develop Linux support as anything beyond a "if you can get it to work, great!" attitude...

---

### Post by Dimath on 2010-11-09
I installed DirectX
```

export WINEPREFIX=/home/me/.wine-lotro
winetricks d3dx9

```
but that didn't help :( 

I was almost sure the game can not run without ATI fglrx driver, but you had it working! It seems to me that this is the driver issue, can I check somehow that I installed the r300g driver correctly? 

This is my lspci output:
```

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400 (prog-if 00 [VGA controller])
       Subsystem: Acer Incorporated [ALI] Device 0094
       Flags: bus master, fast devsel, latency 0, IRQ 45
       Memory at d0000000 (32-bit, prefetchable) [size=128M]
       I/O ports at 2000 [size=256]
       Memory at c8100000 (32-bit, non-prefetchable) [size=64K]
       [virtual] Expansion ROM at c8120000 [disabled] [size=128K]
       Capabilities: [50] Power Management version 2
       Capabilities: [58] Express Legacy Endpoint, MSI 00
       Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit+
       Kernel driver in use: radeon
       Kernel modules: radeon

```

Can it really be specific kernel/driver dependent? I probably can try to reproduce yours exact configuration, if nothing else works.

---

### Post by Dimath on 2010-11-10
Ok, I've got it!
I think I spend like s couple of years trying to solve it :)

So, to get the hardware texture compression to work you need the S3 Texture Compression (S3TC) library libtxc-dxtn0.so

The project web-site is down [http://homepage.hispeed.ch/rscheidegger/dri_experimental/s3tc_index.html]("http://homepage.hispeed.ch/rscheidegger/dri_experimental/s3tc_index.html")

but, a packaged deb is available here:

[http://debian-multimedia.org/dists/unstable/main/binary-i386/package/libtxc-dxtn0.php](http://debian-multimedia.org/dists/unstable/main/binary-i386/package/libtxc-dxtn0.php)

It works for me now.

---

### Post by Serja Daeva on 2010-11-16
I knew there was some package I was missing but I was wracking my brains trying to recall what it was. I'm glad you were able to use some Googlefu to find it. Now that I name it I remember having a hard time finding it myself due to it no longer being maintained, but still vital to running some 3D games. Hopefully someone will pick it back up or at least make it more readily accessible.

Glad you got it working. :D I hope it doesn't flicker for you like it did for me. I've still gotta wipe and reinstall my Ubuntu since it's gotten cluttered with all my mucking about trying various things and experiments and not being very neat behind myself. :P

Winetricks needs to be a little neater behind itself, but that's a whole 'nother ball of wax.

Happy gaming!

---

### Post by JitseDW on 2010-11-30
> **Dimath said:**
> Ok, I've got it!
I think I spend like s couple of years trying to solve it :)

So, to get the hardware texture compression to work you need the S3 Texture Compression (S3TC) library libtxc-dxtn0.so

The project web-site is down [http://homepage.hispeed.ch/rscheidegger/dri_experimental/s3tc_index.html](http://homepage.hispeed.ch/rscheidegger/dri_experimental/s3tc_index.html)

but, a packaged deb is available here:

[http://debian-multimedia.org/dists/unstable/main/binary-i386/package/libtxc-dxtn0.php](http://debian-multimedia.org/dists/unstable/main/binary-i386/package/libtxc-dxtn0.php)

It works for me now.
Hey Dimath, can I ask how you got this working so easily? I installed the libtxc_dxtn library for 64-bit, but it doesn't seem to change anything. Is there something I have to configure or change first? LotRO is still telling me texture compression is not supported, and when I enforce it using driconf it gives me grey screens, clearly without textures at all.

---

### Post by Dimath on 2010-11-30
> **JitseDW said:**
> Hey Dimath, can I ask how you got this working so easily? I installed the libtxc_dxtn library for 64-bit, but it doesn't seem to change anything. Is there something I have to configure or change first? LotRO is still telling me texture compression is not supported, and when I enforce it using driconf it gives me grey screens, clearly without textures at all.

Hmm... Let me think.
I had a clean install of Ubuntu Maverick 10.10
I've installed latest Radeon Gallium driver from the repository, as I described above. And I installed the libtxc-dxtn0.so from the package. I thought the error message was gone for me after that. What is the error message you have, btw?

For the game itself, I followed the [winehq]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=19108") installation guide. I also had to install winetricks d3dx9. And I have latest Wine 1.3 as well.

I also was not sure what I need from xorg-edgers repository so I ended up installing pretty much almost everything from there :) 

I don't remember doing any configuration. I wish I could help more. I can try to remove everything I installed step by step and to see what matters, but that's a lot of work.

---

### Post by JitseDW on 2010-11-30
> **Dimath said:**
> Hmm... Let me think.
I had a clean install of Ubuntu Maverick 10.10
I've installed latest Radeon Gallium driver from the repository, as I described above. And I installed the libtxc-dxtn0.so from the package. I thought the error message was gone for me after that. What is the error message you have, btw?

For the game itself, I followed the [winehq]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=19108") installation guide. I also had to install winetricks d3dx9. And I have latest Wine 1.3 as well.

I also was not sure what I need from xorg-edgers repository so I ended up installing pretty much almost everything from there :) 

I don't remember doing any configuration. I wish I could help more. I can try to remove everything I installed step by step and to see what matters, but that's a lot of work.
"Hardware textures compression support was not detected. This video card feature is required to run the game.", same one as you. Working around that error just gives me grey screens in-game, apart from the UI.

I have wine 1.3.8 as well, didn't use winetricks for d3dx9, instead just copied the d3dx9_36.dll to the lotro directory, which worked perfectly with the proprietary ATI driver.

Didn't get anything from xorg-edgers. Someone on the IRC channel told me texture compression is simply not yet supported by libtxc_dxtn for r600 cards and above. Seeing as I have an ATI HD 4870, which is a r700 (I think), this situation is hopeless for me I guess. I'll just have to stick with the proprietary one and try to get my performance up.

---

### Post by Dimath on 2010-11-30
> **JitseDW said:**
> "Hardware textures compression support was not detected. This video card feature is required to run the game.", same one as you. Working around that error just gives me grey screens in-game, apart from the UI.

I have wine 1.3.8 as well, didn't use winetricks for d3dx9, instead just copied the d3dx9_36.dll to the lotro directory, which worked perfectly with the proprietary ATI driver.

Didn't get anything from xorg-edgers. Someone on the IRC channel told me texture compression is simply not yet supported by libtxc_dxtn for r600 cards and above. Seeing as I have an ATI HD 4870, which is a r700 (I think), this situation is hopeless for me I guess. I'll just have to stick with the proprietary one and try to get my performance up.

This makes sense. Although, I'm not sure if libtxc_dxtn is not an abandoned project.
Also, I think this is a good description of the situation with S3TC and MESA
[http://dri.freedesktop.org/wiki/S3TC]("http://dri.freedesktop.org/wiki/S3TC")

---

