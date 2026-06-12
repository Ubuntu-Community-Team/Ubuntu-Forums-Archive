---
title: "IPTABLES help!"
date: 2010-12-02
forum: Networking &amp; Wireless
---

### Post by mytinytown on 2010-12-02
I have an old SG20 with Ubuntu 7.10 (tried to upgrade it a few times, every time it is finished it will not boot). My issue is I have a WAN and LAN switch built in to the machine. I have the WAN plugged in to my router and all plugged in to the LAN has access. It works perfect, until I turn on the firewall. I finally got the Internet, SSH, Samba and Webmin working. But I loose all access to and from the LAN switch. I will ### all port numbers in my coding:
```

#!/bin/bash
#
# Simple firewall ruleset for Toshiba Magnia SG20.
# Be careful! A typo here could lock you out of your system!
#

IF_WAN="eth1" # The interface that allows Internet access.
IF_LAN="eth0" # The local area network.

IPTABLES=/sbin/iptables

# -- Default policies --

# Strict policy, drop everything then allow specific access,
$IPTABLES -P INPUT DROP
$IPTABLES -P FORWARD DROP
$IPTABLES -P OUTPUT ACCEPT # Currently we allow all outbound traffic

# Flush all old tables
$IPTABLES -F

# Accept everything from localhost, LAN and VPN.
$IPTABLES -A INPUT -j ACCEPT -i lo 
$IPTABLES -A INPUT -j ACCEPT -i $IF_LAN 

# -- MASQUERADE -- Allow machines on your network to have Internet access

# Internet -- hide machines talking to Internet behind this firewall
$IPTABLES -A FORWARD -j ACCEPT -i $IF_LAN -o $IF_WAN

# Allow replies to come back from Internet
$IPTABLES -A FORWARD -j ACCEPT -i $IF_WAN -m state --state ESTABLISHED,RELATED
$IPTABLES -t nat -A POSTROUTING -j MASQUERADE -o $IF_WAN

# -- Internet (WAN) --

# (Uncomment to) Allow unrestricted access to my web server from the Internet.
$IPTABLES -A INPUT -p tcp -m tcp --dport #### -j ACCEPT

# (Uncomment to) Allow unrestricted login access via ssh from the Internet. 
$IPTABLES -A INPUT -p tcp -m tcp --dport #### -j ACCEPT

# (Uncomment to) Allow unrestricted login access via Webmin from the Internet. 
$IPTABLES -A INPUT -p tcp -m tcp --dport #### -j ACCEPT

# SAMBA Accesss
$IPTABLES -A INPUT -p tcp -m tcp --dport #### -j ACCEPT
$IPTABLES -A INPUT -p tcp -m tcp --dport #### -j ACCEPT
$IPTABLES -A INPUT -p tcp -m tcp --dport #### -j ACCEPT
$IPTABLES -A INPUT -p tcp -m tcp --dport #### -j ACCEPT

# Mark status of firewall for the LCD program
touch /var/tmp/firewall_is_on

exit 0;
# that's all!


```Thank you!

---

### Post by mytinytown on 2010-12-02
I don't know if this will help either though, here is my Network Interface:

```

# The loopback network interface
    auto lo br0
    iface lo inet loopback


# Switch (LAN)
    auto eth0
iface eth0 inet manual


# WAN
    auto eth1
    iface eth1 inet dhcp


#Bridge the above
    iface br0 inet static
    bridge_ports eth0 eth1
    address 192.168.2.6
    netmask 255.255.255.0
    broadcast 192.168.2.255
    gateway 192.168.2.1

```

---

### Post by SeijiSensei on 2010-12-02
What does "cat /proc/sys/net/ipv4/ip_forward" return?  If it's zero, then forwarding between interfaces is disabled in the kernel.  Edit (as root) /etc/sysctl.conf and enable "net.ipv4.ip_forward=1".  You'll need to reboot to make this take effect.  For a quick fix without rebooting to test whether this is the problem run 

```
sudo echo '1' > /proc/sys/net/ipv4/ip_forward
```

and see if you have Internet access.

If this isn't the problem, then we'll need to study the iptables rules, but I'm hoping to avoid that! :D

---

### Post by mytinytown on 2010-12-06
/etc/sysctl.conf shows:

