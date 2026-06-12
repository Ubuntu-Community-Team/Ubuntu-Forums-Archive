---
title: "how to use free vpn tunel, alonweb, on Kubuntu 9.04"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by chanyunkwan on 2009-04-26
It's really great that Alonweb support linux environment.
I followed the instruction on the official website of Alonweb to try to make it work on Kubuntu 9.04. But it doesn't work really.

[http://www.alonweb.com/node/3](http://www.alonweb.com/node/3)

After I run the command 
```
sudo /etc/init.d/openvpn start
```
And enter my username and password

The Konsole said OK.

But I can't really use it to connect to the internet. 
for instance, firefox can't access to any website. It looks like it's loading but I can see nothing but a blank page.

I use the same account and it works great on Windows XP. (same network environment)

Do anyone know how to get Alonweb work on Kubuntu 9.04?

Thank you.

---

### Post by Duckieman on 2009-05-24
I have managed to used Ultravpn on Linux. This service is totally free and has great speed, good for downloading torrents if u dont want to get caught):P
[https://www.ultravpn.fr]("https://www.ultravpn.fr/")

---

### Post by wightman.p on 2009-07-14
> **Duckieman said:**
> I have managed to used Ultravpn on Linux. This service is totally free and has great speed, good for downloading torrents if u dont want to get caught):P
[https://www.ultravpn.fr]("https://www.ultravpn.fr/")

I have the OpenVPN client and would like to use this to access teh UltraVPN service.  Any clues on how to do this please?

---

### Post by hifinalx on 2009-07-29
hi i've got the same problem, ubuntu9.04 with xfce4
network-manager-openvpn shows that vpn has connected
and command "route" list :```
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.9.0.1        10.9.226.37     255.255.255.255 UGH   0      0        0 tun0
10.9.226.37     *               255.255.255.255 UH    0      0        0 tun0
94.23.207.54    192.168.0.1     255.255.255.255 UGH   0      0        0 eth0
192.168.0.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         10.9.226.37     0.0.0.0         UG    0      0        0 tun0

```but i can't access any website[via firefox], and has no replay while PING any site, any idea?thanks :D

---

