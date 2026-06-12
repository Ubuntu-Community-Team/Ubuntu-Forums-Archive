---
title: "Basic information on setting up a home vpn"
date: 2011-03-20
forum: Networking &amp; Wireless
---

### Post by Jabrouwer on 2011-03-20
I'm trying to set up a VPN for my home so I can ssh from my Mac to the linux desktop on my LAN remotely, but I have no idea what to do.  The internet seems to suggest using a VPN, but I have no idea what's involved with setting something like that up, and I'm not even sure that's what I need to do.  The linux desktop is on my LAN along with a few windows xp computers, if that matters.

Does anyone care to either help or point me in the direction of good information (preferably suited for networking beginners)?

---

### Post by cherva on 2011-03-20
Read this wiki: [https://help.ubuntu.com/community/OpenVPN]("https://help.ubuntu.com/community/OpenVPN") OpenVPN creates a virtual ethernet device with ip address of your choice ( for example 10.8.x.x ) on any computer you install openvpn. And any computer in your vpn accessed by this ip ( you can access theese addresses only if you are in the same vpn ) is protected because the traffic inside the vpn is encrypted. I can write you a simpler tutorial about how to install and configure it if you are interested in OpenVPN.

---

### Post by Jabrouwer on 2011-03-20
Wow, thanks, I bet that'll be useful.

I'm not sure I understand though, so all I have to do is install openVPN on the desktop on my LAN as the server, then configure the connection on my Mac as the client, and things should work?  Nothing else special needs to be done?

---

### Post by cherva on 2011-03-20
> **Jabrouwer said:**
> Wow, thanks, I bet that'll be useful.

I'm not sure I understand though, so all I have to do is install openVPN on the desktop on my LAN as the server, then configure the connection on my Mac as the client, and things should work?  Nothing else special needs to be done?
Yes, you can install openvpn on any other machine to see each other in the vpn. :) Post here if you have problems.

---

### Post by Jabrouwer on 2011-03-20
Awesome, thanks, I'll be back if I have problems.

---

