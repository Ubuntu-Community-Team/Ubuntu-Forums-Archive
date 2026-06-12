---
title: "Host Unreachable - After returning &quot;interfaces&quot; settings to what worked"
date: 2013-05-22
forum: Networking &amp; Wireless
---

### Post by held7over on 2013-05-22
Ubuntu 12.04 Server version is on both the proposed dedicated Firewall-Router PC1 (having eth0 and eth1 Ethernet cards) and also exists on PC2 which is located behind PC1.  PC1 faces the Internet. On the back side of PC1 it is connected via a crossover cable to PC2.  I'm a novice at this.

I followed the Shorewall setup example exactly (except for their IP addresses) given here: https: //help.ubuntu.com/ community/ ShorewallBasics

I used the Static IP eth0 card version of their instructions in my /etc/network/interfaces file and it worked! PC1 could ping things on the Internet and it could Ping PC2. And PC2 could ping PC1 and Ping things out on the Internet. Perfect!!!

I decided then, (-to screw up my whole day-) and to try having PC1 get it's external eth0 IP via DHCP instead, so I commented out ('#') my entire STATIC section for setting eth0's EXTERNAL IP address and added:

```
# External network interface
auto eth0
iface eth0 inet dhcp
```

-in it's place to have dhcp pick the IP. I then did a-

```
#  ifdown -a;ifup -a
```

And then started pinging from the PC1 computer. I could still ping things on the Internet. I could directly ping PC1's eth1 card's static IP. However, when I tried to ping PC2's static IP address I got 'Host Unreachable' with 100% packet loss. The same happened in trying to ping PC1 from PC2. I then rebooted both machines and the situation did not change. So, not being able to figure out what was wrong, I backtracked and changed PC1 back to its original Static eth0 configuration in /etc/network/interfaces. I then did a 

```
#  ifdown -a;ifup -a
```

And discovered that the exact same problem still exists. A reboot did not help either. There is something about refreshing interfaces I seem not to know or understand....or....I am holding my mouth wrong.

I know there must be something simple I must be missing here in my limited knowledge base??? But, is something contrary surviving both a network refresh and a reboot in my networking somehow???
Thanks! ;)

---

### Post by Hadaka on 2013-05-22
Hi, if you want the router to give pc1 an ip address
just set /etc/network/interfaces to default setting.

```
auto lo
iface lo inet loopback
 
```
that should be all you need in interfaces.
good luck.

---

### Post by held7over on 2013-05-22
Thanks Hadaka, but the problem is, communications died between PC1 and PC2, as it is the same symptoms as though there were no crossover cable between them. And, I have just discovered THERE ISN'T! There is something defective about the snap mechanism on the crossover plug I am using. I just started PC2 pinging PC1 and then crawled down there and started moving the crossover plug on PC1 and then went and looked at the screen and I could see that sometimes everything was working and then sometimes 'host unreachable'.  So, this problem is defective hardware. And my problem is solved. I thought I had check the connection but I hadn't checked it with a live ping going! So, thanks for making me rethink the whole thing again! :)

---

