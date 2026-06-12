---
title: "Limiting bandwidth to client group"
date: 2009-09-30
forum: Networking &amp; Wireless
---

### Post by unimatrix on 2009-09-30
I want to setup some Internet speed limitations in my network. I have drawn a picture of how I've imagined it:

[IMG]http://img24.imageshack.us/img24/1776/10898029.png[/IMG]

Basically, I want to limit both upload and download speed over the internet for all the clients in the yellow cloud to 5M in both directions. The two clients outside it (192.168.2.3 and 192.168.2.4) should be able to get full ul&dl speeds (10Megabits at the moment). But all of them have to be able to access the Linux router with 100M (LAN network speed) locally.

I know this can be done with /sbin/tc
I've tried but failed. It is simply too complicated, and I would be very glad if someone could help me.

---

### Post by sedawk on 2009-09-30
It looks like you need a traffic shaping tool on the
linux router.
Further reading:
[http://en.wikipedia.org/wiki/Traffic_Shaping](http://en.wikipedia.org/wiki/Traffic_Shaping)
(There is a Linux section in the Reference
 "Traffic Shaping Tools" that leads to this page:
 [http://lartc.org/](http://lartc.org/) and a HowTo: [http://lartc.org/howto/](http://lartc.org/howto/) )

While it seems to be possible to do this based
on IP lists it might be easier to do it on
subnets (which is also easier to maintain in the
long run as adding machines doesn't require an
updated configuration).
Do the machines really have to be in the same subnet?
It might be easier if you use two subnets, the
"fast internet subnet" and the "slow internet subnet".
Currently the "fast internet machines" are logically 
in the yellow 192.168.2.0/24 cloud and subnet.

---

### Post by unimatrix on 2009-09-30
Hmm, yes you've got a point there. How do I do that? Just configure 2 subnets in DHCP? I still need all the clients to see each other. If I got one 192.168.2.0 network and another 192.168.1.0 network, they won't see each other.

---

### Post by unimatrix on 2009-09-30
OK, here's the thing. I'm not going to use subnets, because they complicate everything for no reason. I just need two "high-speed" clients anyway, everything else will be limited.

---

### Post by unimatrix on 2009-10-01
OK, so I've managed to write this script that limits the DOWNLOAD speed to everyone except the addresses listed in the $exclude array, and does not limit local transfers.

```

#!/bin/bash

TC=/sbin/tc

dev="eth1"
bandwidth="100Mbit"
limit="5Mbit"
allot="1514"
avpkt="1400"
maxburst="20"
perturb="15"

exclude=("192.168.2.3"
	 "192.168.2.4")

exclusions=${#exclude[*]}

tc_qdisc_show() {
    $TC qdisc show dev $dev
}

adddel="add"
case $1 in
    "add" )
	adddel="add";;
    "del" )
	adddel="del"
	$TC qdisc del dev $dev root
	tc_qdisc_show
	exit 0;;
    * )
	echo "Missing parameter: [ add|del ]"
	exit 0;;
esac

$TC qdisc $adddel dev $dev root handle 12: cbq bandwidth $bandwidth avpkt $avpkt
$TC class $adddel dev $dev parent 12: classid 12:1 cbq bandwidth $bandwidth rate $bandwidth allot $allot weight 10Mbit prio 2 maxburst $maxburst avpkt $avpkt

$TC class $adddel dev $dev parent 12:1 classid 12:11 cbq bandwidth $bandwidth rate $limit allot $allot weight 128Kbit prio 5 maxburst $maxburst avpkt $avpkt bounded
$TC class $adddel dev $dev parent 12:1 classid 12:10 cbq bandwidth $bandwidth rate $bandwidth allot $allot weight 1Mbit prio 3 maxburst $maxburst avpkt $avpkt
	    
$TC qdisc $adddel dev $dev parent 12:10 sfq quantum ${allot}b perturb $perturb
$TC qdisc $adddel dev $dev parent 12:11 sfq quantum ${allot}b perturb $perturb

$TC filter $adddel dev $dev parent 12: protocol ip prio 15 u32 match ip src 192.168.2.0/24 flowid 12:10
$TC filter $adddel dev $dev parent 12: protocol ip prio 20 u32 match ip dst 192.168.2.0/24 flowid 12:11
for ((i=0; i<exclusions; i++)); do
    $TC filter $adddel dev $dev parent 12: protocol ip prio 10 u32 match ip dst ${exclude[i]} flowid 12:10
done

echo -n
echo "***** Result ******"
$TC qdisc show
echo "*******************"

```

Now I need to limit the UPLOAD speed aswell. I'm guessing that has to be done on my other "eth0" card, that is connected to the FTTH switch.

Does ANYONE know how to do that?

---

