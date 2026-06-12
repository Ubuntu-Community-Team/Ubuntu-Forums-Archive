---
title: "How to get my computer a static IP from linksys router"
date: 2009-12-15
forum: Networking &amp; Wireless
---

### Post by tom4everitt on 2009-12-15
Hi all,

just bought a (linux-based) linksys router. First impression is really good, it seems to kick my old d-link routers *** :)

There's one thing I haven't quite been able to figure out yet: how do I forward ssh connections to my computer. 

I found the place where to forward connections on port 22 to some local IP, but how do I assign a static IP to my computer, so I know which IP to forward it too? 


Thx in advance

---

### Post by tom4everitt on 2009-12-15
I found one guide how to set a static IP for the computer, but it only said what to do in the computer (and only mac and windows). 

And as I understand it, the computer is simply given an IP every time it connects, so how can changing something in the computer suffice? If I'm wrong on this point, does anyone know how and where to this in Linux? (i.e make sure the computer has a static IP.)

---

### Post by gpsmikey on 2009-12-15
Some routers support a feature called "static dhcp" or something similar - you go into the router and tell it what IP address to hand out for a specific MAC address.  Now each time that machine requests an address, it will get the one you have specified in the router for that MAC address.  My Linksys WRT54G with Tomato firmware (Linux based) installed on it does support that option. I'm not sure all of them do - you will need to snoop through the documentation for your router.:D

I should have mentioned - there are basically two ways a computer comes up with it's IP address - one is called static and is set in the config files for the computer (and you better be right otherwise it doesn't talk to anything else on the network).  The second way, which is probably the most common is called dynamic address configuration where the computer comes up and requests an IP address on the network.  Whatever is configured to work as a DHCP server (your router typically) will hand out an address that will be in some range of available addresses.  What you are looking for is for the router to always give that computer the same IP address.

mikey

---

### Post by Maheriano on 2009-12-15
Those are some workaround ways to do it but the proper way to get a static IP is to get assigned one from your IP. This is what hosting companies do, it's what's usually meant when someone talks about a static IP. ISP usually charge for them but not too much, call and ask them what the cost is.

---

### Post by gpsmikey on 2009-12-15
He indicated he was already behind a Linksys router, so he is using private IP addresses ( 192.168.?.? ) - the static address your ISP would give you would be on the other side of the router (which is also a concern if you are trying to get to it from the outside world ) The OP question though was on how to get a static IP on a system behind a Linksys router.

mikey

---

### Post by wmcbrine on 2009-12-15
Static IPs don't need to be obtained from the router. Just make sure the address you choose isn't in the range of addresses the router uses for DHCP, so it doesn't inadvertently assign the address to another machine. (The address does still have to be in the same subnet, of course; and by default, your router is probably set up to use the whole subnet for DHCP. So, you'll have to change that.)

You *can* probably set up your router to assign a dynamic IP statically (static DHCP), based on the MAC of your network interface. But you don't *need* to do so. The router can still find your machine without having to assign the address itself.

---

### Post by tom4everitt on 2009-12-15
> **gpsmikey said:**
> Some routers support a feature called "static dhcp" or something similar - you go into the router and tell it what IP address to hand out for a specific MAC address.  Now each time that machine requests an address, it will get the one you have specified in the router for that MAC address.  My Linksys WRT54G with Tomato firmware (Linux based) installed on it does support that option. I'm not sure all of them do - you will need to snoop through the documentation for your router.:D

I should have mentioned - there are basically two ways a computer comes up with it's IP address - one is called static and is set in the config files for the computer (and you better be right otherwise it doesn't talk to anything else on the network).  The second way, which is probably the most common is called dynamic address configuration where the computer comes up and requests an IP address on the network.  Whatever is configured to work as a DHCP server (your router typically) will hand out an address that will be in some range of available addresses.  What you are looking for is for the router to always give that computer the same IP address.

mikey


Ok, thanks for your reply! I'm pretty sure I get the general idea, but I still can't find the option in the menus. 

I have the almost the same router as you do though, I think: Linksys WRT54GL its called (also linux-based :)), you wouldn't happen to remember where in the menus this option was or what it was called?

---

### Post by tom4everitt on 2009-12-15
> **wmcbrine said:**
> Static IPs don't need to be obtained from the router. Just make sure the address you choose isn't in the range of addresses the router uses for DHCP, so it doesn't inadvertently assign the address to another machine. (The address does still have to be in the same subnet, of course; and by default, your router is probably set up to use the whole subnet for DHCP. So, you'll have to change that.)

