---
title: "Atheros wifi very unstable"
date: 2010-10-12
forum: Networking &amp; Wireless
---

### Post by macem29 on 2010-10-12
10.04 Gnome desktop install on Acer Aspire One netbook, wifi connection very unstable since last
round of updates, wondering if ndiswrapper would work better

  
```
 macem29@awnetbook:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
04:00.0 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2382]
04:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2381]
04:00.3 System peripheral [0880]: JMicron Technology Corp. MS Host Controller [197b:2383]
04:00.4 System peripheral [0880]: JMicron Technology Corp. xD Host Controller [197b:2384]
macem29@awnetbook:~$ 
    
``````


macem29@awnetbook:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"XXXXX network"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1C:F0:F0:C5:6C   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

macem29@awnetbook:~$ 
    
```any advice? thanks in advance

---

### Post by macem29 on 2010-10-12
well, more reading and can't find the answer, so thought I'd try a bump, hope to not get flamed too
badly...tried to edit the thread title to be more specific but can't....so here goes: bump

---

### Post by macem29 on 2010-10-13
well, tons more reading, got something working now....will see how stable it is...madwifi Atheros drivers,

instructions here:

[http://ubuntuforums.org/showthread.php?t=1484242&highlight=remove+madwifi](http://ubuntuforums.org/showthread.php?t=1484242&highlight=remove+madwifi)

ran the procedure twice to get it installed without errors, gnome network manager did not seem to like
the madwifi driver, so removed it and installed wicd manager, that worked, was able to see my AP...
wicd would not accept the password, I know it was correct, killed wicd and back to gnome manager,
now it like the driver, scanned and got connected...now I see my wifi has dropped again in the time
it took me to two finger type these few sentences..was gonna change thread status to solved, guess not,
a lot of people here like to slam windows but I'm telling ya all this grief started when I took the last kernel
update and a system restore point sure would be handy for me now...guess I'll keep messing with this
and hope that it gets addressed properly in a another update, been nice chatting with myself :P

---

### Post by bigfootnmd on 2010-10-13
I assume that the instability in the atheros Madwifi drivers you are experiencing happen after a kernel update.  If so
try checking out this

[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

Please pay careful attention to what is said about kernel updates.

Another solution is to load Ubuntu 10.10 which has NATIVE ATHEROS WIFI drivers.

Good luck.

---

### Post by macem29 on 2010-10-15
thanks bigfoot, yes, I had made note of kernel updates killing the madwifi solution...
last 24 hours it's actually been stable, so I've marked the tread solved, a little
leary of updating to 10.10....10.04 was initially rock solid, the last kernel update
seemed to cause the wifi issues and I don't feel like messing around with a
possibly troublesome 10.10 install

---

### Post by putt1ck on 2011-02-25
Intriguingly... 10.10 clean build on Z61t Thinkpad. Kernel updates within the last week. Since wifi crashes when moving consistent data flows e.g. large background download while still using browser for other stuff. Happened 3 times in two days, a reboot resolves it, presuming that a reload of whichever module that has failed would also resolve it.

Very specific symptom - wifi doesn't look like it has crashed and can still "see" the various wifi networks in the area, but it cannot connect to my WPA2 PSK 802.11b/g - it tries but cannot get past the configuring interface stage. Not looked at any logs as yet, but the connection between the kernel update was "quite strong".

---

