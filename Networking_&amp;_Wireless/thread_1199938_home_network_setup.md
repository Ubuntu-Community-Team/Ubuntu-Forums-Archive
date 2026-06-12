---
title: "home network setup"
date: 2009-06-29
forum: Networking &amp; Wireless
---

### Post by tompoe on 2009-06-29
Just switched from DHCP connection to standalone DSL.  I am now working off static IP.  I want to have standalone DSL modem -> Switch -> multimedia computer -> Asterisk PBXinaFlash box on a home network.  I'm running Ubuntu 8.04, and need steps to assign IP address to my multimedia computer.  Is this a command line task?  Any help appreciated.

---

### Post by Iowan on 2009-06-29
Personally, I prefer command line... but first try a manual configuration via Network Manager.  IPv4 settings should let you set up address, netmask, gateway, etc. - although for some reason, it can be tricky to get the settings to stick.

---

### Post by tompoe on 2009-06-29
auto lo
iface lo inet loopback

This is what I have now in my /etc/network/interfaces file.  I found this help site: [http://guides.wkbw.com/How_to_Assign_an_IP_Address_on_a_Linux_Computer-a992026.html](http://guides.wkbw.com/How_to_Assign_an_IP_Address_on_a_Linux_Computer-a992026.html)

$ sudo /sbin/ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast qlen 100
    link/ether 00:0b:db:70:4d:01 brd ff:ff:ff:ff:ff:ff

Would this be a good way to go?

---

### Post by Iowan on 2009-06-29
File looks normal for Network Manager controlled machine. **lshw -C network** will provide similar information to what you found.  
Try setting up a manual address via Network Manager.  It is easier if NM isn't fighting you over assignments in /etc/resolv.conf.  If NM doesn't work, then */etc/network/interfaces* should provide a way.

---

### Post by tompoe on 2009-06-29
Thanks, much, Iowan.  I'm up in Charles City. Is there a users group you recommend I join to get help? The words in network manager are greek to me.  I'll follow your suggestion, and use the experience to learn some vocabulary, if nothing else.

---

### Post by Iowan on 2009-06-29
Although Network Manager is not guaranteed to work, it seems much friendlier than previous versions.

BTW, do you need static address? I'm not familiar with Asterisk PBXinaFlash box, but your DSL modem might be able to serve as DHCP server - and might be able to issue a static *lease* (based on machine's MAC address) to your multimedia computer.

---

### Post by tompoe on 2009-06-29
Good question.  So good, I had to read it multiple times.  If I understand, correctly, there's no reason to do anything with the multimedia box at this point.  

Internet <-> DSL modem <-> switch <-> multimedia box and Asterisk Box.  What would have to be done to give both boxes acess to Internet?  My thinking was, I would have to assign IP to both boxes.  On the Asterisk box, I would follow security settings to protect it.  I would also have to assign IP to multimedia box, and figure out how best to secure it, as well.

---

### Post by dmizer on 2009-06-29
If you want multiple computers, you'll need some way of creating a subnet of some kind. Your DSL provider can only give you one IP address. A switch will not do this for you, you'll need a router of some kind.

Also, since you have a multimedia PC, I highly suggest a firewall. While Linux is immune to virus and malware infections, it is NOT immune to hacking. And since you have a static IP, your computer will be extremely easy to locate.

Is there a particular reason why you want to move from DHCP to a direct connection to the internet?

---

### Post by tompoe on 2009-06-29
Dmizer:  That makes sense to me.  I think.  :)

So, it's Internet <-> DSL modem <-> switch <-> router (eth1)/Asteriskbox (eth0) <-> multimediabox.  I think the Asterisk security setup includes firewall.  This will be a huge feat for me.  Thanks for the input.  If I know where I'm going, I'll feel easier about this.

---

### Post by Iowan on 2009-06-29
I'd put the router between the modem and the switch.  All the boxes can then connect to the switch.  Just my opinion. Router might also be able to serve as DHCP server (instead of modem).

---

### Post by tompoe on 2009-06-29
Iowan:  I'm trying to visualize how I might use either 2 nics in either Asterisk or the multimedia box to direct traffic through the router I configure in the Asterisk or multimedia box.  Is that doable?  Or, is it better to invest in a linux router device?

---

### Post by dmizer on 2009-06-29
I am assuming (perhaps incorrectly) that the "static IP" you mentioned earlier is you WAN IP address (the IP assigned to you by your DSL provider). If you are unsure, you should verify this.

If your DSL modem is only handing you a WAN IP address, then you'll need to set things up according to how Iowan suggests.

Is there a particular reason why you want to route traffic through one of your computers when you have a perfectly good switch to connect to instead? I mean, what's the point in having a switch if you only have one line connected to it.

I would expect to see something like this:
```
Internet => Modem -> Router -> switch -> PBX
                                      -> media server
                                      -> other networked machines
```
Or even this:
```
Internet => Modem -> Router (port 1) -> PBX
                     Router (port 2) -> switch (port 1)
                                        switch (port 2) -> media server
                                        switch (port 3) -> other networked machines.
```

But I'm really not sure exactly what you're trying to accomplish. Is there a reason you want to eliminate your router, and is there a particular reason why you need/want to route traffic through one of your machines?

---

### Post by tompoe on 2009-06-29
IP is WAN assigned by ISP.  

Internet => Modem -> Router -> switch -> PBX
                                      -> media server
                                      -> other networked machines

That looks really good and doable to me.  I would then have a home network.  My pbx replaces landline phone for videophone.  My multimedia box lets me explore the wide wonderful world of making videos.  I'm a Vietnam vet living on a small pension, so my investment actually saves me money, once the investment is paid off.  

What router would you recommend?

---

### Post by dmizer on 2009-06-29
Just about any off-the-shelf router should do fine. If you don't need wireless, then you'll not need to spend much money. Maybe around $30 ~ $50, and in my opinion would be money well spent, mostly because you'll be able to plug it in, configure it, and forget about it.

I don't know much about Astrisk, but it may be difficult to configure it as a router. As for your media server, I think it would be risky to employ it as a router because you may inadvertently expose information due to misconfiguration.

---

### Post by tompoe on 2009-06-29
All good info.  I really appreciate it.  I ordered the pre-configured Pbx-in-a-Flash, and it was shipped earlier, today.  My next step, is to take a look at it when it arrives.  I can then see what their Forum members recommend.  It just may be the Asterisk box acts as a router on a local area network as well as routing calls?

---

### Post by dmizer on 2009-06-29
> **tompoe said:**
> It just may be the Asterisk box acts as a router on a local area network as well as routing calls?

I've been browsing through the documentation, and I really don't think Asterisk is designed for LAN routing duty. There may be a development add-on for it, but I still strongly recommend a hardware router.

---

### Post by tompoe on 2009-06-29
Glad you mentioned going with a hardware router as recommended approach.  I'm off to get a hardware router.

---

