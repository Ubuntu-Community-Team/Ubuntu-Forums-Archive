---
title: "VPN connection cuts off 'normal' internet connection"
date: 2009-12-20
forum: Networking &amp; Wireless
---

### Post by Wiley99 on 2009-12-20
Hi all,

When I connect to my office VPN in Karmic with NetworkManager my regular internet connection is cut off so local Skype, FF etc. won't work. I guess it has something to do with routing everything to the VPN tunnel, but I don't have a clue how to fix / configure this. Can't find much in the forums either. Does anyone have any tips?

Wiley

---

### Post by madverb on 2009-12-20
Generally if you don't use the VPN to route all traffic you will have trouble accessing resources on the VPN.
You can go into Route under the VPN options and select 'Use this connection only for resources on this network'

---

### Post by Wiley99 on 2009-12-20
thanx for your reply. I tried the option you mentioned, didn't work though.
The only thing I (can) use on the network is Terminal Server Client. When I check the optio, TSC doesn't connect.


edit: added explanation

---

### Post by jamesisin on 2009-12-20
I wrote a post on this subject:

[http://www.soundunreason.com/InkWell/?p=1234](http://www.soundunreason.com/InkWell/?p=1234)

Let me know if you have any questions (here or on my site).

---

### Post by Wiley99 on 2009-12-22
> **jamesisin said:**
> I wrote a post on this subject:

[http://www.soundunreason.com/InkWell/?p=1234](http://www.soundunreason.com/InkWell/?p=1234)

Let me know if you have any questions (here or on my site).

Unfortunately I don't seem to get it working. Skype and FF are still gone after I connect to the VPN. Would that be because of the eth0 entry or because of the ppt entry? The VPN always works...

---

### Post by DGortze380 on 2009-12-22
The VPN may not support split-tunneling. The server may be forcing you to tunnel all traffic over the VPN as a security measure.

Connect to the VPN and post the output of

```

netstat -rn

```

and

```

ifconfig -a

```

---

### Post by jamesisin on 2009-12-22
Do follow DGortze380 as he may be on to something with which I am not familiar.

As to your question, eth0 should be your nic while ppt should be your VPN.  You are trying to force your system to route IP and related traffic over eth0.

In what way is it failing?  Is there a problem with my instructions or do you get an error somewhere or something else?

---

### Post by doas777 on 2009-12-22
dns resolution can be a real crapshoot with vpn's using split tunnels, especially when using shortnames for servers. are you specifying the full  dns name, and can you do an nslookup on the remote server?

---

