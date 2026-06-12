---
title: "Intel Integrated Graphics Controller (GM965/GL960)"
date: 2008-11-07
forum: Multimedia Software
---

### Post by dazift on 2008-11-07
I have a compaq presario c700 running hardy and i want to know if i have my drivers set up right and if i dont what i need to do to get it working correctly. I have compiz running and it works good but some of the effects, like water, dont run correctly or quickly so im guessing something is wrong with my graphics drivers.

lspci returns:
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

and in /etc/X11/xorg.conf:
Section "Device"
Identifier	"Configured Video Device"
EndSection

in proprietary drivers i have a driver called "wl" and it is enabled

any help would be appreciated, thank you.

---

### Post by Open-SuSe-A-Me on 2008-11-07
i posted a similar problem last night.  the water effect has never worked with my intel 965, i have only got it to work on my desktop which has a newer nvidia card, so i think our cards just cant handle that effect.

the reason i posted was because of video tearing even with compiz fully uninstalled.

xorg is no help anymore so i cant figure out why my card is not being setup properly automatically when it works fine with hardy.

---

### Post by spoons on 2008-11-07
The card is capable of OpenGL 2 so if it isn't working I suspect the drivers are not implementing certain things.

---

### Post by verevi on 2008-11-13
I have a similar question to the OP.  His xorg.conf does not mention the intel driver.  How do we know that the intel driver is in use?

---

### Post by CJay554 on 2008-12-11
Bump.
I have an Acer 6920 with the same card:
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrat
ed Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Grap
hics Controller (rev 03)


Cedega display an "Fail" on my 3D rendering test after installation, I'm wondering if theres any driver that can work fully on this system?

---

### Post by ergin on 2008-12-18
I have installed 8,10 recently but could not find driver for this graphics controller. Is it available and how do I get it? Thanks.

---

### Post by Conzar on 2008-12-23
Bump, I have a GM965 as well on my Macbook running Ubuntu 8.10. I am a gentoo user so ubuntu is very new to me.  

I've never seen an xorg.conf file that has pretty much nothing in it.  How do I change the driver to i810?

---

### Post by densou on 2009-01-04
many users encountered a failed login or unstable system switching from intel to i810 with Intrepid and i915....

Intrepid works better with a generic xorg.conf (it detected my outdated CRT !! Feisty, Gusty and Hard were never able to do it and I set manually the default resolution I liked with xrandr)

[http://spazioinwind.libero.it/densou/xorg.conf.new](http://spazioinwind.libero.it/densou/xorg.conf.new)
(right-click / save target as)

Canonical doesn't provide newer version of Intel video driver although you'd switch to Jaunty (recommended to developers or avanced users)
However you can find stable backports here:
[https://edge.launchpad.net/~intel-gfx-testing/+archive](https://edge.launchpad.net/~intel-gfx-testing/+archive)
just add those 2 lines to /etc/apt/sources.list :D

---

### Post by jspudz on 2009-01-05
Well add me to this list also. I have a dell inspiron 1525 with a GM965/GL960 and my graphics card is not detected. Basically my xorg.conf is pretty much blank, and it does not list my X3100 intel card. It has the following:

Section "Device"
Identifier "Configured Video Device"
EndSection

Everything seems to "pretty" much work, but my fonts are blurry and not crisp and smooth. 

Has anyone found a solution to this???? Or can point me to some specfic directions on how to get/compile the correct drivers?

---

### Post by jspudz on 2009-01-07
Not sure if anyone is following this thread or not, but this issue has been driving me crazy. I have an Dell inspiron 1525 and have had serious issues getting my video card working properly. Turns out alot of other people have too.  As of right now it looks like this issue is affecting alot of people that use (of all video cards!) intel based chipsets. 

This has been noted and is being tracked here:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/252094](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/252094)

I hope others will find this useful and also speak up to help escalate this issue to the fine folks at ubuntu for a fix.

---

### Post by densou on 2009-01-12
> **jspudz said:**
> Has anyone found a solution to this???? Or can point me to some specfic directions on how to get/compile the correct drivers?

self-quoting, nowadays X3100 uses i965/dri modules (not i915/dri) so you should not expect the same results I had with my gma950 (i915). However it's worth a try, agree ? :popcorn:

> **densou said:**
> [http://spazioinwind.libero.it/densou/xorg.conf.new](http://spazioinwind.libero.it/densou/xorg.conf.new)

[https://edge.launchpad.net/~intel-gfx-testing/+archive](https://edge.launchpad.net/~intel-gfx-testing/+archive)
just add those 2 lines to /etc/apt/sources.list :D

---

### Post by mayank.abhishek on 2009-01-18
Hi!

I just installed a game Savage 2 ([http://savage2.s2games.com/](http://savage2.s2games.com/)) on Ubuntu 8.10 64bit version. But, when I try to run it I get an error message,

> Savage2 - Fatal Error: OpenGL 2.1 not available.
Savage2 - Fatal Error: Segmentation Fault

Segmentation fault


glxinfo | grep "OpenGL"
displays

> OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 965GM 20061102
OpenGL version string: 1.4 Mesa 7.2
OpenGL extensions:
What do I do? Does my graphics card not support OpenGL 2.1?

I asked for help on the game's forum and I was told that Mesa is software-acceleration and I need to get the correct drivers for my graphics card. 

Now how and where do I get the drivers? System>Administration>Hardware Drivers shows nothing.

sudo lshw -C display

shows

>   *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
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
       capabilities: pm bus_master cap_list
       configuration: latency=0


Please Help!!

---

### Post by densou on 2009-01-20
> **mayank.abhishek said:**
> Please Help!!

hi, lad
first I'd suggest to paste here your xorg.conf
X3100 supports OpenGL 2.1 if I guess right....(anyway 100% sure on OGL 2.0)

Intel has the lead among 3d Chipset sold, however I still consider their usability a sadly mess on GNU/Linux (how unfortunate)

Obtain the latest version for Intrepid adding these lines:
```
deb http://ppa.launchpad.net/intel-gfx-testing/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/intel-gfx-testing/ppa/ubuntu intrepid main

```
to your */etc/apt/sources.list* and then do a *apt-get update*, Synaptic should notify you the new stuff to install ;)

---

