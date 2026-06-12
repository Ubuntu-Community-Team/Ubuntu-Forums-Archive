---
title: "Need a decent firewall for my use"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by Sam__ on 2009-02-10
Hello,

I recently got Xubuntu up running a 667 MHz together with 256 megabytes of memory.
My goal is to make this a complete router with built-in firewall.
So far I have managed to get everything working and I am online with PPPoE.
The internal networking is also fixed.
Only thing missing is a firewall (script). I would badly need one as I got Windowns XP running on several machines in the network.
I have seen a couple of scripts ([link #1](https://help.ubuntu.com/community/Router#The%20Firewall%20Script) & [#2](http://rob.pectol.com/content/view/2/29/)) but still unsure if those are any good.
I am mainly focusing on a security at an average level, not so complicated port-opening and an UPnP feature would be lovely (though not necessary).
Appreciative for all feedbacks.
Sam

---

### Post by SunSpyda on 2009-02-10
*buntu comes with UFW (Uncomplicated Firewall) preinstalled. You should set it to block everything except things that *should* be connecting to the internet. I think Ubuntu blocks everything by default, except internet applications and networking daemons. As long as only programs that need internet access are connecting to the internet, you should be reasonably safe. Just set it to block everything and allow programs as you go along.

If you want an easy GUI for UFW, try installing GUFW =)

---

### Post by Sam__ on 2009-02-10
Thanks for reply.
A friend mensioned something about IPtable that is a firewall and also comes with *buntu.
Is IPtable and UFW the samething? (Or do you use both at the same time?)

---

### Post by jerome1232 on 2009-02-10
UFW is just an easy to use frontend to iptables, just about every "firewall" program you'll come across is a tool to configure iptables (since iptables syntax can be rather difficult)

If you looking to use the box as a router/firewall I think I'd recomend using something like smoothwall or ipcop. They are essentially linux distributions dedicated to being a firewall.


[http://www.smoothwall.org/](http://www.smoothwall.org/)
[http://www.ipcop.org/](http://www.ipcop.org/)
[http://www.shorewall.net/](http://www.shorewall.net/)

---

### Post by SunSpyda on 2009-02-11
Yeah I agree. BSDs and Security based Linuxes are probably better for firewalls. Ubuntu is for desktop use, not really firewalls. I would recommend OpenBSD for a firewall OS. But UFW/GUFW on *buntu will probably suite your needs.

---

### Post by Sam__ on 2009-02-11
Hello again,

I have looked up both SmoothWall and IPCop before, and still a bit unsure what will suite my needs, and if it even is neccesary instead of Xubuntu.
When it comes to SmoothWall, I got a bit confused after reading their feature comparison chart [[link]](http://www.pdfmenot.com/view/http://download.smoothwall.net/pdf/Firewall_Comparison.pdf). How am I able to get the other versions, and the Express ones look pretty stripped in that chart.
Also, which one of those two do you suggest I should go for if I change. Is in addition to that any hard to set up those OS's?
Thanks

---

### Post by Sam__ on 2009-02-11
Sorry if this is going off-topic, but at this moment I got problems with the internal networking as I though it would work OK.
Eth1 is used for external networking and eth0 internal.
Also, I am using PPPoE to get connected to external.
Here is a snapshot of /etc/network/interfaces
```
auto lo
iface lo inet loopback

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth1 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet static
address 192.168.1.1
network 192.168.1.0
netmask 255.255.255.0
broadcast 192.168.1.255
```
Other computers won't seem to connect to it either via. DHCP or static.
Tell me if anymore info is needed.
Sam

---

