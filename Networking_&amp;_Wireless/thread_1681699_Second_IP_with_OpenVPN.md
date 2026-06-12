---
title: "Second IP with OpenVPN"
date: 2011-02-04
forum: Networking &amp; Wireless
---

### Post by eldaria on 2011-02-04
Hello, 

I have a VPN service using OpenVPN.
With this I previously had 1 fixed IP, but I recently upgraded for a larger bandwith, and with it I also got a second IP.
But how do I add this IP as a separate interface?


Also I want to make it so that all ordinary traffic goes through the Primary IP, but that I can assign some programs to use the secondary.
For example Apache, or rtorrent.

Any idea how to do this?

---

### Post by SeijiSensei on 2011-02-05
Create two separate .conf files in /etc/openvpn, one for each connection.  If you use the "dev tun" directive, you'll get two interfaces tun0 and tun1.  

You can bind processes to one or other virtual IPs.  For instance, if tun0 has 10.0.0.1 and tun1 has 10.0.0.2, you can tell Apache to listen on the 10.0.0.2 address.  See the "Listen" directive in Apache for details.

---

### Post by eldaria on 2011-02-05
Thanks for picking this up, i'm not so familiar with OpenVPN settings. :-)

So I make a copy of my existing openvpn.conf and rename it openvpn2.conf

What do I need to change?
I guess the ifconfig row needs to have my new IP.
Do I need to change anything else?

For safety I have removed all IP's.
```

dev tap
remote 0.0.0.0
float 0.0.0.0
port 5081
comp-lzo
#ping 15
verb 3
mute 20
ifconfig 0.0.0.0 255.255.255.128
route-gateway 0.0.0.0
redirect-gateway def1
secret /etc/openvpn/key.txt
cipher AES-128-CBC
#dhcp-option DNS 0.0.0.0

```

---

### Post by SeijiSensei on 2011-02-07
Each connection will need a separate port and a unique remote IP in the ifconfig directive.  You can use the same IP on the server end with different remote IPs.  For instance you can have on the server side

port 12345
ifconfig 10.1.1.1 10.1.1.100

in one configuration and

port 23456
ifconfig 10.1.1.1 10.1.1.101

in the other.  I use the same shared key in each case.  You can obviously specify a different key file for each connection, if you prefer, as long as it exists on both the server and the client.

---

