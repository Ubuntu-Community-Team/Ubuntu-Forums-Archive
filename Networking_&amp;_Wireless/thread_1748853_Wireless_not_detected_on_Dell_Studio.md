---
title: "Wireless not detected on Dell Studio"
date: 2011-05-04
forum: Networking &amp; Wireless
---

### Post by kvv_1986 on 2011-05-04
**ISSUE SOLVED: FOUND SOLUTION ON LINUX MINT COMMUNITY**
[http://community.linuxmint.com/tutorial/view/218](http://community.linuxmint.com/tutorial/view/218)
The solution is for debian, but it worked for me on Kubuntu 11.04.



Hi,

I just installed Kubuntu, and my wireless is not getting detected. I tried a variety of solutions I found online, but none worked. It worked perfectly for Ubuntu Gnome.

When I tried installing the Broadcom drivers in the "Additional Drivers", I got an error that the driver could not be installed.
  
Output of lspci:

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)                                                                                       
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)                                                                
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)                                                                       
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)                                                                                      
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)                                                                                      
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)                                                                                      
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)                                                                                     
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)                                                                                           
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)                                                                                              
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)                                                                                              
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)                                                                                              
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)                                                                                              
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)                                                                                      
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)                                                                                      
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)                                                                                      
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)                                                                                     
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)                                                                                                              
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)                                                                                                       
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)                                                                                                  
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)                                                                                                     
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)                                                                                                  
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)                                                                                   
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)                                                                                                     
09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

```

---

### Post by kvv_1986 on 2011-05-04
I ran the script in Hippytaf's sig (sorry if I got the name wrong).

I have attached it in two parts. It exceeded the maximum file size limit.

---

### Post by kvv_1986 on 2011-05-04
**ISSUE SOLVED: FOUND SOLUTION ON LINUX MINT COMMUNITY**
[http://community.linuxmint.com/tutorial/view/218](http://community.linuxmint.com/tutorial/view/218)
The solution is for debian, but it worked for me on Kubuntu 11.04.

---

### Post by northd_tech on 2011-05-04
I read the output from that script, and I saw some "dell wifi" stuff that causes me to ponder a bit...   

Your wireless interface looks to be a Broadcom 4312 wireless, and I seem to recall "chili555" mentioning a problem regarding the "dell-wifi" module causing problems there that somehow interfered with the Broadcom wireless, but I didn't run Linux back when I still had a Dell laptop (an old work computer, or else I would have run dual-boot Linux by choice).

Looking at his most recent posts, I only found some stuff for an Acer laptop wireless that was interfering with an Atheros wireless, but I seem to remember Chili having a quick fix for at least one Dell laptop, too.  Chili's PRETTY-DURN handy when it comes to this Networking stuff!

This is Chili's profile:
[http://ubuntuforums.org/member.php?u=35909](http://ubuntuforums.org/member.php?u=35909)

You might want to send him a personal message and link him to this thread (and let him thank/curse me later ;) )

[]("http://ubuntuforums.org/private.php?do=newpm&u=35909")

---

