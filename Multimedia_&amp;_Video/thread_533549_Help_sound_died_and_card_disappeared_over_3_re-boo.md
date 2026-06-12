---
title: "Help sound died and card disappeared over 3 re-boots"
date: 2007-08-24
forum: Multimedia &amp; Video
---

### Post by defec8ing on 2007-08-24
Help!

I'm using a Sony Vaio VGN-FJ1S laptop. 

 I was watching a film last night. Turned on my computer this morning and I had no sound on either the Alsa or other volume controller.  I re-boot.  Now all I have is an Alsa controller saying PCM (I think that was it...).  I re-boot.  Now all I get is the message:  
[SIZE="3"][COLOR="Red"]
"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured."[/COLOR][/SIZE]


 SO I've been searching around on here for a solution, however most of them tell me to go to system>administration>device manager,  but would you believe it-  that has disappeared too!?

What can I do?

---

### Post by fredj on 2007-08-24
I don't have a System->Aministration->Device Manager either so I wouldn't worry about that.
It seems that sometimes your PC soundcard isn't detected at boot up.
Do you know the name of the soundchip used in your PC? If not open a terminal and type
sudo cat /proc/asound/card0/codec\#*
The first line of output from this should give you the name of the soundchip. Then search for
other posts concerning problems with this soundchip.

---

### Post by defec8ing on 2007-08-24
I tried what you suggested and all I got was this:

:~$ sudo cat /proc/asound/card0/codec\#*
cat: /proc/asound/card0/codec#*: No such file or directory

---

### Post by defec8ing on 2007-08-24
when I type lspci -v

I get this:

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
        Subsystem: Sony Corporation Unknown device 81f1
        Flags: bus master, fast devsel, latency 0, IRQ 3
        Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

---

### Post by defec8ing on 2007-08-24
Also when trying to follow the soundcard issues faq, I get stuck at this point:

:~$ sudo modprobe snd-intel8x0
WARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/core/snd-page-alloc.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/core/snd.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/core/snd-timer.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/core/snd-pcm.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko': No such file or directory
FATAL: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/pci/snd-intel8x0.ko': No such file or directory

---

### Post by defec8ing on 2007-08-24
Fixed:

I unpluged the power and removed the battery- now all sound works as it used to.... is this some kind of bug?

---

