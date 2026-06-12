---
title: "Firestarter PPTP Problem"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by movingover on 2009-01-14
Hello, I've purchased a PPTP VPN from StrongVPN and I've been trying to fiddle with Firestarter to let it give me internet access. I've read a bunch of the how-to documentation and they haven't seemed to work for me, and I suspect I'm just missing one simple bit.

After adding my VPN server to the accepted hosts listing, I can connect to the VPN just fine, but I cannot get any internet access while Firestarter is running. I shut it off and I can browse just fine.

In ifconfig, my eth0 interface is what's plugged into the ethernet, and ppp0 is the interface that the VPN generates. Based on [this post]("http://ubuntuforums.org/archive/index.php/t-266708.html"), I added this to /etc/firestarter/user-pre:
```

# Enable eth1 with vpn -- edit the second line appropriately for your vpn
$IPT -A INPUT -i eth0 -p all -s 0.0.0.0/0 -j ACCEPT
$IPT -A OUTPUT -p all -d 216.131.95.35/0 -j ACCEPT
$IPT -A FORWARD -i ppp0 -p all -s 0.0.0.0/0 -d 0.0.0.0/0 -j ACCEPT

# Forward PPTP VPN client traffic
$IPT -A FORWARD -i $IF -o $INIF -p tcp --dport 1723 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -A FORWARD -i $IF -o $INIF -p 47 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -A FORWARD -i $INIF -o $IF -p 47 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
```
(this was also suggested in the [official Firestarter documentation]("http://www.fs-security.com/docs/vpn.php"))

Then ran the commands based on his suggestions:
```
sudo modprobe ip_conntrack_pptp
<added ip_conntrack_pptp to the end of /etc/modules>
sudo iptables -F
sudo /etc/init.d/firestarter restart
```

To restart everything. Still didn't work, so I tried adding this based on [this howto]("http://www.howtoadvice.com/FirestarterVPN"):
```
iptables -A INPUT -j ACCEPT -s 216.131.95.35 -p esp
iptables -A INPUT -j ACCEPT -s 216.131.95.35 -p udp -m multiport -sports isakmp,10000
iptables -A INPUT -j ACCEPT -i tun+
iptables -A OUTPUT -j ACCEPT -d 216.131.95.35 -p esp
iptables -A OUTPUT -j ACCEPT -d 216.131.95.35 -p udp -m multiport -dports isakmp,10000
iptables -A OUTPUT -j ACCEPT -o tun+
```

I also tried to do the guide posted [here ]("http://ubuntuforums.org/showthread.php?t=801207&highlight=firestarter+ppp0")but when I try to run
```
sudo "iptables-save > /etc/iptables.up.rules"
```
I get a permission denied error ><

Same behavior - no internet unless firestarter is stopped. I really like firestarter but this is killing me! Another solution I tried was to set the internet-connected device to ppp0, but that doesn't work as only some "unknown device" called pan0 is available next to eth0 and eth1 (my two ethernet adapters). Enabling internet connection sharing doesn't help either.


Any ideas? I've spent all day banging my head against the wall so far :/

---

### Post by movingover on 2009-01-15
Nevermind; looks like I'll need to try other options.

---

