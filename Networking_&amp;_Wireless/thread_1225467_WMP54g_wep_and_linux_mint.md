---
title: "WMP54g wep and linux mint"
date: 2009-07-28
forum: Networking &amp; Wireless
---

### Post by Frogster on 2009-07-28
Good evening all,

I am hoping for some help. On this pc I run jaunty with a WMP54g pci card, it worked from the start. No problems no Ndiswrapper, absolutely brilliant after the problems I have had in previous ubuntu versions. 

However, on another pc I run Linux Mint with a WMP54g pci card. This card I cant get to work, Wep doesn't seem to be working. So, any insights or help will be greatly received :o 

```
keith@Bert ~ $ lspci 
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80) 
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge 
00:09.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10) 
**00:0b.0 Network controller: RaLink RT2561/RT61 802.11g PCI **
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) 
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) 
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) 
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) 
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) 
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) 
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) 
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South] 
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60) 
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78) 
01:00.0 VGA compatible controller: nVidia Corporation NV36 [GeForce FX 5700LE] (rev a1) 
keith@Bert ~ $ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wmaster0  no wireless extensions. 

wlan0     IEEE 802.11bg  ESSID:"Tortuga"  
          Mode:Managed  Frequency:2.412 GHz  **Access Point: Not-Associated**   
          Tx-Power=17 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

pan0      no wireless extensions. 

keith@Bert ~ $ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wmaster0  no wireless extensions. 

wlan0     IEEE 802.11bg  ESSID:"Tortuga"  
          Mode:Managed  Frequency:2.412 GHz  **Access Point: Not-Associated**   
          Tx-Power=17 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
 
pan0      no wireless extensions. 

keith@Bert ~ $ lshw -C Network 
WARNING: you should run this program as super-user. 
  *-network:0             
       description: Wireless interface 
       product: RT2561/RT61 802.11g PCI 
       vendor: RaLink 
       physical id: b 
       bus info: pci@0000:00:0b.0 
       logical name: wmaster0 
       version: 00 
       serial: 00:1e:e5:2a:01:df 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list logical ethernet physical wireless 
       configuration: broadcast=yes driver=rt61pci latency=32 **module=rt61pci** multicast=yes wireless=IEEE 802.11bg 
  *-network:1 
       description: Ethernet interface 
       product: VT6102 [Rhine-II] 
       vendor: VIA Technologies, Inc. 
       physical id: 12 
       bus info: pci@0000:00:12.0 
       logical name: eth0 
       version: 78 
       serial: 00:50:8d:5f:05:d2 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=32 maxlatency=8 mingnt=3 module=via_rhine multicast=yes 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 1 
       logical name: pan0 
       serial: 9e:2e:20:52:a6:f5 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes 
keith@Bert ~ $ 
```

---

### Post by Frogster on 2009-07-29
Any help or pointer?

---

### Post by Frogster on 2009-07-30
Hmmm glad it not just me that this has stumped

---

### Post by Frogster on 2009-08-02
Any help or input on this will be greatly appreciated

---

### Post by chili555 on 2009-08-02
May I assume you are entering the WEP code into Network Manager? Is it ten characters or 26 characters? Have you tried both upper and lower case for the letters?```
096C7F28...
```and```
096c7f28...
```The one computer that I allow to run NM loves lower case. It may, in fact, be upper case in the router, but whatever works!

---

### Post by Frogster on 2009-08-02
Wep codes are being entered into "NetworkManager Applet" and all are in the correct case. That was not something I had thought to check. 

The wep code is ten characters in length and has worked in ubuntu 7.10 through to  9.04 (ndiswrapper in prior incarnations), xp and vista.

Thank you for the response. This has me scratching my head as in 9.04 the driver works out the box with no problems but with mint no wep! I thought Mint was 9.04 with extras?

---

### Post by Subito Piano on 2010-06-24
wow - i am wondering if you ever got this figured out.

I have a similar problem.  [Another thread]("http://ubuntuforums.org/showthread.php?t=731755") suggested changing to [wicd]("http://wicd.sourceforge.net/") -- maybe that will help you.

---

### Post by Frogster on 2010-06-24
Hmmm, it was so long ago I cant remember how I solved the problem!!!

I have a feeling I just installed Ubuntu in the end and did away with mint.

However, I have used Wicd and can recommend it

---

### Post by Subito Piano on 2010-06-24
hmm --- wicd didn't work.  I'll try WPA encryption tomorrow or when i get the chance.  Oh, for what it's worth, my machine is the latest Ubuntu Studio (10.04?) and it works great, the machine giving me grief is Mint 7, but i suppose it could be a hardware issue.

---

