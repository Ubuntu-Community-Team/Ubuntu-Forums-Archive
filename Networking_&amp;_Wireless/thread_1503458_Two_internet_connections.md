---
title: "Two internet connections"
date: 2010-06-06
forum: Networking &amp; Wireless
---

### Post by bizkyt on 2010-06-06
Hello,

I'm trying to have two internet connections in my ubuntu 10.04. I can successful have two connection plugged in at the same time: one from wireless, and other from 3G pen.
Now what I want is anything like this: in chrome choose the wireless connection, and in firefox choose the 3G connection, and navigate at the same time with the two connections...
Anyone knows how to do this? 

Regards

---

### Post by Iowan on 2010-06-06
I remember another thread wanting to use specific interfaces with specific applications. I'll try to find it - haven't had much luck so far.

---

### Post by bizkyt on 2010-06-06
I tried both here and google, with no luck :(

---

### Post by bizkyt on 2010-06-07
Anyone?

---

### Post by bizkyt on 2010-06-07
I was searching and find this tutorial: [http://www.vivaolinux.com.br/artigo/Firewall-Linux-Roteamento-avancado-usando-iproute2-e-iptables-(load-balance)]("http://www.vivaolinux.com.br/artigo/Firewall-Linux-Roteamento-avancado-usando-iproute2-e-iptables-(load-balance)")
 
I change it to this:

"IF_LAN='eth0'
IF_LINK1='wlan0'
IF_LINK2='ppp0'
GW_LINK1='192.168.1.1'
GW_LINK2='10.64.64.64'
iptables -t nat -A POSTROUTING -o $IF_LINK1 -j MASQUERADE
iptables -t nat -A POSTROUTING -o $IF_LINK2 -j MASQUERADE
iptables -t mangle -A PREROUTING -i $IF_LAN -p tcp --dport 80 -j MARK --set-mark 2
iptables -t mangle -A PREROUTING -i $IF_LAN -p tcp --dport 89 -j MARK --set-mark 3
iptables -t mangle -A OUTPUT -p tcp --dport 80 -j MARK --set-mark 2
iptables -t mangle -A OUTPUT -p tcp --dport 89 -j MARK --set-mark 3
ip rule add fwmark 2 table 20 prio 20
ip rule add fwmark 3 table 21 prio 20
ip route add default via $GW_LINK1 dev $IF_LINK1 table 20
ip route add default via $GW_LINK2 dev $IF_LINK2 table 21
ip route flush cache"

Move it to  /etc/init.d/ and run in terminal:
sudo update-rc.d netscript defaults
sudo chmod +x netscript

I reboot ubuntu, turn on both wireless and 3G connections, and connect the two by ubuntu network manager. Now in firefox (I don't know even if it's possible to do like this?), but configured a proxy with squid, and put http_port to 89 and grant permission in router to my network ip to port 89. Then put it in firefox proxy definitions: 127.0.0.1:89.
And it didn't work, it stayed the wireless IP in chrome and firefox.

Someone can say me how to configure firefox to acess port 89, or in what I have go wrong?


Best regards.

---

### Post by bizkyt on 2010-06-08
Bump

---

### Post by Eguiguren on 2010-09-16
> **bizkyt said:**
> I was searching and find this tutorial: [http://www.vivaolinux.com.br/artigo/Firewall-Linux-Roteamento-avancado-usando-iproute2-e-iptables-(load-balance)]("http://www.vivaolinux.com.br/artigo/Firewall-Linux-Roteamento-avancado-usando-iproute2-e-iptables-%28load-balance%29")
 
I change it to this:

"IF_LAN='eth0'
IF_LINK1='wlan0'
IF_LINK2='ppp0'
GW_LINK1='192.168.1.1'
GW_LINK2='10.64.64.64'
iptables -t nat -A POSTROUTING -o $IF_LINK1 -j MASQUERADE
iptables -t nat -A POSTROUTING -o $IF_LINK2 -j MASQUERADE
iptables -t mangle -A PREROUTING -i $IF_LAN -p tcp --dport 80 -j MARK --set-mark 2
iptables -t mangle -A PREROUTING -i $IF_LAN -p tcp --dport 89 -j MARK --set-mark 3
iptables -t mangle -A OUTPUT -p tcp --dport 80 -j MARK --set-mark 2
iptables -t mangle -A OUTPUT -p tcp --dport 89 -j MARK --set-mark 3
ip rule add fwmark 2 table 20 prio 20
ip rule add fwmark 3 table 21 prio 20
ip route add default via $GW_LINK1 dev $IF_LINK1 table 20
ip route add default via $GW_LINK2 dev $IF_LINK2 table 21
ip route flush cache"

Move it to  /etc/init.d/ and run in terminal:
sudo update-rc.d netscript defaults
sudo chmod +x netscript
I reboot ubuntu, turn on both wireless and 3G  connections, and connect the two by ubuntu network manager. Now in  firefox (I don't know even if it's possible to do like this?), but  configured a proxy with squid, and put http_port to 89 and grant  permission in router to my network ip to port 89. Then put it in firefox  proxy definitions: 127.0.0.1:89.
And it didn't work, it stayed the wireless IP in chrome and firefox.

Someone can say me how to configure firefox to acess port 89, or in what I have go wrong?


Best regards.

I guess it desn't work as you are marking  packages incoming through  the eth0 . When you connect throught  127.0.0.1 packages are incoming through the lo interface so they doesn't  match the iptables rule and are not marked.

Maybe you should try  to mark packages depending on the user or the PID of firefox/opera (it  would be easier to mark squid's as it's more difficult to need to be  restarted). I can't tell right now which options do you need, but it's  implemented in the latest versions of iptables (maybe something like  this as squid's owner shouldn't be your regular user ):
$IPTABLES -t mangle -A POSTROUTING -o $DEV -m owner --uid-owner $a -j MARK --set-mark 23 

Take a look here: 
[http://forums.gentoo.org/viewtopic.php?t=65826](http://forums.gentoo.org/viewtopic.php?t=65826)

Good luck

---

