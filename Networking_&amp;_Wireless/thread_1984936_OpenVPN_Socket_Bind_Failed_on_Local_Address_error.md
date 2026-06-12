---
title: "OpenVPN Socket Bind Failed on Local Address error"
date: 2012-05-22
forum: Networking &amp; Wireless
---

### Post by Prescilla on 2012-05-22
Good day Ubuntu users!

Can anyone help me on a "socket bind failed" error on OpenVPN.
When I was running Ubuntu Oneiric Ocelot, OpenVPN was working.
After I did a fresh and clean install of Ubuntu Precise Pangolin, OpenVPN keeps getting this "socket bind failed" error and I have never been able to connect since my upgrade.

Please help.

This is my .ovpn file
```
prescilla@prescilla:~/VPN$ cat UDP-Smart.ovpn
client
port 8080
proto udp
dev tun

ca /home/prescilla/VPN/voo/ca.crt
auth-user-pass /home/prescilla/VPN/account.txt
route-method exe

remote 91.227.220.189
dhcp-option DISABLE-NBT

lport 53
keepalive 5 60
resolv-retry infinite
fragment 1400
mssfix
comp-lzo
cipher BF-CBC
persist-key
persist-tun
verb 3
reneg-sec 0
redirect-gateway def1
script-security 2
fragment 1400

```When I start OpenVPN via terminal this is what I get.
```
prescilla@prescilla:~/VPN$ sudo openvpn UDP-Smart.ovpn
[sudo] password for prescilla: 
Wed May 23 02:25:36 2012 OpenVPN 2.2.1 i686-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [eurephia] [MH] [PF_INET6] [IPv6 payload 20110424-2 (2.2RC2)] built on Mar 30 2012
Wed May 23 02:25:36 2012 WARNING: file '/home/prescilla/VPN/account.txt' is group or others accessible
Wed May 23 02:25:36 2012 WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Wed May 23 02:25:36 2012 NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Wed May 23 02:25:36 2012 LZO compression initialized
Wed May 23 02:25:36 2012 Control Channel MTU parms [ L:1546 D:138 EF:38 EB:0 ET:0 EL:0 ]
Wed May 23 02:25:36 2012 Socket Buffers: R=[163840->131072] S=[163840->131072]
Wed May 23 02:25:36 2012 TCP/UDP: Socket bind failed on local address [undef]: Address already in use
Wed May 23 02:25:36 2012 Exiting
```

---

### Post by CGi on 2012-06-03
same problem prescilla. :D
hope anyone could help.

---

### Post by Prescilla on 2012-06-15
I was able to fix this by killing the process that uses port 53 which is dnsmasq.
If you haven't figure it out yet.
Do this, open a terminal

```
netstat -plnt
```You will see that port 53 is being used and this is by dnsmasq.

Search for the process id of dnsmasq
```
pidof dnsmasq
```Kill that process
```
kill process_id
```For example:
kill 2568

Then run your vpn script again.

---

### Post by SeijiSensei on 2012-06-15
Why would you ever want to use a privileged port like 53 for OpenVPN?  Use ports above 1023.  Ports below 1024 are not intended for userspace applications like OpenVPN.

There's a reason why we have the [Internet Assigned Numbers Authority]("http://www.iana.org/protocols").

---

### Post by Prescilla on 2012-06-16
Thank you for the response but I have no idea why the vpn account I got from a friend uses port 53, it is the config file he gave me and so I use that. I can't connect with any other port. That's just how it is.

---

