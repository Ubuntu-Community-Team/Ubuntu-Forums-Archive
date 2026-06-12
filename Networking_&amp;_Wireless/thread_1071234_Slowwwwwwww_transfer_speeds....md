---
title: "Slowwwwwwww transfer speeds..."
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by michealangelo on 2009-02-15
So, I'm new to Ubuntu. I've known about it for a while but just jumped in and started using it... mainly due to this [article]("http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/"). I have an iMac running Leopard 10.5.6 and my Ubuntu box is completely updated with 8.10. Both computers have gigabit and are attached to a gigabit switch that supports jumbo frames. The things is, transfer speeds are incredibly slow. Ubuntu's system monitor maxes out at ~11.5 MiB/s. Am I missing something? There has to be a way to get faster transfer speeds. Any help is greatly appreciated. Thanks, Mike.

---

### Post by dmizer on 2009-02-16
What protocol are you using for the share?

NFS, SMB, FTP?

---

### Post by michealangelo on 2009-02-16
AFP.

There has to be something capping it. I noticed when the computers were plugged into my router, sending a 6.9GB file took ~11 minutes. Now, with the gigabit switch, it still takes ~11 minutes. I've made sure both connections are using gigabit.

---

### Post by dmizer on 2009-02-16
Do you get different results with different protocols? I suggest trying NFS or FTP.

---

### Post by michealangelo on 2009-02-17
Alright. I got it working using NFS. Still the same speeds as AFP. NFS won't let me send the 6.9GB file, but will let me send a ~700MB file across. Using AFP and NFS, both take around a minute to send. What's going on??

---

### Post by dmizer on 2009-02-17
Please post the output of ifconfig from both the Mac and Ubuntu.

Any firewalls between these two boxes? Firestarter on Ubuntu?

---

### Post by michealangelo on 2009-02-18
**Ubuntu (Elite)**

studebaker@Elite:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:91:15:f9  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45779 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10661 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:67011819 (67.0 MB)  TX bytes:761561 (761.5 KB)
          Memory:d0700000-d0720000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1140 (1.1 KB)  TX bytes:1140 (1.1 KB)


