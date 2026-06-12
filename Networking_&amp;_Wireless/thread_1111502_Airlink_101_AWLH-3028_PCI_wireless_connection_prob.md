---
title: "Airlink 101 AWLH-3028 PCI wireless connection problem"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by dagarshali on 2009-03-30
Hi,
I have asked the same question on this forum and I hadn't had any response to it.. I then read through the instructions for posting a thread and I apologize for not following that.

here are the outputs for most of the commands that the threads asks us to post.

machine: Intel Core2 Duo, 4gb ram
Ubuntu: 8.10 Intrepid
Kernel: 2.6.27-11-generic

**lspci**
```
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
03:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185] (rev 20)
```

**iwconfig wlan1**
```
wlan1     IEEE 802.11g  ESSID:"DaGaRsHaLi"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:1F:33:23:B6:B4   
          Bit Rate=54 Mb/s   Tx-Power:46 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:96/100  Signal level:-34 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

**sudo lshw -C network**
```
  *-network
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:03:01.0
       logical name: wlan1
       version: 20
       serial: 00:18:e7:34:47:06
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8185 driverversion=1.53+Realtek,03/21/2008,5.1105.0 ip=192.168.1.4 latency=64 link=yes maxlatency=64 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 6a:26:c2:28:ff:1a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

**iwlist wlan1 scan**
```
wlan1     Scan completed :
          Cell 01 - Address: 00:14:6C:9F:4C:34
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:76/100  Signal level:-47 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:1F:33:23:B6:B4
                    ESSID:"DaGaRsHaLi"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:95/100  Signal level:-35 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:13:10:4F:F4:37
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:73/100  Signal level:-49 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:21:29:91:2C:EB
                    ESSID:"KentNet"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.427 GHz (Channel 4)
                    Quality:34/100  Signal level:-74 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: 00:0B:6B:35:C5:53
                    ESSID:"2403fern1"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.432 GHz (Channel 5)
                    Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 06 - Address: 00:40:F4:FD:72:1A
                    ESSID:"Ida"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:48/100  Signal level:-65 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 07 - Address: 00:11:95:1A:B7:02
                    ESSID:""
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:50/100  Signal level:-64 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 08 - Address: 00:22:6B:96:BB:DC
                    ESSID:"home"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:48/100  Signal level:-65 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: 00:22:3F:24:BB:E2
                    ESSID:"BiBis Spot"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:48/100  Signal level:-65 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: 00:30:BD:C4:E4:70
                    ESSID:"TEVISABH"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:51/100  Signal level:-63 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 11 - Address: 00:1C:DF:5E:36:7D
                    ESSID:"BriPhiWiFi"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:51/100  Signal level:-63 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: 00:13:10:79:22:22
                    ESSID:"linksys - jji"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:48/100  Signal level:-65 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 13 - Address: 00:0F:66:42:52:54
                    ESSID:"MBST"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:48/100  Signal level:-65 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 14 - Address: 00:21:29:A0:BE:C1
                    ESSID:"Deutscher"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

```
[B]
uname -m[/B]r
```
2.6.27-11-generic i686
```
[B]
sudo /etc/init.d/networking restart[/B]
 ```
* Reconfiguring network interfaces...                                          Ignoring unknown interface wlan1=wlan1.
```

**ndiswrapper -l**

```
net8185 : driver installed
	device (10EC:8185) present (alternate driver: rtl8180)
```

The problem is as follows.. I install the wireless driver via ndiswrapper gui. I have tried using net8185.inf for both windows98 and windowsxp. Both have resulted in the same, the result being disconnecting from the network after some time. It wont connect again, even if I select the network. But, I have noticed that if I remove the driver and reinstall again, it connects to the wireless.

The wireless router that i use is Netgear WRG614 and I have am using WPA encryption and I also have a mac address filtered turned on in the router. 

I hope that you guys can shed some light and show me how to fix this problem.

Thanks a bunch in advance..

Vishwa

---

### Post by TBerk on 2009-03-30
I was able to use my realtek's native driver (no ndiswrapper for me) but then I have the rt2860 chipset based pci wireless nic. 

[In fact, you may find quite a lot of diagnostic help by searching the forums for the threads that pertain to "rt2860".] 

Primary to getting a solid connection in 8.10 (at least for me) was ditching the default **network-manager** in favour of **wicd**; 

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) (You can get it via synaptic Package Manager.)

[In fact, you may find quite a lot of diagnostic help by searching the forums for the threads that pertain to "rt2860".] 

One last thing, I recently reinstalled Ubuntu w/ the new beta 9.04 and my existing wireless network card was automatically supported without need for installing ala carte drivers.

With the rollout of 9.04 just around the corner you might look into it's support for your version of network card- it might also apply as a 'fix'.

btw- Despite the fact that I myself haven't touched on it; your inclusion of the data is a good thing.


hth,
TBerk

---

### Post by tgalati4 on 2009-03-30
The card works for me under gutsy using WEP and ndiswrapper with XP drivers. Oh, PIII, 400 MHz.  Not exactly similar.

Card works reliably after suspend. Using a Netgear a/g router.

Try a booting with a live Hardy CD, then set up wireless and test to see if it works for a few days.

---

### Post by dagarshali on 2009-04-04
Hi guys,
Thanks for the response..
I did install WICD and it was working fine for the last couple days and the problem started again today. I would have connected to internet and after some time it disconnects and when click on the wicd manager it say no networks found.. 

At this point if i remove the wireless driver and reinstall the driver, it connects again.. I really am going crazy with this wireless thing.. Can you please help...

I have WPA and mac filtering on my router..

I have ubuntu 8.10 intrepid installed

Regards,
Vishwa

---

### Post by TBerk on 2009-04-09
I'd like to ask, why ndiswrapper and not..

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8185L](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8185L) ?

...the native driver?


TBerk

---

### Post by dagarshali on 2009-04-09
2.6.27-11-generic is the kernel that I have.. Would it still work cos it xas 2.6.22 kernel on the link that you sent me....

Also, how do I install those drivers..?

---

### Post by TBerk on 2009-04-09
> **dagarshali said:**
> 2.6.27-11-generic is the kernel that I have.. Would it still work cos it xas 2.6.22 kernel on the link that you sent me....

That is a very good question, one I'm not yet sure I know the answer to yet.

> 
Also, how do I install those drivers..?


Ah, that I can likely help with. Prior to installing 9.04 I was compiling a similar driver (rt2860) for Ubuntu 8.10. 

Let me get together my 'notes' and I'll repost...

---

### Post by dagarshali on 2009-04-11
> **TBerk said:**
> That is a very good question, one I'm not yet sure I know the answer to yet.




Ah, that I can likely help with. Prior to installing 9.04 I was compiling a similar driver (rt2860) for Ubuntu 8.10. 

Let me get together my 'notes' and I'll repost...

I found this link 
[http://wiki.debian.org/rtl818x](http://wiki.debian.org/rtl818x) would this work for my pci card..

the output of lspci is as below

> 00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

---

### Post by TBerk on 2009-04-13
> 
Let me get together my 'notes' and I'll repost...

OK, looks like I pulled a bonehead move and 'restored' my Bookmark archive over the top of my current bookmarks; wiping out the links I was looking for.

Let me see if I can recreate a few of them for you.


[http://ubuntuforums.org/showthread.php?t=966185&highlight=howto+install+wireless+driver](http://ubuntuforums.org/showthread.php?t=966185&highlight=howto+install+wireless+driver)

OK, that link is a really good one, but it'll need some copy/paste with the files and names of your particular equipment.

Still, if you can use it, it might just fix our problem.


TBerk

---

