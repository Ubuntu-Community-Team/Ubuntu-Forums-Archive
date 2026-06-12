---
title: "DHCP help"
date: 2011-06-28
forum: Networking &amp; Wireless
---

### Post by jsprz8382 on 2011-06-28
hello, first off I am sorry if my question does not make much sense. I do not know much about computers. I'll try anyway, so on to the issue.
I have cable modem connected to one machine (the one I am currently using)
the problem is that many times the Internet detects a different network with IP (169..) and does not let me access the Internet this not only happens in Linux but also on WINDOWS. I think I can fix this problem by formating and installing A Linux OS by manually imputing my cable account # when it asks me if I want my DHCP to be set automatically. Yet it still continues to go of unexpectedly. Also I tried setting the IP,MASK,GATEWAY, manually and no internet access still.
So I would like to know if I can change the DHCP server from within Ubuntu (so I dont have to reinstall it every time.)
And yes I have contacted my ISP they changed the cable modem and it only worked until I plugged the LAN cable into a different machine.
Thank you in advance..

---

### Post by poolet on 2011-06-28
hello try the following:: 

```
sudo vi /etc/network/interfaces
``````

auto [**interface**]
iface [**interface**]inet dhcp

``````

auto [**interface**]
iface [**interface**] inet static
        address 192.XXX.XXX.XX
        netmask 255.255.255.0
        network 192.XXX.XXX.XX
        broadcast 192.XXX.X.XXX
        gateway 192.XXX.X.X

```On the line ‘xxx.xxx.xxx.xxx’ replace the x with the IP of your name server
```
sudo vi /etc/resolv.conf

```
remove the dhcp client....

```
sudo apt-get remove dhcp-client
```
restart your network....
```

sudo /etc/init.d/networking restart
```

---

