---
title: "changing sysctl.conf has no effect in sysctl"
date: 2012-02-26
forum: Networking &amp; Wireless
---

### Post by szabie_szabie on 2012-02-26
Hi All,

I am unable to truly change sysctl rp_filter settings.

I tried to modify sysctl.conf. It now looks like below:

```
# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
net.ipv4.conf.default.rp_filter=0
net.ipv4.conf.all.rp_filter=0
net.ipv4.conf.eth0.rp_filter=0
net.ipv4.conf.wlan1.rp_filter=0
```

after reboot I can see this:
```
$ sudo sysctl -a | grep rp_filter | grep -v arp'
net.ipv4.conf.all.rp_filter = 1
net.ipv4.conf.default.rp_filter = 1
net.ipv4.conf.lo.rp_filter = 1
net.ipv4.conf.eth0.rp_filter = 1
net.ipv4.conf.wlan1.rp_filter = 1
```

what do I miss?
I need to set this to work with VPN.

---

### Post by Toz on 2012-02-26
Hello and welcome to the forums.

I just tested this on 11.10 and it worked as it should. What version of ubuntu are you using?

There is also (in 11.10) the file /etc/sysctl.d/10-network-security.conf that contains some of these values. These values _should_ be overwritten by those in /etc/sysctl.conf, but there was a bug a while ago (a few versions back) where this wasn't happening. Depending on the version you are running, you may be suffering from this bug.

You can also try adding those values to /etc/sysctl.d/10-network-security.conf to see if it works (as a workaround).

Other than that, there maybe some other program/daemon/event that is changing those values in your setup. You could try adding:
```
/sbin/sysctl -p
```
...to the end of your /etc/rc.local file (above the exit 0 command), to force-read the /etc/sysctl.conf file at the end of system initialization.

---

### Post by szabie_szabie on 2012-02-27
I have it tested on two laptop (my mother's and mine), both of them have Ubuntu 11.10 .

My mother's system has accepted these settings and everything works flawlessly. 
But not so my own machine... :(

I have set all the corresponding lines in the /etc/sysctl.d/10-network-security.conf file also - with no luck.

I will try adding 
/sbin/sysctl -p
to my /etc/rc.local file when I will be at home again and I will report if it had success!

---

### Post by szabie_szabie on 2012-02-28
OK, I have not tried to add 
/sbin/sysctl -p 
to the end of my /etc/rc.local file. 
I think it would be useless due to the followings:


After starting my system I see these lines in terminal:

```
$ sudo sysctl -a | grep rp_filter | grep -v arp
net.ipv4.conf.all.rp_filter = 1
net.ipv4.conf.default.rp_filter = 1
net.ipv4.conf.lo.rp_filter = 1
net.ipv4.conf.eth0.rp_filter = 1
net.ipv4.conf.wlan1.rp_filter = 1
$ sudo sysctl -p
net.ipv4.conf.default.rp_filter = 0
net.ipv4.conf.all.rp_filter = 0
net.ipv4.conf.eth0.rp_filter = 0
net.ipv4.conf.wlan1.rp_filter = 0
net.ipv4.conf.lo.rp_filter = 0
$ sudo sysctl -a | grep rp_filter | grep -v arp
net.ipv4.conf.all.rp_filter = 0
net.ipv4.conf.default.rp_filter = 0
net.ipv4.conf.lo.rp_filter = 0
net.ipv4.conf.eth0.rp_filter = 0
net.ipv4.conf.wlan1.rp_filter = 0

```

After I turned on VPN connection, voila:

```

$ sudo sysctl -a | grep rp_filter | grep -v arp
net.ipv4.conf.all.rp_filter = 1
net.ipv4.conf.default.rp_filter = 1
net.ipv4.conf.lo.rp_filter = 1
net.ipv4.conf.eth0.rp_filter = 1
net.ipv4.conf.wlan1.rp_filter = 1
net.ipv4.conf.tun0.rp_filter = 1

```

..and no packet passed through the virtual tun0 adapter.

I think it should be firewall problem / misconfiguration because if I turned it off via Firestarter, all my problems disappeared.

However I don't know what to adjust on the firewall. As I remember it must have "factory settings" yet.

---

### Post by szabie_szabie on 2012-02-28
OK, after some googling I found the solution on more sites.

eg.:[http://www.howtoadvice.com/FirestarterVPN]("http://www.howtoadvice.com/FirestarterVPN")

you have to add the following lines to your firestarter config file:

/etc/firestarter/user-pre

```
iptables -A INPUT -j ACCEPT -s xxx.xxx.xxx.xxx -p esp
iptables -A INPUT -j ACCEPT -s xxx.xxx.xxx.xxx -p udp -m multiport -sports isakmp,10000
iptables -A INPUT -j ACCEPT -i tun+
iptables -A OUTPUT -j ACCEPT -d xxx.xxx.xxx.xxx -p esp
iptables -A OUTPUT -j ACCEPT -d xxx.xxx.xxx.xxx -p udp -m multiport -dports isakmp,10000
iptables -A OUTPUT -j ACCEPT -o tun+
```

just replace xxx.xxx.xxx.xxx with the IP address of your vpn server.

if you are using  Cisco VPN client instead of vpnc then replace tun+ with cipsec0.

---

