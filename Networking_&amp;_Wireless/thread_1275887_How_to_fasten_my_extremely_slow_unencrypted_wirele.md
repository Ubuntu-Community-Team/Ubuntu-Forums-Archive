---
title: "How to fasten my extremely slow unencrypted wireless network"
date: 2009-09-26
forum: Networking &amp; Wireless
---

### Post by Dontknowwhat on 2009-09-26
Hey. My unencrypted wireless network to which i connect is extremely slow, like 10x slower than it should be, for example 40 kb/s instead of 400.

What must i configure to make my internet speed faster, to the maximum?

**lshw -C network** returns this

  *-network:0             
       description: Wireless interface
       product: Wireless PCI Adapter RT2400 / RT2460
       vendor: RaLink
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wmaster0
       version: 00
       serial: 00:0c:76:70:16:52
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2400pci ip=192.168.1.10 latency=32 module=rt2400pci multicast=yes wireless=IEEE 802.11b
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:02:0b.0
       logical name: eth0
       version: 10
       serial: 00:0c:76:26:50:ba
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 3a:e0:10:41:54:9e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


Do i just have to disable ethernet? If yes, how?

---

### Post by darco on 2009-09-26
Is your card an 11b? If so, 11mbs is max.....

"yes wireless=IEEE 802.11b"

Run iwconfig in a terminal and post results...

darco

---

### Post by Dontknowwhat on 2009-09-26
Hos fast is 11 mb/s? I should be having download speeds up to 500 kb/s, not 50 as i am having now in ubuntu.

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"Home"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:50:7F:90:56:70   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=40/100  Signal level:-100 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

### Post by darco on 2009-09-26
> **Dontknowwhat said:**
> Hos fast is 11 mb/s? I should be having download speeds up to 500 kb/s, not 50 as i am having now in ubuntu.

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"Home"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:50:7F:90:56:70   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=40/100  Signal level:-100 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

your bit rate says it all......
run sudo iwconfig wlan0 rate 54M
unless it is a 11b then change the rate to 11M.....

darco

---

### Post by Dontknowwhat on 2009-09-26
[I]Error for wireless request "Set Bit Rate" (8B20) :
SET failed on device wlan0 ; Invalid argument.[/I]



?

---

### Post by Dontknowwhat on 2009-09-26
OK, now i got it working at least partially.

I wrote 

*sudo iwconfig wlan0 rate 11M*

and now it download up to 200 kb/s but that isn't as fast as it can get (500) so i tried the same command using 36M and 54M but that didn't work. The message is the same as above.

How could that be that it works when 11M and not when 36 or 54?

---

### Post by darco on 2009-09-26
because you would need a card that is capable of 54m, like a 11G or N....

darco

---

### Post by Dontknowwhat on 2009-09-26
But i could download up to 500 kb/s the last time i had Ubuntu. And also on Windows XP, so my card is capable.

the problem has to be in my card rt2400pci. Is there a way i could install it with Wireless Windows Drivers? I can't find that .inf and .sys files anywhere tough.

---

