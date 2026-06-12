---
title: "Networking: Speed Issue on Ubuntu 9.04"
date: 2009-10-02
forum: Networking &amp; Wireless
---

### Post by mhgrier on 2009-10-02
Hello everyone!

I'm still a bit of a newbie when it comes to Ubuntu, but I'm learning!

While I have a 1.0gbps connection here at college an a 82540EM wired Gigabit Ethernet Controller, I'm still only getting speeds of 100Mb/s when I look at the "Connection information" for my system.

I did a little bit of research around here, but couldn't find the solution to my problem and I was hoping someone could help.

sudo lshw -C network
```

  *-network        
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: eth0
       version: 02
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI duplex=full firmware=N/A latency=64 link=yes mingnt=255 module=e1000 multicast=yes port=twisted pair *****speed=100MB/s*****
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 62:ed:c6:81:93:e1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


```

Why is it only running at 100Mb/s?
I'm running Ubuntu 9.04 and I'm really hoping to get this going.

Please let me know if you need/want any more information to be able to resolve the issue.  I will respond quickly =)

---

### Post by doas777 on 2009-10-02
what is written on the side of the cable?
what is the model of your switch/router?
what is the output of from ethtool when run on the other host?

most likely you either have cat5 cable or your on a 100mbps switch port.

also, what speed is it that you believe is 100mbps? i get about 30-35mBps on gigabit transfering large files over samba with consumer class nics and switch. get about 8-10 on 100mbps. what are you getting?

---

### Post by mhgrier on 2009-10-02
Thanks for your response doas777!

On the side of the cable: CAT5.  Is this a problem?
I don't know too much about the router, as it is on the other side of the wall from me at college and I don't have access to it.  All I know is that my other Windows computer does run at gigabit speeds.
I'm sorry... I don't know what "output from the ethtool when run on the other host" means.  If you want to give me a code to run in the terminal, I'd be more than happy to do that.

What's the issue with having a CAT5 cable?

When transferring large files over Samba on this machine, can download FROM the machine from another computer at megabit speeds (12.5 megabytes per second at max), and I can upload only around 4-6 megabytes per second.  That's why I believe it is 100mbps.

Thanks again for your response.  Please let me know.

---

### Post by doas777 on 2009-10-02
> **mhgrier said:**
> Thanks for your response doas777!

On the side of the cable: CAT5.  Is this a problem?
I don't know too much about the router, as it is on the other side of the wall from me at college and I don't have access to it.  All I know is that my other Windows computer does run at gigabit speeds.
I'm sorry... I don't know what "output from the ethtool when run on the other host" means.  If you want to give me a code to run in the terminal, I'd be more than happy to do that.

What's the issue with having a CAT5 cable?

When transferring large files over Samba on this machine, can download FROM the machine from another computer at megabit speeds (12.5 megabytes per second at max), and I can upload only around 4-6 megabytes per second.  That's why I believe it is 100mbps.

Thanks again for your response.  Please let me know.

ok i see. yes, Gigabit requires a cat5e cable (e for enhanced I think).

about ethtool, I appologize, i mistook your lshw output for ethtool's. ethtool is a good util for finding info on, and controling your network card. i usually use it if i am concerned about a terminals speed.

it does sound like you are getting 100MB service so I would try swapping the net cable between your two pcs (rebooting  both afterward) and see if your situation reverses itself. if it does, just pick up a peice of cat5e.

good luck

---

### Post by mhgrier on 2009-10-02
Excuse me... my mistake.

The cable that is connected to the Ubuntu machine is labeled "CAT .6" (I'm not sure what the "." means though).

Any other ideas?

---

### Post by doas777 on 2009-10-02
> **mhgrier said:**
> Excuse me... my mistake.

The cable that is connected to the Ubuntu machine is labeled "CAT .6" (I'm not sure what the "." means though).

Any other ideas?
cat6 shoudl do gigabit no problem, but it is possible that the router/switch does not fully support it yet. I would still try swapping the cables at least once. 

you can use ethtool to set your speed and duplex, but I always lost my link if i set it to a speed that my connecting network could not handle. then I had to use ethtool to reinitalize the card and reset the speed back to 100/full.

here is a tutorial on ethtool if you wanna give it a go:
[http://hype-o-thetic.com/2009/08/01/ubuntu-ethtool-permanent-1000basetx-full-duplex/](http://hype-o-thetic.com/2009/08/01/ubuntu-ethtool-permanent-1000basetx-full-duplex/)
and the man page: [http://linux.about.com/od/commands/l/blcmdl8_ethtool.htm](http://linux.about.com/od/commands/l/blcmdl8_ethtool.htm)

---

### Post by mhgrier on 2009-10-03
Thanks for the link to the tutorial, but I'm afraid I'm not quite sure what to do with it.  Does it mean to create a file with that code in it and put it somewhere?
As very much a Linux novice, I'm not quite sure where to go from there.

---

### Post by mhgrier on 2009-10-03
Still having problems.  I tried to do something with the ethtool but I don't think I saved any changes.  Regardless, for some reason now my download speeds are hovering around 1 Mb/s instead of 10-12.  Any more ideas?

---

