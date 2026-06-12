---
title: "Problem getting VPN to work with resolvconf &amp; dnsmasq"
date: 2013-03-31
forum: Networking &amp; Wireless
---

### Post by SixedUp on 2013-03-31
My main laptop is running Ubuntu 12.10 64bit desktop. To access my corporate intranet I need to run a proprietary VPN solution (Lotus Mobility Client, or LMC) which works very well - it actually has some great features. However, as you would expect, LMC is not integrated with Network Manager at all, and writes directly to /etc/resolv.conf, inserting the VPN domain at the head of the search list, and the VPN nameservers before any existing ones. As usual, this causes problems with local name resolution when I am working from my home network.

So for the last couple of days I've been trying to make my VPN play nice with resolvconf and the new local resolver (dnsmasq), trying to get the resolver to handle the VPN smoothly. Since the VPN is proprietary, my options for configuration are limited. The best I can do (as far as I can tell) is to prevent it from updating /etc/resolv.conf at all, and I can have it start a program of my choice when the VPN is established. Since I know the nameservers and domain within my corporate intranet that the VPN would configure, surely I can configure them manually?

After reading all the resolvconf documentation I could find, and the design brief for the DNS resolver changes in 12.04, and the various outstanding bugs, I decided my best option would be to set the VPN to not update /etc/resolv.conf, and have a script invoked by the VPN client use resolvconf to update the resolver manually.

The VPN creates an interface called "wc0", see:
```

$ ifconfig -a -s
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0       1500 0   2584463      0      0 0       4905490      0      0      0 BMRU
lo        16436 0     81161      0      0 0         81161      0      0      0 LRU
wc0        1348 0        11      0      0 0            44      0      0      0 MOPRU
wlan0      1500 0     31160      0      0 0           835      0      0      0 BMRU
```

I generated a file called resolv.wc0 containing something analogous to:
```

search abc.com
nameserver 1.2.3.4
nameserver 1.2.3.5
```

I then established the VPN, and ran the command "sudo resolvconf -a wc0.lmc < resolv.wc0". 

abc.com is added to the search terms in /run/resolvconf/resolv.conf, which is linked to by /etc/resolv.conf, as it should be. Clearly there is no change to the nameserver entry, which still contains 127.0.1.1, which is serviced by dnsmasq. However, attempting to ping a known server (server.abc.com) inside my VPN intranet results in failure to resolve the name. Issuing dig @1.2.3.4 server.abc.com resolves it perfectly, so I have a working connection over the VPN, and the nameservers are up. It appears that the resolver (dnsmasq) is not being updated properly by resolvconf. 

Running "sudo resolvconf -d wc0.lmc" undoes my manual changes, removing abc.com from the search terms in /run/resolvconf/resolv.conf again. But this leaves me out of ideas, and open to suggestions on what I need to do differently to make name resolution within my VPN work. HELP!

---

