---
title: "Suddenly unable connect to internet. Please help!"
date: 2011-01-21
forum: Networking &amp; Wireless
---

### Post by Pipps on 2011-01-21
It's a Dell Mini 10 netbook. Has run Ubuntu and connected to the internet successfully for several years. But over the last 48 hours, it is inexplicably unable to connect. However, router lights up to say that it's connected.

Output of **ipconfig** is as follows:

> lo		Link encap:Local Loopback
		inet addr:127.0.0.1 Mask:255.0.0.0
		inet6 addr: ::1/128 Scope:Host
		UP LOOPBACK RUNNING MTU:16436 Metric:1
		RX packets:164 errors:0 dropped:0 overruns:0 frame:0
		TX packets:164 errors:0 overruns:0 carrier:0
		collisions:0 txqueuelen:0
		RX bytes:12112 (12.1 KB) TX bytes:12112 (12.1 KB)

Please help! Thank you

---

### Post by ripat on 2011-01-21
run and post result of:
```
$ sudo dhclient
```

---

### Post by Pipps on 2011-01-21
Thank you for your help.

Output of **dhclient **is:

> Listening on LPF/eth1/70:1a:04:6d:7d:73
Sending on LPF/eth1/70:1a:04:6d:7d:73
Listening on LPF/eth0/00:24:e8:f2:9e:9a
Sending on LPF/eth0/00:24:e8:f2:9e:9a
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.0.100 from 192.168.0.1
DHCPREQUEST of 192.168.0.100 on eth0 to 255.255.255.255. port 67
DHCPPACK of 192.168.0.100 from 192.168.0.1
bound to 192.168.0.100 -- renewal in 235342 

What does this mean?

---

### Post by ripat on 2011-01-21
It means that you have received 192.168.0.100 from 192.168.0.1, the dhcp server.

What's the result of:
```
$ ip address ls
$ ip route ls
$ sudo cat /etc/resolv.conf
```

---

### Post by psycho5 on 2011-01-21
It means that your laptop requested an IP address from the dhcp server on your router and was able to get it, the last line tells you how long till the IP address expires and is renewed. Meaning that your laptop is connected to your router and is communicating.

192.168.0.1 = your router's IP (DHCP server)

192.168.0.100 = your computer's requsted IP address, which was given by your router aka your Dell's IP address.

---

### Post by Pipps on 2011-01-21
Thanks again for your help.

Output of **ip address ls** is:
> 1. lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN
link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
inet 127.0.0.1/8 scope host lo
inet6 ::1/128 scope host
   valid_lft forever preferred_lft forever
2. eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
link/ether 00:24)e8:f2:9e:9a brd ff:ff:ff:ff:ff:ff
inet 192.168.0.100/24 brd 192.168.0.255 scope global eth0
inet6 fe80::224:e8ff:fef2:9e9a/64 scope link
   valid_lft forever preferred_lft forever
   3. eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
   link/ether 70:1a:04:6d:7d:73 brd ff:ff:ff:ff:ff:ff
   inet 169.254.6.157/16 brd 168.254.255.255 scope link eth1:avahi
   inet6 fe80::721a:4ff:fe6d:7d73/64 scope link
     valid_lft forever preferred_lft forever
	 
Output of **ip route ls** is:
> 192.168.0.0/24 dev eth0 proto kernel scope link src 192.168.0.100
default via 192.168.0.1. dev eth0

Output of **sudo cat/etc//resolv/conf** is:
> nameserver 192.168.0.1.
domain cable.virginmedia.net
search cable.virginmedia.net

What should I do to enable Ubuntu to connect?

---

### Post by ripat on 2011-01-21
Result of:
```
$ dig google.com
$ dig @8.8.8.8 google.com
```

---

### Post by Pipps on 2011-01-21
Output of **dig google.com** is:
> ; <<>> DiG 9.7.0-P1 <<>> google.com
;; global options: +cmd
;; connection timed out; no servers could be reached

Output of **dig @8.8.8.8 google.com** is:
> ; <<>> DiG 9.7.0-P1 <<>> @8.8.8.8 google.com
; (1 server found)
;; global options: +cmd
;; connection timed out; no servers could be reached
 
Thank you again for your help.

---

### Post by ripat on 2011-01-21
Let's see with:
```
ping -c 2 -W 5 8.8.8.8
```

---

### Post by Pipps on 2011-01-21
Output of **ping -c 2 -W 5 8.8.8.8** is:

> Network is unreachable

Thank you again!

---

### Post by ripat on 2011-01-21
And can you ping your gateway?
```
$ ping -C 2 -W 3 192.168.0.1
```

---

### Post by Pipps on 2011-01-21
Output of **ping -c 2 -W 3 192.168.0.1** is also:
> Network is unreachable
Yet both the router and the netbook's modem light up to indicate that a valid connection is being made.

