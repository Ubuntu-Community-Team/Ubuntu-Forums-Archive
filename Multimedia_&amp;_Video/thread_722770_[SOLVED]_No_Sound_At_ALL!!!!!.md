---
title: "[SOLVED] No Sound At ALL!!!!!"
date: 2008-03-12
forum: Multimedia &amp; Video
---

### Post by Programmer DO on 2008-03-12
I've been working on this problem for days. I have a Dell Dimension 4550 computer. Sound worked at one point, but now there is nothing. I've reinstalled the Alsa software to no avail. I cannot reinstall Ubuntu. I would appreciate any help you can give me. 
PS. Ubuntu recognizes my card.
PSS. I am new and need very specific instructions.

Thanks

---

### Post by warp99 on 2008-03-12
Need to know want sound card you have. Please run the following:

```
lspci -v
```

Look for the line "Audio Device" and paste the contents here. I want to rule out any quirks that your card may or may not have. :)

---

### Post by konungursvia on 2008-03-12
Are you dual booting with windows, and does the sound work there? Also, if you search for my post on installing the backports for sound, that might help.

Here is the install for the backports. Do this then reboot if you want to try my solution:

sudo apt-get install linux-backports-modules-generic

---

### Post by superprash2003 on 2008-03-13
try this..may help [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by Programmer DO on 2008-03-13
This is the output:

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
        Subsystem: Dell Unknown device 0142
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at d800 [size=256]
        I/O ports at dc40 [size=64]
        Memory at fe300400 (32-bit, non-prefetchable) [size=512]
        Memory at fe300000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>




Yes sound works perfectly in _Windows XP_.

Edit:
This is the output when I insert
[CODE] sudo lspci -v]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
        Subsystem: Dell Unknown device 0142
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at d800 [size=256]
        I/O ports at dc40 [size=64]
        Memory at fe300400 (32-bit, non-prefetchable) [size=512]
        Memory at fe300000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

---

### Post by Programmer DO on 2008-03-13
> **superprash2003 said:**
> try this..may help [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

There was no change.

Thanks for replying!:!:

---

### Post by Programmer DO on 2008-03-13
> **Programmer DO said:**
> Capabilities: <access denied>

What does this line mean??:confused:

Never mind, it meant that my user did not have permission to view file.

---

### Post by Programmer DO on 2008-03-13
> **konungursvia said:**
> Are you dual booting with windows, and does the sound work there? Also, if you search for my post on installing the backports for sound, that might help.

Here is the install for the backports. Do this then reboot if you want to try my solution:

sudo apt-get install linux-backports-modules-generic

Terminal said that my backports were up to date.

---

### Post by CHEF GO on 2008-03-13
I hope some one has an answer for you, but I don't.
:confused:

---

### Post by Programmer DO on 2008-03-14
I found the solution!!

I found that Ubuntu could not auto detect my headphones or speakers.:KS:):):):biggrin:

Thanks to everyone who posted.

---

### Post by CHEF GO on 2008-03-14
Great. I'm glad it was that simple. :lolflag:

---

### Post by rkrakora on 2008-03-14
How exactly did you solve this?

---

### Post by Programmer DO on 2008-03-14
I went to my sound preferences by double clicking on the speaker icon on my desktop. I then went to the switches section and disabled headphone jack sense.

---

### Post by warp99 on 2008-03-16
FYI, your sound card uses the snd-intel8x0 module:

```
Module snd-intel8x0
-------------------

Module for AC'97 motherboards from Intel and compatibles.
* Intel i810/810E, i815, i820, i830, i84x, MX440
ICH5, ICH6, ICH7, ESB2
* SiS 7012 (SiS 735)
* NVidia NForce, NForce2, NForce3, MCP04, CK804
CK8, CK8S, MCP501
* AMD AMD768, AMD8111
* ALi m5455

ac97_clock - AC'97 codec clock base (0 = auto-detect)
ac97_quirk - AC'97 workaround for strange hardware
See "AC97 Quirk Option" section below.
buggy_irq - Enable workaround for buggy interrupts on some
motherboards (default yes on nForce chips,
otherwise off)
buggy_semaphore - Enable workaround for hardwares with buggy
semaphores (e.g. on some ASUS laptops)
(default off)

AC97 Quirk Option
=================

The ac97_quirk option is used to enable/override the workaround for
specific devices on drivers for on-board AC'97 controllers like
snd-intel8x0. Some hardware have swapped output pins between Master
and Headphone, or Surround (thanks to confusion of AC'97
specifications from version to version :-)

The driver provides the auto-detection of known problematic devices,
but some might be unknown or wrongly detected. In such a case, pass
the proper value with this option.

The following strings are accepted:
- default Don't override the default setting
- none Disable the quirk
- hp_only Bind Master and Headphone controls as a single control
- swap_hp Swap headphone and master controls
- swap_surround Swap master and surround controls
- ad_sharing For AD1985, turn on OMS bit and use headphone
- alc_jack For ALC65x, turn on the jack sense mode
- inv_eapd Inverted EAPD implementation
- mute_led Bind EAPD bit for turning on/off mute LED

For backward compatibility, the corresponding integer value -1, 0,
... are accepted, too.

For example, if "Master" volume control has no effect on your device
but only "Headphone" does, pass ac97_quirk=hp_only module option.
```

On some hardware this module may exhibit some strange behavior, so there is a "quirks" mode with various switches that may or may not be needed.  For example my media server uses this module and I have to swap the controls for headphones and master using the options parameter loaded on startup in the file /etc/modprobe.d/options:

```
options snd-intel8x0 ac97_quirk=swap_hp
```

 Anyway I'm glad you got the sound working again. :)

---

