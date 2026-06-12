---
title: "Ubuntu 10.10 Auto reconnect PPPOE"
date: 2010-11-04
forum: Networking &amp; Wireless
---

### Post by gibz85 on 2010-11-04
Hai

**I** have a dsl connection which i used to connect using gnome network manager. Connection is fine i get internet.. 

**But** really annoying thing is my dsl operator lately(actually for 3 month) have been doing some kind of test on there network which made the connection very unstable..

**Ok** I have connection which has night unlimited download.. Usually what happen is that i put a download and goes to bed and in the morning i switch on the monitor to find it got disconnected 10 minute after i connected  :confused:..

**I** am particularly lean toward RPM based distribution(pclinux os,mandriva opensuse) Which has **pppoe-setup**  from **rp-pppoe** package.. Which on connect creates a pid and it stays connected(really usefull) last time i tried ubuntu was 8.0.4 which used **pppoeconf **for DSL which i created script to stay connected.. But pppoeconf in 10.10 works fine initially but when i restart ubuntu, my network-manager is disabled also i cannot connect using pon dsl-provider(eth0 is gone from ifconfig only lo). With this problem i would have changed back to pclinuxos, But i really really like ubuntu 10.10 look and feel

**To make long story short**

**How can** i reconnect if the connection fails, also i use this connection on night so auto reconnect in network mananger is not an option..
[B]
If all fails[/B] i am thinking about a VM for this simple process

---

### Post by dineshs on 2010-11-04
Why dont you configure your DSL modem(if you have one)in PPPoE mode?If your ISP is BSNL you can try [this]("http://ernakulam.sancharnet.in/ernakulam/bbservice.html") link to configure modem in PPPoE mode(click modem/CPE config in the given link).If you do so you need not use a dialler ie  the connection will be always ON.
> But pppoeconf in 10.10 works fine initially but when i restart ubuntu, my network-manager is disabled also i cannot connect using pon dsl-providerJust do this
First backup  /etc/network/interfaces using
```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```
Now run
```
 gksudo gedit /etc/network/interfaces
```
Let the file contain only these lines ```
auto lo
iface lo inet loopback
```and restart

---

### Post by gibz85 on 2010-11-04
> Why dont you configure your DSL modem

**Hai** i am using [COLOR="Red"]**Tataindicombroadband**[/COLOR], I have **3 connections**,Which i use accordingly,Although i got 3 router its really silly to configure three of those and connect them when i need specific connection.:).

**Ok i** will go with pppoeconf once more... Are you sure interfaces is the only file it modifies, Just to be extra cautious i will backup network folder..
[B]
Thank you[/B] for reply.. This forum gets populated pretty soon.. It took me 5 min to find my post... :KS

---

### Post by dineshs on 2010-11-05
The details such as user id password etc will be in /etc/ppp/peers/dsl-provider .DNS details will be in /etc/resolv.conf

---

### Post by gibz85 on 2010-11-06
```
auto lo
iface lo inet loopback

```
That worked .. Thank you

Just remove the modification made by pppoeconf in interfaces file..

---

