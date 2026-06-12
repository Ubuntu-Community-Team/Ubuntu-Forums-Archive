---
title: "Can't SSH into server until I ping something"
date: 2013-01-09
forum: Networking &amp; Wireless
---

### Post by TBBucs on 2013-01-09
OS1: Ubuntu Server 12.04 (server)
OS2: Windows 7 (network computer)

I'm having a weird problem, and I'm not sure what to do about it. When I reboot the server, then try to SSH into it from another machine on the same network, I get a "connection refused" error. But once I ping the network computer from the server, I can SSH into the server from that computer just fine.

Any idea what would cause this?

About my network setup...the server is ethernet, and the network computers are wireless. The server is assigned a static IP address from a configuration setting, and the network computers all get an address from DHCP.

---

### Post by TBBucs on 2013-01-09
More information. Apparently, after successfully SSHing into the server, then closing putty, I won't be able to SSH into the server again after a few minutes. It seems the connection "wakes up" when I ping from server to client, but then the connection shuts down again after a certain amount of non-connected time.

---

### Post by ahallubuntu on 2013-01-09
Can you be more specific about your network?

Are you setting a static IP on the Ubuntu server itself, or are you letting the router assign one with a DHCP reservation (so it always gets the same IP)?

Are you trying to access it via an IP or via a name?

---

### Post by CharlesA on 2013-01-09
Sounds like the network is dropping out.

Are you connecting to the server to ping via the console or ssh?

---

### Post by TBBucs on 2013-01-10
Hmmm, well, I'm not sure what exactly fixed it, but I'm no longer having this issue. I went on to work on some other network-related tasks, and in the process of setting those up, this issue disappeared.

Thanks for your advice anyway!

---

### Post by PC-Ente on 2013-02-18
Hello folks

Just a Hint, the used network device wasn't showing in my ```
/etc/network/interfaces
```

i added it and now it works for me

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```

my default wired Network is eth0

Hope this helps some people out there... ):P

cya

---

