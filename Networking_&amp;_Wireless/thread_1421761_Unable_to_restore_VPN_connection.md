---
title: "Unable to restore VPN connection"
date: 2010-03-04
forum: Networking &amp; Wireless
---

### Post by ZuperB on 2010-03-04
I am trying to keep a VPN connection open between two Ubuntu 8.04 LTS servers, one in Holland and one in China. Unfortunately, because the connection in China is not great, about 1 time a day the connection drops. I have therefore devised a script, to be started by crontab once every 5 minutes, that checks the connection and if necessary restores it.

```
#!/bin/bash
ping -c 2 -W 10  10.10.10.73 &> /dev/null;
PING = $?;
if [ "$PING"-ne 0]; then
  # Restart pptp connection
  killall pppd;
  sleep 30;
  /usr/sbin/pppd call pptpvpn;
fi
```The script works fine when I start it from the shell but, unfortunately, when starting from cron it generates the following error messages in syslog:

 
bluebuntu /USR/SBIN/CRON[29540]: (root) CMD (/usr/local/bin/checkvpn > /tmp/checkvpn.log 2>&1)
bluebuntu pppd[29551]: pppd 2.4.4 started by root, uid 0
bluebuntu pppd[29551]: Couldn't get channel number: Input/output error
bluebuntu last message repeated 9 times
bluebuntu pppd[29551]: Exit.

In which bluebuntu is my server's name.

Any ideas on why this is happening? I would help me a lot if someone would provide a solution for this issue.

Thanks,
Bob


P. S. My script in /etc/init.d is:

```
#!/bin/bash
   
function routeadd {
   route add -net 10.10.10.0 netmask 255.255.255.0 dev ppp0
   route add -net 10.10.10.73 netmask 255.255.255.255 dev ppp0
}
function makepptp {
  echo pty \"pptp mycompany.nl --nolaunchpppd\" >> /etc/ppp/peers/pptpvpn;
  echo remotename PPTP >> /etc/ppp/peers/pptpvpn;
  echo require-mppe-128 >> /etc/ppp/peers/pptpvpn;
  echo file /etc/ppp/options.pptp >> /etc/ppp/peers/pptpvpn;
  echo ipparam pptpvpn >> /etc/ppp/peers/pptpvpn;
  echo persist >> /etc/ppp/peers/pptpvpn;
  echo usepeerdns >> /etc/ppp/peers/pptpvpn;
  pppd call pptpvpn > /tmp/pptpvpn.log 2>&1 &
}
   
if [ -e /etc/ppp/peers/pptpvpn ]; then
  rm /etc/ppp/peers/pptpvpn;
  echo name myvpn >> /etc/ppp/peers/pptpvpn;
  makepptp;
  sleep 12;
  routeadd;
else
  echo name myvpn >> /etc/ppp/peers/pptpvpn;
  makepptp;
  sleep 12;
  routeadd;
fi
```

---

### Post by ZuperB on 2010-03-20
Guys, do I have to figure out everything by myself?  ;)

  
 Anyway, I found a solution that works. This is my new script /usr/local/bin/checkvpn:

  
```
#!/bin/bash
  
function routeadd {
    /sbin/route add -net 10.10.10.0 netmask 255.255.255.0 dev  ppp0
    /sbin/route add -net 10.10.10.73 netmask 255.255.255.255  dev ppp0
}
  
ping -c 2 -W 10 10.10.10.73 &>  /dev/null;
PING=$?;
if [ "$PING" -ne 0 ]; then
     # Restart pptp connection
     /sbin/ifdown ppp0
     sleep 5;
     /sbin/ifup ppp0
     sleep 30;
     routeadd;
     sleep 3;
fi

```To make this work, I had to add the details for the ppp0 interface  to the file /etc/network/interfaces by adding the following  lines.
  
```
auto ppp0
iface ppp0 inet ppp
     provider pptpvpn

```

---

