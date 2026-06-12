---
title: "wireless problem"
date: 2010-11-14
forum: Networking &amp; Wireless
---

### Post by 673nn10 on 2010-11-14
I installed ubuntu 10.10 on my new Asus K42J and I can't connect to any of my Access point, its always ask for password.  I tried also to reinstall my ubuntu to 10.4 but its the same error. 

cpu - Intel Core i5-460M, 2.53GHz
wireless  -  802.11b/g/n+BT

Here is my lspci output 

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
01:00.0 VGA compatible controller: ATI Technologies Inc Madison [Mobility Radeon HD 5000 Series]
01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
07:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 80)
07:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 80)
07:00.5 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

Thank you.

---

### Post by uRock on 2010-11-14
Does the router use WEP or WPA/WPA2?

---

### Post by 673nn10 on 2010-11-14
the router use wpa&wpa2 personal

---

### Post by bitscarre on 2010-11-14
Can you connect to your access points from other computers?
If possible, have you tried restarting the access point?
Can you remove the encryption and internet connection from the access point and see if you can connect to it that way?

---

### Post by 673nn10 on 2010-11-14
The other machine can connect to accesspoint with the same OS ubuntu 10.4 and 10.10, only this Asus can't connect, I think the problem is in the asus laptop because of wireless card N-type and our Access point is g/b type, is there some special settings i can do to connect my new asus?

---

### Post by lisati on 2010-11-14
> **673nn10 said:**
> The other machine can connect to accesspoint with the same OS ubuntu 10.4 and 10.10, only this Asus can't connect, I think the problem is in the asus laptop because of wireless card N-type and our Access point is g/b type, is there some special settings i can do to connect my new asus?

At first sight, one might think that an "n" card trying to connect to a "b" or "g" network might not work to well. If I understand [this document]("http://download.intel.com/network/connectivity/products/wireless/adapters/1000/323015.pdf") properly, there's probably some option somewhere that will let you connect, but it won't necessarily get the most out of the "n" capabilities.

---

