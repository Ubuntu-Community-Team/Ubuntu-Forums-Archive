---
title: "slow wireless on Dell D800 / Broadcom BCM4306"
date: 2013-04-15
forum: Networking &amp; Wireless
---

### Post by zx2max on 2013-04-15
I am running Ubuntu 11.10 on a Dell D800. My wireless connection is very slow. When I connect directly to modem via ethernet cable I get download speeds of about 60Mbps but when I am on wireless I am only getting about 3Mbps. Here is my output from running lshw -C network as well as iwcofig. Any help would be greatly appreciated. Thanks!

```
*-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:ac:cb:28
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.119 duplex=full firmware=5705-v3.11 latency=32 link=no mingnt=64 multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:11 memory:faff0000-faffffff
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:5 memory:fafec000-fafedfff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:63:c8:38
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43legacy driverversion=3.0.0-12-generic firmware=295.14 ip=10.0.0.7 link=yes multicast=yes wireless=IEEE 802.11bg

```


iwcofig

```
ryan@ryan-Latitude-D800:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Pretty Fly for a Wifi"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:D3:1C:05:C0   
          Bit Rate=18 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:7695  Invalid misc:737   Missed beacon:0
```

---

### Post by zx2max on 2013-04-17
suggestions, anyone? is there any additional information I can provide which would help solve my issue?

---

### Post by mörgæs on 2013-04-17
As a first unscientific approach I would begin with a clean install of 12.10. You have to leave 11.10 anyway in a few weeks.

I like your ESSID :-)

---

### Post by zx2max on 2013-04-17
Thanks. I saw someone else with that ESSID and had to use it. 

I had upgraded to 12.10 but was having problems with the graphics card drivers. My display would not fill the screen (black bars on the sides) and the VGA output didn't work. I was told that my old computer wasn't supported and was advised to downgrade to 11.10 to lower to fix my video card issue. ahhh..trade one problem for another.

---

### Post by mörgæs on 2013-04-18
Now I saw your other thread. The advice given there was not good.

Your graphics card is not strong enough for Ubuntu, but L/Xubuntu 12.10 is a good choice. Try first with only open-source drivers.

---

