---
title: "Newbie - sound card didn't get installed?"
date: 2006-06-25
forum: Multimedia &amp; Video
---

### Post by Stillglade on 2006-06-25
I am a complete newbie with Linux.  I just installed Ubuntu on an old desktop and I am pretty happy with it!  Only problem has been the lack of sound.  I have searched many places but am too much of a noob to understand what I have found.  This much I have gleaned:

The computer is a Compaq Presario 5280.  [Specs here]("http://h10025.www1.hp.com/ewfrf/wc/document?dlc=en&lc=en&product=93160&lang=en&cc=us&docname=c00013312")

It doesn't clearly indicate what sound card it has so the download for the Windows 98 driver for the sound card is [here]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?lc=en&cc=us&dlc=en&os=20&product=93160&lang=en&softwareitem=33955").  So the onboard sound appears to be "ESS 1869/1887/1888 Audio" whatever that means.

I ran "lspci" and no Audio listing shows up:

```
lspcstillglade@ubuntu:~$ lspci |grep audio
stillglade@ubuntu:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 02)
0000:00:03.0 Multimedia controller: Agere Systems V90 WildWire Modem (rev 01)
0000:00:04.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
0000:00:14.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:14.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:14.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:14.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc)
stillglade@ubuntu:~$

```

I don't even know where to look for sound card drivers (does linux even use drivers?).  I really appreciate the time and help that this community brings.

---

### Post by Stillglade on 2006-06-26
Ok, I think I am on to something here.  However, it is a bit over my head.
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=ESS+Technology&card=.&chip=ES18xx&module=es18xx]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=ESS+Technology&card=.&chip=ES18xx&module=es18xx")

Can someone translate this into step by step instructions that will work with Ubuntu?  Basically throughout the documentation it says "if debian do this or if blahblah do this" and it is throwing me off.  Thanks in advance!

---

