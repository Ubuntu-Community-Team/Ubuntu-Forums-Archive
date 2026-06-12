---
title: "OpenVPN; Route LAN from behind client"
date: 2008-12-07
forum: Networking &amp; Wireless
---

### Post by espenfjo on 2008-12-07
Hi!

I have an OpenVPN server at point A.
At point B i have an client which also resides on a LAN 192.168.1.0/24.

I want client C to access the 192.168.1.0/24 net.

I have tried some basic route and push commands from the server, but i really cant get it to work.

---

### Post by jmoorse on 2008-12-07
Are both the client and server's local IP segments the same?  If so you will need to do some clever subnetting to allow routing between...

---

### Post by espenfjo on 2008-12-08
No, A and B/C are not on the same subnets. in any way.
The only connection is the Internet, and the VPN connection.

The server (A) doesnt have any local nets matching the one behind B.

---

### Post by jmoorse on 2008-12-08
Ahh my bad, misread your question.  What does a tracert (Win) / tracepath (Linux) yield to the remote IP after the VPN is established?

---

### Post by ghantoos on 2008-12-08
Hello,

I'll try to make it clear :)
On your server (on A in your case) you must have:
1- in /etc/openvpn/server.conf
```
# Clients configuration
client-config-dir ccd
client-to-client
```2- in /etc/openvpn/ccd/B
```
iroute 192.168.1.0 255.255.255.0
```3- in /etc/openvpn/ccd/C
```
push "route 192.168.1.0 255.255.255.0"
```The B and C files must be the hostnames specified in the client key generations so that openvpn knows which file applies to which host.

Hope this helps,
Cheers,

---

### Post by espenfjo on 2008-12-08
When i add iroute to B i cant ping B.
Logs doesnt say anything useful.

> Mon Dec  8 23:06:44 2008 B/193.214.127.B:1273 OPTIONS IMPORT: reading client specific options from: ccd/B
Mon Dec  8 23:06:44 2008 B/193.214.127.B:1273 MULTI: Learn: 10.8.1.6 -> B/193.214.127.B:1273
Mon Dec  8 23:06:44 2008 B193.214.127.B:1273 MULTI: primary virtual IP for B/193.214.127.B:1273: 10.8.1.6
Mon Dec  8 23:06:44 2008 B/193.214.127.B:1273 MULTI: internal route 192.168.1.0/24 -> B/193.214.127.B:1273
Mon Dec  8 23:06:44 2008 B/193.214.127.B:1273 MULTI: Learn: 192.168.1.0/24 -> B/193.214.127.B:1273
Mon Dec  8 23:06:45 2008 B/193.214.127.B:1273 PUSH: Received control message: 'PUSH_REQUEST'
Mon Dec  8 23:06:45 2008 B/193.214.127.B:1273 SENT CONTROL [dellpos]: 'PUSH_REPLY,dhcp-option DNS 10.8.1.1,route 10.8.1.0 255.255.255.0,topology net30,ping 10,ping-restart 120,ifconfig 10.8.1.6 10.8.1.5' (status=1)


---

### Post by ghantoos on 2008-12-08
I forgot the important part, so here it is:
4- Enable ip forwarding and NATing on B, as root, issue:
```
/sbin/iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
sysctl -w net.ipv4.ip_forward=1
```To enable ip forwarding permenantly[FONT=monospace] vi [/FONT]/etc/sysctl.conf, and add:
```
net.ipv4.ip_forward = 1
```Hope this is it ;)
Cheers,

---

### Post by espenfjo on 2008-12-08
Ok, that might be a bit difficult since it is an Windows XP client :)

But ill poke around a bit and see if i can enable something similar, somehow :)

Thanks

---

