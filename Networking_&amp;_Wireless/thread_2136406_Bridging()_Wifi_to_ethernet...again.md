---
title: "Bridging(?) Wifi to ethernet...again"
date: 2013-04-17
forum: Networking &amp; Wireless
---

### Post by kingrolo on 2013-04-17
I know this has been covered many times but I can't find a scenario that exactly matches my own, and some things still aren't clear to me.

What I have...
1. Server with 2 ethernet sockets. 
2. eth0 (static ip 192.168.0.2) connected to my ADSL modem.
3. eth1 (static ip 192.168.1.2) connected to gigabit router (and a bunch of wired clients)
4. wifi router is connected to above gigabit router and provides wifi access to clients.
5. I have dhcp server, bind9, etc all setup happily on my server.

this all works fine...i use iptables, no bridging, and everything works well. (i set this up a while ago)

Now, this is what I want....
1. I've already added a 3rd NIC to my server (USB3.0 to ethernet adapter) successfuly (now labelled eth2)
2. I want my wifi router connected to this ethernet socket. (and not to the gigabit router)

I assumed this would be possible with just a few tweeks to the iptables, but now I'm wondering if I need to bridge the nics. I'd really like to avoid using bridging.

When I try to connect with my iphone i see bootp broadcasts arriving on eth2 but they go unanswered, so the iphone fails to get an ip.
I can't really see a difference in the two scenarios but traffic on eth2 seems to be ignored while eth0 and eth1 seem to communicate happily.

This is my /etc/network/interfaces file;
```

auto lo
iface lo inet loopback

# The primary network interface (ADSL modem)
auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1             # ip address of ADSL modem
dns-nameservers 127.0.0.1       # bind9 is running on this machine

# The secondary network interface (LAN)
auto eth1
iface eth1 inet static
address 192.168.1.2
netmask 255.255.255.0
network 192.168.1.0

# The tertiary network interface (ANKER USB3.0 -> Gb LAN)
auto eth2
iface eth2 inet static
address 192.168.2.2
netmask 255.255.255.0
network 192.168.2.0

```

Any advice is greatly appreciated.

---

### Post by gorkypah on 2013-04-17
...

---

### Post by kingrolo on 2013-04-18
Thanks for the detailed response. I'm glad to have found someone with a similar setup. I've applied all the changes you suggested but I still can't get wifi access. All the symptoms remain the same. At least there's been no apparent backward steps in the changes I've made. Everything seems to work as before.

tcpdump on interface eth2 still shows bootp messages arriving but the iphone never actually gets served an ip address. dhcp servers is now listening on 'br1' and serves up ip addresses to wired clients only. Any other ideas? Anything in iptables? Anything 'special' in need to configure in the wifi router?

Thanks for your help.

---

### Post by gorkypah on 2013-04-18
...

---

### Post by gorkypah on 2013-04-18
...

---

### Post by kingrolo on 2013-04-18
aha..you beat me to it! Changing the listening socket of the dhcp server got me thinking and I came up with the exact same solution you've just posted. :)
And it works!

So that then made me wonder if the dhcp server was the actual problem and that I could have done without the changes to my interfaces file and bridging etc.
So I went back to my original configuration ('interfaces' file) but dhcp now listening on eth1 & eth2, and everthing works as I wanted..without vlans and bridging.

Thanks so much for your help and getting my brain on the right track.

---

### Post by gorkypah on 2013-04-18
...

---

### Post by kingrolo on 2013-04-18
just out of interest. what's the advantage of multiple SSIDs? and also I thought this was set by the wifi AP. Can this be controlled outside of the wifi device (ie on my server)?

---

### Post by gorkypah on 2013-04-18
...

---

### Post by kingrolo on 2013-04-18
very interesting. I've come across similar problems myself with WPA2 encryption. I was looking at going down the same route as you but my server has no slots left which is why i bought the USB->ethernet adapter (£20) and hooked it up to my existing wifi router. That looks like a really nice card you've got there..and no extra cables/power supplies. I wonder if I can get a USB equivalent at a similar price (compatible with mastermode and hostpad).

---

