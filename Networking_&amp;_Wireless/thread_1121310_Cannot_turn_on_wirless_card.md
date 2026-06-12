---
title: "Cannot turn on wirless card"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by Laxton14 on 2009-04-09
I am using an HP zv5000 and there is a button which, when the wireless card is enable is light up, it however will not turn on. I think that Ubuntu recognizes my wireless card but it still won't connect to my network. Any suggestions would be appreciated.

Thanks in advance.

Additional Info...

When I run:

iwconfig

```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

And when I run

lshw -c network

```
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:4a:1c:b3
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.8 latency=128 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:a3:0c:c5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```

---

### Post by Ayuthia on 2009-04-09
Have you already installed the firmware from System->Administration->Hardware Drivers?

---

### Post by Telelove on 2009-04-10
I faced the same problem when I accidentally turn off the wireless. After all, I have to boot to Win XP and turn on the wireless, then back to Ubuntu.
Is there any possibility to turn it on in Ubuntu? I have searched around but couldn't

---

### Post by Laxton14 on 2009-04-10
> **Ayuthia said:**
> Have you already installed the firmware from System->Administration->Hardware Drivers?

None are shown. Do I need to enable any repositories or anything?

---

### Post by Ayuthia on 2009-04-10
> **Laxton14 said:**
> None are shown. Do I need to enable any repositories or anything?

If you have a working internet connection in Ubuntu, try:
```
sudo apt-get install b43-fwcutter
```
It will ask you if you want it to fetch the firmware.  Say yes if you have a working internet connection and then it should ask you to reboot.  After that, it should start to work.

---

### Post by Laxton14 on 2009-04-12
Good news and bad news.

Good news: The firmware is now installed and are showing in the restricted drivers.

Bad news: I still cannot connect to my wireless network because my network is not showing up in connections window.

Any suggestions? thanks

I also just installed a wifi manager, but it cant find any networks either (my wirless network is fine)

---

### Post by Laxton14 on 2009-04-14
Any one have any ideas? please?

Thanks

---

### Post by Ayuthia on 2009-04-15
Can you post the results of:
```
dmesg|grep b43
```It might help us see why it is not working.

---

