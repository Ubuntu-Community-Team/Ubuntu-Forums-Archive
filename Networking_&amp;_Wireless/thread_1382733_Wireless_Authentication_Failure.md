---
title: "Wireless Authentication Failure"
date: 2010-01-16
forum: Networking &amp; Wireless
---

### Post by bishnabob on 2010-01-16
I have Samsung netbook n130 and am having some serious wireless issues with it.

I have used this post here [http://ubuntuforums.org/showthread.php?t=1321340](http://ubuntuforums.org/showthread.php?t=1321340) to install wireless drivers on it and it picks up several wireless networks including my own.
Whenever I try and connect, it repeatedly asks me for the key and won't ever authenticate it.

I have tried using wicd instead of network manager, using ndiswrapper drivers instead of the ones on the above post.
The access point works fine as my housemate's laptop connects to it using both Windows 7 and Ubuntu, plus his iPhone works on it.
I've tried googling many things from the output of dmesg, but that got me nowhere - I can post it if anyone would like.

Any ideas? I'm completely stuck and have reached the complete end of my linux knowledge.

Any help would be gratefully received!

---

### Post by MarkC502 on 2010-01-16
I am not sure if I can help you or not, but I can let you know some things you could post to help out anyone who looks at your current situation.

1. Which Ubuntu version you are using

2. What wifi chipset your netbook uses ( Atheros, Broadcom Etc )
You can find this by googling around for "wifi chipset" and your netbook model. This is one of the most important as every wifi chipset has drivers that work and ones that might not and if you list that then someone may see it who is familiar with that chipsets peculiarities.

3. What type of Encryption the wireless access point is setup to use ( WEP , WPA or WPA2 )

4. The output of the following command -> sudo iwconfig

5. Driver you are currently using with this device.
You can figure this out as follows, 1st run "lspci -v" (without quotes) and look for your wifi devices information and find the line that says "Kernel driver in use" and that is where your currently loaded driver will be listed.


All those things would help someone a great deal in helping you. Your problem doesn't seem to be network manager related since you said you tried Wicd but maybe it is WPA supplicant related. Also when you go into your ubuntu software sources ( System -> Administration -> Software Sources ) and select the Updates tab , do you have "PROPOSED" checked ? If not you might want to try checking that then doing an update and see if your problem is resolved by a software update.

---

### Post by bishnabob on 2010-01-16
Hi,

The Ubuntu version is 9.10 and 'Proposed' is checked.
The wifi chipset is a Realtek 8192 (as far as I can tell - it did work using the latest rtl819X drivers from the Samsung website and ndiswrapper, but that stopped working as well) .. using the r8192_pci driver.
Wireless encryption is WPA-PSK/WPA2-PSK

iwconfig ouput:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  ESSID:"FlyingMachine"  
          Mode:Managed  Frequency=2.462 GHz  Access Point: Not-Associated   
          Bit Rate:135 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
output from 'lshw -C network'
```
*-network               
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:26:b6:00:31:8e
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xE latency=0 multicast=yes wireless=802.11bgn
       resources: irq:16 ioport:2000(size=256) memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:13:77:bd:f1:e4
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.181 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:26 ioport:3000(size=256) memory:f0510000-f0510fff(prefetchable) memory:f0500000-f050ffff(prefetchable) memory:f0520000-f053ffff(prefetchable)
```

I hope this extra information helps.

---

### Post by bishnabob on 2010-01-17
Some additional information:

When using ndiswrapper and the r819xP driver, I can get an IP. However, it then does nothing and is unable to ping anything on the network.
I've checked the router's logs (I use a smoothwall router, with a netgear WDN2000 as an access point) and I can see the request, offer and pack in the DHCP server logs, so it most definitely gets through.

So I'm at a complete loss. The wireless access point works fine due to the other equipment that uses it - I even added a printer on it earlier today and that's running great.

Any ideas at all?!

---

### Post by bishnabob on 2010-01-18
Sorry to keep replying to my own post, but here's some additional information again:
 
Today I have tried installing Windows 7 and I have a similar issue: after installing the drivers from the Samsung website, I can see wireless networks but am unable to connect to them.
 
This makes me think now that maybe I have hardware issues. Any thoughts?
 
EDIT:
 
Under Windows 7 the wireless connection works on another wireless network. So this leads me to think about a compatibility issue? Maybe it's time to contact Samsung ..

---

