---
title: "NM Wired and Wireless Simultaneously"
date: 2009-01-25
forum: Networking &amp; Wireless
---

### Post by Nate53085 on 2009-01-25
I'm trying to setup the following through the network-manager / network connection

Wireless adapter connected to the internet
Wired adapter connected to another local network

Either works fine if its the only one connected, but if both are enabled, all traffic defaults to the wired network and I can no longer reach the internet.

I can't find anything configuration-wise in network connections that will allow me to do this.

---

### Post by Iowan on 2009-01-26
Currently, NM will only manage one interface.  There are alternatives, see if [this]("http://ubuntuforums.org/showthread.php?t=1024127&p=6513580") one helps.

---

### Post by cariboo on 2009-01-26
I currently have both interfaces working. I set a static ip address for the wired interface in /etc/network/interfaces and let the wireless interface get it's ip address from the router. This isn't supposed to work, but I was playing around with setting up a static ip address and forgot to remove the settings when I installed Network Manager.

This is what my /etc/network/interfaces file looks like:

```
cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static

	address		192.168.1.205
	netmask		255.255.255.0
	broadcast	192.168.1.254
	gateway		192.168.1.1
```

The computer is connected to my 32" LCD HDTV (on which I'm watching TV) and I ran a script I created to see what the ip address was today after I started it up. I noticed in the output that it had two ip addresses, I can use the remote desktop viewer on the wired interface and the wireless interface is downloading a torrent.

Jim

---

### Post by Nate53085 on 2009-01-26
Ok, that answers my question I suppose.  I can easily work this with /etc/network/interfaces as I have done on other machines, I was just trying to stay on the up and up with the new graphical tools.

Thanks for the replies

---

### Post by Post Monkeh on 2009-01-29
i set my laptop up to allow my desktop, connected via lan, to access the internet through it.

here's the settings.

eth0
ip 192.168.1.1
sub 255.255.255.0
gateway/dns 192.168.0.1

wlan
ip 192.168.0.3
sub 255.255.255.0
gateway/dns 192.168.0.1


on the desktop, i used
eth
ip 192.168.1.2
sub 255.255.255.0
gateway 192.168.1.1
dns 192.168.0.1


in fact i'm using that setup right now because i still can't get my belkin wireless adapter to work lol

---

### Post by wlraider70 on 2009-01-29
is eth0 and eth the descriptors for the physical Ethernet cards. 
Or is there something more complicated than that?

Im assuming that my only wired card would be eth0

---

### Post by Post Monkeh on 2009-01-29
sorry yeah, eth is just my desktop's ethernet connection, i was just explaining the whole setup.
i'm really not sure if that setting will work for you.  essentially the reason for the gateway on the ethernet card pointing to my wireless router is because ubuntu accesses your ethernet interface first. this means when you try to access anything online, unless your ethernet card points at your wireless router then you won't be able to get through.

whether or not this setting will also stop you from actually accessing something on your wired lan i'm not sure because i only have it set up to allow my desktop to use my laptop's wireless connection.  i know that i CAN ping my desktop from my laptop, but i haven't got as far as setting up any file sharing or anything yet.

if you did have success, you would find that with the proper set up, anything connected to the wired network could access the internet through your system.

---

### Post by mr_vodoo on 2009-02-25
> **Nate53085 said:**
> I'm trying to setup the following through the network-manager / network connection

Wireless adapter connected to the internet
Wired adapter connected to another local network

Either works fine if its the only one connected, but if both are enabled, all traffic defaults to the wired network and I can no longer reach the internet.

I can't find anything configuration-wise in network connections that will allow me to do this.

Hello,

I have the same problem.

I have a PC with an ethernet card and a wireless card. I receive internet via the wireless card (WPA access point) and I want to share the internet connection to my laptop via the ethernet card (crossover cable). The internet connection in the PC works fine until I plug the ethernet cable.

I am relatively new to Linux, and I using NetworkManager. Some people recommend to disable it, but if I do, how can I connect to the wireless point because Network Administrator for Ubuntu does not have support for WPA.

I would appreciate any help. Thanks in advance

---

