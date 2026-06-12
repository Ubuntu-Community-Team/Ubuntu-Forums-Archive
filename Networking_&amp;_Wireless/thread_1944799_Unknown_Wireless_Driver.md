---
title: "Unknown Wireless Driver?"
date: 2012-03-21
forum: Networking &amp; Wireless
---

### Post by dave2001 on 2012-03-21
I can't identify my wireless driver with normal commands.. any help would be greatly appreciated. I'm trying to identify it so I can reload after suspend, since currently suspending the laptop breaks wifi. I have to know it's name to do that though. Here's my networking info. The wireless connection I'm using is through an Cisco Systems "slot" laptop card.
```

ubuntastic@Ubuntu-A20m:~$ sudo lshw -c network
  *-network               
       description: Cisco Systems
       physical id: 0
       version: 350 Series Wireless LAN Adapter
       slot: Socket 0
       resources: irq:5
  *-network
       description: CreditCard 10Base-T
       product: PS-CE2-10
       vendor: Xircom
       physical id: 0
       version: 2.10
       slot: Socket 1
       resources: irq:4
  *-network:0
       description: Ethernet interface
       physical id: 1
       logical name: eth0
       serial: 00:80:c7:6a:08:91
       capabilities: ethernet physical
       configuration: broadcast=yes driver=xirc2ps_cs multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:0c:85:35:3b:31
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.105 multicast=yes wireless=IEEE 802.11
```

There's no driver listed under network one... which is where it should be I think... any ideas?

---

### Post by dave2001 on 2012-03-22
99 views and no one even has a guess? I hope that's not a bad sign for this getting solved.

I'd love to post more helpful info if anyone can give me clue what that might be.

---

### Post by chili555 on 2012-03-22
> 99 views and no one even has a guess?Most of the guys that know this stuff are in assisted living!

Please run:```
lsmod
```Is the driver *airo* listed? If not, just post the entire *lsmod* and we'll figure it out.

---

### Post by dave2001 on 2012-03-22
> **chili555 said:**
> Most of the guys that know this stuff are in assisted living!


Heh. So that's it!

The output of lsmod does indeed list *airo*! Here are the relevant lines 
```

airo_cs                 2977  1 
airo                   66863  1 airo_cs
pcmcia                 30485  2 airo_cs,xirc2ps_cs

```

Do you think I would need both airo and airo_cs to be reloaded after suspend? Thanks for the "lsmod" suggestion! I should definitely have thought of that! Maybe I should be in assisted living too ;)

---

### Post by chili555 on 2012-03-22
I think airo_cs is your best choice.

I suspect that it didn't show up in lspci because PCMCIA devices have their own identifier: lspcmcia. You might try:```
sudo lspcmcia -vv
```

---

### Post by dave2001 on 2012-03-24
Yep, lspcmcia confirmed airo_cs. Thanks for the help Chili!

---

