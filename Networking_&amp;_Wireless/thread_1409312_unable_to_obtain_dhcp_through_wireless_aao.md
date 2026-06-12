---
title: "unable to obtain dhcp through wireless aao"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by grandmaster on 2010-02-17
/im having the same issues.
linksys router and an acer aspire one.

I have updated to the 9.10 netbook remix and the laptop associates with the router but will not pickup dhcp.

If i specify an address then the machine looks like its connected but will not go to a website.
I manually inserted dns but still nothing.

so i updated to 

linux-backports-modules-karmic-generic
linux-backports-modules-wireless-karmic-generic

Still will not use DHCP , I to am using ethernet at the moment.
Any ideas?

It was working before the update. 

Thanks..

---

### Post by chili555 on 2010-02-17
@grandmaster

Please start a new thread and post:```
iwconfig
lspci -nn
```We will reply as soon as we can. Thanks.

---

### Post by grandmaster on 2010-02-17
/im having the same issues as [http://ubuntuforums.org/showthread.php?p=8840775#post8840775](http://ubuntuforums.org/showthread.php?p=8840775#post8840775)

linksys router and an acer aspire one.

I have updated to the 9.10 netbook remix and the laptop associates with the router but will not pickup dhcp.

If i specify an address then the machine looks like its connected but will not go to a website.
I manually inserted dns but still nothing.

so i updated to

linux-backports-modules-karmic-generic
linux-backports-modules-wireless-karmic-generic

Still will not use DHCP , Iam using ethernet at the moment.
Any ideas?

It was working prior to the update.

---
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"vogon"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <mac address removed>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)

---

### Post by grandmaster on 2010-02-17
ok, I have changed my wireless channel and the machine associated and grabbed an address.

strange though, unless there was too much interference on that channel but my other clients dont seem to have an issue.

the real test will be when i reboot.

---

### Post by grandmaster on 2010-02-17
I dont know if this helps but I changed the wireless channel on my router and the machine associated and obtained an address.

I have not rebooted yet so well see if this is a permanent fix.

ill update later.

GM

---

### Post by grandmaster on 2010-02-17
ok i rebooted and the machine picked up the wireless :popcorn:
fantastic

---

### Post by Elfy on 2010-02-17
Please do not hijack someone elses thread and then post one for yourself, posts merged.

---

