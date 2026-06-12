---
title: "Can't connect to my wireless network."
date: 2010-02-01
forum: Networking &amp; Wireless
---

### Post by jonjmill on 2010-02-01
I have just recently installed Ubuntu 9.10 on an old desktop. I went through the steps using ndiswrapper to obtain all of the necessary drivers for my wireless card, but now when it tries to connect I am prompted for my security password which I enter correctly and nothing happens. It is trying to connect but after about a minute or two I am prompted to enter my password again.

---

### Post by bkratz on 2010-02-01
> **jonjmill said:**
> I have just recently installed Ubuntu 9.10 on an old desktop. I went through the steps using ndiswrapper to obtain all of the necessary drivers for my wireless card, but now when it tries to connect I am prompted for my security password which I enter correctly and nothing happens. It is trying to connect but after about a minute or two I am prompted to enter my password again.

I think we should probably start with "what is your wireless card?" If unknown you can find out with the terminal (Applications>>Accessories>>Terminal) and type in
lspci   (that is LSPCI in lowercase). Also, have you tried to connect without any encryption on the AP just to see if the card is active?
If it is a usb device substitute lsusb for lspci

---

### Post by alessandro.v on 2010-02-01
> **bkratz said:**
> I think we should probably start with "what is your wireless card?" If unknown you can find out with the terminal (Applications>>Accessories>>Terminal) and type in
lspci   (that is LSPCI in lowercase). Also, have you tried to connect without any encryption on the AP just to see if the card is active?
If it is a usb device substitute lsusb for lspci


I have the same problem or more precisely: when I reboot the computer everything seems to work,
then if I have some network load (like streaming youtube) the wireless stops to work
and ask me the password (which it was not asked after reboot).
After a couple of minutes I receive again the request and sometimes it is able to connect again,
most of times no.

lspci gives:

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 Ethernet controller: Attansic Technology Corp. Device 1063 (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

Could you help me??? I was SOOOOOOOOO happy with Ubuntu 9.04....

---

### Post by bkratz on 2010-02-01
@alessandro.v

You probably should start a new thread since you are not the OP, but you probably can find what you need in the last two posts of

[http://ubuntuforums.org/showthread.php?t=1137780&page=3](http://ubuntuforums.org/showthread.php?t=1137780&page=3)

---

### Post by nuwesy on 2010-02-01
I also got that problem. When I type in my WPA key it's loading but after a while the same window shows up and I have to type in the key once again but then it continues doing like this. 

I'm using Ubuntu 9.10 by the way.:(

---

### Post by bkratz on 2010-02-01
@nuwesy

You should start a new thread too!  See this [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)
for the type of information you need to provide.

---

### Post by jonjmill on 2010-02-01
I seem to have solved the problem.  I started by completely removing the security to my router.  I had a connection.  I then changed it to WEP and everything worked fine too.

---

