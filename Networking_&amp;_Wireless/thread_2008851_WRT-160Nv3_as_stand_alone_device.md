---
title: "WRT-160Nv3 as stand alone device"
date: 2012-06-23
forum: Networking &amp; Wireless
---

### Post by Mark_in_Hollywood on 2012-06-23
In this apartment, I and my neighbor share a wireless internet connection. (The equipment is: AT&T DSL 2Wire HG2701 wireless, modem, router.) The equipment is in his apartment. I connect my computer to the 'net via wireless from his place. There are times of day when the signal strength drops too low.

I have an unused Linksys (Cisco) WRT-160N (version 3) wireless router. It has the dd-wrt upgrade installed on it.

I would like to use the WRT-160 to increase the signal strength in this room. I know that the speed may decrease a little. That's not as important as the connectivity stopping. (2 or 3 times a day - depending on temperature, humidity, or sunspots?)

I looked at Cisco's pages for what to do. I read about the WRT-160N v3 at the dd-wrt forums.

I'm lost. If someone could point me to a starting point, I'ld be satisfied. I don't need my hand held. If I brick the router it's not a biggie, as it was a gift.

My first goal is to be able to see the device's pages. The 

 [http://192.168.1.1/](http://192.168.1.1/)

does not open the router's admin pages. The device is plugged into the computer's ethernet jack the cable goes to port #4 on the router. The device's Power, Wireless and Port #4 lights are steady on.

Ubuntu's Network Tools shows an eth0 as one possible interface. Wireless, wlan1 is the other.

The eth0 config shows from Network Tools as:

Network device:	eth0
Hardware address:	40:61:86:06:56:14
Multicast:	Enabled
MTU:	1500
Link speed:	not available
State:	Active
Transmitted packets:	340
Transmission errors:	0
Received packets:	33
Reception errors:	0
Collisions:	0

---

### Post by Mark_in_Hollywood on 2012-06-26
I'm still searching for a way. I found a post, these forums:

[bridging network connection]("http://ubuntuforums.org/showthread.php?t=1750664")

it added:

bridge-utils

and this to /etc/network/interface

iface br0 inet dhcp
     bridge_ports all

I then opened Network Tools, but didn't see anything new. Anybody know what I should no next? I should add that the computer I'm using IS connected wirelessly to the internet. Do I have to disconnect before I can work with the Linksys (secondary or bridged) router?

---

### Post by efflandt on 2012-06-27
How old is the 2701HG-B?  Mine is probably nearly 10 years old and its wireless started giving out a while ago.  So I disabled its wireless and have been using a wireless router behind it for at least a couple of years (SSID and security set same as the 2Wire was).

What network is on the 2Wire LAN (wireless)?  Maybe that is conflicting with (same as) your router LAN.

With your wireless disconnected and ethernet connected to router, see if it shows an ethernet IP and default route:

ifconfig

route -n

If a Gateway shows up, that would be your router IP.  Try connecting to that with a web browser.

But I am not quite sure what you are bridging through your computer, because I see either disabling the 2Wire wireless and seeing if your router puts out a stronger signal, or seeing if your router in "wireless client mode" would connect to the 2 Wire better than your current wireless device.  Neither of those would require bridging through your computer.

---

### Post by Mark_in_Hollywood on 2012-06-28
> **efflandt said:**
> How old is the 2701HG-B?  Mine is probably nearly 10 years old and its wireless started giving out a while ago.  So I disabled its wireless and have been using a wireless router behind it for at least a couple of years (SSID and security set same as the 2Wire was).

The 2Wire is about 3 years old. AT&T sent 2 before it, both broke within 6 months of each other.

What network is on the 2Wire LAN (wireless)?  Maybe that is conflicting with (same as) your router LAN.

I don't know what network(s) I have. Unless you mean those that show up in the drop down box in the panel. Is the network the SSID?

With your wireless disconnected and ethernet connected to router, see if it shows an ethernet IP and default route:

ifconfig

route -n

If a Gateway shows up, that would be your router IP.  Try connecting to that with a web browser.

ifconfig shows eth0 and lan(1) but route -n shows nothing

But I am not quite sure what you are bridging through your computer, because I see either disabling the 2Wire wireless and seeing if your router puts out a stronger signal, or seeing if your router in "wireless client mode" would connect to the 2 Wire better than your current wireless device.  Neither of those would require bridging through your computer.

I cannot have cable access to the 2wire wireless modem router. It's in another apartment in this building. My neighbor & I share that connection.

I want to run a magicJack+ via ethernet cable. If I can set up the 2ndary (wrt-160Nv3) device and allow the magicJack+ to connect via ethernet cable, and then wirelessly back to the host modem, I might be able to use it while in Linux. There are no Linux drivers for magicJack/magicJack+.

---

