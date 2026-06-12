---
title: "Wireless not detected on my HP Pavilion 15-e034TX laptop"
date: 2013-08-09
forum: Networking &amp; Wireless
---

### Post by Aston_Martin on 2013-08-09
I just bought an  HP Pavilion 15-e034TX laptop and I installed ubuntu 11.04 and upgraded to 12.03.

and now laptop not able to detect the wifi however i am to use the internet ethernet cable.

Here is the output of "lspci":

00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 Display controller: Advanced Micro Devices [AMD] nee ATI Device 6660
07:00.0 Network controller: Ralink corp. Device 3290
07:00.1 Bluetooth: Ralink corp. Device 3298
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 07)
09:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5229 (rev 01)


I have also tried the process listed over here

[http://askubuntu.com/questions/168909/why-is-wifi-not-working-on-my-hp-laptop](http://askubuntu.com/questions/168909/why-is-wifi-not-working-on-my-hp-laptop)

but the issue still exists.......

---

### Post by chili555 on 2013-08-09
> I have also tried the process listed over here

[http://askubuntu.com/questions/16890...n-my-hp-laptop](http://askubuntu.com/questions/16890...n-my-hp-laptop)

but the issue still exists....... That is all for a Broadcom wireless card. You have:> 07:00.0 Network controller: Ralink corp. Device 3290I suggest you upgrade to 13.04 where is works by default. If you love pain, tinkering and dirty fingernails, you could follow this: [http://askubuntu.com/questions/253632/how-do-i-get-a-ralink-rt3290-wireless-card-working](http://askubuntu.com/questions/253632/how-do-i-get-a-ralink-rt3290-wireless-card-working)

---

