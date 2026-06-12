---
title: "Slow wireless internet connection"
date: 2013-05-14
forum: Networking &amp; Wireless
---

### Post by daniel488 on 2013-05-14
Hi,

my problem is that my wifi internet connection is very slow, up to 80kB/s but often much slower. Typicall speed is about 600-700 kB/s and it's what I achive on Windows 7. This problem appeard when I was using Ubuntu 12.10. Couple of days ago I installed 13.04 (fresh installation, only /home mounted on another partion is like previously), but it doesn't solve my problem. 
Can you help?

A little related infos:

**iwconfig**:
```
wlan0     IEEE 802.11bgn  ESSID:"primavera"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:39:A5:F6:48   
          Bit Rate=48 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:941  Invalid misc:289   Missed beacon:0

```

**lshw -C network:**
```
*-network
       description: Network controller
       product: BCM43225 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:da400000-da403fff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 88:9f:fa:6e:5d:2a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.8.0-20-generic firmware=N/A ip=192.168.1.100 link=yes multicast=yes wireless=IEEE 802.11bgn
```

---

### Post by praseodym on 2013-05-14
Update the firmware for the driver:
```

wget media.cdn.ubuntu-de.org/forum/attachments/56/18/5007272-Broadcom_Firmware_070513.tar.gz
sudo tar xvf 5007272-Broadcom_Firmware_070513.tar.gz -C /lib/firmware
```
Shutdown currentless for 10 minutes afterwards.

---

### Post by daniel488 on 2013-05-14
Hmm, interesting, I updated it and waited 10 minutes. Then I made speed test on [speedtest.net]("http://speedtest.net") The result was: 0,7 Mb/s download and 4 Mb/s upload. Then I decided to make test on Windows. It was 6,6 Mb/s down and 17,3 Mb/s up. After that I started Ubuntu again and I saw that forum was loaded much faster, new test show 17,1 Mb/s up (yes, up :) ) and 11,5 Mb/s down. I hope it will remain. 

Thanks for your help :)

---

