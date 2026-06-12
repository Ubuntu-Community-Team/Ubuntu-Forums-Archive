---
title: "Wireless Intel 4965 Does Not Works on Ubuntu 9.04 64bit"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by davidfdr on 2009-04-27
Hello guys,

With ubuntu 8.10 my WIFI card works very well.

But after installing a fresh copy of Jaunty (9.04) 64bit, the card is detected but does not list any wi-fi network.


The notebook is an Gateway P-6831FX 4GB RAM, 500gb HD, RAID0 stripe, 8800mgts. 

lspci:
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 RAID bus controller: Intel Corporation Mobile 82801 SATA RAID Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8800M GTS (rev a2)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
03:00.0 Mass storage controller: Silicon Image, Inc. Sil 3531 [SATALink/SATARaid] Serial ATA Controller (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
0c:06.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70) 

```

Anybody here have this problem with Intel wireless cards?

---

### Post by schander on 2009-04-27
Hi All,
I also have Intel 4695 AGN network in my Hp DV6799ea laptop. Although i don;t have exactly the same problem as you, its similar.
I could see other networks no problem. My own network is hidden so I selected the hidden network option and entered the name and then went selcet the WPA(don't remember exactly) encryption (personal) which on my router is WPA-PSK [TKIP] + WPA2-PSK [AES], then entered the password. After waiting a couple of minutes, for it to connect, it asked me for the password again, however the password that was in the dialogue was a hex string, where as I entered a normal ascii string. After serveral minutes the same situation,I gave it a few more goes with different setting but to no avail. :(

So it seems as there maybe a compatability problem with the network card we have.
It used to work ok under 8.10 however it would still be try to reconnect after the laptop went to sleep. I was hoping that this would be fixed.

Satpal

---

### Post by davidfdr on 2009-04-27
> **schander said:**
> Hi All,
I also have Intel 4695 AGN network in my Hp DV6799ea laptop. Although i don;t have exactly the same problem as you, its similar.
...

Satpal

It is very strange. After pushing the killswitch to turn ON / OFF the WI-FI card and bluetooth, sometimes the networks are listed. Not allways.   I think that ours cards have a compatibility issue with ubuntu 9.04 64bit.

---

### Post by davidfdr on 2009-04-27
Still having the problem. Anybody?

---

### Post by helmut0 on 2009-04-27
Yup I lost all my networking.Wired and wireless on upgrade...

---

### Post by davidfdr on 2009-04-27
> **helmut0 said:**
> Yup I lost all my networking.Wired and wireless on upgrade...

It is the same hardware?

---

### Post by abn91c on 2009-04-27
similar bug in kubuntu, reloading the network manager widget seems to solve it.An d of course re-run the network wizard :-)

---

### Post by davidfdr on 2009-04-27
> **abn91c said:**
> similar bug in kubuntu, reloading the network manager widget seems to solve it.An d of course re-run the network wizard :-)

Well, some times works, some times not.

I have to hard turn on / off a lot of times to iwlist scan return some results using the notebook kill wireless switch.

Very strange.
On ubuntu 8.04 and 8.10 everything works very well.

---

### Post by r3dux on 2009-04-28
With Jaunty installed (upgrade from 8.10) my wireless card (Intel 4965) worked, but dropped connection a lot with a bunch of errors like the following:
[126774.231915] iwlagn: Microcode SW error detected.  Restarting 0x2000000.
[126774.252811] iwlagn: MAC is in deep sleep!


I just updated the iwlagn wireless drivers by running:
sudo apt-get install linux-backports-modules-jaunty

Fixed it up fine for me - maybe worth trying for your issues...

---

