---
title: "Ekiga NAT type problem"
date: 2006-07-12
forum: Networking &amp; Wireless
---

### Post by groovomata on 2006-07-12
Hello All! 
I'd like to use Ekiga to video chat on my Kubuntu 6.06 machine. I do not have any problems connecting to the net. The video part doesn't seem to be a problem as my webcam seems to work fine. However I'm having a problem with the network part. My router is a "Bell Canada Home Networking" router. Ekiga specifies to forward:
UDP 5000 - 5100 
TCP 5000 - 5100
TCP 1720
TCP 30000 - 30010  all to the machine ip - which I've done. 
I've also got guarddog and have enabled the various relevant chat protocols MSN messenger, Netmeeting, yahoo messenger, jabber, irc etc. 

Additionally, I've put the following iptable script found on the Ekiga website in guarddog and for good measure forwarded the above ports in guarddog as well. 

#!/bin/sh
echo "Setting up IPtables rules"
IPTABLES=/sbin/iptables # where iptables binary lies
# Setting up Forwarding 
echo 1 > /proc/sys/net/ipv4/ip_forward
# Setting up Dynamic IP for diald/masquerading
echo 1 > /proc/sys/net/ipv4/ip_dynaddr
# Increase the binding time
echo 3600 > /proc/sys/net/ipv4/netfilter/ip_conntrack_udp_timeout
# Setting up IP spoofing protection 
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ] 
then 
        for f in /proc/sys/net/ipv4/conf/*/rp_filter 
        do 
                echo 1 > $f 
        done 
fi
# Devices
LOCAL_DEVICE="lo"			# device for localhost
EXTERNAL_DEVICE="ppp0"		# device for Internet
INTERNAL_DEVICE="eth1"		# device for Intranet    
HALFTRUST_NETS="192.168.1.0/8"
KEEPSTATE="-m state --state ESTABLISHED,RELATED"
# Flush all Rules
$IPTABLES 		-F 
$IPTABLES 		-X
$IPTABLES -t nat 	-F
$IPTABLES -t nat 	-X
$IPTABLES -t mangle	-F
$IPTABLES -t mangle	-X
# Deny all by default 
$IPTABLES -P INPUT	DROP 
$IPTABLES -P OUTPUT	DROP 
$IPTABLES -P FORWARD	ACCEPT
$IPTABLES -N ALLOW_PORTS
$IPTABLES -F ALLOW_PORTS
###### TCP and UDP ports ######
TCP_PORTS=""
for PORT in $TCP_PORTS; do
	$IPTABLES -A ALLOW_PORTS -m state --state NEW -p tcp --dport $PORT -j ACCEPT
done
UDP_PORTS=""
for PORT in $UDP_PORTS; do
	$IPTABLES -A ALLOW_PORTS -m state --state NEW -p udp --dport $PORT -j ACCEPT
done
###### MASQUERADE ######
$IPTABLES -t nat -A POSTROUTING -d ! 192.168.1.0/24 -o $EXTERNAL_DEVICE -j MASQUERADE
    	    
###### LOCALHOST ######
$IPTABLES -A INPUT -p ALL -i $LOCAL_DEVICE -j ACCEPT
$IPTABLES -A OUTPUT -p ALL -o $LOCAL_DEVICE -j ACCEPT
$IPTABLES -A FORWARD -p ALL -i $LOCAL_DEVICE -j ACCEPT
###### FROM INTRANET ######
$IPTABLES -A INPUT -p ALL -i $INTERNAL_DEVICE -j ACCEPT
$IPTABLES -A OUTPUT -p ALL -o $INTERNAL_DEVICE -j ACCEPT
###### ICMP ######
$IPTABLES -A INPUT -p ICMP -i $EXTERNAL_DEVICE -j ACCEPT
$IPTABLES -A OUTPUT -p ICMP -o $EXTERNAL_DEVICE -j ACCEPT
$IPTABLES -A INPUT -p ICMP -s $HALFTRUST_NETS -j ACCEPT
$IPTABLES -A OUTPUT -p ICMP -d $HALFTRUST_NETS -j ACCEPT
###### ALLOWED PORTS ######
$IPTABLES -A INPUT -i $EXTERNAL_DEVICE -s "0.0.0.0/0" -j ALLOW_PORTS
###### ESTABLISHED MODE ######
$IPTABLES -A OUTPUT -o $EXTERNAL_DEVICE	-p TCP $KEEPSTATE -j ACCEPT
$IPTABLES -A INPUT -i $EXTERNAL_DEVICE -p TCP $KEEPSTATE -j ACCEPT
$IPTABLES -A OUTPUT -o $EXTERNAL_DEVICE	-p UDP $KEEPSTATE -j ACCEPT
$IPTABLES -A INPUT -i $EXTERNAL_DEVICE -p UDP $KEEPSTATE -j ACCEPT
###### OUTPUT ######
$IPTABLES -A OUTPUT -o $EXTERNAL_DEVICE	-p ALL -j ACCEPT

Unfortunately I'm still not having any success. Everytime the Ekiga NAT type detects 'Symmetric NAT' and advises me to forward the relevant ports to my machine so that I get 'Cone NAT'. I think the problem may be with my router but I'm not sure. 
Are there any networking gurus out there who can give me a hand?
Thanks,
Erik.

---

### Post by groovomata on 2006-07-30
Okay, I was fiddling with this again. I removed the iptable scripts, I completely disabled my Guarddog firewall, I enable DMZ with my computer's IP address in my router therefore exposing it completely to the internet. Then I ran the Ekiga NAT type test and it still read that I have a symmetric NAT. I really don't know what to do because with no firewalls and with ipforward to my computer no matter what I do I still end up having a Symmetric NAT. 
Does anyone have an ideas for me? Every internet related feature works: I can download torrents, use gnutella, use emule, chat, email, browse, however I still cannot video chat with msn or yahoo. Unfortunately this is sort of a deal breaker for me as I really do need to have a working video chat application. 
Thanks, 
Erik.

---

### Post by leodp on 2006-09-25
Have you tried gyachi or gyache (yahoo), or amsn (MSN)?

Leo

---

### Post by YannickDefais on 2006-10-15
Hello,

You can try installing Ekiga 2.0.3. This *may* solve your problem.

[http://ekiga.org/index.php?rub=5](http://ekiga.org/index.php?rub=5)

Regards,
Yannick

---

