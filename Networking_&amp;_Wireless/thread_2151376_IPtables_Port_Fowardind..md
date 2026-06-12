---
title: "IPtables Port Fowardind."
date: 2013-06-04
forum: Networking &amp; Wireless
---

### Post by netwo on 2013-06-04
Hello guys i wanted to make some port foward to another machine when using a type of port. Basically I wanted to make it more advance than this but I wanted to start with the basics by doing this :

```
iptables -t nat -A PREROUTING -p tcp --dport 3784 -j DNAT --to-destination IP:3784iptables -t nat -A PREROUTING -p udp --dport 3784 -j DNAT --to-destination IP:3784
iptables -t nat -A POSTROUTING -j MASQUERADE
sysctl net.ipv4.ip_forward=1

```
It dosn't seems to work :/ Please help ! 
I'm kinda new for this type of advance settings.

Thank you for your help.

---

### Post by SeijiSensei on 2013-06-04
Are the commands not on separate lines like your entry above?

---

### Post by netwo on 2013-06-04
Yup

---

### Post by prodigy_ on 2013-06-04
> **netwo said:**
> ```
iptables -t nat -A PREROUTING -p tcp --dport 3784 -j DNAT --to-destination IP:3784iptables -t nat -A PREROUTING -p udp --dport 3784 -j DNAT --to-destination IP:3784
```
On this line the same rule is listed twice. Delete the duplicated and try again. Also you need to add:
```
iptables -A FORWARD -p tcp --tcp-flags SYN,RST SYN -j TCPMSS --clamp-mss-to-pmtu
```

---

### Post by netwo on 2013-06-04
Actually i've set the two line together because it changes from tcp & udp so it dosn't really mather. all the code looke like this and still dosn't work :/



[FONT=Verdana]iptables -t nat -A PREROUTING -p tcp --dport 3784 -j DNAT --to-destination IP:3784[/FONT]
[FONT=Verdana]iptables -t nat -A PREROUTING -p udp --dport 3784 -j DNAT --to-destination IP:3784[/FONT]
[FONT=Verdana]iptables -t nat -A POSTROUTING -j MASQUERADE[/FONT]
[FONT=Verdana]sysctl net.ipv4.ip_forward=1[/FONT]
iptables -A FORWARD -p tcp --tcp-flags SYN,RST SYN -j TCPMSS --clamp-mss-to-pmtu

---

### Post by Doug S on 2013-06-04
I assume you have only showed a segment of iptables, which can make it hard for us to know the overall picture.
If eth0 is your internal interface and eth1 is your external interface and 192.168.7.4 is the local computer you are forwarding to, then try this:```
iptables -t nat -A PREROUTING -p tcp -i eth1 --dport 3784 -j DNAT --to-destination 192.168.7.4:3784
iptables -t nat -A PREROUTING -p udp -i eth1 --dport 3784 -j DNAT --to-destination 192.168.7.4:3784
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
iptables -A FORWARD -i eth1 -o eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i eth0 -o eth1 -j ACCEPT
iptables -A FORWARD -i eth1 -o eth0 -p tcp --dport 3784 -d 192.168.7.4 -m state --state NEW -j ACCEPT

sysctl net.ipv4.ip_forward=1
```@prodigy: I have never seen such a line as the one you added. I'll look into it more, but myself I don't use it.

Edit: Note: I wrote the above for a default FORWARD policy of DROP. The FORWARD rules would not be needed for a default policy of ACCEPT.

---

### Post by prodigy_ on 2013-06-04
> **Doug S said:**
> @prodigy: I have never seen such a line as the one you added. I'll look into it more, but myself I don't use it.
See here for example:
[http://lartc.org/howto/lartc.cookbook.mtu-mss.html](http://lartc.org/howto/lartc.cookbook.mtu-mss.html)

---

### Post by prodigy_ on 2013-06-04
> **netwo said:**
> still dosn't work :/
Please post the output of:
```
sudo iptables -L
sudo iptables -L -t nat
ip route show
```
and be more specific. What exactly doesn't work? I have a feeling that you're trying to reach a private IP (192.168.7.4) directly from an external network (over the Internet?) which certainly isn't going to work. You need to connect to the public  IP (provided by your ISP) instead in this case.

---

### Post by netwo on 2013-06-04
Genius , this is working like a charm , how to save this config for the computer keeps it even after a reboot ?

---

### Post by Doug S on 2013-06-04
My iptables rules are loaded via a script because it includes some non-iptables commands, such as the "sysctl net.ipv4.ip_forward=1" one for example. I use this:```
doug@doug-64:~/init$ cat [COLOR=#ff0000]/etc/network/interfaces[/COLOR]
# Smythies 2011.11.15 Can I execute my firewall script from here
#          instead of /etc/rc2.d? Add it.
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
[COLOR=#ff0000]pre-up /home/doug/init/doug_firewall[/COLOR]

# The primary interface (d-link PCI card)
auto eth1
iface eth1 inet dhcp

# Local network interface (uses built in ethernet port)
auto eth0
iface eth0 inet static
  address 192.168.111.1
  network 192.168.111.0
  netmask 255.255.255.0
  broadcast 192.168.111.255
```

---

