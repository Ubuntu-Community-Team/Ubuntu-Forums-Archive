---
title: "getting realtek wifi 8192se  to work on my toshiba satellite l500d 00F"
date: 2009-11-16
forum: Networking &amp; Wireless
---

### Post by topsykretts on 2009-11-16
hey guys..i know this topic has been floating around already..ive done my research already..ive downloaded the specific driver..then installed it on ndiswrapper..for most people it either worked or it didnt..well in my case it worked and it didnt.see i installed the driver throught ndis. and network manager can detect my WEP wifi...but when i try to connect to it...the wheel(32bit karmic koala) just keeps turning..then after a minute or so a window pops up and prompts me to put my password in again.when i put the password in..it does it all over again..im really sure i didnt type my password in wrong..is there something i did wrong or something im not doing?by the way when i go to ndiswrapper it says "unable to see if hardware is present".is there any one who can help me?anyone who has had the same problem and or has the same model laptop as he?thanks in advance to whoever can help..i really do not wanna go back to windows!!but if my wifi doesnt work on this laptop..i might have to hackintosh it..or go back to windows*shivers*..oh and one last thing..ive also tried using WICD incase anyone is gonna recommend that..it didnt even detect my wifi..atleaste network manager can detect my wifi..it just wont connect..aynway..here is the model of my laptop and some result from typing in commands at terminal

LAPTOP: TOSHIBA SATELLITE L500D 00F running 32bit ubuntu 9.10

 ndiswrapper -l:

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
net8192se : driver installed
    device (10EC:8172) present


LSPCI:
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Toshiba America Info Systems Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics]
0e:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
14:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

LSUSB:
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b128 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


LSHW -C NETWORK:
 *-network               
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: wlan0
       version: 10
       serial: 70:1a:04:02:ee:a1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8192se driverversion=1.55+Realtek Semiconductor Corp. latency=0 multicast=yes wireless=IEEE 802.11g
       resources: irq:18 ioport:a000(size=256) memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:14:00.0
       logical name: eth0
       version: 02
       serial: 00:26:22:37:78:86
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.105 latency=0 multicast=yes
       resources: irq:28 ioport:b000(size=256) memory:f0410000-f0410fff(prefetchable) memory:f0400000-f040ffff(prefetchable) memory:f0420000-f043ffff(prefetchable)

also there is a native linux driver..but i dont know how to compile it..can anyone teach me?(newbie here sorry)...here is the link to the native linux driver.. 
[http://launchpadlibrarian.net/339279...12.2009.tar.gz]("http://launchpadlibrarian.net/33927923/rtl8192se_linux_2.6.0010.1012.2009.tar.gz")

---

### Post by topsykretts on 2009-11-16
bump

---

### Post by ArcaVex on 2009-11-16
open up a terminal/konsole and try entering the key whilst its connecting via networkmanager:
e.g.:

**iwconfig wlan0 key *WEPKEY*** (replace *WEPKEY* with your key/passphrase/wpa or whichever you have)

I had the same problem and i connect running a script (not the easiest or best option, but a working one. And i rarely turn my PC off so its fine for me:

iwconfig wlan0 essid NETWORKSSID
iwconfig wlan0 key WEPKEY
dhclient wlan0


Edit:  When i tried with networkmanager it said "authenticating validation" and every 30secs would pop up asking me for the WEP key again.

---

### Post by topsykretts on 2009-11-16
hey there..archavex..tried them both and it doesnt work..heres what i got for the first one:

marc@marc-laptop:~$ iwconfig wlan0 key ************
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Operation not permitted.


and here is what i got for the second one

marc@marc-laptop:~$ iwconfig wlan0 essid njhm1
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not permitted.
marc@marc-laptop:~$ iwconfig wlan0 key *************
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Operation not permitted.

---

### Post by topsykretts on 2009-11-16
anyone?

---

### Post by chellrose on 2009-12-01
> **topsykretts said:**
> hey there..archavex..tried them both and it doesnt work..heres what i got for the first one:

marc@marc-laptop:~$ iwconfig wlan0 key ************
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Operation not permitted.


and here is what i got for the second one

marc@marc-laptop:~$ iwconfig wlan0 essid njhm1
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not permitted.
marc@marc-laptop:~$ iwconfig wlan0 key *************
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Operation not permitted.


You need to have root permissions for these.  Thus,
```
sudo iwconfig wlan0 key
```

and so on.

Hope this helps. :)

---

### Post by howdoesitmatter on 2009-12-01
Hi,
I recently migrated to Ubuntu 9.10. I have a Realtek 8172 on my lenovo. The wireless is not working. Can someone help?

---

### Post by rajeeja on 2009-12-02
One more entry to the list. Installed a fresh Ubuntu9.1 using flash drive on a preins Win7 machine.

It's a TOSHIBA L505 S5988 with a realtek 8191se. No wireless connection detected. I got back to Win7 to type this. Hoping to get a solution soon.

---

### Post by rajeeja on 2009-12-03
bump

---

### Post by northd_tech on 2009-12-04
You guys are in luck- apparently the 8192SE is much different than the Realtek 8192E that I've been trying to fix (and the 64-bit OS makes it that much worse apparently).  The 8192E version is apparently in a Samsung N120 laptop and the Toshiba Satellite P505D that I've been struggling with.

Have a look at chili555's post #2 here- that is probably what you all need for the 8192SE:

[http://ubuntuforums.org/showpost.php?p=8335065&postcount=2](http://ubuntuforums.org/showpost.php?p=8335065&postcount=2)

---

### Post by rajeeja on 2009-12-05
Thanks a lot ! 

I brings some kind of happiness to get into and out of these problems. 

Hail Ubuntu

---

### Post by d-E-a-D on 2009-12-18
Have u guys managed to put it working?
I'm using Ubuntu 9.10 64-bit and compiled rtl8192se_linux_2.6.0010.1012.2009_64.tar.gz to it. After restart I successfully see all my wireless networks and I can authenticate to them.
The problem is when I start accessing the web, after some traffic like using update-manager or surfing 2 or 3 web pages, I see signal from network-manager going down and I lost all connections. If I try to disable and enable the card, my system just crashes and I have to hard reset it... :(
If anyone can help...

Thank you

---

### Post by kjnelan on 2010-05-31
(Okay, I know it's bad form to resurrect old threads, but this does come up near the top in searches so I thought I'd post this anyway.)

If you have tried all of the above and are still having difficulty with your Realtek 8192 as I was, then read the following:

I had one bugger of a time getting the realtek 8192SE to work on my Toshiba Satellite. The fix actually was not on my computer, but on the router. The moment I changed the router from both “WPA2 AND WPA” to just WPA everything worked like a charm. I'm not a programmer and can not even begin to understand why things suddenly just worked after that change, but it did.

I've tried several live CD's, all of which now work with my wireless 8192SE after making just that one change.

Good luck all.

---

