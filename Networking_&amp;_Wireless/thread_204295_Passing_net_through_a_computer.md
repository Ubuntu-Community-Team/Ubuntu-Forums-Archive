---
title: "Passing net through a computer"
date: 2006-06-26
forum: Networking &amp; Wireless
---

### Post by matthewv on 2006-06-26
I'm trying to work out how to configure ubuntu 6.06 server so that i can have another computer connected directly to its second network card and accessing the network attached to the first card, as shown below:

                                NETWORK...
                                /    
INTERNET ==> ROUTER -- NETWORK...
                                \
                                SERVER ==> LAPTOP

The idea is that the laptop will be able to access the network and internet as normal (it also has a wireless net card, but this location is out of range and only has one network port) when connected to the server through the second net card (eth1) on the server. I am looking for some pointers on the best way to do this.

Thanks a lot...

btw, would an ordinary network cable work to connect the server and laptop, or would i need to have crossover cable ( i suspect the latter : ( )

---

### Post by woedend on 2006-06-27
i'd get a crossover cable.  I've read some cards it doesn't matter but to be safe I'd use crossover(that's what I use).
As far as what you are trying to do, not exactly sure.  If youre just trying to share internet, you can either bridge the connection or use NAT.  The easiest way to bridge is to download the package bridge-utils, then add 
iface br0
bridge_ports all

to the bottom of /etc/network/interfaces
then use sudo ifup br0

I myself use NAT since it seems more reliable and easier to setup.  Just download firestarter and check the box (enable internet connection sharing).
To utilize this, you must set the eth card that connects the two computers together to have a static ip address such as 192.168.2.1, netmask 255.255.255.0, no gateway.
Then setup the computer which has no net access to use the IP address 192.168.2.2, gateway 192.168.2.1, and specify the dns servers and it should work.

if i'm way off track here let me know.

---

### Post by matthewv on 2006-06-27
[QUOTE=woedend]i'd get a crossover cable.  I've read some cards it doesn't matter but to be safe I'd use crossover(that's what I use).
As far as what you are trying to do, not exactly sure.  If youre just trying to share internet, you can either bridge the connection or use NAT.  The easiest way to bridge is to download the package bridge-utils, then add 
iface br0
bridge_ports all

to the bottom of /etc/network/interfaces
then use sudo ifup br0

I myself use NAT since it seems more reliable and easier to setup.  Just download firestarter and check the box (enable internet connection sharing).
To utilize this, you must set the eth card that connects the two computers together to have a static ip address such as 192.168.0.1, netmask 255.255.255.0, no gateway.
Then setup the computer which has no net access to use the IP address 192.168.0.2, gateway 192.168.0.1, and specify the dns servers and it should work.

if i'm way off track here let me know.[/QUOTE]
Thanks woedend...

I was thinking of bridging, but wasnt too sure how to accomplish that, or if that would work... firestarter wouldn't work (no gui), i do almost everything by ssh, as it is a headless server. The reason I wanted to know about the cable is that I already have a standard cable, but not crossover, i know they're pretty cheap, but...

Sorry about the diagram, i should have remembered that multiple spaces don't work on web pages, the NETWORK... and SERVER coming from the INTERNET were supposed to come out of the router... 

Thanks a lot, I'll see what I can do, and then post back here. I may have a few problems as the laptop should ideally function without realising the diff... i know that might be kind of hard, but I'd rather that cause it is currently running fine on the net, but I've only got the one network port there, otherwise it'd be a no-brainer

---

### Post by darkenedday on 2006-11-19
If it helps any this is what my interfaces file looks like



auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet static
address 192.168.1.113
netmask 255.255.255.0

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth3 inet static
address 192.168.1.111
netmask 255.255.255.0

auto eth3


iface br0 
bridge_ports all

---

