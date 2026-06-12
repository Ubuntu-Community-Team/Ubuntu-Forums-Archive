---
title: "Automatically obtain a new IP"
date: 2010-01-26
forum: Networking &amp; Wireless
---

### Post by vinaur on 2010-01-26
Hi,

I have an Ubuntu server running behind a router and I generally manage it from a remote location. I ran into a problem today when I changed the subdomain that the router is on and in turn changed all of the ip addresses for everything on the local network. After restarting the router, I can no longer access the Ubuntu server.

I made sure that I changed the port forwarding settings to reflect the changes in ip addresses. Also the router does not even show the Ubuntu server as having an ip address issued to it. So from that I guess that the server never requested for a new ip after the router restarted.

I think I've had this problem before and I ended up restarting the entire server manually. I know that if I restart it, everything should be back to normal. That's what I'll have to end up doing, but I wanted to avoid having this problem in the future, so I was wondering if there is any way to set up the server so that it requests for a new ip address automatically.

Any help would be very much appreciated.
Thank you.

---

### Post by ant2ne on 2010-01-26
```
sudo ifdown eth0 && sudo ifup eth0
```
or
```
dhclient eth0
```
assuming it eth0 is your eth card.

IDK if ifdown ifup will change get a new DHCP IP if /etc/network/interfaces is not set to auto.

---

### Post by vinaur on 2010-01-26
> **ant2ne said:**
> ```
sudo ifdown eth0 && sudo ifup eth0
```or
```
dhclient eth0
```assuming it eth0 is your eth card.

IDK if ifdown ifup will change get a new DHCP IP if /etc/network/interfaces is not set to auto.

/etc/network/interfaces is set to auto, but my problem is that there is no way that I can actually run dhclient command remotely, because I can't access the computer.

What I need it to do is to renew the ip automatically when it can no longer access the network. I suppose it could be possible to ping the gateway once in a while and when the gateway is not responding, try to renew the ip.

Anyone know if this is already implemented in ubuntu?

---

### Post by ant2ne on 2010-01-27
so... you just want it to look for an IP address periodically? like, using cron to do a dhclient request?

---

### Post by vinaur on 2010-01-27
Right, that's what I was thinking. But I was wondering if doing dhclient when the connection is fine would break any active connections. Kind of like what would happen if you did ifdown/ifup

---

### Post by ant2ne on 2010-01-28
Something like...

make a script
```
sudo nano /bin/mypingscript
```put the following in it....
```
PingFail()
{
echo Ping Failed!!!
dhclient eth0
}
ping -c 1 192.168.1.1 && PingFail
```
```
sudo chmod +x /bin/mypingscript
```
Then tell cron to execute it every minute.
```
sudo crontab -e
```
and insert the following
```
  */1  *   *    *    *    /bin/mypingscript.sc
```

Find some way to test it. Maybe assign a bad IP so that the connection gets broken and it then fetches a new IP.

---

### Post by ant2ne on 2010-01-28
> **vinaur said:**
> Right, that's what I was thinking. But I was wondering if doing dhclient when the connection is fine would break any active connections. Kind of like what would happen if you did ifdown/ifupyeah.. i think it would break the connections. the above script only executes dhclient if it fails to ping the gateway of 192.168.1.1.

---

### Post by vinaur on 2010-02-04
Thank for all the help

I haven't actually tested this yet, since I don't want to take the server offline again until i'm physically there.

```
#!/bin/bash
#route is in /sbin
PATH=$PATH:/sbin
#check if network interface is up
ping -n -c 1 127.0.0.1 > /dev/null || exit 1

#find gateway
GW=`route -n | awk '$1 ~ /0.0.0.0/ {print $2}'`

#ping gateway
#dhclient if no response
ETH=eth0
ping -n -c 2 $GW > /dev/null || dhclient $ETH

```

I read around that it's a good idea to first check if the network interface is even up before pinging gateway. Also, this should automatically find the gateway IP.

---

