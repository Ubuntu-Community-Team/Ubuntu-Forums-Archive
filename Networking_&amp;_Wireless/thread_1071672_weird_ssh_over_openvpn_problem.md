---
title: "weird ssh over openvpn problem"
date: 2009-02-16
forum: Networking &amp; Wireless
---

### Post by doorman on 2009-02-16
hy all!

I use openvpn to connect over to my firm's network. Everything worked fine until I upgraded to Intrepid. Now, I can't ssh to any of the servers, but I can do other stuff, such as ping them, browse firm's internal www pages (an exception to that being the trac system installed there). Here is the output I get from ssh:
```

doorman ~ $ ssh baldrick -v
OpenSSH_5.1p1 Debian-3ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to baldrick [192.168.0.240] port 22.
debug1: Connection established.
debug1: identity file /home/doorman/.ssh/identity type -1
debug1: identity file /home/doorman/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/doorman/.ssh/id_dsa type -1
debug1: Remote protocol version 1.99, remote software version OpenSSH_3.9p1
debug1: match: OpenSSH_3.9p1 pat OpenSSH_3.*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-3ubuntu1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
Connection to 192.168.0.240 timed out while waiting to read

```The server is password authenticated, so the keys shouldn't play any role in it. Also, one of the servers has the SSH1 protocol enabled, so I can connect to it using this protocol:
```

doorman ~ $ ssh baldrick -1
doorman@baldrick's password: 
Last login: Mon Feb 16 23:30:13 2009 from 192.168.0.89
doorman@baldrick ~ $

```This is *weird* to me because I also possess a laptop from which I can connect through openvpn and ssh without a problem. The laptop went through the same process of upgrade (from 8.4 to 8.10) as the desktop. There are two basic differences between the two, though:

[LIST=1]
[*]the ssh keys differ
[*]the desktop (the one which can't connect) runs the 64-bit kernel, while the laptop runs the i686 kernel
[/LIST]

What's going on here?

---

### Post by doorman on 2009-02-17
anyone?

---

### Post by BatteryKing on 2009-02-19
I ran into the exact same problem where if I was locally connected it would work, but through OpenVPN it failed.

Here was my fix: Go into /etc/ssh/ssh_config and set: serverAliveInterval 50

I had mine set to one and it seems that is too frequent for slow WAN connections.

---

### Post by doorman on 2009-02-20
thnx for the tip, I'll try it tonight (my current setting for the serverAliveInterval is 5, so I guess this is rather slow for a WAN)

---

### Post by doorman on 2009-02-20
No luck :(

I get the same output, it just waits for a little longer.

I guess this is a lost cause

---

### Post by Shorin on 2010-09-23
This solution worked for me, even though other computers could connect to it just fine. I think it was doing one of those dumb reverse dns lookup things.

---

### Post by ivkosh on 2011-10-28
Hi, 

I had the same problem with openvpn and ssh and now found a solution.
In my case changing openvpn protocol from udp to tcp solved ssh problem.
Look like it was some weird packet loss or mtu problem.

Hope it helps.

---

