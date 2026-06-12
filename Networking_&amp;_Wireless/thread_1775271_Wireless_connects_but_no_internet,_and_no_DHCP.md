---
title: "Wireless connects but no internet, and no DHCP"
date: 2011-06-04
forum: Networking &amp; Wireless
---

### Post by OwnzUrFace on 2011-06-04
so I installed Ubuntu 11.04. I used ndiswrapper like I normally do to use the windows driver to use my Realtek Wireless N USB Wifi Adapter(I use the WinXP2K driver, net8192u.inf). Now, when I try to use DHCP the little icon glitches and it never connects, keeps asking me for my password again, etc. So I decided to set up the info manually. It connects to my network. Sweet. But wait, the internet doesn't work. Any help?

Here's some pictures of the situation:
[http://imageshack.us/g/101/screenshotny.png/](http://imageshack.us/g/101/screenshotny.png/)

---

### Post by poolet on 2011-06-04
[FONT=monospace]Print the following outputs::


[/FONT]```
[FONT=monospace]sudo lshw -C network[/FONT]
```[FONT=monospace]

[/FONT]```
[FONT=monospace]sudo lsmod | grep wlan0[/FONT]
```

```
sudo dmesg | grep wlan0
```

---

### Post by OwnzUrFace on 2011-06-04
> **poolet said:**
> [FONT=monospace]Print the following outputs::


[/FONT]```
[FONT=monospace]sudo lshw -C network[/FONT]
```[FONT=monospace]

[/FONT]```
[FONT=monospace]sudo lsmod | grep wlan0[/FONT]
```

```
sudo dmesg | grep wlan0
```

like, copy what it outputs and post it here?

---

### Post by OwnzUrFace on 2011-06-04
sudo lshw -C network
```

  *-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:02:72:78:0f:93
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8192u driverversion=1.56+Realtek Semiconductor Corp. ip=192.168.0.10 link=yes multicast=yes wireless=IEEE 802.11g

```

sudo lsmod | grep wlan0

(it does nothing)


sudo dmesg | grep wlan0
```

[   14.920747] wlan0: ethernet device 00:02:72:78:0f:93 using NDIS driver: net8192u, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8192 Wireless LAN USB NIC                                     ', 0BDA:8192.F.conf
[   14.920786] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   14.931020] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   45.651506] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   56.040014] wlan0: no IPv6 routers present

```

---

### Post by poolet on 2011-06-04
download wicd and install it.... remove the network manager packed from synaptic, and try again.... don't forget to restart your network... 

```
/etc/init.d/networking restart
```

---

### Post by OwnzUrFace on 2011-06-05
okay, I got wicd running. but when I go to connect, it says "Bad Password". but I know for a fact that I'm using the right password, and I tried all the different WEP settings, none of them worked. My password is a 10-digit 64-bit WEP key.

Edit: my bad, didn't uninstall network-manager correctly. I don't get that error anymore. but when it's set to DHCP, it sits on "Obtaining IP address" forever. And when I set it manually, it says "could not contact access point".

---

### Post by OwnzUrFace on 2011-06-05
and I don't know if you wanted me to run those commands again or not, so I did. Results:


sudo lshw -C network
```

  *-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:02:72:78:0f:93
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8192u driverversion=1.56+Realtek Semiconductor Corp. ip=192.168.0.10 link=yes multicast=yes wireless=IEEE 802.11g

```

sudo lsmod | grep wlan0

nothing

sudo dmesg | grep wlan0
```

[    8.257530] wlan0: ethernet device 00:02:72:78:0f:93 using NDIS driver: net8192u, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8192 Wireless LAN USB NIC                                     ', 0BDA:8192.F.conf
[    8.257571] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   13.603098] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.547705] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.164242] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   35.603261] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   46.248005] wlan0: no IPv6 routers present
[   76.025145] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   79.191604] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   79.419304] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   80.439539] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   86.601782] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   97.200005] wlan0: no IPv6 routers present

```

---

### Post by poolet on 2011-06-06
try to connect by terminal:: 

```
iwconfig "interface" enc your_key 
iwconfig "interface" essid "network_name"
dhcpcd "interface" -d 

```

also if you have second wireless interface try to disable it.. 

ifconfig "interface" down

---

### Post by OwnzUrFace on 2011-06-06
```

michael@mikeslinux:~$ sudo iwconfig wlan0 enc 9022528087
[sudo] password for michael: 
michael@mikeslinux:~$ sudo iwconfig wlan0 essid GoslingFamily
michael@mikeslinux:~$ dhcpcd wlan0 -d
The program 'dhcpcd' can be found in the following packages:
 * dhcpcd
 * dhcpcd5
Try: sudo apt-get install <selected package>
michael@mikeslinux:~$ 
```

I noticed that if I have a static IP and DNS, then it connects after that first command. still no internet though.

EDIT: Scratch that, it connects when I have the static IP and DNS off now, but same output as above. And still no internet. I tried to ping my router too, and that failed.

---

### Post by poolet on 2011-06-06
do you try to connect it via wire ?? 

Try to connect with wire.... 

if its connect via wire, up to your modem/router and change the encryption type from wep to wpa
also change the cipher type to TKIP or AES (the opposite of that is now) 

I have the same problem with usb wireless and i just bring down my first interface....  Also you are using ndiswrapper, try to reistall it... sometimes helps.... 

 follow the instruction here:::

[http://ubuntuforums.org/showthread.php?t=885847]("http://ubuntuforums.org/showthread.php?t=885847")

---

### Post by OwnzUrFace on 2011-06-06
I can't connect via wire. I need to keep the encryption type as WEP for my DS.

*sigh*. maybe I'll just go back to Lucid Lynx. Wifi worked on that. but it crashed a lot. maybe cause I was using Wubi.

---

### Post by OwnzUrFace on 2011-06-07
I installed MAverick Meerkat and it still wasn't working. however, I changed my authentication on the router to WPA2 and it works perfectly now. guess it really didn't like 64-bit 10-digit WEP keys.

---

