---
title: "alsa switchs my devices"
date: 2006-11-02
forum: Multimedia &amp; Video
---

### Post by metalzelot on 2006-11-02
Somehow the installed alsa on my ubuntu (Drapper Drake) switches the alsa devices all the time.

Actually my headset is (0:0) and my soundsystem is (1:0). Yesterday my soundsystem was (2:0) [headset stayed at the same device) and now the devices for headset and soundsystem are changed. So my headset now is (1:0) and my soundsystem is (0:0).

This really sucks because I use dmix in my .asoundrc. So if I start amarok it either cant find sound or it uses the headset instead of my soundsystem.

I recently installed alsa from sources but afterwards reinstalled the ubuntu alsa drivers again because I couldnt remove the alsa driver using apt-get (synaptic) without erasing half of my system (which also really sucks).
Isnt it possible to delete the alsa drivers and tell that he does not have to check dependencies? For example in SuSE its possible.

Now Im thinking about installing the driver from sources again, because they are newer and I have a better management on everything. Its no problem to define which card has to use which device.
Or is this also possible using the ubuntu drivers, just on another way?

I hope someone of you might help me out...

Jonathan

---

### Post by woedend on 2006-11-02
I hate this issue...it happens to me with my webcam of all things.  Anywho, heres the fix.

sudo gedit /etc/modprobe.d/alsa-base

add this as the last line

options snd-usb-audio index=-2


then save...


NOW- in your case, im sure it's not snd-usb-audio.  Whichever device you DONT want at 0, add its module name in place of snd-usb-audio in the text above.
HTH

---

### Post by metalzelot on 2006-11-02
Unfortunately this file doesnt exist... should I just create it or what do you suggest.

Here's an ls of /etc/modprob.d, the file sound was used for defining the devices for the source-driver.

/etc/modprobe.d# ls
aliases       blacklist-framebuffer  bluez              options
apm           blacklist-modem        ibm_acpi.modprobe  sound
arch          blacklist-oss          ipw3945            toshiba_acpi.modprobe
arch-aliases  blacklist-scanner      isapnp
blacklist     blacklist-watchdog     nvidia-kernel-nkc



Any idea on how to uninstall alsa?

---

### Post by woedend on 2006-11-02
hrm, did you reinstall ubuntu's alsa(alsa, alsa-base, alsa-utils I think they are...not sure anymore).
On my system(which isn't ubuntu), I specify modules to load before detection.  That is, they will be loaded before the kernel loads up all other modules.  Youll have to ask someone on ubuntu which file lets you do this, and this will let the module you specify grab 0 automatically.
the alsa-base file should exist, it did with dapper.

---

### Post by joegiampaoli on 2006-11-23
Go to this guide, it saved me from exactly the same problem, works like a charm.;)

[http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)

---

