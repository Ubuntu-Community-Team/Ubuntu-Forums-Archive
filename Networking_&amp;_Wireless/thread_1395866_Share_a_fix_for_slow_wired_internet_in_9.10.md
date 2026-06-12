---
title: "Share: a fix for slow wired internet in 9.10"
date: 2010-02-01
forum: Networking &amp; Wireless
---

### Post by thornpig on 2010-02-01
My desktop's wired internet has been as slow as hell(40k/s,used to be 50m/s) since one update (I guess) in 8.10 intrepid. What I have tried :

1)Update to 9.04 and then to 9.10, to no avail.
2)Tried all the methods found online to disable ipv6 systemwide, to no avail
3)Boot 9.10 from CD, to no avail
3)Clean reinstall 9.10 ,to no avail
4)Reinstall driver for my ethernet controller( Ethernet controller: Broadcom Corporation NetLink BCM5787 Gigabit Ethernet PCI Express), to no avail.

5)Configure the reinstalled ethernet controller driver according to its "README.txt"---TYPE in terminal

[COLOR="Red"]sudo ethtool -s eth0 speed 100 duplex half autoneg off
[COLOR="Red"]
work like a charm!!![/COLOR][/COLOR]

I still don't know the meaning of this command. I am so exited, I can't wait to share this fix to everyone suffering from the slow internet. I don't think you have to reinstall the driver as I did, just try the command above. Good luck!

---

### Post by Fire_Chief on 2010-02-01
> sudo ethtool -s eth0 speed 100 duplex half autoneg off

This configured your network card to turn off auto-negotiation for speed and duplex. It also set the speed to 100Mbps and half duplex.

So even if you were connected to a gigabit switch and have a gigabit NIC in your system, you would not see speed better than 100Mb. For most purposes, this is still fine (especially a home PC getting to the Internet) since you would not even approach half this speed.

Cheers!

---

### Post by thornpig on 2010-02-01
Fire_Chief,

Thanks for the nice reply. Now I am clear about its function.
But I don't understand why the default setting for my ethernet controller in Ubuntu gave me that slow internet.

---

### Post by thornpig on 2010-02-01
Actually the following setting works even better!

sudo ethtool -s eth0 speed 100 duplex full autoneg on

---

### Post by Fire_Chief on 2010-02-01
Some switches and/or network cards do not auto negotiate well together and as a result they cannot agree on a speed and duplex that they should both use to communicate. So you get intermittent communications. Setting one or both sides to a fixed setting elimiates the confusion. This works when you are sure of that both sides can work at the defined settings but are not figuring it out for themselves.

Full duplex always works faster than half since it can then do data receiving and sending at the same time. Half duplex can only send or receive at any one time.

And of course the speed setting is pretty straightforward... 10Mbps < 100Mbps < 1000Mbps (1Gbps) < 10Gbps

---

### Post by Indigo340 on 2010-02-05
**A huge thanks for this fix ! **
My internet speed has been so slow lately and I was searching for a solution, now you have helped me fix it ! Thank you, thank you, thank you !

---

### Post by b9k9kiwi on 2010-02-05
> **thornpig said:**
> Fire_Chief,

Thanks for the nice reply. Now I am clear about its function.
But I don't understand why the default setting for my ethernet controller in Ubuntu gave me that slow internet.

What I don't understand is why this problem, which was talked about throughout the beta phase of 9.10, has been left unresolved to such an extent that users such as us (reasonably experienced but not technogeek) have to scratch around for a fix in the way that we have.

Disabling IPv6 in Firefox improved things for me but browsing is still painfully slow at times.  I'll try "sudo ethtool -s eth0 speed 100 duplex full autoneg on", but I'm not going to hold my breath.

All in all, very disappointing.

---

### Post by Ponch9 on 2010-05-26
```
sudo ethtool -s eth0 speed 100 duplex full autoneg on
```Worked GREAT on Lucid 10.04!!!!
I also changed my DNS to 

```
Time Warner Telecomm has the fasted servers hands down.
     64.129.67.101
     64.129.67.102
     64.129.67.103
```Found that on this post [h]("http://theos.in/windows-xp/free-fast-public-dns-server-list/")[ttp://theos.in/windows-xp/free-fast-public-dns-server-list/]("http://theos.in/windows-xp/free-fast-public-dns-server-list/")

Peace,
Ponch

---

### Post by cincinnatus13 on 2010-05-26
Well, if you want (as a reference to all users) you can download a program called "namebench" (Windows only IIRC) and it will scan all of your available DNS servers nearby and give you the fastest one (along with the second, third, etc. as well as how much faster it is.)
This is mainly in response to the last post.
I'm gonna have to boot over into Ubuntu and try this out. May help my problem.

---

