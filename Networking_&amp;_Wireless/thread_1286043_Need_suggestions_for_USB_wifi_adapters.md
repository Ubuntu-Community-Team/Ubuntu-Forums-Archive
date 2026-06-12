---
title: "Need suggestions for USB wifi adapters"
date: 2009-10-08
forum: Networking &amp; Wireless
---

### Post by spiderworm on 2009-10-08
Hi,

I've gone through two USB wifi adapters now that I should have been able to get working with 9.04 but I couldn't.  Does anyone have a recommendation for a USB wifi adapter that they know plug-and-plays with 9.04?

Thanks in advance,
spiderworm

---

### Post by scorp123 on 2009-10-08
D-Link DWL-G122

They even have a "Tux" Linux mascott on their package. So yes, it pretty much is Linux compatible.

[IMG]http://www.benchmark.pl/uploads/recenzje/1247/dlink1.jpg[/IMG]

---

### Post by scorp123 on 2009-10-08
That's how it looks like when the DWL-G122 is connected:

[IMG]http://dl.getdropbox.com/u/1614648/Screenshots/D-Link_G122.jpg[/IMG]

And here's what happens according to "dmesg":
```

[29826.440103] usb 1-3: new high speed USB device using ehci_hcd and address 5
[29826.712609] usb 1-3: configuration #1 chosen from 1 choice
[29827.019847] phy1: Selected rate control algorithm 'pid'
[29827.023363] Registered led device: rt73usb-phy1:radio
[29827.023407] Registered led device: rt73usb-phy1:assoc
[29827.023447] Registered led device: rt73usb-phy1:quality
[29827.023969] usbcore: registered new interface driver rt73usb
[29827.143207] udev: renamed network interface wlan1 to wlan2
[29831.633500] rt73usb 1-3:1.0: firmware: requesting rt73.bin
[29831.782851] ADDRCONF(NETDEV_UP): wlan2: link is not ready
[29837.184290] wlan2: direct probe to AP 00:18:f8:da:fc:3e try 1
[29837.186590] wlan2 direct probe responded
[29837.186601] wlan2: authenticate with AP 00:18:f8:da:fc:3e
[29837.189113] wlan2: authenticated
[29837.189126] wlan2: associate with AP 00:18:f8:da:fc:3e
[29837.191619] wlan2: RX AssocResp from 00:18:f8:da:fc:3e (capab=0x411 status=0 aid=3)
[29837.191628] wlan2: associated
[29837.203994] ADDRCONF(NETDEV_CHANGE): wlan2: link becomes ready
```

The device takes a second or so to become active ... but other than that it instantly works (since Ubuntu 7.x)

---

### Post by spiderworm on 2009-10-08
Thank you thank you thank you thank you!!!  I will find one of those.  Really appreciate it.

spiderworm

---

### Post by JustMario on 2009-12-12
Hi, I've got that usb stick and can't seem to make it work with 9.10, I can see my wireless network but can't connect to it, this is what I get.

WARNING: you should run this program as super-user. 
*-network description: Wireless interface physical id:1 logical name: wlan0
serial: 00:15:e9:31:8c:60 capabilities: ethernet physical wireless configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg 
wolfpac@wolfpac-desktop:$

I'm a noob user if you guys can help me out but please dumb it down for me :)

---

### Post by bkratz on 2009-12-12
> **JustMario said:**
> Hi, I've got that usb stick and can't seem to make it work with 9.10, I can see my wireless network but can't connect to it, this is what I get.

WARNING: you should run this program as super-user. 
*-network description: Wireless interface physical id:1 logical name: wlan0
serial: 00:15:e9:31:8c:60 capabilities: ethernet physical wireless configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg 
wolfpac@wolfpac-desktop:$

I'm a noob user if you guys can help me out but please dumb it down for me :)




If you can "see" your network apparently the driver issue from the other thread must not be a problem (you might want to check the other).  Is your AP encrypted? Did you setup the network by right clicking on the icon and filling in the details under edit connections?  If you go to the terminal and  execute an-- iwlist scan-- does it show your network and type of encryption there?  Also did you tick the box for enable networking when you right click on the icon.

---

