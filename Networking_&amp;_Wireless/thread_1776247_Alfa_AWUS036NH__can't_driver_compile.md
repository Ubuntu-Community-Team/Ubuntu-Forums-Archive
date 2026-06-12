---
title: "Alfa AWUS036NH  can't driver compile"
date: 2011-06-05
forum: Networking &amp; Wireless
---

### Post by ScourKing on 2011-06-05
I am totally new to Linux and am using the Umbuntu 11.04 latest stable release as of June 5 2011. I have a Alfa AWUS036NH that I have downloaded the lastest drivers from Alfa. I have read for 3 days straight and tryed so many fixes I cant remember them all. My problem is that it connects then after about 15 minutes the connection degrades and i have to unplug and replug in and then it goes down sooner each time. I have edited the black list and blacklisted all the 2870 chipsets as mine has 3070 chipset. once i edited the blacklist I can no longer boot into linux unless I unplug my Alfa (usb) and then once I am into the UI I can plug it back in but the wirless management client up by the top right of my screen that came with ubuntu no longer sees the card and when I do the show devices command from a terminal it doesn't show the adapter either. I also have a wired eth0 that works and a wireless wlan0 thats an internal Aethros that works. After blacklisting though it no longer shows it's name in the wireless manager but does show the connections. I am getting errors when trying to compile the manufactors drivers. I have renamed the 2 files as per several posts and still errors. I have read it works if you load the intel 2200 drivers. I got the compiler and everything but am missing the ieee80211 wireless what evers to compile and make it work. I am at wits end at what to do now to fix it. I am to a point i have typed so much in terminal i dont know what to post to help but maybe starting from scratch will help and i am totally open to.

---

### Post by ScourKing on 2011-06-05
Since posting the above I read [http://ubuntuforums.org/showthread.php?t=1407165&highlight=ralink+3070&page=2](http://ubuntuforums.org/showthread.php?t=1407165&highlight=ralink+3070&page=2) which is my exact problem I have re-edited my blacklist to match the last post in the article. I was trying to compile the same driver from Alfa. I get error codes. When I reboot after the edit of the blacklist my onboard wireless works but doest show the name of the built in netwrok config program on my tool bar in upper right but does show it's connected. As far as my Alfa goes it show nothing and also nothing when i do 
dmesg | grep -e rt2 -e rt3
iwconfig

root@chase-Satellite-L25:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"dd-wrt"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 68:7F:74:26:1F:0A   
          Bit Rate=12 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=34/70  Signal level=-76 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:98   Missed beacon:0

If I remove the blacklisted drivers I then get an wlan1 that says 2870 (as well as having the wlan0) which is the wrong driver but then it also gives me the name of both in the interface on the upper right bar of both devices.

No matter what i try i cant get the built in 3070 or compile my own 3070 driver to load on its own or by my manipulation. Its a toshiba l25-s1195 laptop wit an onboard  Aethros b/g card. I wanted the Alfa for my linksys 320n router for more speed.

---

### Post by ScourKing on 2011-06-05
Here is some more info to help I removed the blacklisted drivers and here is the output
root@chase-Satellite-L25:~# dmesg | grep -e rt2 -e rt3
[   26.753546] Registered led device: rt2800usb-phy1::radio
[   26.753617] Registered led device: rt2800usb-phy1::assoc
[   26.753685] Registered led device: rt2800usb-phy1::quality
[   26.761470] usbcore: registered new interface driver rt2800usb
[   26.766716] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   26.804779] usbcore: registered new interface driver rt2870
root@chase-Satellite-L25:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"dd-wrt"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 68:7F:74:26:1F:0A   
          Bit Rate=9 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=34/70  Signal level=-76 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:104   Missed beacon:0

wlan1     IEEE 802.11bgn  ESSID:"dd-wrt"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 68:7F:74:26:1F:0A   
          Bit Rate=120 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:68   Missed beacon:0

and more

root@chase-Satellite-L25:~# lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

and more

root@chase-Satellite-L25:~# lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:09:02.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:eb:d8:24
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:21 ioport:a000(size=256) memory:c0210000-c02100ff
  *-network:1
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:09:04.0
       logical name: wlan0
       version: 01
       serial: 00:11:f5:a2:2c:f5
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-8-generic firmware=N/A ip=192.168.1.109 latency=168 link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:22 memory:c0200000-c020ffff
  *-network
       description: Wireless interface
       physical id: 3
       bus info: usb@1:8
       logical name: wlan1
       serial: 00:c0:ca:4a:db:91
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=2.6.38-8-generic firmware=0.12 ip=192.168.1.126 link=yes multicast=yes wireless=IEEE 802.11bgn
root@chase-Satellite-L25:~# 


Sorry for long posts trying to stammer out my problem but my brain is fried trying to deal with this for days with reading here and there and not asking for help. Im used to dealing with the read read read and then reread it all newb windows rude community.

---

