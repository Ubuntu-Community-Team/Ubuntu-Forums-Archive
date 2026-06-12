---
title: "Ubuntu 11.10 Masquerade"
date: 2012-03-26
forum: Networking &amp; Wireless
---

### Post by shalkith on 2012-03-26
Good day all!!

It's been a few years since I've messed with Linux but I'm trying to get back in the game.

I've been trying to get Masquerading working on my Ubuntu machine for a bit now with no luck.

I'm trying to share the internet provided from my wlan0 interface to devices connected to my eth0 interface. 

Most guides on the internet basically say to do:
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

There's gotta be more to it than that. Isn't there?
Am I missing something?


Also, I've noticed that when I've got both my wlan0 and eth0 connected I'm not able to browse the web. I think its defaulting to my eth0 interface and there's no internet connection there....

Any way to force my connection via wlan0?

---

### Post by shalkith on 2012-03-27
-Bump-

Anyone here know a bit about masquerading?

---

### Post by shalkith on 2012-03-29
Tried this in the networking forums but didnt get any feedback.

It's been a few years since I've messed with Linux but I'm trying to get back in the game.

I've been trying to get Masquerading working on my Ubuntu machine for a bit now with no luck.

I'm trying to share the internet provided from my wlan0 interface to devices connected to my eth0 interface. 

Most guides on the internet basically say to do:
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

There's gotta be more to it than that. Isn't there?
Am I missing something?


Also, I've noticed that when I've got both my wlan0 and eth0 connected I'm not able to browse the web. I think its defaulting to my eth0 interface and there's no internet connection there....

Any way to force my connection via wlan0?

---

### Post by SeijiSensei on 2012-03-29
> **shalkith said:**
> TThere's gotta be more to it than that. Isn't there? Am I missing something?

Yes, you have to enable packet forwarding in /etc/sysctl.conf.  Set net.ipv4.ip_forward=1 and reboot.

> Any way to force my connection via wlan0?

Make sure your default route is set to point at the wifi router.  Suppose your router has address 192.168.1.1 and wlan0 has 192.168.1.2.  Run the command "route -n" and see if you have a line that reads:

```

Destination    Gateway       [other stuff]
0.0.0.0        192.168.1.1   [other stuff]    

```

If the gateway is another address, presumably one reachable via eth0, say 10.10.10.10, then you need to do this:

```

sudo ip route del default via 10.10.10.10
sudo ip route add default via 192.168.1.1

```

You can get the wrong address if you use DHCP to configure both devices and start eth0 after wlan0.  I'd recommend making the address for eth0 [static]("http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/") so this problem cannot arise.

---

### Post by cariboo on 2012-03-29
Please don't create multiple threads on the same subject, I have merged your threads.

---

### Post by shalkith on 2012-03-30
> **SeijiSensei said:**
> Yes, you have to enable packet forwarding in /etc/sysctl.conf.  Set net.ipv4.ip_forward=1 and reboot.



Make sure your default route is set to point at the wifi router.  Suppose your router has address 192.168.1.1 and wlan0 has 192.168.1.2.  Run the command "route -n" and see if you have a line that reads:

```

Destination    Gateway       [other stuff]
0.0.0.0        192.168.1.1   [other stuff]    

```

If the gateway is another address, presumably one reachable via eth0, say 10.10.10.10, then you need to do this:

```

sudo ip route del default via 10.10.10.10
sudo ip route add default via 192.168.1.1

```

You can get the wrong address if you use DHCP to configure both devices and start eth0 after wlan0.  I'd recommend making the address for eth0 [static]("http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/") so this problem cannot arise.


neither the masquerading or the ip route changes worked :\

I dont know if this helps but:

Going over this again


```
Router -192.168.1.2 (strange config i know but that's what it is right now)


laptop - wlan0 - 192.168.1.110
laptop - eth0 - 172.16.42.42

Linux box - eth0 172.16.42.1

```
If Im on the Linux box I can ping as far as 192.168.1.110

I can not ping 192.168.1.2

Also, when I have both wlan0 and eth0 connected on the laptop I cant ping 192.168.1.2

As soon as i disconnect eth0 I can ping the router and browse the web again.

---

### Post by SeijiSensei on 2012-03-30
With both devices active and connected, please post the results of 

```

route -n
sudo iptables -L -nv
sudo iptables -t nat -L -nv
cat /proc/sys/net/ipv4/ip_forward

```

---

### Post by shalkith on 2012-03-31
> **SeijiSensei said:**
> With both devices active and connected, please post the results of 

```

route -n
sudo iptables -L -nv
sudo iptables -t nat -L -nv
cat /proc/sys/net/ipv4/ip_forward

```

```
paul@ubuntu:~$ sudo route -n
[sudo] password for paul: 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.2     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
172.16.42.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
192.168.1.2     0.0.0.0         255.255.255.255 UH    0      0        0 eth0

```


```
sudo iptables -L -nv
Chain INPUT (policy ACCEPT 957 packets, 829K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  wlan0  eth0    172.16.42.0/24       0.0.0.0/0           ctstate NEW 
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ctstate RELATED,ESTABLISHED 

Chain OUTPUT (policy ACCEPT 1047 packets, 156K bytes)
 pkts bytes target     prot opt in     out     source               destination  
```

```
cat /proc/sys/net/ipv4/ip_forward 
1

```

---

### Post by Jive Turkey on 2012-04-01
You want static ip's for both wlan0 and especially eth0.  Besides /proc/sys/net/ipv4/ip_forward and iptables rules you need your machines and routers (including eth0) behind the Linux box, **to have eth0's ip address as their default gateway**. You may find it helpful to have a DHCP server dish out that info from either the linux box or a router connected to eth0.

I have created what you are setting up now, with dnsmaq and shorewall.

I found this article super helpful [http://www.somewhereville.com/?p=1196]("http://www.somewhereville.com/?p=1196") and I think you will too.

---

### Post by shalkith on 2012-04-02
I got it working! Turns out there's a bug with Ubuntu 11.10. You have to change the settings for each interface you're using and tell it to Ignore IPV6 - I got that cleared up and now its working as intended. 

Thanks everyone for the help!

PS Article can be found here:

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