```

#
# /etc/sysctl.conf - Configuration file for setting system variables
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com
#net/ipv4/icmp_echo_ignore_broadcasts=1

# the following stops low-level messages on console
kernel.printk = 4 4 1 7

# enable /proc/$pid/maps privacy so that memory relocations are not
# visible to other users.
kernel.maps_protect = 1

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next line to enable Spoof protection (reverse-path filter)
#net.ipv4.conf.default.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1
net.ipv4.conf.default.forwarding=1
net.ipv4.conf.all.forwarding=1

# Uncomment the next line to enable packet forwarding for IPv6
net.ipv6.conf.all.forwarding=1

```cat /proc/sys/net/ipv4/ip_forward
Displays:
1

With the firewall off I have full access. With the Firewall On I get connection through the ports that are open, but I do not get internet from the box and I get nothing from eth0 either.

---

### Post by SeijiSensei on 2010-12-06
Just a guess, but I think this rule may be a problem:

```

# Internet -- hide machines talking to Internet behind this firewall
$IPTABLES -A FORWARD -j ACCEPT -i $IF_LAN -o $IF_WAN

```

Since it comes before the masquerading rule, it may interfere with rewriting the source address.  Try replacing it with:

```
$IPTABLES -A FORWARD -j ACCEPT -s 192.168.1.0/24 -d 192.168.1.0/24
```

substituting your actual internal LAN network blocks for 192.168.1.0/24.  Then only internal traffic will be forwarded and no address rewriting will be done for them.

If you run "sudo iptables -t nat -Lnv" do you see packets meeting the MASQUERADE rule?

---

### Post by mytinytown on 2010-12-06
I ran:
root@SG20:~# sudo iptables -t nat -Lnv
iptables: No chain/target/match by that name

This is what I get with the firewall on or off.

I changed the line:
# $IPTABLES -A FORWARD -j ACCEPT -i $IF_LAN -o $IF_WAN
$IPTABLES -A FORWARD -j ACCEPT -s 192.168.2.0/24 -d 192.168.2.0/24
I made the IP 192.168.2.0 instead, that is my network.

ran sudo iptables -t nat -Lnv
and got the same "iptables: No chain/target/match by that name" thing.

Also still no outgoing internet. I do have LAN though. Just no outgoing internet from the lan or the server.

You said "Since it comes before the masquerading rule, it may interfere with rewriting the source address." did you want me to move the rule?

---

### Post by mytinytown on 2010-12-06
I also wanted to add, I have Apache2 set up and I can access the server using the URL addressed to it, but I can not access any websites from the server. Like with the firewall on I can not even do sudo apt-get update.

This is the only thing that does not work.

---

### Post by SeijiSensei on 2010-12-06
Sorry!  I forgot iptables refuses to let you concatenate the "L" option with other things.  "iptables -t nat -L -nv" works correctly.  You'll see the rules in the PREROUTING and POSTROUTING chains.

Can you post the results of that command, and of "iptables -L -nv" as well. That will display the main INPUT, FORWARD, and OUTPUT chains.  Put the results inside [noparse]```

```[/noparse] tags for easy reading.

PS:  You don't need to use sudo if you're already root.  Ubuntu frowns on running as the root user and is designed to have you use sudo as an ordinary user to obtain root privileges.

---

### Post by mytinytown on 2010-12-06
OK this is what I got:
```

root@SG20:~# iptables -t nat -L -nv
Chain PREROUTING (policy ACCEPT 133K packets, 20M bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain POSTROUTING (policy ACCEPT 121K packets, 21M bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 MASQUERADE  0    --  *      eth1    0.0.0.0/0            0.0.0.0/0
    0     0 MASQUERADE  0    --  *      eth1    0.0.0.0/0            0.0.0.0/0
    0     0 MASQUERADE  0    --  *      eth0    0.0.0.0/0            0.0.0.0/0
    0     0 MASQUERADE  0    --  *      eth1    0.0.0.0/0            0.0.0.0/0
    0     0 MASQUERADE  0    --  *      eth1    0.0.0.0/0            0.0.0.0/0
    0     0 MASQUERADE  0    --  *      eth1    0.0.0.0/0            0.0.0.0/0
    0     0 MASQUERADE  0    --  *      eth1    0.0.0.0/0            0.0.0.0/0
    0     0 MASQUERADE  0    --  *      eth1    0.0.0.0/0            0.0.0.0/0
    0     0 MASQUERADE  0    --  *      eth1    0.0.0.0/0            0.0.0.0/0
    0     0 MASQUERADE  0    --  *      eth1    0.0.0.0/0            0.0.0.0/0
    0     0 MASQUERADE  0    --  *      eth1    0.0.0.0/0            0.0.0.0/0

Chain OUTPUT (policy ACCEPT 17287 packets, 2556K bytes)
 pkts bytes target     prot opt in     out     source               destination


```

