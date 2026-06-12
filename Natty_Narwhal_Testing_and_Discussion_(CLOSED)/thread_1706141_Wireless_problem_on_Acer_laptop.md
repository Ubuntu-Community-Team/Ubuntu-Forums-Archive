---
title: "Wireless problem on Acer laptop"
date: 2011-03-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Mesanna on 2011-03-13
Hi folks, I'm having a hell of a problem getting wireless to work on Natty and wonder if anyone could give me some pointers. I'm no guru but I've done a bit of Googling and tried a few things, but I don't know what to try next. My laptop is an Acer Aspire TimelineX 4820T. This is a clean install of Natty Alpha 3 with all updates available installed. I installed the Broadcom proprietary drivers when the system prompted me.

When I first switch on the laptop, I have to click on the network icon on the taskbar to tick Enable Wireless, (though it doesn't seem to make any difference). There is a light on the front of the laptop itself, showing wireless is switched on, so as far as I can tell wireless is physically enabled on the laptop.

When I type **sudo iwconfig**, I get the following:

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:144 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=5/5  Signal level=0 dBm  Noise level=-11 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I think the problem line is Access Point:-Not Associated.

When I type **sudo ifconfig**, I get the the following:

```
eth0      Link encap:Ethernet  HWaddr c8:0a:a9:95:69:6a  
          inet6 addr: fe80::ca0a:a9ff:fe95:696a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:28710 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16486 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:40290622 (40.2 MB)  TX bytes:1485702 (1.4 MB)
          Interrupt:43 

eth1      Link encap:Ethernet  HWaddr 78:e4:00:36:08:d1  
          inet6 addr: fe80::7ae4:ff:fe36:8d1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:336 errors:0 dropped:0 overruns:0 frame:0
          TX packets:336 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24992 (24.9 KB)  TX bytes:24992 (24.9 KB)
```

If I type **sudo iwlist eth1 scan**, it sees my router (as well as a bunch of others), but I just don't know how to make it connect.

Typing **sudo lshw -C network** gives the following output:

```
  *-network               
       description: Ethernet interface
       product: AR8151 v1.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: c8:0a:a9:95:69:6a
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:d3400000-d343ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: BCM43225 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 78:e4:00:36:08:d1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d2400000-d2403fff
```

If I type **sudo rfkill list**, I get the following:

```
0: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

Obviously that first line "**Soft blocked: yes**" must be the problem, but I don't know how to fix it. I tried typing **sudo rfkill unblock all**, but, for some reason, this turns off the wifi light on the front of the laptop, and I need to type **sudo ifconfig eth1 up** for the light to come back on. 

If I type **sudo nm-tool** into the terminal, I get this:

```
NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        C8:0A:A9:95:69:6A

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             unavailable
  Default:           no
  HW Address:        78:E4:00:36:08:D1

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 



```

NB Wired ethernet works perfectly, I just didn't have an ethernet cable plugged in while I ran these tests. 

Obviously the laptop is detecting the network card and that fact that it can scan and see a bunch of wifi connections in the area would imply that there's nothing physically wrong. I can ping 127.0.0.1, but I can't ping my router on 192.168.0.1. It says Network is unreachable. I tried to manually configure a network connection using a tutorial I found, but with no joy. I turned off the security password on my router for testing purposes too, but that didn't make any difference either.

I hope I've included enough information for someone to give me some ideas of what to try next. If you need anything else, let me know. Thanks in advance :)

---

### Post by -::Bas::- on 2011-03-14
Unfortunately I have no solution for your problem, but I have the 'exact' same problem.:(
On an Acer Travelmate 8172Z, with Braodcom n card, I get the exact same results as you trying to connect to my wifi.
I'm a bit confused as to why the kernel doesn't seem to want to activate the card correctly.

---

### Post by Mesanna on 2011-03-14
Well at least I'm not alone ;)

It's annoying when wireless works perfectly on the previous release but won't work on the new version. I really wanted to test out Natty but if I can't get the internet working, then there's not much point.

I'll wait another day or so and see if anyone else has any suggestions, but otherwise I'm going to have to go back to Maverick.

---

### Post by -::Bas::- on 2011-03-14
I've ordered a new wireless network card (Atheros) hoping the driver is in the kernel and working. It never felt good anyway havin the binary Broadcom blob in my system.. :-)

But I still want this sorted out, for other people's sake.

/edit: for some reason the Taheros dodn't work in the Acer. Already sold the laptop and am back on the Lenovo form work which works out of the box..

---

