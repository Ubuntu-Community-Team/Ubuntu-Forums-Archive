---
title: "host not accepting connections or responding to ping anymore"
date: 2013-02-09
forum: Networking &amp; Wireless
---

### Post by Jay Christnach on 2013-02-09
My laptop has internet connectivity and I can log in to my desktop from it. The laptop's IP address is 192.168.1.34 according to ifconfig. I can run an ssh session from the laptop to the desktop which has 192.168.1.33 without any problem. I can't ping the laptop from the desktop, I get a destination unreachable message. Also x2go and ssh is not working (of course, IP unreachable)

Both computers run 3.2.0-37 as kernel (uname -a) and are xubuntu 12.10 (not very sure, where can I have a look to confirm this?). The laptop is connecting wirelessly if that could matter.

This has been working for years now until rather recently, maybe a few weeks from here. Maybe some update has screwed something up on the laptop?

I'd appreciate any help on troubleshooting this and I hope the problem has not already been posted as a variant in another thread.

---

### Post by Doug S on 2013-02-09
> Both computers run 3.2.0-37 as kernel (uname -a) and are xubuntu 12.10 (not very sure, where can I have a look to confirm this?).This should tell you:```
doug@doug-64:~$ [COLOR=red]cat /etc/*-release[/COLOR]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
NAME="Ubuntu"
VERSION="12.04.2 LTS, Precise Pangolin"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu precise (12.04.2 LTS)"
VERSION_ID="12.04"

```I wonder if you have a firewall running on your LapTop and not on your DeskTop (or maybe less restrictive on your DeskTop). Have a look at your iptables. Do this:```
sudo iptables -v -x -n -L
```

---

### Post by Jay Christnach on 2013-02-10
Hello Doug,

I have no file ending in -release in /etc. Maybe xubuntu doesn't use these? /etc/apt/sources.list contains sources for the "precise" release.

There are no rules defined for iptables on neither of both machines.

/etc/hosts.allow and /etc/hosts.deny are empty too. 

I now tried a wired connection. I got 192.168.1.40 for eth0 from my dhcp server. Now I can ping and connect to the laptop under that address.

lspci tells me the wifi  is a bcm4313 controller from broadcom.

The router I connect to both wirelessly and wired is used only as a switch and wlan (I have another router in the basement which routes to the internet). I can ping my android smartphone from both computers over the wlan.

Interestingly 'arp -a' lists all my computer's MAC addresses including the laptop's (both wired and wireless)...

Oh, now after trying around and disconnecting the wired connection I can ping the laptop again. So I think this needs further observation to see how that problem could be reproduceable.  It worked again after I pinged the wifi address from a third computer while the laptop was connected to wired ethernet.

The laptop certainly got upset when it noticed it would get serious when I installed wireshark :-)

So it's not the end of the story, it will certainly happen again. Thanks for wanting to help for now.

best greetings

---

### Post by Jay Christnach on 2013-02-10
It didn't take long to reappear. I ran the following experiment. I find it has to do with broadcasting and/or arp.

Laptop (nyquist; 192.168.1.34; 70:f3:95:b5:8b:f0) only connected to wifi. Running wireshark to monitor traffic.

Desktop (fermi; 192.168.1.33; 00:50:8d:b2:19:de) connected to switch, running wireshark.
root@fermi:~# arp -d 192.168.1.34
root@fermi:~# ping 192.168.1.34
PING 192.168.1.34 (192.168.1.34) 56(84) bytes of data.
From 192.168.1.33 icmp_seq=1 Destination Host Unreachable
fermi asks (repeatedly) for the MAC address I deleted from the cache:
806    524.954452    AbitComp_b2:19:de    Broadcast    ARP    42    Who has 192.168.1.34?  Tell 192.168.1.33

on the laptop:
no sign of the arp request seen in wireshark

on another computer (maxwell; 192.168.1.100) connected by wired ethernet, using tcpdump:
10:51:02.098055 ARP, Request who-has nyquist tell fermi, length 46

now from the laptop:
jay@nyquist:~$ ping 192.168.1.33
PING 192.168.1.33 .... 64 bytes from 192.168.1.33

now fermi (the desktop) nows the MAC of the laptop (nyquist) again, because it has replied to it and put its address in arp cache:
root@fermi:~# arp -a
nyquist (192.168.1.34) at 70:f3:95:b5:8b:f0 [ether] on eth0
? (192.168.1.1) at 00:13:49:02:cf:16 [ether] on eth0
? (192.168.1.40) at 1c:c1:de:b0:4b:3d [ether] on eth0
maxwell (192.168.1.100) at 00:50:ba:c0:98:0a [ether] on eth0

and then I can communicate with it again:
ping 192.168.1.33 ... reply from 192.168.1.33
 
unfortunately I have no other wifi device except my android phone at the moment. I could test if the arp broadcast gets send over wifi. I'll see if I can get tcpdump to work on it.

So clearly it has something to do with address resolution or broadcast reception. I tried to log out of wifi with my phone and then back in. I didn't see the dhcp request of the phone from the laptop.  Nor does a ping to the broadcast address appear there. That's not normal or is it?

---

### Post by Doug S on 2013-02-10
Hi Jay,
 
Sorry that my reply was of no value.
I have nothing to add to what you are already doing, and agree that getting down to the packet level with tcpdump and wireshark is the way to go.
 
By the way, on my network my wireless router is setup as a switch also. I also have tcpdump data from my main server/router. While I have never had any troubles with the wirelesss side of things, including when something is plugged into a wired connection on the wirless router, I do see some odd ARP entries in the tcpdump data. If I figure out anything that might relate to your situation, I'll report back (unlikely).

---

