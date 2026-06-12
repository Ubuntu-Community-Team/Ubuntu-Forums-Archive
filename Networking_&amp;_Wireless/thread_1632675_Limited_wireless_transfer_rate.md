---
title: "Limited wireless transfer rate"
date: 2010-11-28
forum: Networking &amp; Wireless
---

### Post by deviant on 2010-11-28
Hello guys, 

Having the most annoying issue. When I use my WiFi connection, after a couple of minutes my transfer is limited to ~130kps, regardless of what / how I download: browsing, wget, torrent, etc.
The only way to regain full download speed is to disconnect and reconnect to the router, which is hardly a solution.

Just to make it clear, it is NOT throttling because I have 3 more computes on the same router, running Win XP/7, and none of them has this issue -> which led to believe that this is related to my Linux box.

I`m using 10.04.1 x64, Acer Travelmate 6592. 
I`m connected to a Linksys WRT54GL running DD-WRT, WPA/WPA2 encryption.
Driver iwlang for my Intel Wifi, 54Mb/s speed, signal around 80-90 / 100.


lshw -c Network:
```
*-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:a0:d1:a8:1f:99
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=0.3-0 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:29 memory:fc400000-fc41ffff memory:fc425000-fc425fff ioport:1840(size=32)
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 61
       serial: 00:1d:e0:19:79:a5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.102 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:31 memory:fa000000-fa001fff

```

lshw | head: 
```
portable                  
    description: Computer
    product: TravelMate 6592
    vendor: Acer
    version: PSMBOU-1234567
    serial: LXTNE0Z64983002E112300
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: administrator_password=disabled boot=oem-specific frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=8AED27C0-3F04-11DD-A70E-00A0D1A81F99
  *-core

```

iwconfig: 
```
wlan0     IEEE 802.11abgn  ESSID:"XXXXXXX"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:18:F8:F1:F0:04   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

ifconfig: 
```
wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:19:79:a5  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:e0ff:fe19:79a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1781594 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1392774 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1875596552 (1.8 GB)  TX bytes:735013429 (735.0 MB)

```

---

### Post by deviant on 2010-11-28
Tailing /var/log/syslog, it seems that each time my connection is dropping speed, I get this : 

```
Nov 28 22:30:23 Portable kernel: [30601.984315] iwlagn 0000:06:00.0: Microcode SW error detected.  Restarting 0x82000000.
Nov 28 22:30:23 Portable kernel: [30602.237844] Registered led device: iwl-phy0::radio
Nov 28 22:30:23 Portable kernel: [30602.237876] Registered led device: iwl-phy0::assoc
Nov 28 22:30:23 Portable kernel: [30602.237902] Registered led device: iwl-phy0::RX
Nov 28 22:30:23 Portable kernel: [30602.237932] Registered led device: iwl-phy0::TX

```

LE:
After some more google-ing, it seems that this is related to temperature of the WiFI chip - it`s getting hot and when it reaches ~60C - KABOOM, it drops / slows the connection. 

Now, the sad part - this used to be a issue with kernel 2.6.27 and I`m currently on 2.6.32.26.

One work-around for this was to let the chip manage the power level, but when i do "sudo iwconfig wlan0 power on" I get:

```
 itch@Portable:~$ sudo iwconfig wlan0 power on
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.

```

So, any other suggestions ?

---

### Post by cybergnome on 2010-11-28
Since internet download rates can vary with respect to the internet itself, the real way to test is to measure DTR across the LAN.  If that corroborates your findings, I might wonder if computer performance issues on the wireless machine are slowing it down.  You can experiment with that by varying the load while using wireless or even simplifying the encryption.

You might also want to try another wireless adapter and see if it experiences the same problem.  If not, then the device may be failing.

---

### Post by deviant on 2010-11-28
@cybergnome: thank you for your answer. 
One question though: what exactly is DTR and what tool / method would you recommend to perform the test. 

Also, I`m not complaining here about latency & so. But when my connection is "neutered" from 2Mb to something like 130kps, while the other notebook next to mine is downloading the same file from the same location on the same router it makes me believe that the issue is in my sandbox not on the Big Bad Internet :)

---

### Post by uncaspi on 2010-11-28
To ensure you not have been hacked please stay connected and close all applications and do sudo tcpdump -i wlan0

assuming your wlan interface is wlan0.

If there are heavy traffic through your card when all app is shut down you've been hacked or got a worm.

---

### Post by deviant on 2010-11-28
@uncaspi: thank you for your suggestion. I will try that. 
But I`m quite sure I`m not hacked. 
A [search](http://www.google.ro/webhp?sourceid=chrome-instant&ie=UTF-8&ion=1#hl=ro&expIds=17050,25657,26486,27080,27819&xhr=t&q=iwlagn+0000%3A06%3A00.0%3A+Microcode+SW+error+detected.++%22Restarting+0x82000000%22&cp=74&pf=p&sclient=psy&site=webhp&aq=f&aqi=&aql=&oq=&gs_rfai=&pbx=1&fp=ddf48388b8228db9&ion=1) will bring lots of forums and discussion boards full of ppl complaining about the same issue. I find it hard to believe that all those ppl are also being hacked :D

---

### Post by uncaspi on 2010-11-28
That's right but it could be a worm. Try to eliminate the possibilities.

---

### Post by cybergnome on 2010-11-28
If the chip IS overheating, the only practical solution is to cool your system.  That's fan's for a desktop, and perhaps a cooling lap for a laptop.  Overheating leads to eventual failure. :-(

---

### Post by deviant on 2010-11-29
I`m sticking to my idea that this is software related. I`ve been having this notebook for like 2 years and never experienced something like this, yet the moment I reverted to 10.04.1, BOOM, all of a sudden I`m getting this. And as other ppl mention across the Internet, it is actually some error with microcode from Intel`s driver. 

I will try to compile the latest one as soon as I get home and see how it goes. 
Ultimately I can buy another WiFi adapter for my notebook, provided that this one is not soldered to MB. Though I`m hoping this won`t be necessary.

---