### Post by jdthood on 2013-04-03
The local forwarding nameserver listening at 127.0.1.1 is an instance of dnsmasq controlled directly by NetworkManager and fed nameserver information exclusively by NetworkManager. On your machine NetworkManager is not aware of the nameservers on the VPN and so NM-dnsmasq also doesn't know about these nameservers. Telling resolvconf about the VPN nameservers doesn't help because NetworkManager does not obtain information from resolvconf. (The standalone dnsmasq instance from the "dnsmasq" package *is* supplied with nameserver information by resolvconf, but that's not relevant here.)

Are you using NetworkManager to establish a LAN connection and then the LMC VPN client to establish the VPN connection? If so then it should suffice (1) to disable the NetworkManager-controlled instance of dnsmasq. Edit (with root privileges) /etc/NetworkManager/NetworkManager.conf and comment out the line "dns=dnsmasq" so that it looks like "#dns=dnsmasq"; then "sudo restart network-manager". Once this is done, NM won't run a slave dnsmasq instance to which it feeds nameserver information; instead it will feed its nameserver information to resolvconf and resolvconf will be able to combine that information with the information provided by your command "sudo resolvconf -a wc0.lmc < resolv.wc0".

You will probably have also to change one other thing. Resolvconf prioritizes nameserver addresses according to interface type. The list, in order of priority, of interface types can be found in /etc/resolvconf/interface-order. NetworkManager's information is registered under the name 'NetworkManager' which matches on the last line of the list. Your record name, 'wc0' will also match on the last line and will sort after 'NetworkManager'. To change this, (2) add a line 'wc*([^.]).lmc' after the 'tap*' line in /etc/resolvconf/interface-order.

---

### Post by SixedUp on 2013-04-04
> **jdthood said:**
> The local forwarding nameserver listening at 127.0.1.1 is an instance of dnsmasq controlled directly by NetworkManager and fed nameserver information exclusively by NetworkManager.
Ah. I think this was the key piece of the puzzle that I hadn'd realised. I had thought that everything (including NetworkManager) was feeding information into that instance of dnsmasq via resolveconf, allowing dnsmasq to do it's magic for all the interfaces that were "resolvconf enabled".

> On your machine NetworkManager is not aware of the nameservers on the VPN and so NM-dnsmasq also doesn't know about these nameservers. Telling resolvconf about the VPN nameservers doesn't help because NetworkManager does not obtain information from resolvconf. (The standalone dnsmasq instance from the "dnsmasq" package *is* supplied with nameserver information by resolvconf, but that's not relevant here.) 

Are you using NetworkManager to establish a LAN connection and then the LMC VPN client to establish the VPN connection?
Exactly this. The really nice feature of LMC that I alluded to in my last post is that it maintains it's connection state across network disconnects or transport layer changes. So I use NM to manage the real network interfaces (be they ethernet, WiFi, or bluetooth to my cellular connection) and then the VPN layers itself over whichever is the fastest of the currently available network interfaces. This means that once my VPN is established, I can seamlessly roam from network to network, or even suspend/resume the laptop, and the VPN endeavours to maintain itself optimally. And as much as possible, this is transparent for any connections across the VPN.

> If so then it should suffice (1) to disable the NetworkManager-controlled instance of dnsmasq. Edit (with root privileges) /etc/NetworkManager/NetworkManager.conf and comment out the line "dns=dnsmasq" so that it looks like "#dns=dnsmasq"; then "sudo restart network-manager". Once this is done, NM won't run a slave dnsmasq instance to which it feeds nameserver information; instead it will feed its nameserver information to resolvconf and resolvconf will be able to combine that information with the information provided by your command "sudo resolvconf -a wc0.lmc < resolv.wc0".
So, I assume that resolvconf will now reflect the nameserver information for all the interfaces (physical and my VPN) into /run/resolveconf/resolv.conf, which will be linked to by /etc/resolv.conf - which I can see will work (subject to some ordering issues as you discuss below) but that leaves me slightly confused (nothing unusual there!):
Why does NetworkManager include its own instance of dnsmasq if it's purely for its own use? and, assuming there is a good reason for that,
Would the "best" solution therefore be to run a "standalone" version of dnsmasq that *everything* is able to feed into and use for name resolution? Ie, should I actually install another copy of dnsmasq, configured similarly to the NM-dnsmasq, and have resolvconf front-end it for both NM, and my VPN? And if not, why not? (As you can tell, I'm groping around at the limit of my knowledge here!)
 
> You will probably have also to change one other thing. Resolvconf prioritizes nameserver addresses according to interface type. The list, in order of priority, of interface types can be found in /etc/resolvconf/interface-order. NetworkManager's information is registered under the name 'NetworkManager' which matches on the last line of the list. Your record name, 'wc0' will also match on the last line and will sort after 'NetworkManager'. To change this, (2) add a line 'wc*([^.]).lmc' after the 'tap*' line in /etc/resolvconf/interface-order.
Yes, that makes sense; I can see that you'd normally want the VPN nameservers checked before those of the physical interfaces.

Thanks for the help - I really appreciate understanding this.

---