Thank you for all your help so far, I am heading home for the evening be back in 16 hours.

---

### Post by mytinytown on 2010-12-07
Is there a way to tell which connection is eth0 and eth1? Is it possible I have eth1 as WAN when eth0 is WAN? If so, how can I tell?

---

### Post by SeijiSensei on 2010-12-07
Unplug one of the wires and see what addresses you have left.

That said, now that I see that you're using bridging, I'm afraid I can't help you more.  I never use bridging and prefer simply to route packets between interfaces.  What happens if you remove the bridge definition in /etc/network/interfaces?

---

### Post by mytinytown on 2010-12-07
I noticed a few other details.

Like to access the server using Webmin I must have the Webmin port open in the firewall to access it from the LAN side.

So if I:
```

# (Uncomment to) Allow unrestricted login access via Webmin from the Internet. 
$IPTABLES -A INPUT -i $EXTIF  -p tcp -m tcp --dport 10000 -j ACCEPT

```I can access Webmin, but if I:
```

# (Uncomment to) Allow unrestricted login access via Webmin from the Internet. 
# $IPTABLES -A INPUT -i $EXTIF  -p tcp -m tcp --dport 10000 -j ACCEPT

```I loose access to Webmin from the LAN side. I thought that I should not need that port open to access Webmin on this side of the firewall?

If I remove this line

```

# Internet -- hide machines talking to Internet behind this firewall
$IPTABLES -A FORWARD -j ACCEPT -i $INTIF -o $EXTIF

```Everything works like I don't have the firewall on, like it should, but if I comment out:
```

# (Uncomment to) Allow unrestricted access to my web server from the Internet.
# $IPTABLES -A INPUT -i $EXTIF  -p tcp -m tcp --dport 80 -j ACCEPT

```I can still access the apache2 website and I don't think I should be able to.

I am so confused by IPTABLES. I did some online research again, and still can not get anywhere.

---

### Post by mytinytown on 2010-12-08
Wow,

I am sorry yesterday I did not see y our reply when I posted.

So you claim I do not need to bridge?

Well I will remove the bridge and see what the damage is.

I will get back with you once this is done.

---

### Post by mytinytown on 2010-12-08
OK

Here is my network/interface now:
```

# The loopback network interface
    auto lo
    iface lo inet loopback


# Switch (LAN)
    auto eth0
    iface eth0 inet static
    address 192.168.2.6
    netmask 255.255.255.0
    broadcast 192.168.2.255
    gateway 192.168.2.1


# WAN
    auto eth1
    iface eth1 inet dhcp

```Now I did the above and I have no bridge.
So now, Samba does not work.
My LAN connection does not work.
Accessing Webmin or SSH with my IP address does not work.
The only access I have is using the URL I have.

```


root@SG20:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:10:C6:18:6D:AE
          inet addr:192.168.2.6  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::210:c6ff:fe18:6dae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:77331 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42923 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:16087970 (15.3 MB)  TX bytes:18301405 (17.4 MB)
          Interrupt:10 Base address:0xe000

eth1      Link encap:Ethernet  HWaddr 00:10:C6:17:31:E5
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1:avah Link encap:Ethernet  HWaddr 00:10:C6:17:31:E5
          inet addr:169.254.7.31  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3075 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3075 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2044609 (1.9 MB)  TX bytes:2044609 (1.9 MB)

```I unplugged the cable from my WAN and plugged it to my LAN and reboot. Now everything works good. But this makes me feel a little less safe.

Not sure what the "eth1:avah" is all about. My router IP is using 192.168.2.1.

---

### Post by mytinytown on 2010-12-09
```

root@SG20:~# cat /proc/sys/net/ipv4/ip_forward
1

```
```

root@SG20:~# iptables -t nat -L -nv
Chain PREROUTING (policy ACCEPT 50441 packets, 15M bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain POSTROUTING (policy ACCEPT 1099 packets, 173K bytes)
 pkts bytes target     prot opt in     out     source               destination
  174 36788 MASQUERADE  0    --  *      eth1    0.0.0.0/0            0.0.0.0/0

Chain OUTPUT (policy ACCEPT 1273 packets, 210K bytes)
 pkts bytes target     prot opt in     out     source               destination

```

There is some info you needed a few posts ago, and since I changed things I'd thought I'd re-post it.

---

