---
title: "OpenVPN - Ubuntu -  Windows7"
date: 2012-02-20
forum: Networking &amp; Wireless
---

### Post by blackice8r on 2012-02-20
Hi guys,

I have Ubuntu Server 11.10 running as a VM on a HP microserver 24/7
I use it mostly as a NAS box, sharing stuff with Samba and for download : torrents , newsgroups etc

When I'm at work I connect to it using TeamViewer, it was fast to setup but I can't always use it as my colleges need it too.

So I started looking at a VPN solution.

My home setup:
- dumb cable modem  - connected to a Belking Access Point that also handles  DHCP
- connected to the Belking is a gigabit switch
- connected to the gigabit switch - my mycroserver (ESXi running Ubuntu as a VM) and my pc

Fallowing this tutorials: 
[https://help.ubuntu.com/11.04/serverguide/C/network-configuration.html#bridging](https://help.ubuntu.com/11.04/serverguide/C/network-configuration.html#bridging)
[https://help.ubuntu.com/11.04/serverguide/C/openvpn.html](https://help.ubuntu.com/11.04/serverguide/C/openvpn.html)
I've setup OpenVPN on Ubuntu, I installed the OpenVPN client on my work laptop and copied the below files :
/etc/openvpn/ca.crt

/etc/openvpn/easy-rsa/keys/hostname.crt

/etc/openvpn/easy-rsa/keys/hostname.key

/etc/openvpn/ta.key

from the Ubuntu server to C:\Program Files\OpenVPN\config  on the windows 7 machine

I changed hostname.crt and hostname.key to my laptop's name.crt  and respectively .key

I've setup port forwarding on the Belkin for port 1194 UDP/TCP

I was expecting to have problems with the dynamic Ip and to have to look into a dynamic dns sollution but I didn't even get that far yet :)


I start the OpenVPN GUI but nothing happens...

I was expecting to have to enter an IP to connect to or something like that but nothing.

How does this work? Am I missing something?

And...would you think a IP SEC VPN might be better/easier to setup?


many thanks!

---

### Post by blackice8r on 2012-02-22
anybody...nobody? :-(

---

