---
title: "shell scripts not executing properly"
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by sh@dowl1ght on 2009-02-02
just recently, i have found that ubuntu will not execute scripts properly anymore.

below is a small script i wrote for a mobile wifi access point:

echo "    Mobile WiFi Accees Point"
echo "by Shadowlight, 2009, Madwifi Version"
echo "" && echo "Enter desired Broadcast ESSID:"
read NETNAME
echo "Enter Internet Interface:"
read INETIFACE
ifconfig ath0 down
wlanconfig ath0 destroy
wlanconfig ath0 create wlandev wifi0 wlanmode ap
iwconfig ath0 mode master essid $NETNAME
ifconfig ath0 10.0.0.1 netmask 255.255.255.0
route add -net 10.0.0.0 netmask 255.255.255.0 gw 10.0.0.1
killall dnsmasq && dnsmasq

iptables --flush
iptables --table nat --flush
iptables --delete-chain
iptables --table nat --delete-chain
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING --out-interface $INETIFACE -j MASQUERADE
iptables --append FORWARD --in-interface ath0 -j ACCEPT
iptables -t nat -A PREROUTING -p udp --dport 53 -j DNAT --to 192.168.1.1
echo "Done."

after running this i do iwconfig, and ath0 does not have an ESSID.

however, if i run the *iwconfig ath0 mode master essid $NETNAME* line manualy, (obviously substituting the veriable with whatever essid) ie type it straight into the shell, then it works.

this is realy doing my head in, as i have to just enter all those commands into the shell everytime i want to run it.

i have not heard of anything like this before. hope someone can help.

thanks.

---

### Post by nixscripter on 2009-02-03
Try running the script with: ```
bash -x scriptfile
``` so you can see what it's doing. There might be some variables not substituting or whitespace getting added where it shouldn't be.

---

