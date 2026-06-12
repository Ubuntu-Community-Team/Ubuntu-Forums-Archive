---
title: "Openvpn client auto restart"
date: 2009-10-19
forum: Networking &amp; Wireless
---

### Post by dad311 on 2009-10-19
I have several Ubuntu workstations using Openvpn.  Each of these workstations will auto start Openvpn when booting.  If the network connection goes down, Openvpn will die and not restart.

Does anyone know how to make Openvpn auto-restart upon a connection failure?

thx

---

### Post by hackeron on 2011-01-23
Anyone?

---

### Post by dad311 on 2011-01-23
I use this little script to check the connection a few times during the day via the crontab.  If you use this script you might need to edit the openvpn restart command.



#cat vpn.sh

IP=192.168.100.27
RESULT=`ping -c 8 -W 2 $IP | grep transm | awk '{print $4}'`
echo "Result is $RESULT"

if [ $RESULT -eq 0 ]
then

/usr/sbin/openvpn --config /etc/openvpn/vpn.conf > /var/log/vpn.log&


echo "OpenVPN restart"
date
else

echo "No restart needed"
date

fi

---

