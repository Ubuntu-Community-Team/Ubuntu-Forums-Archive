---
title: "Internet connection on a lan client"
date: 2008-12-31
forum: Networking &amp; Wireless
---

### Post by giovannilenzi on 2008-12-31
We have a small lan with a pc connected to Internet through a hsupa modem (Novatel MC950D).
On this pc I installed Ubuntu 8.10 home edition.
Ubuntu have correctly discovered and set up the modem.
The modem works quite fine: in Umts it is able to reach 1,8 Mbs in download and in upload (!).  Using Windows I was able to force the hsdpa mode and I got something more in download (in my place the hsdpa signal is very feeble and it is necessary to force the modem), but I don't know how to do this in Ubuntu, but this is not the major problem.
I shared the connection using firestarter (probably this is the worst way, but it is the only one I know).
The problem is that when I use Internet on a client I get only a very slow connection, not more than 320 kbs in download and much lesser in upload!
Which parameters should I set in order to get the same speed using the clients?
ps. Sorry form my bad English!

---

### Post by Iowan on 2008-12-31
Perhaps you've already seen [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") help page for connection sharing.

The MTU setting can be adjusted - *might* help with transfer speeds.  *Normal* value is 1500. I've seen some threads where this value has dropped to <600 - system did not work well.

---

### Post by giovannilenzi on 2009-01-02
Thanks.
I saw it, but I thought it was good only for an external modem connected through ethernet.
I tried the first way, instead of using Firestarter.
I disinstalled Firestar, Dhcp3, Iptables to be sure.
I reinstalled Iptables.
I followed the instructions, using as ip 192.168.0.4 for the gateway because we have an old windows gateway that uses the number 1 (usually we don't uses it).
I inserted the following commands:

sudo ifconfig eth0 192.168.0.4
sudo iptables -A FORWARD -i ppp0 -o eth0 -s 192.168.0.0/24 -m state --state NEW -j ACCEPT
sudo iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A POSTROUTING -t nat -j MASQUERADE
sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"

It runs and I can get a better speed on the client, but not yet the speed that I get on the server (about 400kb against 1,8mbs).
Where should I change the Mtu?
[Another problem, when I restart the server I lost the iptables configuration and I must reenter all the commands above. This last problem is SOLVED following [https://help.ubuntu.com/community/IptablesHowTo]](https://help.ubuntu.com/community/IptablesHowTo])

---

### Post by giovannilenzi on 2009-01-07
I tried to change the Mtu in the ppp, the results was worst.
I tried to connect using several different programs (network-manager, wvdial, vodafone connect utility...)
I tried to share the connecion using Firestarter, network-config, changing manually iptables...
I get always the same: the umts modem works well on the server, but the clients are not able to use all the band.
What should a newbee do more than this??
Could be a problem of the cache of the server?

---

### Post by superprash2003 on 2009-01-07
you mean slow speeds for clients?? slow download speed or browsing speed?

---

### Post by giovannilenzi on 2009-01-07
I mean slow download speed for clients. The upload speed is even worst.

---

### Post by superprash2003 on 2009-01-08
well if multiple clients are downloading at the same time , each client would get low speed..

---

### Post by giovannilenzi on 2009-01-15
Sorry if I answer only now, I was not here for a week.
The problem is not the massive usage.
If I try to download from only one client I get a very slow speed. 
Now, I made so many change and finally I get a good speed in upload even on the clients, but not yet in download.
This is quite funny.:confused:
I still think that is a problem of the server's cache or something like this. I do not know ubuntu.

---

