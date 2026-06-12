---
title: "w/ Atheros AR5BXB63 using Ndiswrapper"
date: 2007-07-18
forum: Multimedia &amp; Video
---

### Post by aubreyisland on 2007-07-18
Once you get Ubuntu up, you'll notice there is no sound. Don't panic, get some headphones, it's right there...

Now take a breather...

To enable the speakers, unplug your headphones, and type...

```
alsamixer
```

Use your right arrow to get to "Surround," hit up till the volume is RED then type M to unmute the front speakers and tada!

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=38516&stc=1&d=1184744694[/IMG]

---

### Post by sexypapa on 2007-07-24
YES, YES, YES, IT WORKS!!!!!

WOHOOOOOOOO!!

THANKS A BUNCH!:popcorn:

---

### Post by bks on 2007-09-26
I have this same chipset and this same problem, but when I try this fix I get

```
bradford@Aspire5050-bschroe:~$ alsamixer

alsamixer: function snd_mixer_load failed: Invalid argument

```

---

### Post by bks on 2007-09-26
When I first opened my Volume Control the speakers were turned all the way down, so I cranked them up, but still nothing.  My Volume control does say "Volume Control: Conexant 2c06 (OSS Mixer)"

---

### Post by bks on 2007-09-26
Sorry, browser glitch, double post.

---

### Post by GothPanda on 2007-10-03
Okay...  I'm definitely using Kubuntu, and I'm getting the same error.  How do I get the alsa mixer working in Kubuntu?

Also, I'm having problems with Acer_acpi, so if anyone can help, that'd be great...

---

### Post by bks on 2007-10-10
I'm begining to think it's the x86-64 architecture that is the problem. I have an AMD Turion64 and I've found that many of the programs that used to work on my 32bit system don't on this new 64bit. Which makes sense, but I hadn't thought about it before.

---

### Post by jimmyridge on 2008-02-12
umm whats alsa got to do with an atheros card? anyway i replied to a bug report and for those in need of getting this card working the madwifi driver works like a charm never ever use ndiscrapper especialy for an atheros chip bleh its just the driver needs to be patched to work with this device 


heres a link to my bug reply [https://bugs.launchpad.net/ubuntu/+source/madwifi-tools/+bug/181769](https://bugs.launchpad.net/ubuntu/+source/madwifi-tools/+bug/181769)
madwifi ticket [http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)  NATIVE LINUX DRIVER
"for AR5007 chipsets."
the patch the ticket speaks of [http://madwifi.org/attachment/ticket/1679/madwifi-ng-0933.ar2425.20071130.i386.patch?format=raw](http://madwifi.org/attachment/ticket/1679/madwifi-ng-0933.ar2425.20071130.i386.patch?format=raw)

and a lil site i have that holds a prepatched source tarball   [http://hst.ath.cx/madwifi](http://hst.ath.cx/madwifi)  <even aircrack injection patched>

try having that sort of fun with ndiscrapper

i cant wait to play with ath5k and its open HAL  makes me wonder im no madwifi expert but readin stuff about the HAL and the atheros SDR "Software Defined Radio" ... wouldnt it be possible to transmit/receive on any frequency? like an RF scanner mode? that'd be neat even if it is just a pipe dream.

---

