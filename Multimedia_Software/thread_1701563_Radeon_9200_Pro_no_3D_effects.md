---
title: "Radeon 9200 Pro: no 3D effects"
date: 2011-03-06
forum: Multimedia Software
---

### Post by halbbitter on 2011-03-06
Hello,

I have just installed fresh Ubuntu 10.10 on my old desktop, which has ATI Radeon 9200 Pro (RV280) video card.
The card is working, but (as I understand) in very basic mode, without 3D support (no OpenGL). Stellarium not working, same as ExtremeTuxRacer.

As I understand, this card should be well supported by open-source Radeon driver... in this case I would expect it to work out-of-the-box. But it doesn't.
"Additional Drivers" utility shows that there are no compatible proprietary hardware drivers available (which is expected, because this card is no longer supported by ATI/AMD).

What do I do, where should I start? Thanks in advance.

---

### Post by The Flying Penguin on 2011-03-06
Make sure xserver-xorg-video-ati is installed. Search for it in Synaptic Package Manager. Install it if its not already and then reboot. That should do it.

Check out [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) for info regarding the open source driver. If you feel comfortable doing so you can try using the driver from [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) as suggested in the link I gave you. It is going be the default 3d driver in the next Ubuntu release, 11.04.

---

### Post by halbbitter on 2011-03-06
The Flying Penguin: thanks for the response!

I've checked the Synaptic, and yes, xorg-video-ati is installed (as well as xorg-video-radeon). 
How can I check which driver is actually running? The system doesn't have "xorg.conf", so I guess the driver is chosen at runtime.

Regarding the new PPA driver, the page says it is good for "r300-r500 (Radeon 9500 - X2300) cards", so I'm not sure if it can help with my card...

---

### Post by The Flying Penguin on 2011-03-06
To check which driver you are using type ```
sudo lshw -C video
``` into the terminal. It may take a minute for it collect the relevant data. Look for the line that says "configuration: driver=XXX". Instead of XXX the driver being used should be listed. I believe the open source driver is simply listed as "radeon". If you were using the proprietary driver it would say "fglrx".

What driver does it say you are using?

And you are right about the PPA driver. I looked at the list of cards wrong and thought your card was the r350 but its the rs350. I missed the s :(

---

### Post by halbbitter on 2011-03-07
here is the output:

[FONT=Courier New]*-display:0             
       description: VGA compatible controller
       product: RV280 [Radeon 9200 PRO]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-3.0 pm vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=32 mingnt=8
       resources: irq:16 memory:c0000000-c7ffffff ioport:a800(size=256) memory:cfef0000-cfefffff memory:cfec0000-cfedffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV280 [Radeon 9200 PRO] (Secondary)
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 mingnt=8
       resources: memory:b8000000-bfffffff memory:cfee0000-cfeeffff[/FONT]

so it says driver is "radeon". This means, I am mistaken about 3d support not working at all. Rather, it is unstable, and crashes when I try to run the application that requires it:

[FONT=Courier New]user@host:~$ stellarium
using default graphics system specified at build time:  raster 
QProcess: Destroyed while process is still running.
 ------------------------------------------------------- 
[ This is Stellarium 0.10.5 - [http://www.stellarium.org](http://www.stellarium.org) ] 
[ Copyright (C) 2000-2010 Fabien Chereau et al          ] 
 ------------------------------------------------------- 
Writing log file to: "/home/user/.stellarium/log.txt" 
File search paths: 
  0 .  "/home/user/.stellarium" 
  1 .  "/usr/share/stellarium" 
Config file is:  "/home/user/.stellarium/config.ini" 
Qt GL paint engine is:  "OpenGL" 
stellarium: ../../radeon/radeon_cs_gem.c:181: cs_gem_write_reloc: Assertion `boi->space_accounted' failed.
Aborted[/FONT]

---

### Post by The Flying Penguin on 2011-03-08
Does compiz work for you? Make sure you turn it off when running 3d applications as it sometimes prevents them from running properly, especially on older hardware.

Let's test your OpenGL. Paste the following into terminal:
```
LIBGL_DEBUG=verbose glxinfo
```What is the output? Specifically, what does the "OpenGL renderer string" say? It should list your card. If it says "software rasterizer" then you don't have 3d hardware acceleration.

Also, just from briefly searching it seems that a lot of people have problems with Stellarium.

I did find this though: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/481669](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/481669)

The user in post #8 has the same card you do and claims to have fixed the problem.

                 It seems to be an easy fix, assuming it works. EnablePageFlip in xorg.conf seems to have been the culprit for him. Follow his example.

To edit xorg.conf
```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by halbbitter on 2011-03-10
thanks for your help! I tried what you have suggested:

1) I wasn't deliberately running compiz :) Anyway, I have disabled all "Visual Effects" in "Appearance" settings, restarted the X. No change.
2) I don't have xorg.conf (is it because the system runs HAL?). I'm not sure, if I will create the new file, will it be actually used by the system?
3) output of the glxinfo is attached.  This part looks correct:
     OpenGL renderer string: Mesa DRI R200 (RV280 5960) 20090101 x86/MMX+/3DNow!+/SSE TCL DRI2

but the output also contains errors like this:

ibGL: OpenDriver: trying /usr/lib/dri/tls/r200_dri.so
libGL: OpenDriver: trying /usr/lib/dri/r200_dri.so
libGL: Can't open configuration file /etc/drirc: No such file or directory.
libGL: Can't open configuration file /home/user/.drirc: No such file or directory.
libGL: Can't open configuration file /etc/drirc: No such file or directory.
libGL: Can't open configuration file /home/user/.drirc: No such file or director

- whatever it means.

---

### Post by Yellow Pasque on 2011-03-10
Those errors are common. You can install driconf program and run it to make them go away.
For more detailed errors, run compiz-check: [http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

---

### Post by halbbitter on 2011-03-10
Solved!

I have installed the newest X (with drivers) provided by xorg-edgers, following the instructions on this page:
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

Stellarium works, ExtremeTuxRacer works, desktop visual effects work just fine. Wow!

Will see how stable it is.

---

### Post by The Flying Penguin on 2011-03-19
Cool man, good job! Glad you found a fix.

I have a 9250 and an extra machine sitting around but never bothered to mess with it. Now I suddenly feel the desire to go set it up with Ubuntu :p

---

