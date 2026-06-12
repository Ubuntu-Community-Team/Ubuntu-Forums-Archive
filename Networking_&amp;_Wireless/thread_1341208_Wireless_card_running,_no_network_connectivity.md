---
title: "Wireless card running, no network connectivity"
date: 2009-11-29
forum: Networking &amp; Wireless
---

### Post by djmoore85 on 2009-11-29
Hey there, have a small issue I have been trying to resolve for about a day. I currently am running Ubuntu minimal install with GNOME over it, and have run into a snag. I have a BCM43xx wireless card which I have ndiswrapper claiming and running, however I cannot for all that I am worth get it to connect to my router. I have it hardwired for now until the issue is resolved. Does anyone have any ideas why I am unable to connect to my home network? Thanks in advance for any help

---

### Post by jward3010 on 2009-11-29
I'm assuming you're using network-manager for your network connections. If yes, then when you click the network icon (top right) do wireless networks appear - if no, what appears exactly? Maybe take a picture with your "PrntScrn" button.

---

### Post by djmoore85 on 2009-11-29
[IMG]http://i100.photobucket.com/albums/m18/djmoore85/Screenshot-1.png[/IMG]

Here is the screenshot of what I am getting through network-manager. I also can put the outcome of code:


```
daniel@MinBuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
daniel@MinBuntu:~$ ifconfig

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:61:14:3d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:c0204000-c0206000 
```

```
daniel@MinBuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:16:36:06:f0:17
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.101 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: wlan0
       version: 02
       serial: 00:14:a5:61:14:3d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,04/21/2005, 3.100. latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```


Hope this info will help. Please don't hesitate to let me know what else may be needed

---

### Post by djmoore85 on 2009-12-01
Anybody? I checked to ensure I have the wpasupplicant package installed

---

### Post by jward3010 on 2009-12-02
Thanks for all that info, it's exactly what we need.

I assume you're adding the network manually  with network manager, I don't see any nm-applet in the upper right to show you detected wireless networks. To get nm-applet running hit Alt+F2 on your keyboard and type in nm-applet and hit enter. If it appears click on it to see if it shows any wireless networks.

Also one other command to try is:
```
sudo iwlist scanning
```
Post it's output as well.

---

