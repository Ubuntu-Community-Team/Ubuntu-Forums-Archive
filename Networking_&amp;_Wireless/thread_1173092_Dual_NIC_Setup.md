---
title: "Dual NIC Setup"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by HDave on 2009-05-29
I have a box with two ethernet ports on it.  After installing Ubuntu, ifconfig only reports eth0.  However, I can see from lspci that both are recognized.

I've googled myself silly, but cannot find out how I can set up eth1?

I am not interested in bonding the two NICs together, I am more interested in using the second one as a bridge to my vmware server virtual machines.  I know how to set up the virtual machine bridge, but can't seem to get eth1 working.

Thanks in advance!

---

### Post by Iowan on 2009-05-29
I'm not sure if the new version of Network Manager can handle more than one interface yet... It seems to tolerate definitions set up in */etc/network/interfaces*. You might try setting up a static address for one of the interfaces.

---

### Post by arch0njw on 2009-08-09
I am going to hope a bump here will help plunge out an answer.   I also have a dual NIC and have been frustrating myself at trying to get it to work.  Under KDE 4.2.x setting up a static IP isn't all that easy through the GUI, so I have had to go straight to /etc/network/interfaces.  Here is what I have in that file:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address a.b.c.140
netmask 255.255.255.0
network a.b.c.0
broadcast a.b.c.255
gateway a.b.c.1

auto eth1
iface eth1 inet static
address a.b.c.141
netmask 255.255.255.0
network a.b.c.0
broadcast a.b.c.255
gateway a.b.c.1

```

_**Note**_:  I have replaced my real IP address with a.b.c because... we'll, that's just me.  There are real numbers there.

This is what I get from ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:1b:fc:03:ee:bc
          inet addr:a.b.c.140  Bcast:a.b.c.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:fcff:fe03:eebc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1499 errors:0 dropped:0 overruns:0 frame:0
          TX packets:324 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:200098 (200.0 KB)  TX bytes:54545 (54.5 KB)
          Interrupt:19

eth1      Link encap:Ethernet  HWaddr 00:1b:fc:03:e5:c0
          inet addr:a.b.c.3  Bcast:a.b.c.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:fcff:fe03:e5c0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15741 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14064 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:11977534 (11.9 MB)  TX bytes:2534114 (2.5 MB)
          Interrupt:16
```As you can tell, it is not giving me what I want.  What I want is two static IP addresses as I hope my interfaces file specfies.

Help?  How do I get that?

---

### Post by Iowan on 2009-08-09
[Here]("https://help.ubuntu.com/community/UbuntuLTSP/Trunking") is an article on NIC bonding. There are other articles on bridging... otherwise, having two NIC's in same subnet might not work well.

---

### Post by arch0njw on 2009-08-09
> **Iowan said:**
> [Here]("https://help.ubuntu.com/community/UbuntuLTSP/Trunking") is an article on NIC bonding. There are other articles on bridging... otherwise, having two NIC's in same subnet might not work well.

Bonding seems to be the universal answer on this.  What I don't understand is that if I leave these to be configured by DHCP, both addresses are on the same subnet, and I can ping both IPs from other machines.

But I think I get it now:  bonding isn't just about putting two NICs on the same IP, but is also about cumulatively adding their access speeds.  Right?

---

### Post by HDave on 2009-08-09
To do bonding you have to have both cards plugged into the same switch.  It needs to be a "managed" switch and you have to tell the switch via the setup screens that port x and port y are link aggregated (bonded)...and then indicate the link aggregation type.

