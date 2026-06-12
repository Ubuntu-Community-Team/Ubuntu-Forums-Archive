---
title: "Bridging Ethernet Ports &amp; Keeping Static IP On One Port"
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by am3nd on 2010-03-11
Hello!

Pretty much a n00b in the Linux world unfortunately. I'm currently using Ubuntu 9.1, and a motherboard which has two Ethernet ports on it.

What I would like to do is bridge these ports, so I can plug in another Ethernet cable and run it to an unmanaged switch in my room (handy for my work laptop when on-call and building other PCs, etc).

I.e. Router --> 8-Port Switch --> My PC.
Eth 0 --> 192.168.1.100 static
Eth 1 --> 5-Port Switch --> DHCP

I believe this is the config to make the ports bridged:

ifconfig Eth0 0.0.0.0
ifconfig Eth1 0.0.0.0
brctl addbr Bridge0
brctl addif Bridge0 Eth0
brctl addif Bridge0 Eth1
ifconfig Bridge0 u[FONT=Verdana]p

- How do I save this so upon reboot it sticks?
- How do I force Eth0 to remain as a static IP of 192.168.1.100?

Thanks :)
[/FONT]

---

### Post by koszta on 2010-03-11
try looking at /etc/network/interfaces
[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/]("http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/")

---

### Post by am3nd on 2010-03-11
Can't someone tell me more specific information?

I feel like I've been reading over and over again on google and nothing really tells me anything right.

shell@MINISTRY:~$ sudo ifconfig Eth0 0.0.0.0
SIOCSIFADDR: No such device
Eth0: ERROR while getting interface flags: No such device

That doesn't even work :|

---

### Post by Pauligrinder on 2010-03-11
> **am3nd said:**
> Can't someone tell me more specific information?

I feel like I've been reading over and over again on google and nothing really tells me anything right.

shell@MINISTRY:~$ sudo ifconfig Eth0 0.0.0.0
SIOCSIFADDR: No such device
Eth0: ERROR while getting interface flags: No such device

That doesn't even work :|

you have a typo there at least. In Linux, lowercase and uppercase letters are treated as separate letters, so -> it's eth0, not Eth0. I'm also pretty sure bridge0 is supposed to be in lowercase.
not sure about the rest though, sorry. but shouldn't it work by entering the IP to be used instead of 0.0.0.0?
also, to have a static address, you can edit /etc/network/interfaces, adding something like this:

```
iface eth0 inet static
address <address>
netmask <mask>
network <network address (not sure if necessary)>
broadcast <broadcast address (not sure if necessary)>
gateway <address>
```

---

### Post by am3nd on 2010-03-11
Oh thank you. I was so tired last night I didn't even notice the capital letters.

I will try this again tonight.

As for the 0.0.0.0, I have read that that selection of config was just for creating the bridge initially. And then you configure each interface's IP address, mask, etc, afterwards.

Guess I'll find out tonight!

---

### Post by am3nd on 2010-03-12
No real luck. Setting the bridge up obviously takes down my connection to my router .. but I still see static IP address assigned in /etc/network/interfaces

Does anyone know how to set this up properly? Sorry, bit of a n00b, not really sure what to do.

---

### Post by helgman on 2010-03-13
Hello,

By making the bridge you are trying to turn your computer into a "switch", right?

Have you tried setting the IP-address on the bridge interface?

```
ifconfig Bridge0 192.168.1.100/24
```

Seems to be working on my machine. As for making it "sticky", it might need a bit more research ...

*EDIT: Or not, [https://help.ubuntu.com/community/NetworkConnectionBridge](https://help.ubuntu.com/community/NetworkConnectionBridge)*

Regards,
Helgman

---

### Post by am3nd on 2010-03-14
Setting an IP on the bridge didn't work. I couldn't get to the Internet :(

Even tried assigning static on the eth0 again with sudo ifconfig eth0 192.168.1.100/24 .. still didn't help.

---

### Post by helgman on 2010-03-14
Did you try to reach the computer from within the network when you did set the IP on the bridge? Just to make sure that it's not something else that is keeping you of the net.

Regards,
Helgman

---

