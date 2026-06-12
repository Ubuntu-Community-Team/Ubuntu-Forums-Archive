---
title: "connect two ubuntu computers via crossover cable"
date: 2010-05-31
forum: Networking &amp; Wireless
---

### Post by ario on 2010-05-31
I tried to connect two ubuntu computers via crossover network. But sometimes they can connect and see each other and even ping each other and sometimes not!
Each time, each of my PC's can ping it's own IP address but may not ping the other PC. I tried to disconnect cable, reconnect, disable network, enable it again, change IP address, disconnect via Network Manager Applet, reconnect and... . But when one of them don't want to connect I can't do this anyway!
Anyone know's what must be the problem? Sometimes it took about many seconds to get them connected, and sometimes they can't connect for many hours.
I must add that I have an ADSL modem on one of two Ubuntu PCs that connect via another cable.
Any help will be appreciated.

---

### Post by ario on 2010-10-02
Bump!

---

### Post by luvshines on 2010-10-02
Have you checked the firewall rules ??

iptables -L

Try switching them off.
sudo service iptables stop

Also:
sudo ufw disable

---

### Post by dmizer on 2010-10-02
What do you mean by "connect"? Do you only want to transfer data between the two computers (the second computer cannot access the internet)? Or are you trying to set up internet connection sharing?

---

### Post by ario on 2010-10-02
> **dmizer said:**
> What do you mean by "connect"? Do you only want to transfer data between the two computers (the second computer cannot access the internet)? Or are you trying to set up internet connection sharing?

Both of them. They sometimes can ping each other and sometimes simply can't! I checked it a thousand of times and found that it must be the pppd!
Now I must do these painful steps whenever I want to connect them:
[LIST]
[*]Disconnect all pppoe connections via eth0 by running **poff -a**
[*]Connect each computer via it's relating ethernet card
[*]ping a computer from another
[*]Bring pppeo connection on
[*]Ping computers again and poff -a again if ping failed!
[/LIST]

---

### Post by dmizer on 2010-10-03
Are you not using network-manager to configure your network?

---

### Post by ario on 2010-10-03
The problem is that I'm using a script I created myself for automatic connection through dsl modem called Autoppp.
So I cannot use network manager for my dsl connections. But for wireless and wired it differs.

---

### Post by dmizer on 2010-10-03
> **ario said:**
> The problem is that I'm using a script I created myself for automatic connection through dsl modem called Autoppp.
So I cannot use network manager for my dsl connections. But for wireless and wired it differs.

Is there some particular reason you need to use the ppp script? Network-manager does handle PPPoE connections just fine. Network-manager also makes internet sharing much easier.

