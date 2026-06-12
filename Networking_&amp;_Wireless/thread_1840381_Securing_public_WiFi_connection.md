---
title: "Securing public WiFi connection"
date: 2011-09-07
forum: Networking &amp; Wireless
---

### Post by zatkowich on 2011-09-07
Hello, 

I googled a while, but its still not clear for me.

I am connecting to Internet through public hotspot and I want to have my connection secure. Could somebody explain to me a bit closer how can I reach this, for example with VPN?

I have Xubuntu 11.04, but I suppose this does depends not on a distro.

Many thanks in advance.

---

### Post by haqking on 2011-09-07
> **zatkowich said:**
> Hello, 

I googled a while, but its still not clear for me.

I am connecting to Internet through public hotspot and I want to have my connection secure. Could somebody explain to me a bit closer how can I reach this, for example with VPN?

I have Xubuntu 11.04, but I suppose this does depends not on a distro.

Many thanks in advance.

To VPN you need somewhere to VPN to such as a corporate VPN server etc.

You can you use a free service [http://techpp.com/2009/07/09/top-5-free-vpn-clients/](http://techpp.com/2009/07/09/top-5-free-vpn-clients/) a little out fo date but you get the idea

Dont ever use a public connection for online banking etc.

You could also use [Tor ]("https://www.torproject.org/")

But when you use someone elses router there are always potential for man in the middle, DNS spoofing etc etc.

Be wary of login sites and error messages,  Try to limit public hotspot to plain old surfing without giving out any credentials etc.

---

### Post by mikewhatever on 2011-09-07
Here you go:
[http://www.howstuffworks.com/vpn.htm](http://www.howstuffworks.com/vpn.htm)

Most decent VPN services are not free. Another option is to set up an SSH server, if you have a spare computer at home.

---

### Post by Dangertux on 2011-09-07
For VPN I suggest checking out OpenVPN, of course if you have one system and it is only accessing the internet via public wifi this won't help you very much.

[http://openvpn.net/](http://openvpn.net/)

You could also check out something like this. For a subscription fee they provide you with a VPN to connect to.

[http://vpnmachine.com/](http://vpnmachine.com/)

Also in the same boat as the first option if you can set up a machine elsewhere you can also use an ssh tunnel.

Tor is also a decent alternative, however it's not really as great as people make it out to be. It does a decent job at obfuscating and encrypting your traffic, but it's been proven that someone can sniff Tor traffic rather easily. 

Honestly, I would look for an alternate solution to free public wifi.

---

### Post by zatkowich on 2011-09-08
Thank you for your answers, they helped at least a bit :-)

---

### Post by haqking on 2011-09-08
> **zatkowich said:**
> Thank you for your answers, they helped at least a bit :-)

NO problem, remember when you are using someone elses connection you have no control over how it is configured (or at least very little control)

The best tool at your disposal if you have to use it is common sense (applies to all areas of IT Security) it is always at the user where any security mechanisms in place fall apart.

Dont use secure sites that could possibly reveal your personal details as these might be able to get captured easily (such as online banking and the like)

So limit your personal surfing on possibly open connections.

Try using a VPN as mentioned or TOR or SSH to your own box, but as mentioned by Damgertux if preferrable dont use open hotspots.

get yourself a mobile dongle or something ;-)

---

