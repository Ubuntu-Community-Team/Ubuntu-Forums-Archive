---
title: "no wireless on Presario CQ56"
date: 2011-02-03
forum: Networking &amp; Wireless
---

### Post by rebeltaz on 2011-02-03
I installed Ubuntu 10.10 on my gf's new Presario CQ56 laptop and I cannot get wireless working. I saw on here where this is supposed to work out of the box, but of coiurse in my case - no. 

It's like it doesn't even see the wireless card. Can someone give me some help? She is going to kill me because it worked fine in Win7!

BTW - here is the output of lspci if it helps:
```

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
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Network controller: RaLink Device 5390
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

*** edit *** 

I installed the RaLink drivers from their web site and now Ubuntu sees the card and the card sees the network, but it refuses to connect to any one of them. I am using WEP keys.

*** EDIT ***


Dagnabit! I was surfing for an hour and then I rebooted the computer. Now it will not connect to the router again. I even removed the WEP key and made it open. Still will not connect.

SOMEONE PLEASE HELP before I have to go back to Windows on this freaking laptop!!!

Thanks...

New update...

Out of three routers, it will connect to one perfectly every time, but never the other two.

The one it connects to is a Netopia 3347-02. The ones that it will not connect to are a D-Link DI-514 and a Belkin F5D7230-4.

As far as I can tell, they are all configured equally. I had DHCP disabled on the two it doesn't connect to, so I tried enabling that and even giving the laptop manual IPv4 settings, but nothing is working. I don't understand why it will connect to the Netopia just fine but not the others!!!!

---

### Post by Samzystrange on 2011-05-07
The solution to this is here:
[http://ubuntuforums.org/showthread.php?t=1751685](http://ubuntuforums.org/showthread.php?t=1751685)
Hope it helps you too!

---

### Post by rebeltaz on 2011-11-27
I just now saw this reply. I wanted to thank you. I may not really care anymore, though. After several months of issues with this laptop and the so-called customer support at HP - [http://www.robotsandcomputers.com/phpBB3/viewtopic.php?f=4&t=75](http://www.robotsandcomputers.com/phpBB3/viewtopic.php?f=4&t=75) - they are going to replace this laptop. Hopefully with a model that will work. 

Thank you again...

---

