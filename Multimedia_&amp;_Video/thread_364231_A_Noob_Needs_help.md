---
title: "A Noob Needs help"
date: 2007-02-18
forum: Multimedia &amp; Video
---

### Post by skooge on 2007-02-18
Hi, I'm kind of new to Ubuntu and I need some help.  I just put Dapper Drake on my IBM Thinkpad T22 and I need to know what type of Architecture it is so I can download totem-xine from this site.--> [http://packages.debian.org/testing/gnome/totem-xine]("http://packages.debian.org/testing/gnome/totem-xine")

---

### Post by rsambuca on 2007-02-18
I'm not running Dapper (I am running Edgy right now), but I am pretty sure that it is in the synaptic packages.

Go to your Synaptic Package Manager (System -> Administration -> Synaptic Package Manager) and do a search for "totem-xine" and I am sure it is there.

---

### Post by taurus on 2007-02-18
Probaby an i386--x86.  Why not use this link instead?

[https://help.ubuntu.com/community/MultimediaApplications#totem-xine](https://help.ubuntu.com/community/MultimediaApplications#totem-xine)

---

### Post by skooge on 2007-02-18
Ok, it is playing DVDs now.  But the video is realy jerky.  Any ideas on whats going on?

---

### Post by Kevf on 2007-02-18
Jerky as in? Got the right videodriver installed?

---

### Post by skooge on 2007-02-18
the video stops and goes.  it has whatever driver ubuntu installed.

---

### Post by taurus on 2007-02-18
What graphic card do you have on that machine?

```
lspci
```

---

### Post by skooge on 2007-02-18
this is what my lappy is.-->[http://www.linuxhardware.org/article.pl?sid=01/09/04/0135236&mode=thread]("http://www.linuxhardware.org/article.pl?sid=01/09/04/0135236&mode=thread")

---

### Post by skooge on 2007-03-08
> **taurus said:**
> What graphic card do you have on that machine?

```
lspci
```

0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
0000:00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
0000:00:03.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 0c)
0000:00:03.1 Serial controller: Agere Systems LT WinModem (rev 01)
0000:00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
0000:00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
0000:01:00.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 13)0000:06:00.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001a (rev 01)

---

### Post by skooge on 2007-03-31
I recently found out that it does not have savage driver installed, it has the defalt driver that Ubuntu installed.  Can someone please tell me how I can go about installing the right driver?

---

