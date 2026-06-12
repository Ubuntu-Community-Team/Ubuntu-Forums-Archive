---
title: "Blacklisting onboard soundcard"
date: 2007-12-02
forum: Multimedia &amp; Video
---

### Post by nix_12345 on 2007-12-02
Hi

I have an onboard sound card (SigmaTel STAC9721,23 also referred to as AC97) which I have disabled through my BIOS since I am using an Audigy 1. This works fine in Windows but Ubuntu keeps on recognizing the AC97 card which causes a conflict and no sound. 

I want to black list the AC97 card but I'm not sure how to do it. So far what I've figured out is that I:

Go to the terminal

type: sudo gedit /etc/modprobe.d/blacklist

and then add the following lines to the bottom of the file:

# added to correct sound issues
blacklist snd-*something*


The problem is I don't know what the *something* should be. I have tried snd-ac97 and snd-ac97-codec but that doesn't resolve anything.

---

### Post by natewiebe13 on 2008-01-26
what you want to do is open terminal

less /proc/asound/modules

it will come up with a list of audio drivers in use.
in my case it gave me

 0 snd_cmipci
 1 snd_via82xx
/proc/asound/modules (END) 

the one i want out is snd_via82xx
copy the name and exit

then take the name and blacklist it in /etc/modprobe.d/blacklist
here is mine.

_______________________________________________________

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# onboard sound
blacklist snd_via82xx

____________________________________________________________

then restart your computer and that should fix your problem. i think your problem was that you have to put an underscore instead of a dash, but anyways let me know

good luck

---