What should be done next?

---

### Post by mips on 2011-01-21
Post output of **netstat -nr**

---

### Post by Pipps on 2011-01-21
Output of **netstat -nr** is:
> Kernel IP routing table
Destination   Gateway   Genmask   Flags  MSS Window  irtt Iface

Thank you!

---

### Post by ripat on 2011-01-21
> **Pipps said:**
> Output of **ping -c 2 -W 3 192.168.0.1** is also:

Yet both the router and the netbook's modem light up to indicate that a valid connection is being made.

What should be done next?

That's strange because the dhcp request seems to work when you execute dhclient meaning that your dhcp server responds to your request.

Try again this:
```
$ sudo dhclient; ip address ls; ip route ls; ping -c 1 -W2 $(ip route show | awk '/default/ {print $3}')

```

---

### Post by Pipps on 2011-01-21
Output of **dhclient; ip address ls; ip route ls; ping -c 1 -W2 $(ip route show | awk '/default/ {print$3}')** is:

> Listening on LPF/eth1/70:1a:04:6d:7d:73
Sending on   LPF/eth1/70:1a:04:6d:7d:73
Listening on LPF/eth0/00:24:e8:f2:9e:9a
Sending on   LPF/eth0/00:24:e8:f2:9e:9a
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPREQUEST of 192.168.0.100 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.100 from 192.168.0.1
bound to 192.168.0.100 -- renewal in 287640 seconds.
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 00:24:e8:f2:9e:9a brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.100/24 brd 192.168.0.255 scope global eth0
    inet6 fe80::224:e8ff:fef2:9e9a/64 scope link tentative 
       valid_lft forever preferred_lft forever
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 70:1a:04:6d:7d:73 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::721a:4ff:fe6d:7d73/64 scope link tentative 
       valid_lft forever preferred_lft forever
192.168.0.0/24 dev eth0  proto kernel  scope link  src 192.168.0.100 
default via 192.168.0.1 dev eth0 
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=1.88 ms

--- 192.168.0.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 1.882/1.882/1.882/0.000 ms

I hope this helps. Thank you!

---

### Post by ripat on 2011-01-22
From the above output we can see that you have received an IP address lease from the DHCP server, that it was assigned to your eth0 interface, that the route to the gateway is built and that you can ping your server. In other words, you are connected to your LAN and from there to your router which is the exit/entry point to the internet. When you have that, you should be able to ping, say 8.8.8.8. Try again:

```
$ dig google.com
$ dig @8.8.8.8 google.com
```

If not successful you should check your router to see if it has received an "external" IP from your ISP. You should be able to administrate the router from your browser by typing it's IP 192.168.0.1 in the address bar.

---

### Post by Pipps on 2011-01-22
The commands **dig google.com** and **dig @8.8.8.8 google.com** seem to now still produce exactly the same result as before.

When I log into my router, it says that it has assigned the Ubuntu laptop the following:

> IP address 192.168.0.100
MAC address 00:24:E8:F2:9E:9A

I currently have several other computers on this network which are all connecting fine.

I am really grateful for your continued support.

---

### Post by ripat on 2011-01-22
Strange, your Ubuntu box seems to be blocked out. Can you check what the other computers have as network setup?

If they are windows I think that the command is *ipconfig -all*

---

### Post by Pipps on 2011-01-22
I have a Windows machine at:
> IP 192.168.0.101 	
MAC 00:22:15:FA:A0:1E

And an XBMC HTPC at:
> IP 192.168.0.102 	
MAC 38:E7: D8:79: D9: D4

What do you think?

---

### Post by Pipps on 2011-01-22
I should further add, that upon booting the netbook from a live USB disk, the 'network detected' notification, and a working internet connection, are both present.

What could this all mean?

---

### Post by ripat on 2011-01-22
Can you post the result of the *ipconfig --all* command on the windows machine.

May be you have a ill-conceived firewall on the Ubuntu box? What's the output of:
```
$ sudo iptables-save
```

---

### Post by Pipps on 2011-01-22
Thanks for your further assistance. I will post this output as soon as I can.

---

### Post by ravengangrel on 2011-01-23
Hello, Pipps,

Do you have connection if you remove the cable and put it on again, or in case it's a wireless device, reconnecting to the network?

If so, check this thread:
[http://ubuntuforums.org/showthread.php?p=10388871&posted=1#post10388871](http://ubuntuforums.org/showthread.php?p=10388871&posted=1#post10388871)

---

### Post by Pipps on 2011-01-24
I have needed to take a shortcut so I have just reinstalled UNR. All is working fine now.

Thank you everyone, especially Ripat, for all your help!

---

