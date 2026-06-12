---
title: "ubuntu 11.4 - Intel Wireless WiFi Link 4965AGN"
date: 2011-06-07
forum: Networking &amp; Wireless
---

### Post by me_loco on 2011-06-07
as per pytheas22, i'm attaching few details here.
my download speed would starts at 470 kB/s and gradually decreases until it reaches 116 kB/s. Loading web pages seems to be fine.


please help.
thanks.


Thinkpad T61

time wget yahoo.com

--2011-06-07 22:53:49--  [http://yahoo.com/](http://yahoo.com/)
Resolving yahoo.com... 67.195.160.76, 69.147.125.65, 72.30.2.43, ...
Connecting to yahoo.com|67.195.160.76|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://www.yahoo.com/](http://www.yahoo.com/) [following]
--2011-06-07 22:53:49--  [http://www.yahoo.com/](http://www.yahoo.com/)
Resolving [www.yahoo.com](www.yahoo.com)... 69.147.125.65, 209.191.122.70, 67.195.160.76, ...
Connecting to [www.yahoo.com|69.147.125.65|:80](www.yahoo.com|69.147.125.65|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://ca.yahoo.com/?p=us](http://ca.yahoo.com/?p=us) [following]
--2011-06-07 22:53:49--  [http://ca.yahoo.com/?p=us](http://ca.yahoo.com/?p=us)
Resolving ca.yahoo.com... 67.195.160.76, 69.147.125.65, 209.191.122.70, ...
Connecting to ca.yahoo.com|67.195.160.76|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html.2'

    [   <=>                                 ] 146,453      267K/s   in 0.5s    

2011-06-07 22:53:50 (267 KB/s) - `index.html.2' saved [146453]


real	0m1.359s
user	0m0.016s
sys	0m0.020s


---------------------------------------------------------------


time wget 74.125.91.105

--2011-06-07 22:56:15--  [http://74.125.91.105/](http://74.125.91.105/)
Connecting to 74.125.91.105:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html.3'

    [ <=>                                   ] 9,463       --.-K/s   in 0.007s  

2011-06-07 22:56:15 (1.21 MB/s) - `index.html.3' saved [9463]


real	0m0.129s
user	0m0.012s
sys	0m0.000s


----------------------------------------------------------------


lspci -nn

00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) [8086:2a03] (rev 0c)
00:19.0 Ethernet controller [0200]: Intel Corporation 82566MM Gigabit Network Connection [8086:1049] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller [8086:2811] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller [8086:2828] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4230] (rev 61)
15:00.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev ba)
15:00.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 04)


---------------------------------------------------------------


iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"In-Fire-Baptize"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:22:6B:9C:3B:4F   
          Bit Rate=72.2 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1133  Invalid misc:12   Missed beacon:0


----------------------------------------------------------------


dmesg | grep -e iwl -e wlan

[   14.103524] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   14.103527] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   14.103593] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.103603] iwlagn 0000:03:00.0: setting latency timer to 64
[   14.103633] iwlagn 0000:03:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[   14.142134] iwlagn 0000:03:00.0: device EEPROM VER=0x36, CALIB=0x5
[   14.142138] iwlagn 0000:03:00.0: Device SKU: 0Xb
[   14.145312] iwlagn 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   14.145406] iwlagn 0000:03:00.0: irq 46 for MSI/MSI-X
[   14.233789] iwlagn 0000:03:00.0: loaded firmware version 228.61.2.24
[   14.502195] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   14.786526] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.914299] wlan0: authenticate with 00:22:6b:9c:3b:4f (try 1)
[   31.916065] wlan0: authenticated
[   31.916090] wlan0: associate with 00:22:6b:9c:3b:4f (try 1)
[   31.919843] wlan0: RX AssocResp from 00:22:6b:9c:3b:4f (capab=0x411 status=0 aid=2)
[   31.919847] wlan0: associated
[   31.959843] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   42.352036] wlan0: no IPv6 routers present
[   67.228038] iwlagn 0000:03:00.0: iwlagn_tx_agg_start on ra = 00:22:6b:9c:3b:4f tid = 0

---

### Post by pytheas22 on 2011-06-08
Thanks for the information.  I can tell from your command output that loading webpages is fine (wget worked without a problem), and there's nothing in dmesg to indicate an issue.  So that's good, but also leaves me with little idea as to what the cause of the issue could be.

What kind of files are you trying to download that become slow?  If you could post a link to a specific example of what you're downloading so that I could try downloading it myself, that would be great.  And are you sure the issue is on your computer's end, and not a problem with the uploading server, or with your wireless router or Internet connection?

---

### Post by me_loco on 2011-06-08
> **pytheas22 said:**
> Thanks for the information.  I can tell from your command output that loading webpages is fine (wget worked without a problem), and there's nothing in dmesg to indicate an issue.  So that's good, but also leaves me with little idea as to what the cause of the issue could be.

What kind of files are you trying to download that become slow?  If you could post a link to a specific example of what you're downloading so that I could try downloading it myself, that would be great.  And are you sure the issue is on your computer's end, and not a problem with the uploading server, or with your wireless router or Internet connection?

i noticed it when downloading fedora 15 iso, it would gradually drop down in speed. Others suggested that i turn network wireless switch off while booting then put it back on when system is up. I checked last night and was working just fine.

Thank you for trying to help me.

---

### Post by pytheas22 on 2011-06-08
> i noticed it when downloading fedora 15 iso, it would gradually drop down in speed. Others suggested that i turn network wireless switch off while booting then put it back on when system is up. I checked last night and was working just fine.

Thank you for trying to help me.

It doesn't make much sense to me that disabling the wireless while the computer is booting would make a difference.  But I don't know everything.

If it works now, I would suspect that the problem was not on Ubuntu's end, but either with your Internet connection or the server that was uploading the ISO file to you.  Your wireless card should work very well with Ubuntu; Intel wireless chips are probably the best you can have on Linux.

---

### Post by grahammechanical on 2011-06-09
The other month when trying to download the 11.04 ISO image I found that the 700MB CD download was going to take about 7 hours but the 4GB DVD download would take less than 2 hours. Two different servers were being used for these download services.

I also found it quicker to download the DVD ISO image than to do a distribution upgrade. That was due to the high demand at the time. A few weeks later I did complete a distribution upgrade and it was very fast.

So, failing download speeds could most certainly be due to the ability of the server to serve up the file and not to the OS.

Regards.

---

### Post by pytheas22 on 2011-06-09
> The other month when trying to download the 11.04 ISO image I found that the 700MB CD download was going to take about 7 hours but the 4GB DVD download would take less than 2 hours. Two different servers were being used for these download services.

I also found it quicker to download the DVD ISO image than to do a distribution upgrade. That was due to the high demand at the time. A few weeks later I did complete a distribution upgrade and it was very fast.

So, failing download speeds could most certainly be due to the ability of the server to serve up the file and not to the OS.

Good point.  Downloading Ubuntu ISOs is always very slow if you do it right after a new release, because everyone else is doing it too.  I usually just download the ISOs via torrents, which puts less stress on Canonical's servers and tends to be much faster :)

---

