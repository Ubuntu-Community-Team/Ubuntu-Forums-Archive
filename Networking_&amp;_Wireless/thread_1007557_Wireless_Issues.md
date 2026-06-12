---
title: "Wireless Issues"
date: 2008-12-10
forum: Networking &amp; Wireless
---

### Post by fearnloath on 2008-12-10
I'm using a Broadcom 4328 in ubuntu 8.04. Ive been reading threads and cant seem to find a answer to my problem. I dont know a whole lot about linux, and im trying to learn. The below information is what other people asked, so i'm trying to provide it ahead of time.

So i found and enabled the "Broadcom STA wireless driver" under the hardware Drivers. when i type iwconfig in the terminal, i get: 

> iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated


when i type "sudo dhclient eth1", I get:

> dhclient eth1
Listening on LPF/eth1/00:21:00:05:f3:ef
Sending on   LPF/eth1/00:21:00:05:f3:ef
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


"sudo iwlist eth1 scanning" turns up:

>          Cell 01 - Address: 00:19:5B:95:17:26
                    ESSID:"J_WAN"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:5/5  Signal level:-17 dBm  Noise level:-90 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: CE:FD:17:75:14: D0
                    ESSID:"J_WAN"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:5/5  Signal level:-17 dBm  Noise level:-90 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s


Any help i could get would be great thanks :)

---

### Post by loboc on 2008-12-10
do you have the network-manager installed, its a little program that lives in your tray and configures things like the wireless or VPNs 

```

sudo apt-get install network-manager-gnome

```

[http://projects.gnome.org/NetworkManager/](http://projects.gnome.org/NetworkManager/) for info

---

### Post by fearnloath on 2008-12-10
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
network-manager-gnome is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


It was uninstalled when i tried installing wcid, but that didnt work, so i uninstalled it and reinstalled Network manager

---

### Post by Matt Yun on 2008-12-10
> **fearnloath said:**
> I'm using a Broadcom 4328 in ubuntu 8.04. Ive been reading threads and cant seem to find a answer to my problem. I dont know a whole lot about linux, and im trying to learn. The below information is what other people asked, so i'm trying to provide it ahead of time.

So i found and enabled the "Broadcom STA wireless driver" under the hardware Drivers...

I successfully use a Broadcom BCM4328 based wifi chip, for Hardy.  The restricted Broadcom STA wireless driver doesn't work. You have to use ndiswrapper.

This guide, although written for Feisty, works with Hardy:  [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

For the BCM4328, download the R151517.EXE driver:
```
wget http://myspamb8.googlepages.com/R151517-pruned.zip
unzip R151517-pruned.zip
```

Then, load the driver with ndiswrapper:
```
sudo ndiswrapper -i bcmwl5.inf
sudo modprobe ndiswrapper
```

I've had a better experience with wicd instead of Hardy's network-manager.  I haven't tried Intrepid's network-manager.

---

### Post by fearnloath on 2008-12-10
Awesome, thank you very much :) Between that and setting a static IP instead of a dynamic one, wireless is up and running

---

