---
title: "Wireless working but no internet - Atheros AR9285 ath9k"
date: 2011-11-24
forum: Networking &amp; Wireless
---

### Post by bmuir5 on 2011-11-24
I just received my new Dell Inspiron 15 N5040 and right away installed Ubuntu 10.04.3 LTS.  I automatically had wireless - I can see several wireless networks and can connect to mine.  However, I can't access the internet.  I am connected via wireless and can access the internet with another laptop and can access the internet with the new laptop via ethernet connection.  I've found many posts in the forums about problems with the driver but since I can connect to the wireless network I'm not sure the problem is with the driver.  Any help would be appreciated.

Output of lspci:

bmuir@bmuir-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
12:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
13:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

Output of iwconfig:

bmuir@bmuir-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"bm"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:22:75:B5:52:28   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by praseodym on 2011-11-24
Hi,

update the driver via cable:

```
sudo apt-get install linux-backports-modules-wireless-lucid-generic
```
and reboot. Check:

```
iwconfig
sudo iwlist scan
rfkill list
lsmod
```

---

### Post by bmuir5 on 2011-11-24
Thanks for the reply.  I swear I tried this before but removing and then installing the backports worked.

---

### Post by dasking on 2011-11-25
i had the same issue what it is that theres an issue with saving the connection and keeping it on what i did was disconnect and connect again

---

