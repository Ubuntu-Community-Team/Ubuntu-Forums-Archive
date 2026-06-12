---
title: "Open VPN &amp; Samba client problem"
date: 2009-08-13
forum: Networking &amp; Wireless
---

### Post by BarryDocks on 2009-08-13
Hi there,

I am having trouble mounting the samba shares once connected via OpenVPN.  Client is a Ubuntu 9.04, server is 8.04 lts 64 bit

My OpenVPN server IP is 192.168.0.100 and is is behind a NAT router gateway IP 192.168.0.1 with the appropriate port open udp

I have tried adding the following line to tne smb.conf:
> hosts allow = 192.168.0.100 10.8.0.0/24 127.0.0.1

and the following line to the server.conf:
> server 10.8.0.0 255.255.255.0
route 10.8.0.0 255.255.255.255

I can successfully connect to the server with the client and see all the samba shares but when I try to browse them I get "unable to mount location - Failed to mount windows share

Help!:confused:

---

### Post by dmizer on 2009-08-13
When connecting to samba shares via a VPN tunnel (rather than the more complicated bridged VPN), you will probably be unable to access the share via places > connect to server.

Please try the 2nd link in my sig.

---

### Post by BarryDocks on 2009-08-13
Thanks, but the stuff in your link is too technical for me:(

Would I be better configuring a TCP conection rather than udp?

BTW addinf the allow hosts to the smb file stopped everything inlcuding local browsing

---

### Post by dmizer on 2009-08-13
> **BarryDocks said:**
> Thanks, but the stuff in your link is too technical for me:(
If you read it carefully and follow the directions closely, you should be successful, especially if you've already been successful in creating a VPN connection.

> **BarryDocks said:**
> Would I be better configuring a TCP conection rather than udp?
All VPN connections are UDP. If you are competent enough with networking to correctly configure a bridged VPN network, you should be able to also configure your samba shares according to the second link in my sig.

> **BarryDocks said:**
> BTW adding the allow hosts to the smb file stopped everything inlcuding local browsing

I'm not sure I understand what you're referring to here. There's nothing in my howto that suggests adding "allow hosts" to a smb file.

---

### Post by paulisdead on 2009-08-13
Have you tried opening a Nautilus window, hitting ctrl-L to get the location bar, and typing in smb://servername/sharename?  This works fine for me.

---

