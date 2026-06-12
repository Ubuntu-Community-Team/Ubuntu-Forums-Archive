---
title: "Wireless Problems – EEEPC 1015PE – UNR"
date: 2011-03-23
forum: Networking &amp; Wireless
---

### Post by david.flights on 2011-03-23
Hello! I am running Ubuntu Netbook Remix 10.4 with a Asus eeepc 1015PE. My problem is I cannot connect to any wireless networks, wired network is working fine. I can see availble wireless networks and when I try to connect to them, the “connection established” dialogue box appears, but in Google Chrome webrowser I  cannot access webpages. Skype does not connect. System Moniter it shows no activitiy sending or reciving data. I also cannot ping google.com or yahoo.com from the terminal. Not connected right? This is my first post request for help, and I've read many, many articles already. I am new to Ubuntu, so all help appreciated. Thanks  in advance!
   
  I have checked the BIOS for onboard devices and both WLAN and LAN are enabled.
   
  I have run sudo apt-get update while connected to the wired network. 
  I have tried (unsucesfully) sudo apt-get install linux-backports-modules-jaunty 
  I have also tried (unsucessfully) sudo apt-get install linux-backports-modules-wireless-lucid-generic 
  I have also tried (unsucesffuly) sudo apt-get install linux-backports-modules-intrepid-generic
  Here are some terminal outputs: 
   
  **david@david-1015PE:~$ lshw -C network** 
  WARNING: you should run this program as super-user. 
    *-network               
         description: Wireless interface 
         product: BCM4313 802.11b/g LP-PHY 
         vendor: Broadcom Corporation 
         physical id: 0 
         bus info: pci@0000:02:00.0 
         logical name: eth1 
         version: 01 
         serial: 74:f0:6d:4a:2d:5a 
         width: 64 bits 
         clock: 33MHz 
         capabilities: bus_master cap_list ethernet physical wireless 
         configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=10.42.43.1 latency=0 multicast=yes wireless=IEEE 802.11 
         resources: irq:17 memory:fbffc000-fbffffff 
    *-network 
         description: Ethernet interface 
         product: AR8132 Fast Ethernet 
         vendor: Atheros Communications 
         physical id: 0 
         bus info: pci@0000:01:00.0 
         logical name: eth0 
         version: c0 
         serial: 20:cf:30:10:5d:15 
         width: 64 bits 
         clock: 33MHz 
         capabilities: bus_master cap_list ethernet physical 
         configuration: broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A latency=0 multicast=yes 
         resources: irq:45 memory:f7fc0000-f7ffffff ioport:ec00(size=128) 
   
  ** david@david-1015PE:~$ iwconfig** 
  lo        no wireless extensions. 
   
  eth0      no wireless extensions. 
   
  eth1      IEEE 802.11  Access Point: Not-Associated   
            Link Quality:5  Signal level:199  Noise level:168 
            Rx invalid nwid:0  invalid crypt:0  invalid misc:0 
   
  **david@david-1015PE:~$ ping -c 5 google.com **
  ping: unknown host google.com 
   
   
  **david@david-1015PE:~$ nm-tool **
   
  NetworkManager Tool 
   
  State: connected 
   
  - Device: eth1  [riverine] ----------------------------------------------------- 
    Type:              802.11 WiFi 
    Driver:            wl 
    State:             connected 
    Default:           no 
    HW Address:        74:F0:6D:4A:2D:5A 
   
    Capabilities: 
      Speed:           8 Mb/s 
   
    Wireless Properties 
      WEP Encryption:  yes 
      WPA Encryption:  yes x`
      WPA2 Encryption: yes 
   
    Wireless Access Points (* = current AP) 
      *riverine:       Ad-Hoc, C6:AE:98:A7:1C:BF, Freq 2412 MHz, Rate 8 Mb/s, Strength 100 WEP 
   
    IPv4 Settings: 
      Address:         10.42.43.1 
      Prefix:          24 (255.255.255.0) 
      Gateway:         0.0.0.0 
   
   
   
  - Device: eth0 ----------------------------------------------------------------- 
    Type:              Wired 
    Driver:            atl1c 
    State:             unavailable 
    Default:           no 
    HW Address:        20:CF:30:10:5D:15 
   
    Capabilities: 
      Carrier Detect:  yes 
   
    Wired Properties 
      Carrier:         off 
   
  **david@david-1015PE:~$ uname -a **
  Linux david-1015PE 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux
   
   Any recommendations or help, much appreciated.

---

