---
title: "Inconsistent wireless connectivity"
date: 2006-02-13
forum: Networking &amp; Wireless
---

### Post by joehill on 2006-02-13
I got the latest version of ndiswrapper (1.9) compiled and for the moment my new wireless card (Linksys Wireless G WPC54GS version 2.1) is working some of the time.  (Better than with ndiswrapper 1.1, which I couldn't get to work at all.)

The problem is that although the card works fine most of the time in my home network, if I go out and try to use another wireless network that works fine for the people around me (I'm writing my dissertation now and tend to work a lot in cafes and such), I have lots of problems.  For the most part it detects the network without any problem and I can select the network with the graphical network configuration tool, then it goes through all the motions of connecting (very long "wait" cursor).  But it always takes a lot of tinkering around and waiting before it works, if it works.

When I select the network, maybe half the time it simply fails to connect (I get the little red diamond to the side) and the other half it shows all the signs of connecting--giving me all the blue diamonds and the blue flashes as if sending and receiving data, and iwconfig says I'm connected.  But even then most of the time I can't access the internet.  Sometimes if I wait about 20 minutes I'll have internet access.  In almost every case though, when moving to a new network I have to select the network I want and then reboot (waiting 3 to 5 minutes for the "configuring network interfaces" to get unstuck--maybe I should just ctrl-C here), then disconnect/connect/disconnect/connect, then wait a while, then it may start working.  It's sort of annoying when I'm trying to show my friends how cool Ubuntu is and I can't even get connected.

Thanks!

---

### Post by joehill on 2006-02-14
Note: my original wording made it sound like I had already resolved this problem (I did indeed resolve a different but related problem), so just so you know, I'm still hoping for answers.  Thanks.

---

### Post by m0nstr42 on 2006-04-17
I'm having almost the same problem with ndiswrapper.  I will go from home to campus (or a cafe, etc), shut down my laptop (since I don't have suspend/hibernate working at all), start up at the new place, try to connect to the new network, sometimes get no connection, sometimes get a connection but no dhcp lease (despite it working fine for computers around mine), and sometimes get a connection.  A lot of times if I reboot (!?!?) it works the second time.

---

### Post by rabidphage on 2006-04-17
The same problem has been annoying me as well. I don't even use ndswrapper
here's the dhcp error.
I've got no idea whats going on.

darx@darx:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:13:ce:3c:ce:3c
Sending on   LPF/eth0/00:13:ce:3c:ce:3c
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPNAK from 172.25.24.1
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 172.25.24.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 172.25.24.1
SIOCADDRT: Network is unreachable
bound to 172.25.26.240 -- renewal in 1783 seconds.

I'm posting from Windows XP. 
Nobody seems to know the answer. I've been searching for weeks.](*,)

---

### Post by m0nstr42 on 2006-04-19
I may have a solution.  Instead of using iwconfig/ifconfig/dhclient to bring things up, I found a way to set up custom scripts for ifup.  The gist of it is that I added ndiswrapper to /etc/modules (so it loads automatically on boot) and then wrote a file /etc/network/somenet.interfaces :

```
# /etc/network/school.interfaces
# use: ifup -i school.interfaces wlan0

auto wlan0
iface wlan0 inet dhcp
wireless-essid myschoolessid

```

Then bring it up with ```
ifup -i school.interfaces wlan0
```

I also have a home.interfaces and others (e.g. panera.interfaces), then since they aren't in the main /etc/network/interfaces they aren't brought up automatically on boot, I can choose different networks I use by using a different interface file, and it lets me use ifup to do it which seems to be more reliable than iwconfig/ifconfig/dhclient.  I've only been using it for a day or so, but it seems to be working like a champ.

Since you have to have a new interfaces file for every new network, I wrote a rudimentary script to generate the interfaces file and a script, a la
```

sudo ~/scripts/wifi-add somenet wlan0    # to add it the first time, then just
sudo ~/scripts/wifi-somenet              # to bring it up after that
```
If anyone is interested in using and/or helping me develop it, please contact me.  I have an idea for getting it to automatically grab one from an iwlist if one of your "set up" networks is there on boot.  It definitely needs work but I'm happy to share.

---

