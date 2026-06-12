---
title: "Setup - WEP wireless - static ip - Ubuntu 8.04 server"
date: 2009-02-06
forum: Networking &amp; Wireless
---

### Post by boof1988 on 2009-02-06
I want to setup a music server and (for now) I mainly need help with setting up the WEP wireless networking.

The interface name is eth1.

Other knowns:
[LIST]
[*]ESSID
[*]host ip address
[*]gateway ip address
[*]DNS addresses
[*]network hex key
[*]the wireless card worked using Xubuntu 8.04 so hopefully the needed drivers are included with the server version (will have to see)
[/LIST]

I cobbled together some commands from [this thread](http://ubuntuforums.org/showthread.php?t=571188).  Haven't tried them yet because the server is currently connected (connected it before I set the router to *static ip*) to my network and I dont want it to be not-connected until I have the confidence (help) to fix it.

This is what I have cobbled together for a temporary setup (using the WEP connection part and the static ip part of the noted thread):

```
sudo ifconfig eth1 down
sudo dhclient -r eth1
sudo ifconfig eth1 <host ip address> netmask 255.255.255.0 up
sudo route add default gw <gateway address>
sudo iwconfig eth1 essid "<essid>"
sudo iwconfig eth1 key <hex key>
sudo iwconfig eth1 mode Managed

```

Again... I haven't tried it yet.

These are the questions I'd like answered if possible:
[LIST=1]
[*]Are all these commands necessary?
[*]What commands (if any) do I need to add(change)?
[*]What does each command do?
[*][Possibly for another thread...]How do I set up the server so that it will be connected to my network when I boot it up (I don't need to be logged in at bootup, I just need to be able to log into it over my network)?
[/LIST]

Any help is appreciated.

---

### Post by Bölvaður on 2009-02-10
The reason no one answered the thread is possibly because everything seems to be in order. But the most obvious things might be the biggest trouble. I'd guess that wireless is not on eth1 but on wlan0, let us see the output of ifconfig and iwconfig.

Also you may only need 

Here is an executable file I made containing a short script to connect to my university's wireless network:

```

sudo iwconfig eth1 mode managed
sudo iwconfig eth1 essid HINET
sudo dhclient eth1

```

note that eth1 is my wireless but not wlan0 like for most ppl I would assume. The output from "iwconfig" is

```
lo   no wireless extensions
eth0   no wireless ext....
eth1  IEEE 802.11b ESSID:"HINET".......
```

dhclient calls for a new ip via DHCP. So you might not want to use that unless if you are waning new ip. Static IPs will already be connected.


BTW this might be because kernel upgrate, you might need to install again drivers if you had to do that, or even go back to older kernel or release of ubuntu.

---

### Post by geirha on 2009-02-10
Look here for a guide on networking (to set up during boot):

[https://help.ubuntu.com/8.10/serverguide/C/network-configuration.html](https://help.ubuntu.com/8.10/serverguide/C/network-configuration.html)

For the wireless part you'll want to read the manual page wireless(7)
```
man 7 wireless
```

---

