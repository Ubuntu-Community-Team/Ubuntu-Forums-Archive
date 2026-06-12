---
title: "Can't connect to router"
date: 2009-09-27
forum: Networking &amp; Wireless
---

### Post by miclav on 2009-09-27
I need help connecting to the internet again. I have an HP laptop running Linux Hardy Heron beside Vista Home Premium. I have a Linksys Wireless N router WRT150N and DSL internet.  
First a little history behind what has happened. All connections worked great until 3 days ago, when the download rate & browsing speed through my wireless connection slowed down dramatically in both operating systems to 1-2Mbps...on the hard wired desktop computer it is consistently at 100Mbps. I have no idea why it happened but after 2 days of this, I decided to try changing the settings in my router and the download rate shot up to 78Mbps. The browsing speed is also fast again.
Here are the changes I made to the router: I changed the Network Mode to Wireless N only from Mixed, changed the Radio Band to Wide-40MHz Channel from Auto, and changed the Wide Channel to 8. Now the wireless connection in Vista works great but I can't connect in Linux. It recognizes the network but won't connect even when I enter the shared key. When I put the settings back to what they were previously, it will connect but of course everything is back to a snail's pace.
Right now I am in Linux on my laptop, hardwired to the router via a second ethernet cable and I am connected just fine, even with the new router settings, so something is wrong in the wireless setup.
Does anyone have a solution for me?

---

### Post by miclav on 2009-09-28
Now I cannot connect wirelessly in Linux even when I return the router to the original settings! Can anyone please help?

---

### Post by Groover20 on 2009-09-28
I know it's not standard procedure for Linux, but did you try rebooting the laptop?  I've had issue with mine when it "wakes" up after sleep or hibernate mode.  The network key is keyed in correctly, but it just keeps looking for the network.

---

### Post by miclav on 2009-09-28
I've done that a few times to no avail.
If this helps, here is the result of the lspci command in the terminal:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

### Post by miclav on 2009-09-29
OK...I solved my own problem. You may think it a bit drastic but it worked! Here's what I did.
I backed up my Home folder to my external hard drive and re-installed Hardy Heron. I also reset my router to factory settings and re-entered the security information, and voila! Everything worked just fine, but  the download rate and browsing speed was again really slow. I saved the settings for my router (I just learned that I could do that in my investigative efforts), and repeated the router changes indicated in my original post.
Again Linux could not connect wirelessly so I decided to see if changing one option at a time would make any difference. I noticed that I could change the Network Mode back to Mixed and still retain the changes to the Wireless-N settings. I restarted Linux and it connected perfectly with all the desired speed. So what I needed to do was change the Wireless-N settings and the channel, but retain the Mixed setting on the Network Mode.
I must have really screwed up something in Linux in my efforts to get the networking functional, so I decided that a clean install was the best option.
Just thought I would post this in case anyone else might be struggling with the same issues.

---