Check Out:  [https://wiki.ubuntu.com/LinkAggregation]("https://wiki.ubuntu.com/LinkAggregation")

I can't speak for others, but I have never used the "network" and "broadcast" attributes in /etc/network/interface...but have always had things work.

The other thing I could suggest is to look into /etc/udev/rules.d/70-persistent-net.rules to make sure the ethX and mac addresses are good and that there are no duplicate entries.

---

### Post by arch0njw on 2009-08-09
> **HDave said:**
> To do bonding you have to have both cards plugged into the same switch.  It needs to be a "managed" switch and you have to tell the switch via the setup screens that port x and port y are link aggregated (bonded)...and then indicate the link aggregation type.

Check Out:  [https://wiki.ubuntu.com/LinkAggregation](https://wiki.ubuntu.com/LinkAggregation)

I can't speak for others, but I have never used the "network" and "broadcast" attributes in /etc/network/interface...but have always had things work.

The other thing I could suggest is to look into /etc/udev/rules.d/70-persistent-net.rules to make sure the ethX and mac addresses are good and that there are no duplicate entries.

I only added the network and broadbase attributes as a trial based on a blog I found.  They made no difference.

Here are two relevant entries from that file, no duplicates:
```
# PCI device 0x11ab:0x4362 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1b:fc:03:ee:bc", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x11ab:0x4362 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1b:fc:03:e5:c0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
```

I think I have to come back to my original question.  If I leave both of these eth* entries as dhcp, they both get a unique IP on my network which is ping'able from other computers.  So why is this being so obstinate about having static IPs set?  Invariably, ONE will take the static IP, and the other will get an IP assigned by DHCP.

---

### Post by HDave on 2009-08-09
Is a.b.c.141 already taken by anything else on your network?  The udevs file is perfect....can't imagine what else it could be.

---

### Post by DGortze380 on 2009-08-09
> **HDave said:**
> To do bonding you have to have both cards plugged into the same switch.  It needs to be a "managed" switch and you have to tell the switch via the setup screens that port x and port y are link aggregated (bonded)...and then indicate the link aggregation type.

Check Out:  [https://wiki.ubuntu.com/LinkAggregation]("https://wiki.ubuntu.com/LinkAggregation")

I can't speak for others, but I have never used the "network" and "broadcast" attributes in /etc/network/interface...but have always had things work.

The other thing I could suggest is to look into /etc/udev/rules.d/70-persistent-net.rules to make sure the ethX and mac addresses are good and that there are no duplicate entries.

Not quite accurate, a number of unmanaged switches support 802.1q and 802.3ad, and a number of bonding modes don't require it.

---

### Post by arch0njw on 2009-08-10
> **HDave said:**
> Is a.b.c.141 already taken by anything else on your network?  The udevs file is perfect....can't imagine what else it could be.

I keep finding, and therefore should remember, that networking changes sometimes require a reboot.  Maybe there is a daemon other than /etc/init.d/networking that needs to be restarted or something that needs to be flushed.

The upshot is that I now have these two unique IP addresses.  Dual NIC with static IP is now working.

I may try the bonding thing after I sort out a couple other issues.  I like the idea of possibly doubling my network throughput.

---

### Post by arch0njw on 2009-08-18
This configuration **stopped** working as soon as I upgraded to KDE 4.3.  I have filed a bug with KDE.  I will update the results here.  But for reference, here is the bug:

[https://bugs.kde.org/show_bug.cgi?id=204265](https://bugs.kde.org/show_bug.cgi?id=204265)

---

### Post by HDave on 2009-10-02
Just wanted to close the loop on this thread.  I got both of my NICs working.  One NIC is setup as eth0 with a static IP.  The other NIC is set up also as a static IP, but with an IP of 0.0.0.0 which disables it's use from within Ubuntu, but leaves it available for use by my virtual machines in VMWare.  So I have the LAN plugged into eth0 and the DMZ plugged into eth1.  It's working awesome....

---

### Post by bangbong on 2011-02-14
Thanks for the heads up on checking the udev folder.. my bonding just work flawlessly.

---

### Post by enkrypt3d on 2011-02-19
This isn't the proper way to setup bonding...

First you need to remove network-manager:

apt-get purge network-manager

And install ifenslave-2.6:

apt-get install ifenslave-2.6

Then reboot and set /etc/network/interfaces to something like this: 


auto bond0
iface bond0 inet static
        address 192.168.1.69
        netmask 255.255.255.0
        gateway 192.168.1.1
        slaves all
        bond-mode 4
        bond-miimon 100
up /sbin/ifenslave-2.6 bond0 eth2
up /sbin/ifenslave-2.6 bond0 eth3

Then you can do /etc/init.d/networking restart to make the changes take effect. 

Now do ifconfig and you should only see bond0 active (with an IP)


root@Glitch:/etc/modprobe.d# ifconfig
bond0     Link encap:Ethernet  HWaddr 00:15:17:0b:7f:56  
          inet addr:192.168.1.69  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:17ff:fe0b:7f56/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:1106075 errors:0 dropped:0 overruns:0 frame:0
          TX packets:566446 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1585605118 (1.5 GB)  TX bytes:38243369 (38.2 MB)

eth2      Link encap:Ethernet  HWaddr 00:15:17:0b:7f:56  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:564687 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4268 (4.2 KB)  TX bytes:37948229 (37.9 MB)
          Interrupt:19 Memory:febe0000-fec00000 

eth3      Link encap:Ethernet  HWaddr 00:15:17:0b:7f:56  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:1106041 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1759 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1585600850 (1.5 GB)  TX bytes:295140 (295.1 KB)
          Interrupt:16 Memory:feb80000-feba0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1175 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1175 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:93685 (93.6 KB)  TX bytes:93685 (93.6 KB)


See here for further details on other things you need to configure:

[http://wiki.hiit.fi/display/it/NIC+bonding+on+Linux](http://wiki.hiit.fi/display/it/NIC+bonding+on+Linux)

Hope this helps!

---

