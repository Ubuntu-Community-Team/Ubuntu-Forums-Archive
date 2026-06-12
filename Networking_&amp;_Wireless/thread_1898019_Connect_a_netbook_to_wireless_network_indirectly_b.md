---
title: "Connect a netbook to wireless network indirectly by another laptop"
date: 2011-12-20
forum: Networking &amp; Wireless
---

### Post by giannisk88 on 2011-12-20
[FONT="Verdana"]Good Evening everyone,
I want to do something for my graduation exercise (thesis) which i'll describe in few lines.
So, i've got 2 lap tops
**1 [COLOR="Lime"]netbook[/COLOR]**: it has one LAN iface and one WLAN iface (onboard)
**1 [COLOR="Red"]laptop[/COLOR] **: it has one LAN iface and one WLAN iface (onboard)
Both of the PCs have ubuntu 11.10 installed.

I also have
**1 modem/router** from my ISP

Just to help you the modem/router has the internal ip: 192.168.2.1/24

Now, i have to execute 2 things with those things. I will show 
You the first one.

The [COLOR="red"]laptop pc[/COLOR] is connected via the WLAN iface with my modem/router which provides internet to my [COLOR="red"]laptop[/COLOR].

I want to connect my [COLOR="lime"]netbook PC[/COLOR] from the LAN iface to the LAN iface of my [COLOR="red"]laptop PC[/COLOR] and do these things:

1) [COLOR="red"]Lap-top pc[/COLOR] will provide IP to my [COLOR="lime"]netbook pc[/COLOR] when i connect each other (so i want [COLOR="red"]Lap-top[/COLOR] to be a DHCP-server)
2) [COLOR="red"]Lap-top pc[/COLOR] will provide Internet connection via it's WLAN inface (which is connected to the local network) to the [COLOR="lime"]netbook pc[/COLOR] when it's connected on it's LAN interface.


What i've done is to download and install (from Synaptic Package Manager) to my [COLOR="red"]Laptop[/COLOR] the gadmin-dhpcd which is my DHCP-server and it working very well.

The question now is:
What i have to install to my [COLOR="red"]Laptop[/COLOR] so that it can provide internet to my [COLOR="lime"]Netbook[/COLOR] ? ?
May i have to  install a DNS server in [COLOR="red"]Laptop [/COLOR]or i have to do more things?


Thank You for your time

Giannis


P.S. Graphically
[ATTACH]209430[/ATTACH]
[/FONT]

---

### Post by Kralizec on 2011-12-20
I've done this very thing before using IP masquerading: [http://linux.about.com/od/ubusrv_doc/a/ubusg18t03.htm]("http://linux.about.com/od/ubusrv_doc/a/ubusg18t03.htm")

I'm not sure about providing much more, because it may infringe on forum rules regarding helping with homework assignments.

---

### Post by praseodym on 2011-12-20
Hi,

you possibly need a "cross-cable" to connect with only one client or a switch for more than one.

Settings:

[COLOR="Red"]Laptop PC:[/COLOR]
Right-click on the network-manager applet->Edit connections
You can edit the current wired profile or create a new one. Un-checkbox "connect automatically" with any wired profile, otherwise these will connect!
_IPv4 settings:_
Wireless: Automatic (DHCP)
Wired: "Together with others" (using german layout here, you will find the right one)

[COLOR="Lime"]Netbook:[/COLOR]
_IPv4 settings:_
Wired: Automatic (DHCP)

The network-manager uses the following IP addresses:

    [LIST]
[*]    10.42.48.1 - static IP-address of wireless card in Ad-Hoc-Modus or of the LAN card/gateway
[*]    255.255.255.0 - netmask
[*]    10.42.48.255 - broadcast
[*]    10.42.48.10 to 10.42.48.100 - IP-address-pool
[/LIST]

---

### Post by giannisk88 on 2011-12-20
Thank You very much Kralizec and praseodym.
I'll try both of these techniques and if i want something else i'll post again.

---

