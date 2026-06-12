---
title: "Internet connection sharing"
date: 2009-02-16
forum: Networking &amp; Wireless
---

### Post by action_owl on 2009-02-16
I am trying to set up internet connection sharing in Xubuntu: the Xubuntu Box has a Wireless Pci card(that is connected to the internet) and an ethernet card that is connected to a router.

My other computer will connect to that router and thus to the internet, but the issue that I am facing is that while I'm on the internet if I plug in the ethernet cable to the router it automatically disconnects me from my wireless card and connects me to the router only. 
how do I fix this so that I can use both at the same time?

thanks

---

### Post by dmizer on 2009-02-16
Try this: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by action_owl on 2009-02-16
> **dmizer said:**
> Try this: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

I followed that guide the whole way through then when I plugged in my ethernet connection the same thing happened: it kicked me off of the wireless network and tried to connect to eth0 for internet

---

### Post by dmizer on 2009-02-16
Please post the output of:
```
sudo ifconfig
```

---

### Post by action_owl on 2009-02-18
Ath0 is the internet connection, and I want to share to eth0


ath0      Link encap:Ethernet  HWaddr 00:0b:c8:5b:a7:33  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:88ff:fe8b:ada3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8538 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5314 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11878649 (11.8 MB)  TX bytes:479996 (479.9 KB)

eth0      Link encap:Ethernet  HWaddr 00:10:b5:b7:c0:01  
          UP BROADCAST MULTICAST  MTU:576  Metric:1
          RX packets:41 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4226 (4.2 KB)  TX bytes:6200 (6.2 KB)
          Interrupt:9 Base address:0x3000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:98 errors:0 dropped:0 overruns:0 frame:0
          TX packets:98 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4508 (4.5 KB)  TX bytes:4508 (4.5 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-0D-88-8B-AD-A3-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:209630 errors:0 dropped:0 overruns:0 frame:30606
          TX packets:13059 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:29911624 (29.9 MB)  TX bytes:923679 (923.6 KB)
          Interrupt:10

---

### Post by dmizer on 2009-02-18
Okay, it seems as though your eth0 configuration is not making it.

Please post the contents of this file:
```
/etc/network/interfaces
```
Are you using Ibex?

---

### Post by Hero of Time on 2009-02-21
Do you use Network Manager? If you do, remove it or disable it. Removing is probably better. From what I know about NM, is that when it detects a new connection, it will drop the other one. So if there is a wifi link, and it detects a connected cable, it drops the wifi and will start using wired. Best to configure your network through /etc/network/interfaces.

---

### Post by action_owl on 2009-02-24
thanks Hero, that's exactly what was happening,
I thought that it was some auto setting/program deal

---

### Post by mr_vodoo on 2009-02-25
Hello,

I am relatively new to Linux, and I am trying Ubuntu at the moment. I have the same problem. Every time I plug the ethernet cable my wifi drops and can connect to Internet, if I unplug the crossover cable everything gets to normal.

I am using Network Manager. As hero said I can remove it, but if I do, what program can I use to connect to wifi? As network administrator does not support WPA, and my wireless connection is WPA.

I have a desktop PC connected via wireless to an access point. I have also an ethernet card in this PC.

I have a laptop with an ethernet card, I can connect both computers with a crossover cable, but every time I do as I mentioned, the internet stops working.

All I want to do is share the internet connection, so I can connect to Internet from my laptop.

Thanks for any help.

---

### Post by Iowan on 2009-02-25
[Internet/ConnectionSharing]("https://help.ubuntu.com/community/Internet/ConnectionSharing")
[Disabling Network Manager]("https://help.ubuntu.com/community/NetworkManager#Disabling%20Network Manager")

---

### Post by mr_vodoo on 2009-02-25
Hello Iowan, and thanks for answer so quickly. However, the answer you posted does not answer my question of how to connect to WPA access point once I disable NetworkManager.

Kind regards

---

### Post by computer_freak_8 on 2009-02-25
> **mr_vodoo said:**
> However, the answer you posted does not answer my question of how to connect to WPA access point once I disable NetworkManager.
Someone please correct me if I am mistaken, but wouldn't this be an issue of setting up IPtables so that it forwards the connection between the interfaces? I know that that is how I managed to share my wired Internet connection with a wireless client. (I never did disable the Network Manager.)

@mr_vodoo:
Post the output of the following:
```
sudo cat /etc/network/interfaces
sudo ifconfig
```
Also, what version number (of Ubuntu) are you running?

---

### Post by dmizer on 2009-02-25
Here's how to connect to WPA without Network-Manager: [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

mr_Voodoo, please do not cross post in multiple threads. Thank you :)

---

### Post by mr_vodoo on 2009-02-25
Hello dmizer,

Thanks for the answer. I will try that as soon as possible, and will let you know if it could make it...

Sorry to post in multiple threads.

Regards

---

### Post by mr_vodoo on 2009-02-27
Hello again,

I have managed to get it working now.

My wireless card has a RT61 chipset.

**What I did:**

Remove network manager

```
sudo apt-get remove network-manager network-manager-gnome
```

Install RutilT trough synaptic package manager

Blacklist rt61pci driver (next generation driver), adding "blacklist rt61pci" line to:

```
sudo gedit /etc/modprobe.d/blacklist
```

I blacklisted this driver because RutilT did not show WPA option.

Download Ralink Enhanced Legacy Drivers, so that WPA could work with rutilt

```
http://rt2x00.serialmonkey.com/wiki/index.php/Downloads
```

And installed following this manual [http://www.aircrack-ng.org/doku.php?id=rt61]("http://www.aircrack-ng.org/doku.php?id=rt61")

After that Rutilt worked just fine, and I had wireless internet connection.

I followed the manual referred by Iowan [Internet connection sharing]("https://help.ubuntu.com/community/Internet/ConnectionSharing")

But I was still having problems with the internet connection sharing, I think the problem was that I was establishing my static eth0 IP as 192.168.0.1 which was in the same subnet as my wireless internet IP 192.168.0.X that I was getting from the wireless router through DHCP. 

I also had to look in the file "resolv.conf" to know my DNS server ```
cat /etc/resolv.conf
``` which once again was 192.168.0.1

So I assigned the static IP 192.168.1.1 address to my ethernet card and it worked.

For the client I assigned the following static configuration:

IP: 192.168.1.2
Netmask: 255.255.255.0
Gateway: 192.168.1.1 (static IP from eth0 in ubuntu)
DNS: 192.168.0.1 (info in resolv.conf)

And now I have a desktop ubuntu computer connected to wireless internet and sharing internet connection to a windows vista laptop through a crossover cable.

:lolflag:

Thanks to Dmizer, Iowan, Wieman01 and all the forum that I spent 4 whole days reading to make it work but I am very happy now.

:P

---

### Post by dmizer on 2009-02-27
Fantastic!

I know it's frustrating having to fight things for so long, but as time goes on you learn how to get through it much more quickly.

---

