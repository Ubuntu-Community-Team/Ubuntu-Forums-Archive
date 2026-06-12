---
title: "Another &quot;slow internet&quot; case"
date: 2013-04-11
forum: Networking &amp; Wireless
---

### Post by MarkFSmith on 2013-04-11
Hello - I am new to this site so I apologise in advance if I have not supplied enough information. Since upgrading to 12.04 my wifi has been running at very slow speed - apparently I am not the only one to experience this. Normally when rebooted everything works fine for a short while and then things grind to a halt.  I have tried a number of "fixes" posted in various places but none have seemed to work. The measured rate is down at less than 10kb/s using the usb wifi card (Belkin Components F5D7050 Wireless G Adapter v3000 [Ralink RT2571W]). If I use my android phone connected to the wifi and tethered to the computer (Dell Inspiron 530) I am getting measured rates of 3-4Mb/s, so clearly something is wrong and I have run out of ideas. I would appreciate any help as I am getting very frustrated at my lack of knowledge and ability to solve this.

Many thanks, Mark

The following may be of use:

**iwconfig wlan0**
wlan0     IEEE 802.11bg  ESSID:"Gargoyle"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:BF:C4:A0:91   
          Bit Rate=24 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=40/70  Signal level=-70 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:15   Missed beacon:0

The Belkin uses RT73usb:

**lsmod | grep "rt73"**

rt73usb                27029  0 
crc_itu_t              12627  1 rt73usb
rt2x00usb              20061  1 rt73usb
rt2x00lib              48836  2 rt73usb,rt2x00usb

**sudo lshw -C network**


  *-network               
       description: Ethernet interface
       product: 82562V-2 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1e:c9:7e:02:5c
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k firmware=1.1-2 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:41 memory:fdfc0000-fdfdffff memory:fdfff000-fdffffff ioport:ff00(size=32)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlan0
       serial: 00:1c:df:5b:1c:66
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=3.2.0-32-generic-pae firmware=1.7 ip=192.168.1.103 link=yes multicast=yes wireless=IEEE 802.11bg

---

