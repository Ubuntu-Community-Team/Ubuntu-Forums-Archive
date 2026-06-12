---
title: "Nvidia GeForce FX 5500 Dual Monitor Setup Problem"
date: 2013-02-17
forum: Multimedia Software
---

### Post by AzTRaveller on 2013-02-17
> **neogeek said:**
> I finally got my dual monitors to work with the Nvidia GeForce FX 5500.

Here is what I did -

- Installed the nvidia-glx-new package and the nvidia settings using the Synaptic Package Manager
- Opened up terminal and typed in sudo /usr/bin/nvidia-settings
- Applied the X screen for both.
- Restarted the computer.

It also solved the problem of the login screen being cut off - I guess it was set to a lower resolution.

Hope this helps.
I've been searching and trying and rebooting for 2 months, now attempting to get my GFX5500 working on 2 monitors.  My CRT-0 also comes up as disabled, if the DFP-0 is plugged in.  Getting tired of "I GOT IT WORKING, THANKS" without any detailed steps (commands used) to succeed.  Went to that link above touting a video of "HOW TO", and found no video link.  I've tried the "splice 2 xorg.conf together and it works, suddenly" instructions, have had log in on a terminal to blow the final "xorg.conf" away to get my screens back, so many times I can scream.  

I'm running nVIDIA driver 173 (as per most of the forums), I'm using 10.04 on my desktop.  The "XSCREEN for Both" is grayed out (as always).  I have finally concluded nVIDIA has a problem with detecting multiple screens (or at least their "tool" does).    
I've heard "xserver" has fixed it for some, but cannot seem to download/find that.

I'm sure there a single line "command" (or several) that will force nVIDIA to "see" the other screen (set screen =2), but where is that "documented in detail"?

I constantly see people stating they have dual, or multiple screens working.  Maybe under a different topic, those people can upload their "xorg.conf" files and detailed command steps they have used to "duplicate" their success, for others, whether it is single card, or multiple cards.  I wouldn't mind getting one of those triple or quad cards, but without proper instructions (detailed examples -- step-by-step-command-instructions) it's simply a waste of everyone's time and money).

Thank you for your support

---

### Post by BicyclerBoy on 2013-02-17
Before you get closed for thread necromancy...

Are you sure those video outputs are independent?

Some of the old cards had more output connections than real ramdacs or actual outputs.

For ex..
- the TV out can be same as the analogue in the DVI-A
- the HDMI out can be one link of a DVI-D
- the VGA out can be linked to DVI-A..


The data I find for FX5500 suggests
VGA                    (2048 x 1536)
DVI-I single link  (1600x1200 max)
S-video..

You may have to stack the monitors in the desktop as top-bottom & not side-by-side..

Try with display resolutions less <=1024 so the max &/or width height of desktop is <=2048.

With both monitors connected..what's in /var/log/Xorg.0.log ?

---

### Post by AzTRaveller on 2013-02-17
This PCI-X model has 1 DVI connector, only.  I have a "Y" cable that splits the DVI to 1 VGA and 1 DVI.  "Famous quote:  It works fine with Windows   ..... ".  I can even use 3 monitors (in Windows), by adding one to the MoBo VGA connector.  

Now I would like to at least make the 5500 work under Linux.  Both monitors are 1440 x 900 & I can get either monitor to work as long as the other isn't connected (on VGA or DVI), but not both.  As was mentioned by the previous poster, with both connected, the CRT-0 is "disabled" when the DVI (DFP-0) is connected.  Again, nVIDIA cannot "see" 2 monitors, even though it can, when either is connected to either connector.  The log file says it cannot find "module nouveau".  As always, I have searched the web and cannot easily find that module (though I could find the typical; let's build it from scratch.  Isn't anything available "ready to install & run in Linux?"  .....).  In using "Add/Remove Programs", it says it's already installed (why am I not surprised)  ......

I know someone is out there that has done this successfully multiple times and is willing to patiently document "how" they did it.

---

### Post by BicyclerBoy on 2013-02-18
Some versions of this card have 3 output connectors..1x DVI-I & 1x VGA.

nouveau is the foss driver for nVidia h/w & is included in *buntu kernel & distro.

The nouveau driver should be blacklisted/blocked by nVidia driver installation.

It is easy enough to force the CRT-0 output on if it is not connected/detected.
/etc/X11/xorg.conf
If file not exist then can create with 
nvidia-xconfig or nvidia-settings
```

Option  "ConnectedMonitor"  "DFP, CRT"

```
Might need this to set primary etc..
```

 Option "UseDisplayDevice" "DFP-0, CRT-0"

```

The CRT will need a monitor section with appropriate H & V freq data for req video mode.
In the CRT screen section prob need:
```

Option "UseEDID" "False"

```
Logout/login & then post the Xorg.0.log file..

---

### Post by QIII on 2013-02-18
Moved to its own thread.

---

