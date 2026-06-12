---
title: "Bridge wireless and eth connection"
date: 2010-03-30
forum: Networking &amp; Wireless
---

### Post by Bungler on 2010-03-30
There is much information available about this topic, however I still can't get it to work.
This is what I would like to achieve:
Part 1: I want my desktop to serve as an ad-hoc host for a wireless network to serve my laptop and my phone for the internet connection 
Part 2: I want to synchronize my home folders through this connection

Hardware involved:
EDIMAX 7128g wireless network adapter, it can be used in ad-hoc mode, but does not support master mode. So in the end this means I have to stick to WEP encrytion

Software involved:
Both my desktop and my laptop run 9.10 64-bit. I connect through a ppp connection, created by the pppoeconfig setup, which creates the internet portal ppp0 through my wired network card eth0


For now I just tried to achieve part 1 and I cannot get it to work.
I tried the following:

I've installed:
apt-get install bridge-utils

Using:
[http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html](http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html)

I was able to setup an adhoc host and get my laptop to connect. However, when I setup the bridge, my internet connection cuts out (problem 2). Furthermore, when I reboot the desktop, the connection doesn't re-initiaze properly and I need to setup a new ad-hoc host again. I want a more solid solution, so I just want to put everything in the /etc/network/interfaces file (problem 1). This is the first thing I need to solve: I cannot get a wireless network running by using the following code:

```
#Wireless Setup
auto wlan0
iface wlan0 inet manual
iwconfig wlan0 mode ad-hoc && \
iwconfig wlan0 essid ubuntuwireless
# WEP encryption will be added when this works
```

I've tried many variations, but this is at least some code which does not give any errors and covers what I think is necessary.
When I add the bridge interface, my internet connection drops:

```
#Bridge interface
auto br0
iface br0 inet static # might be DHCP
    address 10.1.1.1
    network 10.1.1.0
    netmask 255.255.255.0
    broadcast 10.1.1.255
    bridge-ports eth0 wlan0 # might have to be ppp0
```

I tested this when I used the method of creating the ad-hoc host through the network manager (which I do not want to do).

Furhtermore, I've also  tried the easiest solution, which would be to use Firestarter for bridging, however it keeps on giving errors about 'device not ready'. Many more people have this problem and since there is not much to modify in this program, I just abandonend to use Firestarter.

I know that I also need to forward the packages in order to share a connection, similar to:
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)
But since I cannot set up the wireless properly I cannot test it and for now it didn't make sense to work on this.

I hope I've provided enough information to work with. Who can help me out of this mess?

---