You *can* probably set up your router to assign a dynamic IP statically (static DHCP), based on the MAC of your network interface. But you don't *need* to do so. The router can still find your machine without having to assign the address itself.

Ok, cool, so that would be the other way to do it... Do you know which config-file/menu you would put this information in? I'm using fedora/ubuntu, but I guess it shouldn't matter much.

---

### Post by oldfred on 2009-12-15
You can do it all thru ifconfig, but you have to type in all the parameters. It is easy to use system, preference, network connections and edit if you alrady have the DHCP set up or add if not.

Make sure the address you set is outside the range of offered DHCP addresses the router is using.
            [FONT=Arial] Starting IP  Address: [/FONT]            **192.168.1.100 **or use any number up to 100 [B](router is usually 1)
[/B]

---

### Post by tom4everitt on 2009-12-15
So I went into the network connections menu, 
found the linksys connection under wireless, 
chose manual instead of automatic DHCP, 
set IP to 192.168.1.10, 
set netmask to 255.255.255.0,
set gateway to 0.0.0.0

So far everything seemed fine, it connected to the router with this new settings, and ifconfig said I had the right local IP (192.168.1.10). 

But then no matter what DNS-server I chose, I can't load web-pages. (I tried nothing, OpenDNS, and the one found in /etc/resolve.conf.)

I wonder what might be the problem...

---

### Post by tom4everitt on 2009-12-15
So further googling reveals that the original firmware of linksys wrt54gl does not support assigning a static ip to a mac address. 

So either I have to change firmware to something called dd-wrt (which seems easy enough since linksys routers seems to be supported), or I'll have to figure this with setting an ip on my own computer. It's really weird I can't access web pages with my manual setting, it must be something with the dns-server, mustn't it?

---

### Post by oldfred on 2009-12-15
I have this router and just changed from DHCP to fixed. Reset DHCP range on the router. Did an ifconfig down & and ifconfig up. And it worked just fine with setting on computer.

Linksys WRT54GL
    Firmware Version:     v4.30.7, Jun. 20, 2006

---

### Post by tom4everitt on 2009-12-15
Sorry, sounds great, but could you explain it in a little more detail?

---

### Post by oldfred on 2009-12-15
I thought I had it working but it was still on DHCP. It took one more setting.[Screenshot-Editing Auto eth0.png]("http://ubuntuforums.org/attachment.php?attachmentid=140067&stc=1&d=1260919441")

---

### Post by gpsmikey on 2009-12-15
OK, the first problem - being able to get out to the outside world - is you broke the gateway - the gateway address is typically the same as the address of the router from the LAN side (in this case, it would probably be 192.168.1.1 )  As far as the firmware on the router, as I indicated, I have Tomato installed on mine because I liked some of the features it had, however, I'm not sure if it is available for your router.  Again, there are two ways to end up with a fixed IP address on your computer - either set it up in the config files on the system or if the router supports it, set it up so it is always handed that address when it requests an IP address via DHCP.  If you set it up on the config files in the computer, you need to make sure you are outside the range that the router will hand out via DHCP (that will be in the router configuration).  The advantage to using the "static DHCP" address routine is that you can leave your computer to use DHCP and if you hook up to a different network, it will be able to get an address from the router for that network.  Linksys tends to use the 192.168.1.? addresses while the SMC routers use 192.168.2.? for their default addresses.  In general, a MAC address is "hardwired" - it is the Media Access Control (if I remember correctly) - a 48 bit number that is actually 2 parts 24 bits are a vendor ID and 24 bits are a serial number, so you can actually tell from the MAC address who made your network card.  The IP address on the other hand is something gets assigned to the system when it needs to access a network and the address it gets is either set in the config files on the system or is handed out via the DHCP server (which in this case is the router).  Hopefully that explains it a bit better.

mikey

---

### Post by tom4everitt on 2009-12-16
I got it working now, thank you all! 

The problem was simply that I had put in the wrong gateway, as soon as I changed it to the IP of the router, it worked. 

Also, the setting to use a specific IP (instead of one assigned by the router) was set specifically for my linksys connection, so I think my computers standard way to connect to networks will still be to get an IP from the network (DHCP).

I'll see if I change the firmware some time in the future, sounds like fun. Especially OpenWRT seemed cool, looked like a "full" linux system for embedded devices, with its own package manager, so you could simply choose which features you want and which not.

Once again, thanks!

---

