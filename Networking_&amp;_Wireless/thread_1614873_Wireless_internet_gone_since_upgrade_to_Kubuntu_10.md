---
title: "Wireless internet gone since upgrade to Kubuntu 10.10"
date: 2010-11-06
forum: Networking &amp; Wireless
---

### Post by mdekoning on 2010-11-06
Since I've upgraded to Kubuntu 10.10 I've lost my wireless internet. In Windows 7 everything's fine, but in Kubuntu wicd keeps giving a "Unable to get IP address message". Is there any way to solve this problem?

Here's some output that might help:

dmesg | grep wlan0

wlan0: associate with **:**:**:**:**:** (try 1)
wlan0: RX AssocResp from **:**:**:**:**:** (capab=0x411 status=0 aid=2)
wlan0: associated
wlan0: deauthenticating from **:**:**:**:**:** by local choice (reason=3)

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:     off/any  
          Mode:Managed  Frequency:2.447 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:    off   Fragment thr:    off
          Power Management:     off

lspci

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]
02:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
05:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

Thanks in advance.

---

### Post by coffeecat on 2010-11-06
The good news is that you are using this wireless chipset...

> **mdekoning said:**
> 05:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

.... which I can tell you works just fine in Ubuntu/gnome 10.10 using the default network manager applet for me at least.

Whether wicd is your problem, I really don't know. I have little experience of it. So, whether reverting to network manager will help, again I don't know. It would be a challenge, but doable. You have to uninstall wicd before you can re-install nm. Which makes installing network manager - um - fun.

**Edit:** when I say "just fine", I mean just fine in G mode. With my router set to 'N' I can surf most sites OK (except Yahoo) and surf this forum, but when I try to post, the connection to the forum hangs. Which is quite weird. So I have my router set to 'G'. With...
> Mode:Managed  Frequency:2.447 GHz

... I'm guessing your router is also set to G, but something to check.

---

### Post by mdekoning on 2010-11-06
> **coffeecat said:**
> 


... I'm guessing your router is also set to G, but something to check.
Thanks for replying.

Is there an easy way to check this?

---

### Post by coffeecat on 2010-11-06
Log into the router admin interface from your web browser and go to wireless settings.

---

### Post by ajgreeny on 2010-11-06
I don't think you have to remove wicd before installing network-manager these days.  It was necessary in the past, but I have certainly had both installed in gnome and both running at the same time with no obvious problem, but also no obvious advantage to one over the other, as far as I could see.

KDE (kubuntu) may be different from gnome in this respect, but I would think you should still be able to get a wireless signal, whichever DE you use.

---

### Post by LouisaLou on 2010-11-06
Hi, 

I'm a total newcomer to Ubuntu but am enjoying learning the ropes. I apologize in advance for the naivete of my questions...

I arrived in the Central African Republic only to find that my wireless (on an HP Mini 5102) wasn't working -- it didn't detect any wireless networks. So I wiped off Windows and installed Ubuntu 10.10, hoping that would help. Luckily, it did! (Partly.) 

At first, I still didn't get any wireless networks. I messed around with all the various things you have to do to get Broadcom wireless drivers working. Finally, following a forum suggestion, I installed Wicd -- and this did the trick. Not knowing any better, I kept Network Manager alongside Wicd, but Wicd is what works much better. (Is there a reason to un-install Network Manager?)

However, when I try to connect wirelessly to the network at this country's one cafe with wifi (which usually works really well, by CAR standards), the network doesn't appear. At the office, when I open Wicd, it includes a box with the message "<connection name>: obtaining IP address", and bit by bit it connects. But when I open Wicd at the cafe, this doesn't happen -- it just gives me a list of random signals from nearby offices (all secured and low-signal), none of which I can connect to. Any ideas how I could get the cafe network to show up?

I'm at the office now, and so it's working. However, in order to get it working I had to restart three times -- Wicd only seems to work about half or 33% of the time. Sometimes I get the message: "Connection failed: unable to get IP address" and sometimes I get the message "No wireless networks detected." Then I try again and eventually it works. So far. 

Any suggestions/advice would be so much appreciated! I'm headed out to a small provincial town many hours from the capital, and there will be only one wifi connection there, so I'm eager to work the bugs out beforehand. I'm happy to post more technical info, I just need a little guidance!

Thanks so much!!

---

### Post by LouisaLou on 2010-11-06
My apologies -- I think I posted this in the wrong place. Like I said, I'm new to this...So sorry.

---

### Post by coffeecat on 2010-11-06
> **ajgreeny said:**
> I don't think you have to remove wicd before installing network-manager these days.  It was necessary in the past, but I have certainly had both installed in gnome and both running at the same time with no obvious problem

I'm very glad to hear it. back in Karmic days, if you wanted to try wicd, it removed network manager and if you wanted nm back, you had to uninstall wicd first. Which led to some fancy footwork with the command line and some ethernet cable. Ho hum.

---

### Post by mdekoning on 2010-11-10
This seems to be a wicd issue. I've installed KNetworkManager again and it has no problems connecting at all.

---

