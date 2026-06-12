---
title: "Trying to get an OpenVPN server running in Ubuntu"
date: 2010-09-06
forum: Networking &amp; Wireless
---

### Post by dave_birdi on 2010-09-06
Followed this guide to the letter:

[https://help.ubuntu.com/10.04/serverguide/C/openvpn.html](https://help.ubuntu.com/10.04/serverguide/C/openvpn.html)

Tried to run command:

**sudo /etc/init.d/openvpn restart**

And just get a fail returned.

This is what the log-file says...


##############################################

Tue Sep  7 00:05:31 2010 OpenVPN 2.1.0 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [MH] [PF_INET6] [eurephia] built on Jul 20 2010
Tue Sep  7 00:05:31 2010 NOTE: when bridging your LAN adapter with the TAP adapter, note that the new bridge adapter will often take on its own IP address that is different from what the LAN adapter was previously set to
Tue Sep  7 00:05:31 2010 NOTE: your local LAN uses the extremely common subnet address 192.168.0.x or 192.168.1.x.  Be aware that this might create routing conflicts if you connect to the VPN server from public locations such as internet cafes that use the same subnet.
Tue Sep  7 00:05:31 2010 NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Tue Sep  7 00:05:31 2010 Diffie-Hellman initialized with 1024 bit key
Tue Sep  7 00:05:31 2010 /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Tue Sep  7 00:05:31 2010 Control Channel Authentication: using 'ta.key' as a OpenVPN static key file
Tue Sep  7 00:05:31 2010 Outgoing Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Tue Sep  7 00:05:31 2010 Incoming Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Tue Sep  7 00:05:31 2010 TLS-Auth MTU parms [ L:1574 D:166 EF:66 EB:0 ET:0 EL:0 ]
Tue Sep  7 00:05:31 2010 TUN/TAP device tap0 opened
Tue Sep  7 00:05:31 2010 TUN/TAP TX queue length set to 100
Tue Sep  7 00:05:31 2010 /etc/openvpn/up.sh br0 tap0 1500 1574   init
bridge br0 does not exist!
Tue Sep  7 00:05:31 2010 script failed: external program exited with error status: 1
Tue Sep  7 00:05:31 2010 Exiting

##############################################

It says init bridge br0 does not exist. Do I need to create it in the network config or something?

---

### Post by b0b138 on 2010-09-06
Yes, it looks like you need to create the bridge. In the very beginning it says "This guide will assume that one VPN node, the server in this case, has a bridge interface configured. For more information on setting up a bridge see the section called &#8220;Bridging&#8221;." Follow that link and setup a bridge.

---

### Post by dave_birdi on 2010-09-06
Many thanks for the quick reply, I'll try this tomorrow.

Thanks again!

---

### Post by dave_birdi on 2010-09-07
Alright, I've created the bridge and the OpenVPN server is successfully up an running on my Ubuntu machine. I have set up port forwarding from my router to place my machine in DMZ.

Could anyone provide me a sample client configuration?

Do I need to make any firewall changes in Ubuntu?

---

### Post by Iowan on 2010-09-07
[Here]("https://help.ubuntu.com/community/VPNClient") is a help page - dunno if it has the sample you're looking for, though.

---

### Post by dave_birdi on 2010-09-08
Yeh unfortunately all of these client machines are windows based.

---

### Post by annoyingrob on 2010-09-08
I recommend using this howto: [https://www.thebakershome.net/openvpn_tutorial](https://www.thebakershome.net/openvpn_tutorial)

Here's a sample configuration for my old work network. ca.crt, robert.crt and robert.key also need to be included with this config file on the client machine. Instructions on how to generate the keys can be seen in the link above.

```

client
dev tap
proto udp

# The hostname/IP and port of the server.
remote vpn.xxxxxxx.com 1194

# Keep trying indefinitely to resolve the
# host name of the OpenVPN server.  Very useful
# on machines which are not permanently connected
# to the internet such as laptops.
resolv-retry infinite

# Most clients don't need to bind to
# a specific local port number.
nobind

# Try to preserve some state across restarts.
persist-key
persist-tun

ca ca.crt
cert robert.crt
key robert.key

ns-cert-type server

# Enable compression on the VPN link.
# Don't enable this unless it is also
# enabled in the server config file.
comp-lzo

# Set log file verbosity.
verb 3


```

---