**Leopard (Micheal's iMac)**

Micheals-iMac:~ Micheal$ ifconfig
lo0: flags=8049<UP,LOOPBACK,RUNNING,MULTICAST> mtu 16384
	inet6 fe80::1%lo0 prefixlen 64 scopeid 0x1 
	inet 127.0.0.1 netmask 0xff000000 
	inet6 ::1 prefixlen 128 
	inet6 fd6f:d08d:6b44:2b4a:21e:c2ff:fe05:f1d2 prefixlen 128 
gif0: flags=8010<POINTOPOINT,MULTICAST> mtu 1280
stf0: flags=0<> mtu 1280
en0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
	inet6 fe80::21e:c2ff:fe05:f1d2%en0 prefixlen 64 scopeid 0x4 
	inet 192.168.1.140 netmask 0xffffff00 broadcast 192.168.1.255
	ether 00:1e:c2:05:f1:d2 
	media: 1000baseT <full-duplex,flow-control> status: active
	supported media: autoselect 10baseT/UTP <half-duplex> 10baseT/UTP <full-duplex> 10baseT/UTP <full-duplex,hw-loopback> 10baseT/UTP <full-duplex,flow-control> 100baseTX <half-duplex> 100baseTX <full-duplex> 100baseTX <full-duplex,hw-loopback> 100baseTX <full-duplex,flow-control> 1000baseT <full-duplex> 1000baseT <full-duplex,hw-loopback> 1000baseT <full-duplex,flow-control> none
fw0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 4078
	lladdr 00:1e:52:ff:fe:5b:da:e6 
	media: autoselect <full-duplex> status: inactive
	supported media: autoselect <full-duplex>
en1: flags=8823<UP,BROADCAST,SMART,SIMPLEX,MULTICAST> mtu 1500
	ether 00:1e:52:87:30:d1 
	media: autoselect (<unknown type>) status: inactive
	supported media: autoselect
vmnet8: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
	inet 172.16.46.1 netmask 0xffffff00 broadcast 172.16.46.255
	ether 00:50:56:c0:00:08 
vmnet1: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
	inet 172.16.152.1 netmask 0xffffff00 broadcast 172.16.152.255
	ether 00:50:56:c0:00:01 


No firewalls on either machine.

---

### Post by dmizer on 2009-02-18
Try disabling IPv6 on the MAC. See if that improves thigns.

---

### Post by michealangelo on 2009-02-18
No performance changes after disabling IPv6.

---

### Post by dmizer on 2009-02-18
Try changing the Mac MTU to 1500.

---

### Post by michealangelo on 2009-02-18
The MTU was already set to 1500.

---

### Post by dmizer on 2009-02-18
My mistake, I looked at the line above your en0 :oops:

What switch are you using, and what MTU size does it support? What about HDD performance?

On Ubuntu, you can try:
```
sudo hdparm -tT /dev/sda
```
Or whatever your hard drive is labeled.

Also, what ethernet adapter are you using in the Ubuntu box? If you don't know the chipset, you can find out with this command:
```
lshw -C network
```

You can also try an MTU of 9000 for jumbo frames. Here's how to do it in Ubuntu: [http://www.ubuntugeek.com/how-to-change-mtu-maximum-transmission-unit-of-network-interface-in-ubuntu-linux.html](http://www.ubuntugeek.com/how-to-change-mtu-maximum-transmission-unit-of-network-interface-in-ubuntu-linux.html)

---

### Post by michealangelo on 2009-02-19
I'm using a Netgear GS605. I couldn't find a specific number for the MTU it supports but I know it supports jumbo frames. HDD performance is

**/dev/sda**
Timing caches reads:  2598 MB in 2.00 seconds = 1299.94 MB/sec
Timing buffered disk reads:  206 MB in 3.02 seconds = 68.11 MB/sec

[B]/dev/md0
[/B]Timing caches reads:  2418 MB in 2.00 seconds = 1209.29 MB/sec
Timing buffered disk reads:  696 MB in 3.01 seconds = 231.34 MB/sec

My ethernet adapter is an Intel 82567V-2.

I'm trying to set my MTU to something higher, but changing it to 9000 on my iMac made Finder crash. And after a restart, I'm still having trouble with Finder. Hmm...

**EDIT:**
Seems like whenever the MTU is set to 9000 in Ubuntu, Finder freaks. As soon as it's back to 1500, problem goes away.

---

### Post by dmizer on 2009-02-19
What card are you using on the Mac? Have a look here: [http://www.xlr8yourmac.com/osx/os_x_network_cards.html](http://www.xlr8yourmac.com/osx/os_x_network_cards.html) there's a few comments about a higher mtu causing finder to crash.

md0 suggests you are using software raid which could be the cause of slowdowns too. Are you sure your ethernet cable is gigabit compliant? How is it routed ... (heat sources, lots of kinks, through lots of power supplies)?

---

### Post by michealangelo on 2009-02-19
I'm using the internal card in an iMac from late 2007 (not exactly sure which card that is). Finder only seems to crash when the MTU is set to 9000 on the Ubuntu machine. I think this may have to do with the machine showing up in my sidebar.

I am using a software RAID, but wouldn't that speed things up? I wasn't aware cables had to be gigabit compliant. I know they're using gigabit because my switch shows a green light for gigabit and an orange light for 100. It's not routed any special way. Nothing seems to be interfering with it severely.

---

### Post by dmizer on 2009-02-19
No, contrary to popular belief, raid does not make things faster, and software raid even less so.

I read this:
> **michealangelo said:**
> I'm trying to set my MTU to something higher, but changing it to 9000 on my iMac made Finder crash. And after a restart, I'm still having trouble with Finder. Hmm...
to mean that you were having problems when you changed the MTU on the mac.

While you also said that you were having problems when you changed the MTU on Ubuntu, problems could also be related to the Mac. The finder issue may not present itself if you use a protocol other than samba to connect the machines as Samba generally has terrible performance and may not be able to pipe through at gigabit speeds.

Also, yes ... there is gigabit specific cable (cat6). While most cat5 cable can handle gigabit without problems, it is still a potential problem.

I'm really just grasping at straws here because speed issues can be caused by a wide variety of things, on either the Mac or the Ubuntu machine ... or both.

---

### Post by michealangelo on 2009-02-19
Hmm.. Is there any way I can tell if the RAID is slowing things down?

The first time I changed the MTU, I changed it in Ubuntu first, then Leopard. When I mentioned Finder freaked, I think it was only because the change caught up with Leopard, then caused it to crash. Now, if the MTU is set to 9000, everything is fine. It only crashes when Ubuntu is set to 9000.

Also, correct me if I'm wrong, but I'm pretty sure I'm using AFP and not Samba. I'm using Netatalk for the share.

Should I pick up some cat6 cables?

---

### Post by dmizer on 2009-02-20
> **michealangelo said:**
> Should I pick up some cat6 cables?
Frankly, I doubt that will help. It's possible, but I don't think I would suggest spending money on it. If you're in a situation where you need to get new LAN cable, make sure you get CAT6, otherwise you're probably fine with CAT5 as long as it's in good condition.

I'm really out of ideas on this though. Do you have any other gigabit cards you can swap into your Ubuntu machine for testing?

---

### Post by michealangelo on 2009-02-22
Well, I went ahead and bought some CAT6 cables. We'll see if that makes any kind of difference. I really hope this helps... Any other ideas?!

---

### Post by michealangelo on 2009-02-23
Ok, I've finally got some progress. I found that if I change 'full-duplex, flow-control" to just "full-duplex" on my iMac, I get pretty decent speeds. The 6.9GB file now transfers in about 3 minutes instead of 11. Not bad. BUT... While file transfer is happening, I pretty much lose internet. Any way to fix this?

---

### Post by michealangelo on 2009-03-14
So... I've made a little more progress. Currently, my setup is:

Internet --> WRT54G Router --> Switch --> iMac/Server/etc

I've discovered that if I unplug the cable connecting the switch to the router and leave only my iMac and the Ubuntu server connected, that same 6.9GB file transfers in less than a minute. So I'm pretty sure the connection to the router is where the block is. I have a straight-thru cable running from the uplink port on the switch to one of the ports on the router. I've looked online for help with connecting a gigabit switch to a 10/100 router and everything says there shouldn't be any transfer issues. So my question is... how am I able to keeps these transfer speeds and still have internet (no connection to router = no internet)?

---

### Post by michealangelo on 2009-03-15
anyone...?

---

### Post by dmizer on 2009-03-15
While your router is indeed your bottleneck, I think the problem is the switch. The switch shouldn't be sending switched traffic through the router, but it apparently is.

---

