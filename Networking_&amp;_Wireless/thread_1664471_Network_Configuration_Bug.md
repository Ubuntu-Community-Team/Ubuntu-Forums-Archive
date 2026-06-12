---
title: "Network Configuration Bug?"
date: 2011-01-11
forum: Networking &amp; Wireless
---

### Post by MakubeX on 2011-01-11
I've been encountering a problem in the network configuration (since Ubuntu 10.04 and now) in Ubuntu 10.10. I'm not really a newbie but I still created my thread on the Newbie category.

Here are the threads:

[http://ubuntuforums.org/showthread.php?t=1660966](http://ubuntuforums.org/showthread.php?t=1660966)
[http://ubuntuforums.org/showthread.php?t=1549733](http://ubuntuforums.org/showthread.php?t=1549733)

My lab's configuration uses a static IP address. The problem is that the configurations keep on going bonkers. I set the values, save/apply, then after a shutdown or reboot, the Network Icon on the bar will say that there's no network connection. Checking the Profiles on the Network Connections - sometimes a new profile is being created. At the times the MAC address on the Network Manager no longer matches the MAC address of the hardware (when I get its value via ifconfig).

Is this a bug? It's supposed to be easy configuring the network via both graphical and command line ways, right? But I'm teaching my students who're just new to this OS and at times they become frustrated with it - just because the network configuration's going bonkers. :(

I'm looking forward to a solution to this challenge here. Thank you in advance. :)

---

### Post by sj1410 on 2011-01-11
I generally dont use network manager to configure my ip address. i configure it in


```


sudo nano /etc/network/interfaces


``` 

and type in the following

```
 

auto eth0
iface eth0 inet static
        address 192.168.0.105
        netmask 255.255.255.0
        gateway 192.168.0.1
        dns-nameservers 8.8.8.8 8.8.4.4


``` 

BUT before that you need to uninstall network manager or it will reset you configuration again.

```
 
sudo apt-get remove network-manager

```

---

### Post by MakubeX on 2011-01-11
Impressive! I think it worked already! Thanks a lot!

---

### Post by MakubeX on 2011-01-12
Just an update - unfortunately, it did NOT work anymore when I returned to the lab. I tested the connection twice (through reboots and shutdowns) after configuring it and it was working, but the following day it went bonkers again.

When I do a /sbin/ifconfig command, it just returns info about the loopback and there was no eth0 found. Is the name eth0 supposed to be fixed? I also tried restarting it through "/etc/init.d/networking restart" but sometimes I encounter this: "Failed to bring up eth0".

I read something from [http://www.zdnet.com/blog/btl/10-things-not-to-like-about-ubuntu-1004/35713](http://www.zdnet.com/blog/btl/10-things-not-to-like-about-ubuntu-1004/35713) that there's a "service network restart" command. Is this the new way to restart the network for ubuntu 10.04/10.10?

A friend also told me that perhaps in order for the static IP configuration to work, I have to update the system first. However, this will just be hassle because in order to update via online, the network connection should work first and foremost.

It seems that there's really a network configuration bug. Help.

UPDATE:
After some searching, I've found this bug report: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/524454](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/524454)

So is this the right way then? [http://www.ubuntugeek.com/how-to-fix-network-manager-disabled-problem-in-ubuntu-10-04-lucid.html](http://www.ubuntugeek.com/how-to-fix-network-manager-disabled-problem-in-ubuntu-10-04-lucid.html)

---

### Post by chili555 on 2011-01-12
> When I do a /sbin/ifconfig command, it just returns info about the loopback and there was no eth0 found. Is the name eth0 supposed to be fixed? I also tried restarting it through "/etc/init.d/networking restart" but sometimes I encounter this: "Failed to bring up eth0".That suggests that the driver for the ethernet card is not loading and creating an interface. If you run:```
sudo lshw -C network
```You should see a driver associated with the network card. Here is a sample from my computer:```
*-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 99:16:41:e6:cb:88
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes [COLOR="Red"]driver=e1000e [/COLOR]driverversion=1.0.2-k4 firmware=0.5-1 latency=0 link=no multicast=yes port=twisted pair

```If you identify and load the driver:```
sudo modprobe your_driver
```The interface should come to life. Then up the interface which will re-read your /etc/network/interfaces file:```
sudo ifup eth0
```You can get the system to load the driver automagically on boot without further intervention with:```
sudo su
echo your_driver >> /etc/modules
exit
```Post back if you need additional assistance.

---

### Post by ripat on 2011-01-12
Is the interfaces file still as suggested above? If yes, post the result of

```
$ ip link show
$ ip address show
$ sudo ifdown --verbose eth0
$ sudo ifup --verbose eth0
```

---

### Post by CharlesA on 2011-01-12
I have a feeling network manager is being a pain.

Try running this:

```
sudo ifconfig -a
```

That'll show all available interfaces.

---

### Post by sj1410 on 2011-01-12
> **CharlesA said:**
> I have a feeling network manager is being a pain.

Yes very true network manager is pain. i prefer uninstalling it and configuring network in /etc/network/interfaces

---

### Post by MakubeX on 2011-01-13
> **ripat said:**
> Is the interfaces file still as suggested above? If yes, post the result of

```
$ ip link show
$ ip address show
$ sudo ifdown --verbose eth0
$ sudo ifup --verbose eth0
```

Here are the results for

1) ip link show

```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN qlen 1000
    link/ether 00:17:31:61:7a:c6 brd ff:ff:ff:ff:ff:ff
```

2) ip address show
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN qlen 1000
    link/ether 00:17:31:61:7a:c6 brd ff:ff:ff:ff:ff:ff
    inet 10.35.32.62/20 brd 10.35.47.255 scope global eth0
```

3) sudo ifdown --verbose eth0 and sudo ifup --verbose eth0

```
user@ubuntu:~$ sudo ifdown --verbose eth0
ifdown: interface eth0 not configured
user@ubuntu:~$ sudo ifup --verbose eth0
Configuring interface eth0=eth0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant

ifconfig eth0 10.35.32.62 netmask 255.255.240.0  	   	up
SIOCSIFFLAGS: Cannot allocate memory
SIOCSIFFLAGS: Cannot allocate memory

```

---

### Post by MakubeX on 2011-01-13
> **chili555 said:**
> The interface should come to life. Then up the interface which will re-read your /etc/network/interfaces file:```
sudo ifup eth0
```

This resulted to:

SIOCSIFFLAGS: Cannot allocate memory
Failed to bring up eth0

---

### Post by MakubeX on 2011-01-13
I'm now wondering if it's a wrong move that I already removed the package network-manager.

---

### Post by chili555 on 2011-01-13
> **MakubeX said:**
> This resulted to:

SIOCSIFFLAGS: Cannot allocate memory
Failed to bring up eth0Did you identify which driver was not loading? Which one? Were there any error messages as you modprobed it?

---

### Post by MakubeX on 2011-01-13
> **chili555 said:**
> Did you identify which driver was not loading? Which one? Were there any error messages as you modprobed it?

Yes, but there was no error in modprobing it.

---

### Post by chili555 on 2011-01-13
Which one? I wonder if there are conflicting drivers. What does this tell us?```
dmesg | grep your_driver
```Of course, substitute the actual driver's name.

---

### Post by ripat on 2011-01-13
> **MakubeX said:**
> I'm now wondering if it's a wrong move that I already removed the package network-manager.

No. ifup doesn't need n-m to bring an interface up.

Anything weird in dmesg or /var/log/syslog?

---

