---
title: "Wireless Bridge - Is this theoretically possible?"
date: 2010-04-22
forum: Networking &amp; Wireless
---

### Post by iain_colin on 2010-04-22
Hey guys, I've been trying for the past month or two to set up my new network at home, and banging my head trying to get this to work. I'll start with a diagram of the situation


Router <=======> Ubuntu Server <-------> Switch <------->Desktop's


Where === is a "wireless" connection, and --- is an ethernet connection.
I'm trying to get this set up so that the router acts as the internet gateway, and a DHCP server. The Ubuntu Server connects via wireless and acts almost as a transparent gateway to the Desktop's, while still being able to connect to the internet. The server connects to the other desktop's via a dumb switch.

Am I thinking pie in the sky here or is this theoretically possible?

Oh, and the Ubuntu server is using a DWA-110 Wireless USB Dongle, if that helps at all. It's set up using Ubuntu Server 9.10, with all the wireless settings working perfectly at this moment in time.

---

### Post by iponeverything on 2010-04-22
> Where === is a "wireless" connection, and --- is an ethernet connection.
I'm trying to get this set up so that the router acts as the internet gateway, and a DHCP server. The Ubuntu Server connects via wireless and acts almost as a transparent gateway to the Desktop's, while still being able to connect to the internet. The server connects to the other desktop's via a dumb switch.


I think it's perfectly doable.

To clarify, the ubuntu server is just a transparent bridge which also happens to have access to the net?

See this link:

