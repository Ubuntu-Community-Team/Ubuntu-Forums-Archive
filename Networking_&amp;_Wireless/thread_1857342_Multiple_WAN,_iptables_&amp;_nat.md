---
title: "Multiple WAN, iptables &amp; nat"
date: 2011-10-10
forum: Networking &amp; Wireless
---

### Post by 11notes on 2011-10-10
Hi there, I've got a problem, currently I have a self built "Ubuntu Firewall" using iptables with only one WAN interface, works great, even with multiple subnets and so on. Now I'm planing to add more WAN interfaces due to the fact that I need multiple public ip addresses. The problem is I don't know where to start to modify my current setup, as you might have guessed by now I'm not an expert. I've allready googled and found a few examples which are smiliar to mine but I've adjust mine to theirs it won't work at all.

Here is my current setup:

**iptables**```
#!/bin/sh
IPT="/sbin/iptables"
# I N T E R F A C E S
DNS="10.0.0.3"

LO="lo"

WAN="eth0"
        WAN_IP="`ifconfig $WAN | grep \"inet addr\" | cut -f 2 -d \":\" | cut -f 1 -d \" \"`"
        
LAN="eth1"
        LAN_CIDR="10.0.0.1/24"
        LAN_IP="10.0.0.1"
            LAN_EXCHANGE="`nslookup mail.xxx.xx $DNS | tail -2 | awk -F ": " '{print $2}' `"

DMZ="eth2"
        DMZ_CIDR="11.0.0.1/24"
        DMZ_IP="11.0.0.1"
            DMZ_WWW="`nslookup www.xxx.xx $DNS | tail -2 | awk -F ": " '{print $2}' `"