If you must use the CLI for your connection, then you'll also have to use the CLI to implement connection sharing. Here's a howto for that: [https://help.ubuntu.com/community/Internet/ConnectionSharing#Ubuntu%20Internet%20Gateway%20Method%20%28iptables%29](https://help.ubuntu.com/community/Internet/ConnectionSharing#Ubuntu%20Internet%20Gateway%20Method%20%28iptables%29)

---

### Post by ario on 2010-10-04
> **dmizer said:**
> Is there some particular reason you need to use the ppp script? Network-manager does handle PPPoE connections just fine. Network-manager also makes internet sharing much easier.

If you must use the CLI for your connection, then you'll also have to use the CLI to implement connection sharing. Here's a howto for that: [https://help.ubuntu.com/community/Internet/ConnectionSharing#Ubuntu%20Internet%20Gateway%20Method%20%28iptables%29](https://help.ubuntu.com/community/Internet/ConnectionSharing#Ubuntu%20Internet%20Gateway%20Method%20%28iptables%29)

Ok. I already used CLI for this. The problem is mentioned above. I must to use a bothersome routine every time to get to computers connected. And the question is why it is this way? How can I get rid of this problem?

---

### Post by dmizer on 2010-10-04
> **ario said:**
> Ok. I already used CLI for this. The problem is mentioned above. I must to use a bothersome routine every time to get to computers connected. And the question is why it is this way? How can I get rid of this problem?

If you have followed the tutorial I linked, then it will work on boot.

---

### Post by ario on 2010-11-01
> **dmizer said:**
> If you have followed the tutorial I linked, then it will work on boot.

Sure it works. But the problem is:
I turn on server. It is only connected to DSL modem via lan and thus to Internet.
After a while I plug LAN cable.
No I need to turn the servers monitor on! Type 
poff -a
and then
pon dsl-provider 
to get to computers connected and connected to Internet. Remember that the second computer is not always connected when first computer boots up. It may get connected after a while and when this happens, I must and must do that annoying routine. Written a script to do that automatically. It will detect this problem by seeing ping [www.google.com](www.google.com) result. Whenever ping fails means new computer connected and ubuntu is sucking on Internet! It will poff and pon to solve this. But this will takes at least about 30 seconds to reconnect, because it's not good to me to write a script to ping google each second. Same problem when connect the second computer (My Laptop) trough wireless. I can not ping other computer until poff and pon on server.
Any Idea?

---

### Post by dmizer on 2010-11-01
Please post the contents of your /etc/network/interfaces file from the server.

---

### Post by ario on 2010-11-02
> **dmizer said:**
> Please post the contents of your /etc/network/interfaces file from the server.
Thanks. Here:
```

auto lo
iface lo inet loopback


iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual
```

---

### Post by dmizer on 2010-11-02
Check this document for information on how to make ppp work on boot: [https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

Edit:
Also, do you only have one ethernet card?

---

### Post by ario on 2010-11-03
> **dmizer said:**
> Check this document for information on how to make ppp work on boot: [https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

Edit:
Also, do you only have one ethernet card?

Making PPPoE to work on boot will solve the problem of disconnecting when other computer gets connected?

```
+-----+           +----------+            +-----------+
| DSL |----LAN----|   PC#1   |----LAN-----|    PC#2   |
+-----+           +----------+            +-----------+
                       |
                       |
                     WLAN
                       |
                       |
                  +-----------+
                  |  LAPTOP   |
                  +-----------+

```When PC#2 or LAPTOP connects to PC#1, DSL connection will be disconnected. Regardless it is connected on boot, not connected or any other situation!
Ok?

---

### Post by ario on 2010-11-09
Any Idea?

---

### Post by dmizer on 2010-11-11
> **ario said:**
> Making PPPoE to work on boot will solve the problem of disconnecting when other computer gets connected?

According to what I've read about your problem ... yes, if you make PPPoE work on boot, you will correct your problem.

---

### Post by ario on 2010-11-12
> **dmizer said:**
> According to what I've read about your problem ... yes, if you make PPPoE work on boot, you will correct your problem.

Why I can't do that:
I created an open source [project]("http://sourceforge.net/projects/autoppp/") to be a very very small micro-piece of linux world and to give DSL users usually in third-world an option to have an automatic DSL connections with these features:
[LIST]
[*]Redial whenever you've been disconnected by ISP server (Sometimes although your connection is still up you cannot ping [www.google.com](www.google.com))
[*]Connect payed internet connection account on days and free bandwidth account on night automatically
[*]Run download managers like Vuze and Aria2 at night using free bandwidth DSL account (You can sleep and your PC will download the new version of Ubuntu All over the night! It's third world:D)
[*]Watch if your connection is broken by pinging google and reconnect if needed
[*]and...
[/LIST]
Using this script I cannot connect on boot because this way if someties in some special situations connection between PC and ISP broke, autoppp script cannot disconnect cause root privilages needed.
Now my smart script will detect another computer is connected by seeing that ping fail! it will automatically disconnect and reconnects, and it seems that this is enough for me and other fancy graphical ways to solve this problem is not working easily.
Thanks.
Maybe forget this for now, until any good idea.

---

### Post by dmizer on 2010-11-13
Then all you need to do is configure the network as linked above and write a daemon (which will run as root) that restarts networking if ping fails.

```
ping
if ping = "no reply"
/etc/init.d/networking restart
```

---

### Post by ario on 2010-11-13
> **dmizer said:**
> Then all you need to do is configure the network as linked above and write a daemon (which will run as root) that restarts networking if ping fails.

```
ping
if ping = "no reply"
/etc/init.d/networking restart
```

Man you're right! But I promise I just relized this solution before! I mean right after my last post on this tread I went into toilet and suddenly this idea came to my brain to break apart my autoppp script in two parts, one for download management, and one for monitoring connection and a new feature:
```
shutdown -P now
```
which must run as root:)
Yes. I will try this. Will come here and prompt if this (connection to DSL on boot) solve the disconnect problem.
Thanks for all your helps. God bless you man;)

---

### Post by ario on 2011-02-11
Solved! The problem was in steps of sharing Internet connection. After running the command dpkg-reconfigure, it asked me to "When should ipmasq be started?". You must choose "After network services have been started". Or else (i.e. by selecting default option) you can not access your server until Internet connection brought up.
That was all. ipmasq hadn't been started until Internet connection brought up:)

---

