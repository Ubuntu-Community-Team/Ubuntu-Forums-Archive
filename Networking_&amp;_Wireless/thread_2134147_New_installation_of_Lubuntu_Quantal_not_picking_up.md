---
title: "New installation of Lubuntu Quantal not picking up wi-fi"
date: 2013-04-10
forum: Networking &amp; Wireless
---

### Post by raen on 2013-04-10
Until yesterday, my Acer Aspire One D250-1165 ran Ubuntu 10.04.1 Lucid. For obvious reasons, that needed to change. So I backed it up and clean-installed Lubuntu 12.10 Quantal from a live USB stick.

It connected to the internet just fine when I plugged in an ethernet cable, but now I'm at a friend's house and it's not picking up the wi-fi at all. I opened up Network Connections and the only thing it lists is Wired connection 1, last used (inexplicably, since more than 10 hours have passed) 44 minutes ago. (The clock isn't properly updating, either, but I figure I'll deal with the wi-fi connection first, then address my other issues.)

I'm borrowing my friend's computer (running Windows) to post this.

What do I need to do for it to be able to sniff out wi-fi?

Thanks,
raen

---

### Post by pinballwizard on 2013-04-10
post the output of ```
lspci
```

Lets start with finding out what network hardware you have.

---

### Post by raen on 2013-04-10
> **pinballwizard said:**
> post the output of ```
lspci
```

Lets start with finding out what network hardware you have.

Here we go:

```

$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GSE Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
03:00.0 Ethernet controller: Atheros Communications Inc. AR8132 Fast Ethernet (rev c0)

```

Thanks,
raen

---

### Post by pinballwizard on 2013-04-10
Off the top of my head, a Broadcom card is gonna need a proprietary driver. Run jockey and see if there is one?

Edit; The last hardware I ran that had a Broadcom driver also had issues with wifi. Jockey offered two drivers, and I vaguely remember having to test both to find one that works.

---

### Post by raen on 2013-04-10
> **pinballwizard said:**
> Off the top of my head, a Broadcom card is gonna need a proprietary driver. Run jockey and see if there is one?

Edit; The last hardware I ran that had a Broadcom driver also had issues with wifi. Jockey offered two drivers, and I vaguely remember having to test both to find one that works.

```

$ jockey
jockey: command not found

```

Well, that can't be good.

---

### Post by pinballwizard on 2013-04-10
> **raen said:**
> ```

$ jockey
jockey: command not found

```

Well, that can't be good.

Sorry, mate, used KDE for too many years, (Jockey is the old KDE program to look for drivers)

I'm not 100% sure with Lubuntu, but go to Settings and look for something along the lines of "Additional Drivers"? I have such an animal in regular Ubuntu...

Edit: In Quantal, it is now in Preferences > Software Sources > Additional Drivers.

---

### Post by raen on 2013-04-10
> **pinballwizard said:**
> Sorry, mate, used KDE for too many years, (Jockey is the old KDE program to look for drivers)

I'm not 100% sure with Lubuntu, but go to Settings and look for something along the lines of "Additional Drivers"? I have such an animal in regular Ubuntu...

Edit: In Quantal, it is now in Preferences > Software Sources > Additional Drivers.

Thanks for the edit! I was just about to post that I couldn't find it!
Under the Additional Drivers tab, it says:

```

O Broadcom Corporation: BCM4312 802.11b/g LP-PHY
   This device is not working
   o Using Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source (proprietary)
   x Do not use the device
O Unknown: Unknown
   This device is using a manually-installed driver.
   o Using Non-free firmware for Linux kernel drivers from linux-firmware-nonfree (proprietary) //greyed out
   o Contunue using a manually installed driver
   x Do not use the device //greyed out

```

Underneath, it says:
No proprietary drivers are in use.
A proprietary driver has private code that Ubuntu developers can't review or improve. Security and other updates are dependent on the driver vendor.

raen

---

### Post by pinballwizard on 2013-04-10
> **raen said:**
> Thanks for the edit! I was just about to post that I couldn't find it!
Under the Additional Drivers tab, it says:

```

O Broadcom Corporation: BCM4312 802.11b/g LP-PHY
   This device is not working
   o Using Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source (proprietary)
   x Do not use the device
O Unknown: Unknown
   This device is using a manually-installed driver.
   o Using Non-free firmware for Linux kernel drivers from linux-firmware-nonfree (proprietary) //greyed out
   o Contunue using a manually installed driver
   x Do not use the device //greyed out

```

Underneath, it says:
No proprietary drivers are in use.
A proprietary driver has private code that Ubuntu developers can't review or improve. Security and other updates are dependent on the driver vendor.

raen
Select the option to install the proprietary driver?

Look here if you need help installing the driver:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
[http://askubuntu.com/questions/55868/how-to-install-broadcom-sta-wireless-cards-bcm43xx-chipsets](http://askubuntu.com/questions/55868/how-to-install-broadcom-sta-wireless-cards-bcm43xx-chipsets)
[http://ubuntuforums.org/showthread.php?t=896713](http://ubuntuforums.org/showthread.php?t=896713)

---

### Post by raen on 2013-04-10
> **pinballwizard said:**
> Dunno your feelings on free (open and beer) software, but to get it to work, select the 

```
 o Using Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source (proprietary)
```

option and tell us?

Philosophically, I adore FLOSS. Practically, well, it's all over the board.

Anyhow, I hit the radio button, hit "Apply Changes," entered my password, and it reverted right away to "Do not use this device" being selected. I'm starting to suspect that "This device is not working" does not simply mean "You are not currently using this device." :(

Thanks,
raen

---

### Post by raen on 2013-04-10
> **pinballwizard said:**
> Select the option to install the proprietary driver?

Look here if you need help installing the driver:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
[http://askubuntu.com/questions/55868/how-to-install-broadcom-sta-wireless-cards-bcm43xx-chipsets](http://askubuntu.com/questions/55868/how-to-install-broadcom-sta-wireless-cards-bcm43xx-chipsets)
[http://ubuntuforums.org/showthread.php?t=896713](http://ubuntuforums.org/showthread.php?t=896713)


I need to scare up a modem and ethernet cable. This might take a while.

Thanks,
raen

---

### Post by pinballwizard on 2013-04-10
> **raen said:**
> 
Anyhow, I hit the radio button, hit "Apply Changes," entered my password, and it reverted right away to "Do not use this device" being selected. I'm starting to suspect that "This device is not working" does not simply mean "You are not currently using this device." :(

Thanks,
raen

Are you online when doing it? It will download the driver if you are...

---

### Post by raen on 2013-04-10
> **pinballwizard said:**
> Are you online when doing it? It will download the driver if you are...

I hadn't been, but I am now that I found a wired connection. It worked like a charm, and I am now on the wi-fi.

THANK YOU! :D
raen

---

### Post by raen on 2013-04-10
Okay, where did they put the thing to mark this as "SOLVED"?

---

