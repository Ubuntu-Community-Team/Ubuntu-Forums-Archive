---
title: "ETH0 Not Configured? No wired network access after reboot"
date: 2012-04-26
forum: Networking &amp; Wireless
---

### Post by Razmear on 2012-04-26
Been working on this for about 2 hours, and checked several posts here before posting. 
After rebooting my desktop PC, Kubuntu 11.10, I was prompted to do my updates, I tried and it gave the error that it could not get the package files, this is when I noticed there was a network error. 
All was fine prior to this. 

I can not even connect to my router via the web interface using it's IP address. 
I have swapped cables, network ports on the router, and no change. 
My wifes PC (which I'm using now, also Kubuntu 11.10) is connecting to the web fine thru the same router. 
When I unplug a network cable, the network manager notices this and reports cable is unplugged. 

In Konsole, ping 8.8.8.8 returns:
Connect: Network is unreachable

sudo ifdown eth0 && sudo ifup eth0 returns:
ifdown: interface eth0 not connected
ignoring unknown interface eth0 = eth0

I've gone into network manager and set eth0 to Automatic (was custom DNS settings) with no change. I've rebooted several times, logged into Ubuntu desktop, failsafe mode, and tried several other things which I'm sure I'm forgetting to mention here, and still no joy. 

In Kinfocenter it shows under device viewer -> network interfaces that eth0 is a RTL 8111/8168B ethernet adapter by RealTek 
The hardware address in this screen matches the output of ifconfig -a
However in the Network Information -> Network devices section of the same Kinfocenter it only lists 'lo' and not eth0.

Im guessing some config file got whacked somewhere, but I'm out of ideas what to look for next. Any help would be appriciated.

---

### Post by albandy on 2012-04-26
Try this:
sudo ifconfig eth0 up
sudo dhclient eth0

and ping your router.

---

### Post by Razmear on 2012-04-26
sudo ifconfig eth0 up completed without message
sudo ifconfig dhclient eth0 returned:
unknown host eth0
ping of router still failed.

I ran ifconfig on both my wifes PC (the working one) and mine and on her's it shows 
ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:30:67:ae:xx:xx
          inet addr:192.168.15.101  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::230:67ff:feae:6ef7/64 Scope:Link
and on mine the inet addr: portion is missing.

---

### Post by Razmear on 2012-04-26
OK, got it fixed. The missing inet addr: line was the clue I needed.
I went into network manager and set the IP4 section to Manual and plugged in the IP address and gateway (router IP) and now it's connecting again. 

Not sure what blew out the config, but at least it's up and running again.

---

### Post by esodan on 2012-07-09
I have a Lenovo C200, I had a problem with eth0 (e100 driver), just doesn't stablish link, this is what you need to do:

a) install your distribution (I'm using Ubuntu 12.04)
b) update packages
c) power off AND DESCONECT FROM POWER SUPPLY
d) connect again to power supply and turn on the PC
e) Now you have a link up and a card working

Hope some one needs this information (may be me in the future)

---

