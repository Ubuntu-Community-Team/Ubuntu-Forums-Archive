---
title: "problem watching tv with all the players"
date: 2009-09-23
forum: Multimedia Software
---

### Post by ramadan on 2009-09-23
Totem >> how to scan?
me tv>> cant see the dvb card (skystar 2)
kaffeine >> there is a signal, but no channel after scan

skystar 2
nVidia 8800
ubuntu 9.04 64bit

---

### Post by andrew.46 on 2009-09-24
Hi Ramadan,

I am afraid that I have no experience with watching TV with MPlayer except to know that it can be done. The html documentation speaks of the details here:

[http://www.mplayerhq.hu/DOCS/HTML/en/tv.html](http://www.mplayerhq.hu/DOCS/HTML/en/tv.html)

and certainly the man pages have some details on automatic scanning:

```

 -tvscan <option1:option2:...> (TV and MPlayer only)
     Tune the TV channel scanner.  MPlayer will also print value  for
     "-tv  channels=" option, including existing and just found chan-
      nels.

     Available suboptions are:

      autostart
         Begin channel scanning immediately  after  startup  (de-
         fault: disabled).

      period=<0.1-2.0>
         pecify  delay in seconds before switching to next chan-
         nel (default: 0.5).   Lower  values  will  cause  faster
         scanning, but can detect inactive TV channels as active.

      threshold=<1-100>
         Threshold value for the signal strength (in percent), as
         reported by the device (default: 50).  A signal strength
         higher  than this value will indicate that the currently
         scanning channel is active.

```

But I am afraid I do not have access to a TV tuner card to test any of this, perhaps this will provide a start?

Andrew

---

### Post by HappyFeet on 2009-09-24
Post the output of
```
lspci
```

---

### Post by ramadan on 2009-09-25
> **HappyFeet said:**
> Post the output of
```
lspci
```

this is the output of lspci

ramadan@ramadan-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
04:01.0 Network controller: Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card (rev 02)

the skystar 2 card (rev 2) is my only reason to install 9.04 cos 8.04 doesnt support it.

Ubuntu 9.04 64bit
nVidia 8800
skystar 2 rev. 2

---

