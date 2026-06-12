---
title: "Mobile broadband not working with Ubuntu 9.10"
date: 2009-11-20
forum: Networking &amp; Wireless
---

### Post by lads on 2009-11-20
Hello everyone. 

I bought a USB 3G broadband stick some months ago (Huawei E160E). At the time I had some difficulties getting it to work with Ubuntu 8.10, but after identifying a particular issue with my laptop it eventually started working. Check the story here:

[http://ubuntuforums.org/showthread.php?t=1161080](http://ubuntuforums.org/showthread.php?t=1161080)

Since then I have used this USB stick successfully in other computers and with other distros: Ubuntu 9.04 and Debian 5.

Yesterday I upgraded one of my Ubuntu systems to the latest release (9.10) and so far I haven't managed to get it to work. I connect the stick and Ubuntu recognizes it, I'm presented with the correct internet provider options and am able to proceed with the connection. The GNOME icon indicates an active connection and the stick's led lights up. The problem is: I can't connect to any website or ping any server.

This is very strange, running ifconfig I get the following:

```

lads@Kohntarkosz:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:81:ed:9b:07  
          inet6 addr: fe80::224:81ff:feed:9b07/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22287 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2244 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4090611 (4.0 MB)  TX bytes:405533 (405.5 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2727 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2727 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:489247 (489.2 KB)  TX bytes:489247 (489.2 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:62.169.121.2  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:234 (234.0 B)  TX bytes:249 (249.0 B)


```

I don't know what the errors mean, but it seems I'm at least getting an IP address.

I've tried in two different computers getting similar results, so I guess this is not an hardware related issue.

Can anyone help? Thanks.

---

### Post by hal10000 on 2009-11-20
It seems as if you have a connection, otherwise you would'nt have got an ip-address.
Maybe you have a dns problem. Look into your /etc/resolv.conf file and verify if you have a nameserver entry.

---

### Post by lads on 2009-11-21
Thanks for the reply Hal.

Moments ago I tried to create the connection with the live cd and all went well. So I went back to my system, and repeated the registration process, this time it worked.

I can't explain what happened but might have been some dns broadcast issue.

Thanks.

---

