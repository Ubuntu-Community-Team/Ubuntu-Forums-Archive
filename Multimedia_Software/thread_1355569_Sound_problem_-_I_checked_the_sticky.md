---
title: "Sound problem - I checked the sticky"
date: 2009-12-15
forum: Multimedia Software
---

### Post by soundismessed on 2009-12-15
Hi,

My sound won't work in any program.  I tested with System>Administration>System Testing.  Didn't work.

OS: 
Ubuntu 9.10 (karmic)
Kernel Linux 2.6.31-14 generic
GNOME 2.28.1

Hardware:
System testing indicates I have
0 [ICH5           ]: ICH4 - Intel ICH5
                      Intel ICH5 with AD1980 at irq 17

Note: aplay -l indicates 2 entries for above, like this:
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I am trying to use basic stereo headphones and connecting to onboard jacks ( I tried all jacks)

I turned everything up that I could in alsamixer.  There is no bar for "Headphon" (though it's unmuted) but I assume that's irrelevant, even though I'm trying to use headphones.  I think that relates to my CD drive, or some aux connection.

What do people think?  Do you need more information?

Thanks in advance.  And if you help code Ubuntu, you guys seriously rock out with your cocks out.

---

### Post by lidex on 2009-12-15
I'll go out on a limb here...search for "sl-modem-daemon" in synaptic. If it's installed, uninstall it.
Next run these commands, one at a time, in a terminal:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```
Now reboot. If that doesn't help try enabling backports in "System>Administration>Software Sources" on the "Updates" tab and running those commands again. Reboot.

---

