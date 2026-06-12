---
title: "Using two NICs"
date: 2009-11-30
forum: Networking &amp; Wireless
---

### Post by OdSquad64 on 2009-11-30
First I'll say I've read a few tutorials on this, but none of them seem to be exactly what I'm looking for.  I'll explain my situation and see if anyone can give me some advice.

Right now I'm in a college dorm room with 6 ethernet jacks, If I connected 6 computers to each one, each computer would be able to upload a torrent at about 11.5 MB/s, all at the same time.  My desktop computer has two NICs, and I'd like to be able to use both of them to upload at around 20MB/s.  Based on my circumstances, would I be able to do this?  Also, I have no control over my IP address and it changes every time I restart my computer, so if I make it static, I have no network connection.  I think this is the part that messes me up on the tutorials for port bonding, because they all tell me to make my IP address static.  Can anyone tell me exactly what I need to do to make this happen, if it is possible?

I really appreciate any help you can give me.

---

### Post by nelfin on 2009-11-30
Presumably. It's called NIC teaming, but I haven't got two NICs in any of my desktops, so I've never done it personally.

Try:
[http://www.howtoforge.com/network_bonding_ubuntu_6.10](http://www.howtoforge.com/network_bonding_ubuntu_6.10)
[http://ubuntuforums.org/showthread.php?t=99668](http://ubuntuforums.org/showthread.php?t=99668)
[http://ubuntuforums.org/showthread.php?t=163453](http://ubuntuforums.org/showthread.php?t=163453)

---

### Post by OdSquad64 on 2009-11-30
Thanks for the help.
Unfortunately though, those are kind of old and I found that some of the files it says to edit no longer exist.  Searching for NIC bonding led me to this: [http://linuxshellaccount.blogspot.com/2009/01/setting-up-dual-dual-nic-bonding-on.html](http://linuxshellaccount.blogspot.com/2009/01/setting-up-dual-dual-nic-bonding-on.html)
Even though this is pretty much up to date, it points me to the folder /etc/modprobe.d/arch which I don't seem to have either.  Reading some more into it I found that some people have been having problems with bonding after upgrading to 9.10, which is what I'm using.  I haven't found anything to get this working yet, but I'll keep looking.
Thanks for your help and If anyone else knows how to get this working, I'd greatly appreciate it.

---

### Post by peepingtom on 2009-11-30
I'm sorry I really don't know the proper way to do this. I'd love to hear a proper explaination. I bet you can do this with chroot. Or if you're into a horrible hacky lazy way, use VirtualBox and bridge its ethernet ports to a physical port. However, that VirtualBox bridge would be a good way to screw around with this without destroying your working setup, you could add a 3rd NIC and use the other 2 in a VM until you figure out what you're doing.

Please post back if you get this working, i'd love to do this with wifi :D

---

### Post by DGortze380 on 2009-11-30
First, there is no way you're getting 11.5 MB/s over the internet.

You probably mean 11.5 Mb/s ... which is rather slow. This indicates to me that your college is limiting your bandwidth.

You can bond your two NICs, which (assuming 10/100 NICs) would give you a max bandwidth of 200 MB/s. This doesn't help you any. Your problem is not the physical limitation of your NIC, it's the bandwidth limitation imposed by your network. Even bonded NICs only have 1 IP address, thus you'd be subject to the same bandwidth limiting as 1 NIC.

Even if we hypothetically assume you're getting an impossible speed of 11.5 MB/s ... bonding your NICs STILL wouldn't help you any. Your 1 NIC has a max bandwidth of 100 MB/s ... you're not maxing 1 NIC, so adding a second won't give you any extra speed.

---

### Post by OdSquad64 on 2009-11-30
I definitely mean 11.5MB/s,  my NICs are 1000Mb/s, but the school's lines are only 100Mb/s and we get every drop of it

---

### Post by DGortze380 on 2009-11-30
> **OdSquad64 said:**
> I definitely mean 11.5MB/s,  my NICs are 1000Mb/s, but the school's lines are only 100Mb/s and we get every drop of it

I'm afraid you're mistaken...

regardless, you're not maxing out your first NIC, thus adding a second won't gain you any bandwidth. I'm sorry.

---

### Post by OdSquad64 on 2009-12-01
> **DGortze380 said:**
> I'm afraid you're mistaken...

regardless, you're not maxing out your first NIC, thus adding a second won't gain you any bandwidth. I'm sorry.


Here's a screenshot from the system monitor.  I'm just uploading torrents.

---

### Post by OdSquad64 on 2009-12-01
Also, I'm not maxing out my NIC, but I am maxing out the line.  There is another line available for me to max out with my other NIC though

---

### Post by DGortze380 on 2009-12-01
> **OdSquad64 said:**
> Also, I'm not maxing out my NIC, but I am maxing out the line.  There is another line available for me to max out with my other NIC though

So bond the NICs ... I'm still not convinced you'll get any additional bandwidth.

LAN is entirely different, but you're just not going to get those speeds over the internet. Period.

EDIT: You also need to consider where that speed is measured... you may be pumping out 11MiB/s at the NIC, but if most of those packets are getting dropped at the border, the bandwidth measure at the NIC is misleading and essentially useless... run a bandwidth test and see if you still get 11MiB/s up. [http://www.speedtest.net/](http://www.speedtest.net/)

---

### Post by OdSquad64 on 2009-12-01
[http://www.speedtest.net/result/639443039.png](http://www.speedtest.net/result/639443039.png)
I suppose it's possible that I'm uploading a torrent to someone in the same dorm.  Either way I'd still like to know how to do this, even if it could only improve LAN speeds.

---

### Post by OdSquad64 on 2009-12-09
So can anyone help me with this?  I think my biggest problem is deviating from the tutorials to use DHCP instead of a static IP.  Is there a way to do this with a bond?

---

### Post by DGortze380 on 2009-12-09
[https://help.ubuntu.com/community/LinkAggregation](https://help.ubuntu.com/community/LinkAggregation)

just change 

```

###Adapter bonding for eth0 and eth1
auto bond0
iface bond0 inet static
address 192.168.1.1
netmask 255.255.255.0
gateway 192.168.1.254
dns-nameservers 192.168.1.254
post-up ifenslave bond0 eth0 eth1
pre-down ifenslave -d bond0 eth0 eth1

```

to

```

###Adapter bonding for eth0 and eth1
auto bond0
iface bond0 inet dhcp
post-up ifenslave bond0 eth0 eth1
pre-down ifenslave -d bond0 eth0 eth1

```

---

