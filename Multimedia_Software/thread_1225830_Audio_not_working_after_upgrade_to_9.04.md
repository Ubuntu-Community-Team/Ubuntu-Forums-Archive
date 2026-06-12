---
title: "Audio not working after upgrade to 9.04"
date: 2009-07-29
forum: Multimedia Software
---

### Post by HarryBhat on 2009-07-29
I upgraded my laptop (Dell Studio) to Jaunty yesterday night. But since then, I'm not able to get any sound from any application. I tried the tricks given in some forums but they didn't seem to work. 

The details of my audio devices are-
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

The weirdest thing is that the file /etc/modprobe.d/alsa-base is empty.

When I try to temporarily load the device by typing 'sudo modprobe snd- IDT 92HD73C1X5' , I get the error message as shown-
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
FATAL: Module snd_ not found.

Could someone help me out with this?

---

### Post by HarryBhat on 2009-07-29
No answers? :confused:

---

### Post by igorzwx on 2009-07-29
You may try OSS4, if your hardware is supported
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

It might be reasonable to install another Ubuntu 9.04
(in dual boot) for experiments.

---

### Post by HarryBhat on 2009-07-29
> **igorzwx said:**
> You may try OSS4, if your hardware is supported
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

It might be reasonable to install another Ubuntu 9.04
(in dual boot) for experiments.

But is OSS4 as advanced as ALSA?

---

### Post by igorzwx on 2009-07-29
From my subjective point of view, OSS4 is much better than ALSA.
read in Wikipedia:
[http://en.wikipedia.org/wiki/Open_Sound_System](http://en.wikipedia.org/wiki/Open_Sound_System)

and also this:

[LIST]
[*][Open Sound System - Home page]("http://www.opensound.com/")
[*][Building the Open Sound System From Source]("http://www.4front-tech.com/wiki/index.php/Building_OSSv4_from_source")
[*][Sorry State of Sound in Linux]("http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html")
[*][State of sound in Linux not so sorry after all]("http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html")
[*][OSS is dead. Long live OSS!]("http://4front-tech.com/hannublog/?p=5")
[/LIST]
This is more objective:
[http://wiki.archlinux.org/index.php/OSS](http://wiki.archlinux.org/index.php/OSS)

[LIST]
[*][2 Advantages and disadvantages vs. ALSA]("http://wiki.archlinux.org/index.php/OSS#Advantages_and_disadvantages_vs._ALSA") 
[LIST]
[*][2.1 Advantages over ALSA (for users)]("http://wiki.archlinux.org/index.php/OSS#Advantages_over_ALSA_.28for_users.29")
[*][2.2 Advantages over ALSA (for developers)]("http://wiki.archlinux.org/index.php/OSS#Advantages_over_ALSA_.28for_developers.29")
[*][2.3 Disadvantages vs. ALSA]("http://wiki.archlinux.org/index.php/OSS#Disadvantages_vs._ALSA")
[/LIST]
[/LIST]

---

### Post by HarryBhat on 2009-07-29
> **igorzwx said:**
> From my subjective point of view, OSS4 is much better than ALSA.
read in Wikipedia:
[http://en.wikipedia.org/wiki/Open_Sound_System](http://en.wikipedia.org/wiki/Open_Sound_System)

and also this:

[LIST]
[*][Open Sound System - Home page]("http://www.opensound.com/")
[*][Building the Open Sound System From Source]("http://www.4front-tech.com/wiki/index.php/Building_OSSv4_from_source")
[*][Sorry State of Sound in Linux]("http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html")
[*][State of sound in Linux not so sorry after all]("http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html")
[*][OSS is dead. Long live OSS!]("http://4front-tech.com/hannublog/?p=5")
[/LIST]
This is more objective:
[http://wiki.archlinux.org/index.php/OSS](http://wiki.archlinux.org/index.php/OSS)

[LIST]
[*][2 Advantages and disadvantages vs. ALSA]("http://wiki.archlinux.org/index.php/OSS#Advantages_and_disadvantages_vs._ALSA") 
[LIST]
[*][2.1 Advantages over ALSA (for users)]("http://wiki.archlinux.org/index.php/OSS#Advantages_over_ALSA_.28for_users.29")
[*][2.2 Advantages over ALSA (for developers)]("http://wiki.archlinux.org/index.php/OSS#Advantages_over_ALSA_.28for_developers.29")
[*][2.3 Disadvantages vs. ALSA]("http://wiki.archlinux.org/index.php/OSS#Disadvantages_vs._ALSA")
[/LIST]
[/LIST]

Ok, Im convinced. But Im not that apt at command lines. So hw do I install it using Synaptic?
Also, do I need to remove ALSA before I install OSS? Can Synaptic do it automatically?

---

### Post by igorzwx on 2009-07-29
You cannot do such things with Synaptic.
Command line.

Install another Ubuntu 9.04 in dual boot for experiments.
This is the fastest and the most effective way to learn Linux.
To install OSS4 means to hack the Linux kernel in some way.
Very interesting experiment.
Really cool!

---

### Post by HarryBhat on 2009-07-29
> **igorzwx said:**
> You cannot do such things with Synaptic.
Command line.

Install another Ubuntu 9.04 in dual boot for experiments.
This is the fastest and the most effective way to learn Linux.
To install OSS4 means to hack the Linux kernel in some way.
Very interesting experiment.
Really cool!

So what do i do now?

---

### Post by igorzwx on 2009-07-29
Take book:

Ubuntu Linux for Dummies.chm

read some 20 pages (with pictures)

Install another Ubuntu 9.04 in dual boot (or multiple boot)

Install OSS4 there following this instruction:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

First of all, check if your hardware is supported by OSS4
**Does OSS Support My Hardware?**

 Check the list [here]("http://mercurial.opensound.com/?file/6bf18b4a87d6/devlists/Linux"). Some devices may not have full functionality (e.g. the X-fi module is limited to stereo output at the time of this writing, and jack sensing may not work on Azalia-compliant "High-Definition" devices, which are very common on motherboards and laptops today). If you're in doubt, consult the "Additional Support" sources found towards the end of this document.

**try to make it carefully!**

I will send you a private message with my e-mail address

---

