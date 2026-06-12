---
title: "No sound from headphones jack 10.4"
date: 2010-07-27
forum: Multimedia Software
---

### Post by sedpatrick on 2010-07-27
Hello, 

I have a little issue. 

I have netbook Asus EEE PC 1001PX (he's got only one jack for headphone and mic, i dont' know how this could work... but anyway) 

I have no sound from headphone, from speakers is ok. 

I've already edit /etc/modprobe.d/alsa-base.conf and insert the options snd-hda-intel model=asus at the bottom, still nothing.

I've try also to uninstal linux-backports-wireless... and still nothing. 

Card: Intel HDA. 

Any suggestions?

Thx.

---

### Post by max2009ro on 2010-07-27
Try options snd-hda-intel model=auto

---

### Post by sedpatrick on 2010-07-27
Still nothing.

---

### Post by sedpatrick on 2010-07-29
Any other ideas?

---

### Post by jperez on 2010-07-29
Same issue, but on Asus Eee PC 1018PB running Easy Peasy 1.6.  Since it is based off Ubuntu Netbook Remix, figured I'd check here.  Anyone have a solution?

Jesse~

---

### Post by lidex on 2010-07-30
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by tommcd on 2010-07-30
Sorry if this sounds elementary, but just because you have not mentioned it, did you try running **alsamixer** in the terminal and make sure that all levels are unmuted and turned up?
Also, try going to: system > preferences > sound, and try setting everything to alsa if it gives you that option.
I'm not sure if this is in the menu for Easy Peasy. It is in the menu for Ubuntu 10.04 though.

---

### Post by jperez on 2010-07-30
> **tommcd said:**
> Sorry if this sounds elementary, but just because you have not mentioned it, did you try running **alsamixer** in the terminal and make sure that all levels are unmuted and turned up?
Also, try going to: system > preferences > sound, and try setting everything to alsa if it gives you that option.
I'm not sure if this is in the menu for Easy Peasy. It is in the menu for Ubuntu 10.04 though.

Tried and no options for headphones.  Easy Peasy 1.6 is based on Lucid and has all the same options.  So no, no options for it and yes, I have tried alsamixer in the terminal.  Thanks for the reply though.

Jesse~

---

### Post by jperez on 2010-07-30
> **lidex said:**
> Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```

```
Linux jesse-ep-netbook 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux


**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ii  alsa-base                              1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                             1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                             4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                     0.10.28-1                                       GStreamer plugin for ALSA
ii  libsdl1.2debian-alsa                   1.2.14-4ubuntu1                                 Simple DirectMedia Layer (with X11 and ALSA 

Codec: Realtek ALC269
```

Everything separated by paragraph return.

Jesse~

---

### Post by lidex on 2010-07-30
The auto model should work. Try upgrading your alsa install using the alsa-upgrade link in my sig. Remove all custom entries from alsa-base .conf first.

---

### Post by jperez on 2010-07-31
> **lidex said:**
> The auto model should work. Try upgrading your alsa install using the alsa-upgrade link in my sig. Remove all custom entries from alsa-base .conf first.

Worked beautifully!  Ran the script last night, finished it up this morning and headphones are working perfectly.  Thanks for the help, greatly appreciated!

Jesse~

---

### Post by lidex on 2010-08-01
Purrrrfect, as Catwoman would say. Please mark the thread solved using 'Thread Tools' up top.

---

### Post by pecuna on 2011-01-13
Thanks, man!! This thing with the script works perfect to me too!\\:D/

---

