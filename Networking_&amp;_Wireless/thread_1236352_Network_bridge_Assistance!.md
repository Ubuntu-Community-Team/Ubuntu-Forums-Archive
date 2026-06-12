---
title: "Network bridge Assistance!"
date: 2009-08-10
forum: Networking &amp; Wireless
---

### Post by ruddyrum on 2009-08-10
Hi,   

I have my internet connection on wlan0 from a wireless router downstairs, and another router connected to eth0 to connect other devices to my pc/internet!     

To be precise the devices hooked up to the router are consoles, so i would ultimately like to get them online like i can in windows. In windows, i simply select the two network connections, and &quot;bridge them&quot;. Using DHCP the bridge is automatically assined an IP address

Using Wicd network manager i can only connect to one or the other, i cant have both running at the same time. I am also running Ubuntu 8.10      

Any help is much appreciated

---

### Post by ruddyrum on 2009-08-10
Thought i might add that the interfaces im trying to bridge are: eth0 and wlan0 just incase it makes a difference!

---

### Post by fwre01 on 2009-08-10
You can create a bridge in Ubuntu using 'bridge-utils' (im pretty sure thats in the repo's) I've only ever set this up manually, the this is the idea...

You create a bridge group (ie, br0) and then add interfaces into that bridge group. You can add as many as you want and it creates what is essentially a layer 2 switch. Then it should just be a case of connecting a switch to your eth0 interface and connecting the devices you want to access the net. They should all pick up and IP address from the wireless side of the bridge.

Ive never tried to create a bridge group with a WLAN interface, I assume that would still work. Someone might want to correct me on that.

Alternately, you can create a router from your PC. (i have made one of these for my friends to connect his xbox to the internet in the same situation and it has worked great)

---

### Post by ruddyrum on 2009-08-10
will give this a go and post back.

just so you know, both routers have DHCP enabled. router1 (wifi internet) is 192.168.0.1 and the other (clients router) 192.168.0.2. Should i turn DHCP off on the client router?

---

### Post by fwre01 on 2009-08-10
Yes, if you build a bridge group you will only need one.

---

### Post by ruddyrum on 2009-08-10
added:
```
iface br0 inet dhcp
bridge_ports eth0 wlan0
```
to /etc/network/interfaces and then ran  sudo ifup br0

Bridge worked, i could ping all client, but not the gateway for the internet (192.168.0.1) so as a result... no internet!

saw that the bridge br0 was retrieving the lease from 192.168.0.2 when it should be getting the lease from 192.168.0.1 !!!

So i have now disabled DHCP on the client router and now it is not retrieving an IP at all

Can you bridge a wireless connection in linux?

---

### Post by ruddyrum on 2009-08-10
well it seems windows has one up on linux... have been looking at this all day, and have found many unanswered threads here and on other forums regarding this issue!

Seems you can easily take a wired internet connection and re-route it through a wireless card to make a homemade wirless connection/router, but strangely wireless to wired doesnt work! Im no expert but the issue seems to be with the wireless authentication.

I would love to be proven wrong, and see this working on linux!!

---

### Post by fwre01 on 2009-08-11
Yeah, I was slightly sceptical of bridging a WLAN and ETH interface. In a typical network to 'bridge' two wired segments, both AP's need to participate and negotiate the bridge, but this simply isnt happening with your laptop.

My advise would be to 
* connect your PC to the wireless network.

* Then assign the ETH interface a static IP address of say 192.168.16.10 255.255.255.0 (no default gateway). 

* Then change the DHCP scope on the wired side router to be 192.168.16.0, handing out 192.168.16.10 as clients default gateway.

* enable routing on your PC by using this command 
```
echo "1" > /proc/sys/net/ipv4/ip_forward
```

* then use this command to PAT the addresses on the wired side to the IP address of your PC on the wireless side
```
iptables -t nat -A POSTROUTING -o wlan0 -s 192.168.16.0/24 -j MASQUERADE
```

I realise thats a lot to do, but it should work well. Might have a few teething problems, but ive used this setup to connect my friends xbox to his internet in the same fashion and it works well.

---

