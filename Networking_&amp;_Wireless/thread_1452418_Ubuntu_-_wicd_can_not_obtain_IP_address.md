---
title: "Ubuntu - wicd can not obtain IP address"
date: 2010-04-11
forum: Networking &amp; Wireless
---

### Post by AKG_8 on 2010-04-11
I am very new to linux .. and got into problems right away ..

when I connect to the internet via a wired connection it works .. bu when connecting tothe wireless the wicd can see all the available connections but is not able to obtain IP address .. please help 

I was using network manager before which also had the same problem so switched to wicd but the problem persists..

I have tried all WEP, WPA, insecure connection .. but nothing worked

here is the wicd log


2010/04/11 22:35:28 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
2010/04/11 22:35:36 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
2010/04/11 22:35:48 :: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
2010/04/11 22:35:51 :: No DHCPOFFERS received.
2010/04/11 22:35:51 :: No working leases in persistent database - sleeping.
2010/04/11 22:36:01 :: DHCP connection failed
2010/04/11 22:36:01 :: exiting connection thread
2010/04/11 22:36:01 :: Sending connection attempt result dhcp_failed

Please help !

---

### Post by 2hot6ft2 on 2010-04-11
Connect wired obviously
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get install network-manager-gnome
```
since you wont get much help with wicd since ubuntu doesn't come with it and as you already found out that doesn't help. And it has its own bugs.
Then we need to know what you're running.
What version of ubuntu?
32 bit 64 bit?
And we need to know what wifi adapter you have so

If internal PCI
```
lspci
```
That's LSPCI in lower case, and post the results.

If it's a USB adapter
```
lsusb
```
That's LSUSB in lower case, and post the results.

Then maybe we can help you get it up and running.
By the way welcome to the forum.
I'm about to call it a night in a few minutes, but someone should drop in and if not I'll check back in the morning and see where you are with it.

---

### Post by AKG_8 on 2010-04-12
Hi .. thanks for the reply

I am using Ubuntu 9.10 32 bit version

The wireless card is[SIZE=1][COLOR=black] Intel® PRO/Wireless 3945ABG Network Connection and the driver installed is iwl3945

I did install network-manager but still the problem is there. It shows my network in the list but does not connect to it.

here are the results of the commands you asked me to run

[/COLOR][/SIZE]    abhishek@abhishek-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface  Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
05:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
05:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
05:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
   
  abhishek@abhishek-laptop:~$ lsusb
Bus 004 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  

Thanks a lot for your help .. I'll be looking forward to see your reply

---

### Post by 2hot6ft2 on 2010-04-12
> **AKG_8 said:**
> 
I am using Ubuntu 9.10 32 bit version

The wireless card is[SIZE=1][COLOR=black] Intel® PRO/Wireless 3945ABG Network Connection and the driver installed is iwl3945

I did install network-manager but still the problem is there. It shows my network in the list but does not connect to it.

here are the results of the commands you asked me to run

[/COLOR][/SIZE]    abhishek@abhishek-laptop:~$ lspci
```

02:00.0 Network controller: **Intel Corporation PRO/Wireless 3945ABG** [Golan] Network Connection (rev 02)

```
   
  abhishek@abhishek-laptop:~$ lsusb
```
Bus 004 Device 002: ID 03f0:171d **Hewlett-Packard Wireless (Bluetooth + WLAN)** Interface [Integrated Module]

```

Looks like you have 2 wireless adapters connected.
They are both probably trying to connect and if they both get IP Addresses your connection will be next to useless since the pc wont be able to decide which one to use. I always disable one when I have more than 1 connected so since one is a usb adapter unplug it and try to connect.

When you setup your connection you are using the network manager in the top right panel right?
Right click on it and select Edit connections then Wireless and create or edit your connection details.
Once everything else is set the way it should be put your passkey in the Wireless tab and click Apply.
Don't click Close yet give it a chance to connect, you may have to put your pass key in again and click Apply again.
If it connects then you can click on Close and you'll be connected.
If not then we need to look further.

I have to disable bluetooth on mine because it creates a problem for some reason on my WLAN/Bluetooth card.

Your adapter seems to be one with reported issues so you may need to just disable the internal **Intel Corporation PRO/Wireless 3945ABG** and use the usb adapter instead. See this thread for more info. on that:
[Compaq Presario V3410TU Iwl3945 problem]("http://ubuntuforums.org/showthread.php?t=1441776&highlight=iwl3945&page=2")
Particularly the posts by chili555 as he is very good at troubleshooting wireless problems.

So if you have a switch that will turn off the internal Intel wireless adapter you could just turn it off with the switch and try getting your usb adapter to work instead.

03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface
Appears to have a Broadcom a BCM4310 chip and from what I can find it **"might"** work using the restricted driver in
System > Administration > Hardware Drivers

It may not work either. After a lot of searching without finding a way to get it to work I stopped at this one.
[[Bug 426754] [NEW] bluetooth does not work in GNOME in karmic]("http://osdir.com/ml/ubuntu-bluetooth/2009-09/msg00096.html")

[Here's the search I was going thru]("http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:official&q=03f0:171d+ubuntu&start=10&sa=N") if you want to have a look for yourself.
I did other searches as well like searching the forum with no luck.

You may just have an unfortunate set of hardware and be stuck with the choice of getting a new adapter that is supported under ubuntu or (hate to say it) giving Lucid 10.04 Beta a shot and see if one of them will work in it. If you want to give Lucid a shot you can upgrade to it using a wired connection with this command.

Open a terminal
Applications > Accessories > Terminal
and run
```
sudo update-manager -d
```
Update Manager should open up and tell you: New distribution release '10.04' is available. Click Upgrade and follow the on-screen instructions.

Or download it here: [http://www.ubuntu.com/testing/lucid/beta2](http://www.ubuntu.com/testing/lucid/beta2)

That's all I can do for you, good luck in whichever you choose to do.

---

### Post by AKG_8 on 2010-04-12
Thanks so much for the suggestion .. i will try them and post the resuls ..

---

