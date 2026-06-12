---
title: "Atheros 802.11 Wireless Lan Card HELP &quot;Driver was just disabled, but is still in use&quot;"
date: 2008-12-19
forum: Networking &amp; Wireless
---

### Post by Khaos139 on 2008-12-19
I have a

**Satellite A215-S4757**

And when I go to Hardware Drivers its shows the driver

**Support for Atheros 802.11 wireless LAN cards.**

Then when I try to activate it it says

**This driver was just disabled, but is still in use.**

Please help I don't know what to do

I am connected through wired atm so I can download anything if u need me too.

**_Info_**

Computer
```
Satellite A215-S4757
```

Wireless Brand, Model and Wireless Chipset
```
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
14:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
1a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
1a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
1a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
1a:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.
```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:1b:38:17:23:0b  
          inet addr:192.168.4.2  Bcast:192.168.4.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe17:230b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7386 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6231 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8703014 (8.7 MB)  TX bytes:706939 (706.9 KB)
          Interrupt:220 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5436 (5.4 KB)  TX bytes:5436 (5.4 KB)

```

---

### Post by Khaos139 on 2008-12-19
Here are two pics

[B][U]Before I click Activate
[/U][/B]
[img]http://img370.imageshack.us/img370/2909/screenshot1xy4.png[/img]

**_After I Click Activate_**

[img]http://img370.imageshack.us/img370/7453/screenshot2rp9.png[/img]

---

### Post by Khaos139 on 2008-12-20
hmm, I've been looking around but the problem is I can't find anybody with this is issue

I also forgot to say that even tho it says other driver in use... I don't think its working, and I would install wcid, But I have had a troubles getting network manager to install

---

### Post by Northsider on 2009-01-26
BUMP  Please anyone have an idea?  I have the *same exact problem* and it's driving me nuts!  Any help would be appreciated.  Thanks

---

### Post by Northsider on 2009-01-27
bump.

---

### Post by Jimro on 2009-01-31
I've got the same problem.  Acer 5520-5912 laptop.  Yesterday I finally ran some of the updates and it killed my wireless connection.  Been trying to fix it all day.  Seems like a kernel update is the most likely suspect.

The wireless works under Vista so I know that it is not hardware.

Jimro

---

### Post by Jimro on 2009-01-31
[http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/]("http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/")

The above link solved my problem.  I don't know which update killed my wireless, but fixing things through terminal is getting to be tiresome.  

Jimro

---

### Post by Brian_Newbie on 2009-01-31
Wow. The same thing has happened to me. I get no wireless networks showing up at all and 8 networks showed up just before the kernel updates but not immediately after the kernel update. Thus it must have something to do with the update. 

Jimro, I used that procedure before to get my wireless working under intrepid ibex. 

Do I need to uninstall anything first or just re-run those same commands in terminal?

---

### Post by Brian_Newbie on 2009-01-31
I just wanted to say that I repeated the installation procedure I used the first time in this link: [http://blog.hyperandy.com/2008/11/01...untu-810-ibex/](http://blog.hyperandy.com/2008/11/01...untu-810-ibex/)

and it worked like a charm. I'm not sure why the update caused the wireless not to work but it's an academic question now.

---

### Post by uwave on 2009-01-31
Yep...Same thing just happened to me...
New .23 updates on Hardy and then NO wireless
I use an Atheos 5006 card as well. I've got a sneaky suspicion someone does'nt like Atheos.
The HAL driver has been disabled 
Also, They only way I could get my laptop to boot completely was to use  
recovery mode..or a previous kernel..also I did notice that it hangs for 5 min at:
21.296233 ATA1.00 configured for UDMA/66 area for my drive..
then for 2  min at : 
21.772030 ATA2.00 ATAPI UJDA750 DVD/Drive UDMA/33
Then I did see something saying about an unknown symbol for Atheos ATH_HAL several times then it continued
I wish I could have copied the screen but it flashed too quick.
Right now I'm having to use wired internet here to find a solution and just now seen this post.
.22 and before worked fine for the wireless.
After .19 is when it started to hang at the ATA driver area but I lived with it.
Heres hoping the fix it prettyquick

---

