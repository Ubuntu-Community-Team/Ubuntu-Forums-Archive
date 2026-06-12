---
title: "Network Bridging"
date: 2009-12-16
forum: Networking &amp; Wireless
---

### Post by Rexhunt on 2009-12-16
Hi I am a 15 year old with an interest in alternative operating systems, currently I have running a headless computer with ubuntu, a cat 5 ethernet connection to a wireless router and an old coax connection to a powermac which I am going to put linux on in the near future, an old 486 that is running win98 and will be recognised by the first ubuntu computer and also a computer running win98/xp and ubuntu however I need to fiddle around wth th drivers for the network card. on the cat 5 router I have an old iMac which may possibly have linux put on it, a win xp computer we are setting up for gaming and a win xp computer that runs the first ubuntu computer through tight vnc viewer. in this network I have no internet despite having satelight on a wireless connection.
 
Could anyone help me in connecting the coax and cat 5 connections. I am also being sent by an uncle a wireless card that I would like to use to connect all of the computers to the internet.
 
Also as an aside is there a way to set up a ubuntu computer as a file server for mac and windows without having to connect it to an internet connection.
 
p.s. all the ubuntu is 8.04
 
Thanks in advance.

---

### Post by ubu_can on 2009-12-16
You should be able to do what you want if you install samba server (for the windows computers) and ssh server for the linux (and mac?) ones.  What do you mean by "without having to connect it to an internet connection"? You do not need to have outside access in order to have a file server within your LAN; you need that (outside access), if you want to access your files from outside.

As an aside: Since you are only fifteen, I feel I can give you an advice. No matter how technologically deft you may be, you will gain a lot more if you learn to write in proper english syntax: short, concise sentences. (To understand what I mean, try to read your post.)

---

### Post by seeker5528 on 2009-12-16
Bridging won't work between an ethernet and wireless connection.

Even if it is ethernet to ethernet, I suspect what you really want is shared connection/gateway approach, not bridged connection.

There is a how to for this and a forum thread describing a different method:

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)
[http://ubuntuforums.org/showthread.php?t=103881](http://ubuntuforums.org/showthread.php?t=103881)

If you do actually want to try the bridging there is a HowTo for that:

[https://help.ubuntu.com/community/BridgingNetworkInterfaces](https://help.ubuntu.com/community/BridgingNetworkInterfaces)

Later, Seeker

---

### Post by Rexhunt on 2009-12-19
Sorry about speaking in long sentences thats just how I talk and particularly type.
 
By saying that I have no internet connection what I mean is that all of the computers that I described cannot connect to the internet without moving them out to the good computer and mum doesn't like that. However once the internet connection has been shaped I can generally download up to a couple of megs at a time.

---

### Post by ubu_can on 2009-12-22
Again, not clear. What do you mean by:

"cannot connect to the internet without moving them (computers) out to the good computer"?

First, make sure you have your LAN working. What I mean by that is that all your computers can get an IP address from your router (either wired or wireless), they can ping each other, and possible you can transfer files from one to another. If you have that, then it should be easy to connect to the outside world from any computer. Depending on whether you have Windows or Linux, you may have to do some adjustments.  You have to be a bit more precise on what problem you have and what you want to accomplish.

---

### Post by puppywhacker on 2009-12-22
what he means is:
Normally the satellite internet is connected to the main computer, so he can disconnect it and establish a connection from his other computer and he can then download a few megabytes.

All computers in the same physical network need an ip-addresses in the same range (like 192.168.1.2 and 192.168.1.3). The PC that will act as gateway will have two interface cards and two ip-addresses that are not in the same range. The other PC's can than route to the gateway, and the gateway routes the packets further. Bridging is on a lower level connecting all the networks as one, where the gateway broadcasts everything it receives to the other networks, that is usually a bad idea.

Like seeker5528 said it is better to do routing, and you could do NAT internet connection sharing. Setup your ip-addresses and experiment with the command "route"

And to save ou some troubleshooting time. A gateway will not route packets until you allow ip-forwarding.
```

sysctl -w net.ipv4.conf.all.forwarding=1

```

P.S. Not everybody is a native speaker and any attempt to write english should be encouraged by tolerating mistakes. A little flexibility goes a long way.

---

### Post by ubu_can on 2009-12-22
I will be the last one who criticizes someone for his/her english (being myself not a native speaker, either). What I tried to do was to offer some advice so that he/she would express the question in a clearer manner, in order to elicit more answers.

Anyway, I just realized that the OP's internet connection does not come through the router, but through a wireless interface, in which case a routing/bridging is necessary, as suggested by other members. Most of my comments earlier had to do with the local network (LAN).

---

### Post by Rexhunt on 2009-12-23
The router is set by default to 10.1.1.1 255.255.255.0 this can be changed. So would the best course of action be to leave the gateway computer on dhcp for the ethernet which gives it 10.1.1.6 255.255.255.0 the subnet mask may be fifferent.
 
Then set the other card for the coax to 192.168.1.1 255.255.255.0.
 
Or do I need to change the subnet mask?

---

### Post by puppywhacker on 2009-12-23
That will work because the network part is the same 10.1.1. and the host part is different so 10.1.1.1 and 10.1.1.6 are in the same network

On the coax card you have the 192.168.1.X network. So use ip-addresses that start with 192.168.1. and set the gateway to 192.168.1.1

Then you can either on the 10.1.1.1 make a route to 192.168.1.X via 10.1.1.6 or you can create a NAT.

```
sysctl -w net.ipv4.conf.all.forwarding=1
iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE

```

```

[192.168.1.4] --- [192.168.1.1]
                  [ 10.1.1.6  ] --- [10.1.1.1]

```

P.S. Sorry ubu_can, I just try to spread love =)

---

### Post by Rexhunt on 2009-12-23
So when I get my wireless card can I set it up the same way?

---

