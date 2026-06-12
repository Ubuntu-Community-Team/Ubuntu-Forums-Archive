---
title: "Did I do something wrong or is it my ISP stupid?"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by Arukas on 2009-01-19
Did I do something wrong or is it my ISP stupid?
Yesterday, I talked to my ISP and asked them about my service. The conclusion was, I have one line coming in, and its up to me to split it between my computers.

My gateway has two NIC cards in it, one the internet and the other my home network. After I set everything up, I tried to use the internet on one of my home computers. And I got the internet, but I got one of those "registration pages" But the gateway computer's web browswer works fine.

Here's my concern, my ISP should only see my gateway/proxy computer. And the gateway computer should do all the talking to the ISP. And since the gateway computer can use the internet okay, Why is it acting different with the computer on the home network?

Both computers have Xubuntu 8.04 on them.

---

### Post by Iowan on 2009-01-19
Apparently you have connection sharing working, but... [here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is a help page that *might* shed some light.

---

### Post by Arukas on 2009-01-19
I didn't shed enough light on it, sounds more confusing then what I have been reading.  

Here's my proxy.sh I am using.  

[PHP]
#!/bin/sh
INTIF="eth0"
EXTIF="eth1"
EXTIP="`/sbin/ifconfig eth1 | grep 'inet addr' | awk '{print $2}' | sed -e 's/.*://'`"
/sbin/depmod -a
/sbin/modprobe ip_tables
/sbin/modprobe ip_conntrack
/sbin/modprobe ip_conntrack_ftp
/sbin/modprobe ip_conntrack_irc
/sbin/modprobe iptable_nat
/sbin/modprobe ip_nat_ftp
echo "1" > /proc/sys/net/ipv4/ip_forward
echo "1" > /proc/sys/net/ipv4/ip_dynaddr
iptables -P INPUT ACCEPT
iptables -F INPUT 
iptables -P OUTPUT ACCEPT
iptables -F OUTPUT 
iptables -P FORWARD DROP
iptables -F FORWARD 
iptables -t nat -F
iptables -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT
iptables -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE
[/PHP]

I am using a cable modem, and I have a dynamic address.  

I changed part of the script, because it didn't was giving me errors.

The third line was oringally 
[PHP]
EXTIP="`/sbin/ifconfig ppp0 | grep 'inet addr' | awk '{print $2}' | sed -e 's/.*://'`"
[/PHP]

I changed ppp0 to eth1 because from what I understand ppp0 is for a dialup connect, and I am thinking I made an incorrect change.  


And just so you know when I run the script with the ppp0 instead of eth1, I get this

[PHP]
-e 

SETTING UP IPTABLES PROXY...
ppp0: error fetching interface information: Device not found
Loading required stateful/NAT kernel modules...
    Enabling IP forwarding...
    External interface: eth1
       External interface IP address is: 
    Loading proxy server rules...
-e        Proxy server rule loading complete



[/PHP]

---