[http://www.networkoptimizationnews.com/Neworkmonitoringsetup.html](http://www.networkoptimizationnews.com/Neworkmonitoringsetup.html)

---

### Post by iain_colin on 2010-04-22
> **iponeverything said:**
> I think it's perfectly doable.

To clarify, the ubuntu server is just a transparent bridge which also happens to have access to the net?

See this link:

[http://www.networkoptimizationnews.com/Neworkmonitoringsetup.html](http://www.networkoptimizationnews.com/Neworkmonitoringsetup.html)

Yeap, transparent bridge. Lets the DHCP server on the router offer the leases, and acts essentially as a wireless card for all the desktops off the switch.

Thanks for the link, I'll have a go at the instructions in a bit. Would you suggest actually using Knoppix, or just using the Ubuntu server installation I have going instead?

---

### Post by P4man on 2010-04-22
Certainly possible. Havent done it, but maybe this helps:
[https://help.ubuntu.com/community/NetworkConnectionBridge](https://help.ubuntu.com/community/NetworkConnectionBridge)

---

### Post by iponeverything on 2010-04-22
> **iain_colin said:**
> Yeap, transparent bridge. Lets the DHCP server on the router offer the leases, and acts essentially as a wireless card for all the desktops off the switch.

Thanks for the link, I'll have a go at the instructions in a bit. Would you suggest actually using Knoppix, or just using the Ubuntu server installation I have going instead?

Definitely keep ubuntu server install, the link is useful for the basic bridge configuration commands. The commands are fairly distribution independent.

@P4man 's link is better, as its geared directly to ubuntu..

---

### Post by P4man on 2010-04-22
Actually, this article seems to suggest it may not be possible, or at least not as easy as I would have thought:
[http://www.linuxfoundation.org/collaborate/workgroups/networking/bridge](http://www.linuxfoundation.org/collaborate/workgroups/networking/bridge)

A quote:

>  It doesn't work with my Wireless card!

This is a known problem, and it is not caused by the bridge code. Many wireless cards don't allow spoofing of the source address. It is a firmware restriction with some chipsets. You might find some information in the bridge mailing list archives to help.
Has anyone found a way to get around Wavelan not allowing anything but its own MAC address?
(answer by Michael Renzmann (mrenzmann at compulan.de))

Well, for 99% of computer users there will never be a way to get rid of this. For this function a special firmware is needed. This firmware can be loaded into the RAM of any WaveLAN card, so it could do its job with bridging. But there is no documentation on the interface available to the public. The only way to achieve this is to have a full version of the hcf library which controls every function of the card and also allows accessing the card's RAM. To get this full version Lucent wants to know that it will be a financial win for them, also you have to sign an NDA. So be sure that you won't most probably get access to this peace of software until Lucent does not change its mind in this (which I doubt never will happen).

If you urgently need to have a wireless LAN card which is able to bridge, you should use one of those having the prism chipset onboard (manufactured by Harris Intersil). There are drivers for those cards available at [www.linux-wlan.com](www.linux-wlan.com) (which is the website from Absoval), and I found a mail that says that there is the necessary firmware and an upload tool available for Linux to the public. If you need additional features of an access point you should also talk to Absoval. 

I think the article is slightly dated,  but the problem is probably still there.

---

### Post by iponeverything on 2010-04-22
> **P4man said:**
> Certainly possible. Havent done it, but maybe this helps:
[https://help.ubuntu.com/community/NetworkConnectionBridge](https://help.ubuntu.com/community/NetworkConnectionBridge)

If you are ever ask to drop a tap into a compromised switched network.. its quite useful.

---

### Post by iponeverything on 2010-04-22
checkout dd-wrt x86 -- If it is able to do it, you pretty much just try to approximate the same configuration under Ubuntu.

---

### Post by iain_colin on 2010-04-22
Just Reading through the dd wrt x86 page, it says it only supports wireless for registered users. Also, I would prefer some form of Linux distro, would like this pc to act as an overnight downloaded and a home web server.

---

### Post by frantid on 2010-04-22
You might try this:


[http://www.faqs.org/docs/Linux-mini/Proxy-ARP-Subnet.html](http://www.faqs.org/docs/Linux-mini/Proxy-ARP-Subnet.html)

---

### Post by iain_colin on 2010-04-22
An update on this:
 
Followed the instructions in the first method (they seemed to be exactly the same as the ones in the second), turned the bridge on, and... nothing! Lol.

I couldn't get a DHCP address from the Router, and network traffic wouldn't pass through either.

Will try again today, might have screwed up somewhere. Also, since the wireless is WPA protected, I have to use wpa_supplicant to access, with this being run as part of rc.local.

---

### Post by iain_colin on 2010-04-23
Okay I've tried it with two USB dongles, and neither of them have seemed to work. I guess firmware may be an issue.

I've been trying to think of a way around this, is there any way to set it up with the Ubuntu Server acting like a secondary router, issuing DHCP leases to the desktop's, and working as a gateway? In this case, is it possible for external devices on the wireless network, to access those on the wired network, via the gateway?

---

### Post by frantid on 2010-04-23
What you've just mentioned is the link I posted.  It should do exactly what you want as long as the Ubuntu box allows the forwarding.

---

### Post by iain_colin on 2010-04-23
Thanks for that. As I was googling more on ARP Proxying, I found some instructions that were written to get a wifi bridge working with VirtualBox, a situation very similar. That method uses parprouted and bcrelay, going to try it out tomorow. 
Thanks again :)

---

### Post by iain_colin on 2010-04-23
Finally got this working thanks to some hacked together commands :D
I'll post the method below in case anyone else is wondering. Only think that doesn't work so far is my iPhone Remote application with iTunes, but I think thats a limitation of using this method.

```
#!/bin/bash
# sofar.sh

echo "Turn on Wireless"
ifconfig wlan0 down
ifconfig eth0 down
wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
ifconfig wlan0 up
ifconfig eth0 up
dhclient wlan0


echo "Change system settings"
sysctl net.ipv4.ip_forward=1
sysctl net.ipv4.conf.wlan0.proxy_arp=1
sysctl net.ipv4.conf.eth0.proxy_arp=1
ip addr add 192.168.1.20/32 dev eth0

iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
echo "Parprouted"
parprouted wlan0 tap0
bcrelay -d -i eth0 -o wlan0
```

Some of that may be redundant, but I included it anyway. Thanks again guys :D

---

