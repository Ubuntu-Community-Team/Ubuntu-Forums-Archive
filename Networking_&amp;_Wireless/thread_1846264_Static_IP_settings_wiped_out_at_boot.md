---
title: "Static IP settings wiped out at boot"
date: 2011-09-18
forum: Networking &amp; Wireless
---

### Post by Singlebbl on 2011-09-18
With apologies to the Eagles, I stab it with my steely knife but I just can't kill the beast ... DHCP that is ...  :confused:

I'm running 10.04.3 LTS from a pendrive (with persistence).  I removed network-manager and network-manager-gnome using the Synaptic Package Manager.  I then setup /etc/network/interfaces and /etc/resolv.conf.  Following the suggestion in [http://ubuntuforums.org/showthread.php?t=1787555&highlight=static+ip+gnome](http://ubuntuforums.org/showthread.php?t=1787555&highlight=static+ip+gnome), I run /etc/init.d/networking restart and the network starts up with the static settings as confirmed by ifconfig.  But when I reboot, something is wiping out my static versions of /etc/network/interfaces and /etc/resolv.conf with a couple of generic DHCP ones.  

Can anyone tell me how to setup a static IP so it will persist across system restarts?

---

### Post by chili555 on 2011-09-18
May we see your two files?> I then setup /etc/network/interfaces and /etc/resolv.conf. Also, please show us:```
ps aux | grep -i network
```Thanks.

---

### Post by Singlebbl on 2011-09-18
Info for static IP as defined by me.  BTW, this works to the extent that I can access the internet (Firefox), ping my XP system, and ping this system from XP:  

1.  /etc/network/interfaces:
```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
        address 192.168.0.6
        netmask 255.255.255.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

```2.  /etc/resolv.conf:
```
nameserver 156.154.70.1
nameserver 209.244.0.3
domain
search

```3.  aux info following successful sudo /etc/init.d/networking restart:  
```
ubuntu@ubuntu:~$ ps aux|grep -i network
ubuntu    5114  0.0  0.0   3324   856 pts/0    S+   01:57   0:00 grep --color=auto -i network
```Info following reboot:
1.  /etc/network/interfaces:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```2.  /etc/resolv.conf:
```
nameserver 209.18.47.61
nameserver 209.18.47.62
```3.  aux info:  
```
ubuntu@ubuntu:~$ ps aux|grep -i network
ubuntu    5112  0.0  0.0   3324   856 pts/0    S+   01:56   0:00 grep --color=auto -i network
```

---

### Post by chili555 on 2011-09-19
> I'm running 10.04.3 LTS from a pendrive (with persistence).If your /etc/network/interfaces and /etc/resolv.conf get rewritten, then I don't believe persistence is working correctly.

---

### Post by Singlebbl on 2011-10-22
> **chili555 said:**
> If your /etc/network/interfaces and /etc/resolv.conf get rewritten, then I don't believe persistence is working correctly.

[SIZE=3]Yes, that certainly seems like a real possibility.  

Having been thru the process of setting up a static IP several times on the pendrive, I felt comfortable trying it on my production system.  So, like before, I removed network-manager and network-manager-gnome using the Synaptic Package Manager, setup /etc/network/interfaces and /etc/resolv.conf, ran /etc/init.d/networking restart to start up with the new static settings and confirmed them with ifconfig.  And following a reboot, the static settings were retained.  

The only difference between what I did on the pendrive and the production systems is that on the pendrive I removed the packages in two steps, first removal followed by deletion of settings, and on the production system I did it in one step of complete removal.  If time & tides permit, I will retest the pendrive using the one step process and post the results here. [/SIZE]

---

