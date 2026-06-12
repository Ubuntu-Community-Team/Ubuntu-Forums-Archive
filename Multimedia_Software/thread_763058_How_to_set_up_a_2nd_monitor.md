---
title: "How to set up a 2nd monitor?"
date: 2008-04-22
forum: Multimedia Software
---

### Post by bharkins on 2008-04-22
What is the process for running a 2nd monitor with 8.04? The process is straightforward in Vista in  a window. Is there any similar procedure or, what are the commands?

---

### Post by famous3warriors on 2008-04-22
in terminal use sudo nvidia-settings and that should get you to where you need to set up dual monitor. or you could use gksu displayconfig-gtk using the alt+f2 and that should help also.

---

### Post by theacoustician on 2008-04-22
You can install the nVidia control panel (a GUI) from Synaptic.  From there you can configure your displays.  Very easy to use.  I'm fairly certain that ATi is the same general deal, but I don't have a desktop that has dual monitors on an ATi card.

---

### Post by bharkins on 2008-04-24
> **famous3warriors said:**
> in terminal use sudo nvidia-settings and that should get you to where you need to set up dual monitor. or you could use gksu displayconfig-gtk using the alt+f2 and that should help also.

I used nvidia-settings and got partial operation. I can get the image displayed on either the 2nd or laptop screen. The 2nd monitor is using my Samsung HDTV, which works fine with Vista. I can set the resolutions on both screens from the settings, but the background stretches across both monitors. What I want is exact duplicates of both screen with proper aspect ratio.

On one of the configuration setups, an error showed:

"Failed to get MetaMode (1) 'CRT-0 1920x1080@1920x1080 +0 +0 DFP-0: nvidia-auto-select@1680x1050+ 1920 +0 (mode 3600x1050, id51)' on screen 0" 

There's a lot of information there, but what to do with it? I have not directly edited the xorg.conf file yet, as it appears that is supposed to happen through the settings screen. Any assist greatly appreciated.

---

### Post by theacoustician on 2008-04-28
> **bharkins said:**
> I used nvidia-settings and got partial operation. I can get the image displayed on either the 2nd or laptop screen. The 2nd monitor is using my Samsung HDTV, which works fine with Vista. I can set the resolutions on both screens from the settings, but the background stretches across both monitors. What I want is exact duplicates of both screen with proper aspect ratio.

On one of the configuration setups, an error showed:

"Failed to get MetaMode (1) 'CRT-0 1920x1080@1920x1080 +0 +0 DFP-0: nvidia-auto-select@1680x1050+ 1920 +0 (mode 3600x1050, id51)' on screen 0" 

There's a lot of information there, but what to do with it? I have not directly edited the xorg.conf file yet, as it appears that is supposed to happen through the settings screen. Any assist greatly appreciated.It looks like you're having a problem with you computer being able to read the EDID code from the TV.  Is it a CRT?  Even if it isn't, if you can't get a valid EDID, you'll probably have to edit your xorg.conf file manually.

---

### Post by bharkins on 2008-04-29
> **theacoustician said:**
> It looks like you're having a problem with you computer being able to read the EDID code from the TV.  Is it a CRT?  Even if it isn't, if you can't get a valid EDID, you'll probably have to edit your xorg.conf file manually.

Agreed, I'm working on that. There is an interesting long Forum tutorial (thread #85769) regarding dual monitors but it goes back to 2006. While xorg.conf is in all distros I assume, mine in Hardy 8.04LTS is very short without the long detail options, etc. In the Device, Monitor and Screen section, it states "Configured Video Device, and Monitor" with no further information about resolution, etc. Is there new updates about editing xorg.conf for dual monitors using Hardy or Gutsy?

I am using HP notebook computer and the 2nd monitor is a Samsung HDTV which works fine in Vista. Any inputs greatly appreciated.

---

### Post by richardson_beach on 2008-06-14
[I]I have a Dell Inspiron 5100, ATI 7500 card with a second Princeton monitor.  The standard 8.04 install detected both properly and both display properly.

I want to enable dual monitor, not twin, capability, however, and haven't been able to do that.  The fglrx driver is apparently not applicable to the 7500, so I'm looking for assistance in proceeding forward.

Cheers,


 [/I]

---