# ---------------------------------------------------------------
# I N I T :: I P T A B L E S
# ---------------------------------------------------------------
modprobe ip_tables
modprobe ip_conntrack
$IPT -F
$IPT -Z
$IPT -X
echo 1 > /proc/sys/net/ipv4/ip_forward
for f in /proc/sys/net/ipv4/conf/*/rp_filter; do
    echo 1 > $f
done
$IPT -P INPUT DROP
$IPT -P OUTPUT ACCEPT
$IPT -P FORWARD DROP

# ---------------------------------------------------------------
# C H A I N S :: C R E A T E
# ---------------------------------------------------------------
    # I N T E R F A C E S
    $IPT -N LO
    $IPT -N LAN
    $IPT -N WAN
    $IPT -N DMZ

    # Z O N E S
    $IPT -N WAN2DMZ
    $IPT -N DMZ2WAN
    $IPT -N WAN2LAN
    $IPT -N LAN2WAN
    $IPT -N LAN2DMZ
    $IPT -N DMZ2LAN

    # L O G S
    $IPT -N LOGSPAM
    $IPT -N LOGACCEPT
    $IPT -N LOGREJECT


# ---------------------------------------------------------------
# C H A I N S :: S E T U P
# ---------------------------------------------------------------
    # I N P U T & O U T P U T
    $IPT -t filter -A OUTPUT -p ALL -s $LAN_CIDR -j ACCEPT
    $IPT -t filter -A OUTPUT -p ALL -s $DMZ_CIDR -j ACCEPT
    $IPT -A INPUT -i $LO -j ACCEPT
    $IPT -A OUTPUT -o $LO -j ACCEPT

    # Z O N E S
    $IPT -A LO -j ACCEPT
    $IPT -t filter -A LAN -j ACCEPT
    $IPT -t filter -A WAN -m state --state ESTABLISHED,RELATED -j ACCEPT
    $IPT -t filter -A DMZ -m state --state ESTABLISHED,RELATED -j ACCEPT
    $IPT -t filter -A WAN2DMZ -m state --state ESTABLISHED,RELATED -j ACCEPT
    $IPT -t filter -A DMZ2WAN -j ACCEPT
    $IPT -t filter -A WAN2LAN -m state --state ESTABLISHED,RELATED -j ACCEPT
    $IPT -t filter -A LAN2WAN -j ACCEPT
    $IPT -t filter -A LAN2DMZ -j ACCEPT
    $IPT -t filter -A DMZ2LAN -m state --state ESTABLISHED,RELATED -j ACCEPT

    # L O G S
        # B R U T E F O R C E
        $IPT -A LOGSPAM -j LOG --log-prefix "FWLOG SPAM:"
        $IPT -A LOGSPAM -j REJECT

        # A C C E P T
        $IPT -A LOGACCEPT -j LOG --log-prefix "FWLOG ACCEPT:"
        $IPT -A LOGACCEPT -j ACCEPT

        # D E N Y
        $IPT -A LOGREJECT -j LOG --log-prefix "FWLOG REJECT:"
        $IPT -A LOGREJECT -j REJECT

# ---------------------------------------------------------------
# R O U T I N G
# ---------------------------------------------------------------
    # D M Z
        # W W W
            #HTTP :: WAN
            $IPT -t nat -A PREROUTING -d $WAN_IP -p tcp --dport 80 -j DNAT --to-destination $DMZ_WWW:80
            $IPT -A WAN2DMZ -m state --state NEW -d $DMZ_WWW -p tcp --dport 80 -j LOGREJECT

            $IPT -t nat -A PREROUTING -d $WAN_IP -p tcp --dport 21 -j DNAT --to-destination $DMZ_WWW:21
            $IPT -A WAN2DMZ -m state --state NEW -d $DMZ_WWW -p tcp --dport 21 -j LOGACCEPT

    # L A N
        # E X C H A N G E
            #SMTP & HTTPS :: WAN
            $IPT -t nat -A PREROUTING -d $WAN_IP -p tcp -m multiport --dports 25,443 -j DNAT --to-destination $LAN_EXCHANGE
            $IPT -A WAN2LAN -m state --state NEW -d $LAN_EXCHANGE -p tcp -m multiport --dports 25,443 -j LOGACCEPT
            
    # W A N
        # F I R E W A L L
            #SSH :: WAN
            $IPT -A WAN -m recent --name SPAM --set -p tcp -m multiport --dports 22 -d $WAN_IP
            $IPT -A WAN -m recent --name SPAM --rcheck --seconds 600 --hitcount 4 -p tcp -m multiport --dports 22 -d $WAN_IP -j LOGSPAM
            $IPT -A WAN -m state --state NEW -p tcp -m multiport --dports 22 -d $WAN_IP -j LOGACCEPT

# ---------------------------------------------------------------
# C H A I N S :: A C T I V A T E
# ---------------------------------------------------------------
$IPT -t nat -A POSTROUTING ! -s $WAN_IP -o $WAN -j SNAT --to-source $WAN_IP
$IPT -A INPUT -i $LAN -j LAN
$IPT -A INPUT -i $WAN -j WAN
$IPT -A INPUT -i $DMZ -j DMZ
$IPT -A INPUT -i $LO -j LO
$IPT -A FORWARD -i $WAN -o $DMZ -j WAN2DMZ
$IPT -A FORWARD -i $DMZ -o $WAN -j DMZ2WAN
$IPT -A FORWARD -i $WAN -o $LAN -j WAN2LAN
$IPT -A FORWARD -i $LAN -o $WAN -j LAN2WAN
$IPT -A FORWARD -i $LAN -o $DMZ -j LAN2DMZ
$IPT -A FORWARD -i $DMZ -o $LAN -j DMZ2LAN
```**network/interfaces**```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
        address 10.0.0.1
        netmask 255.255.255.0
        network 10.0.0.0
        broadcast 10.0.0.255

auto eth2
iface eth2 inet static
        address 11.0.0.1
        netmask 255.255.255.0
        network 11.0.0.0
        broadcast 11.0.0.255
```**route result**```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
84.241.96.0     *               255.255.255.0   U     0      0        0 eth0
10.0.0.0        *               255.255.255.0   U     0      0        0 eth1
11.0.0.0        *               255.255.255.0   U     0      0        0 eth2
default         fix-cable-custo 0.0.0.0         UG    100    0        0 eth0
```When I add eth3 (2nd WAN interface) I get an IP from my ISP, I can ping and lookup DNS from the Ubuntu Server itself, **but** any client in the subnets (eth1 -> LAN, eth2 -> DMZ) lose the internet connection. I think its a problem with the routing table? Might that be the case? I also cant connect to the server from the www using ssh.

---

### Post by poolet on 2011-10-10
check your routing table again... it's seems that your problem comes from your rooting table... If you don't find any strange with rooting table, clean/flush your DNS cache...  do not reject any probability, can blame anything.... beleive me I have saw strange issues with iptables and nat!!! 



sudo aptitude install nscd


```

sudo /etc/init.d/nscd restart

```

---

### Post by SeijiSensei on 2011-10-10
You can create multiple aliases for an interface by using devices called eth:N, where N is some integer.  So if you already have eth0 assigned to one public address, use ifconfig to create eth0:0 and assign it another address.  You'll probably find it easiest just to add the ifconfig commands to /etc/rc.local, or follow [this approach](http://www.cyberciti.biz/tips/ubuntu-linux-creating-ethernet-alias-for-eth0-network-device.html).

---

### Post by 11notes on 2011-10-11
@SeijiSensei
That won't work, my ISP assigns static IPs to the MAC-Address of the eth device, so it needs to be a real eth device I guess? I use this Ubuntu Box inside ESXi so I have one Virtual Switch with 2 Virtual eth devices which are connected through one single real nic to the isp.

@poolet
If I add the second WAN with the same gateway as the first one everything works fine until I add my second WAN to iptable rules (like accepting ssh from wan1 & wan2) then everything breaks again...

---

### Post by Drenriza on 2011-10-11
I have never understood why you want an ubuntu server to administrate your network instead of letting the routers / switch administrate network traffic, vlans and so on and so forth. Servers are in my idea of network only used for extensive vpn logins. Such as Active Directory credentials.

---

### Post by 11notes on 2011-10-11
@Drenriza
Not a very useful answer! I do this because I don't want to use a finished product and have everything handed to me, I want to learn, and that's why I try to build my own multi wan, multi subnet Ubuntu Router, there's nothing wrong with that.


Maybee I should point out that all the public IP's I got are in the same subnet on the same gateway. All I need to know is how to accept those IPs with my IPtables so that no matter what public IP you use, you always end up in the same IPtables rule.

---

### Post by Drenriza on 2011-10-11
> **11notes said:**
> @Drenriza
Not a very useful answer! I do this because I don't want to use a finished product and have everything handed to me, I want to learn

Settle down pls. If you think that you can only learn about networking, is by building a "ubuntu router" then i am speechless. And i wonder how a company like Cisco and HP,s network department can survive. To get traffic to a router (from your ISP or what not) through your internal switch and then send the traffic to a "ubuntu router" to then decide what should happen with the traffic. I and bet it then goes back to your switch again. Well that sure is top dollar.

Then sure i am sorry and i bow for the networking master at hand. I can now see that the time i have spent on Cisco equipment setting up complicated networks has been waste of time. Because everything is handed to me.

Damn you BGP, TCP/IP, VLANS, VPN TUNNELS WITH HASH VALUES! and all you others.
Damnnn you alllll

---

### Post by 11notes on 2011-10-11
@Drenriza
Bad hairday or whats your problem? You can use your mighty cisco devices and let me configure my home ubuntu router, when you can't help me out, go f*ck yourself and spam somewhere else I don't need your bullsh*t, I need help with **my** problem not *your* midlifecrisis.

---

### Post by poolet on 2011-10-11
something is going wrong with your rooting table!!! check the following link maybe helps you to understand better how they works... At the end if that's isn't helps you I would prefer to re-build your configuration from the beginning... And if I said from the beginning from the beginning ;).. Just shut it down and re-build the whole thing am 100% sure that you forget something and you will find it!! Networks are strange and as the period of time goes their being more and more strange... Last month I was working some delay that we had on system with VOIP the true is that I was never saw a similar problem since we do not have only a overload/delay but all ip telephone was not recognize the details that came from server..... after 2 hours of working the problem was solved with flushing the DNS... and re-configure the metric and the VLAN's as I said you **must **be prepare for the most unexpected problem!!! So do not waste your time looking for a problem, just re-build the whole configure and your problem will be solved!!!  Hope that helps you!!!

[http://www.dd-wrt.com/wiki/index.php/Iptables_command](http://www.dd-wrt.com/wiki/index.php/Iptables_command)

---

### Post by 11notes on 2011-10-11
@poolet
I rebuilt it two times and rebootet everything at least 20 times :p, I got it to the point that the internet is working on all subnets in and out, the only problem left is that I can only access the router using the main eth0 public ip address, again that must be a routing problem, but I don't know where to start, every guide is for outgoing dual wan connections and doenst mention a thing about incoming traffic from dual wan. All I want is that no matter which external IP you use, you allways endup in the same iptable rules and get forwarded to the internal server (www, email, ftp, ssh etc). I've taken a look at this [Guide]("http://serverfault.com/questions/316402/ubuntu-10-10-ip-configuration-using-2-ip-addresses") and try this later, for now I locked my self out of my server due to a ip rule flush 8-[

here's the result of my routing table```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
84.241.96.0     0.0.0.0         255.255.255.255 UH    0      0        0 eth1
84.241.96.0     0.0.0.0         255.255.255.0   U     0      0        0 eth3
84.241.96.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 eth1
11.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 eth2
0.0.0.0         84.241.96.1     0.0.0.0         UG    0      0        0 eth0
0.0.0.0         84.241.96.1     0.0.0.0         UG    100    0        0 eth0
0.0.0.0         84.241.96.1     0.0.0.0         UG    100    0        0 eth3
``````
#!/bin/sh
# interface
IF1=eth0
IF2=eth3

# ips
IP1=84.241.96.XX
IP2=84.241.96.XX

# gateways
P1=84.241.96.1
P2=84.241.96.1

# ip network
P1_NET=84.241.96.0
P2_NET=84.241.96.0

ip route add P1_NET dev IF1 src IP1 table WAN1
ip route add P2_NET dev IF2 src IP2 table WAN2


ip route add default via P1 table WAN1
ip route add default via P2 table WAN2


ip route add P1_NET dev eth1 src IP1
ip route add P2_NET dev eth2 src IP2


ip route add default scope global nexthop via P1 dev eth1 weight 5 nexthop via P2 dev eth2 weight 5

ip rule add from IP1 table WAN1
ip rule add from IP2 table WAN2
and the ip route configruation
```
but still can't access server on second wan ip, only from first wan ip....

---

### Post by poolet on 2011-10-12
I would think about it!!! :)

---

### Post by 11notes on 2011-10-13
maybe the problem is that those two wan interfaces are from the same isp in the same subnet and not on multiple isps on different subnets.... still can't figure it out oO

---

### Post by Vost on 2012-11-23
Hi to all!
I'm new on this forum, and listening to this discussion. I want to tell something; im so happy that there are user that learn in a practical way.
second; i understend, by your writings, that you are trying to achive multi WAN for load balancing. But maybe the problem is same IP on both NIC's. 
So i would try to create a virtual lan and then bridge it to one of the NIC's (ex. eth0). The virtual should be configured to do NAT and change the IP and/or subnet. so you can try to eliminate the IP problem, if it is a problem.
The fastest way should be (and te most mitigating) to conncet one LAN (WAN) on one external router and make NAT in there. so you should get in ubuntu NIC different subnet....

if this works you can make this internali in ubuntu by description above.

---

