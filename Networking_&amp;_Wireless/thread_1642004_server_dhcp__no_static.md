---
title: "server: dhcp : no static"
date: 2010-12-09
forum: Networking &amp; Wireless
---

### Post by amalafrida on 2010-12-09
Fresh install of 10.04.1 server; installs seamlessly; finds network no problem.

However, establishing static connection is driving me batty.  Will not take.  I've reconfigured "interfaces" file several times.  My fingers are numb ifdown-ing and ifup-ing and /etc/init.d/network restart-ing.

I have two files in /etc/network ... interfaces and interfaces~ (one static and the other dhcp).  I can switch them in and out of play.  The dhcp works and pings out like a champ.  static is dead, just dead.  Cannot ping router ... nothing.

Just any old suggestion would be much appreciated.

Thanks in advance.

r.

---

### Post by amalafrida on 2010-12-09
Failed to include relevant info in previous post.

eth0      Link encap:Ethernet  HWaddr 00:19:21:54:8f:d0  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:21ff:fe54:8fd0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5264 (5.2 KB)  TX bytes:6361 (6.3 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1416 (1.4 KB)  TX bytes:1416 (1.4 KB)


auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.102
network 192.168.1.0
broadcast 192.168.1.255
netmask 255.255.255.0
gateway 192.168.1.254

---

### Post by bdoherty09 on 2010-12-09
Something I was coming here to look for too.  I remember someone once telling me that sometimes the interfaces file isn't what is controlling it.  For example, I have a static ip.  I am not using Server edition so I can go thru the GUI and see it and set it (which is how I did it).  Now, a cat of my interfaces file looks like:

auto lo
iface lo inet loopback

and that's it.  Obviously, this isn't where the control is.  So, the answer to both of our problems are probably the same, but I don't know what that answer is.  Hopefully, someone will come along soon and point us in the right direction........or tell me I am completely wrong.

---

### Post by amalafrida on 2010-12-10
Yes, your observation is on point.  My box running 10.04 desktop presents the same behavior.  Actual changes to the network setup are not reflected in /etc/network/interfaces file.

Hope someone comes along soon with an elegant response.

r.

---

### Post by amalafrida on 2010-12-10
Removed router from network.  Linked up server box directly through modem with static ip.  Working well.

Clearly, (or almost clearly), my problem lies with router configuration.  Netgear  WGR614.

Back for more later ...

---

### Post by tredegar on 2010-12-10
If you are going to use a static IP (which I like on my little network) do not forget that you'll have to set up the address of your nameserver (which will usually be the LAN IP of your router, 10.0.0.2 in my case) in **/etc/resolv.conf**

```
tred@home:~$ cat /etc/resolv.conf
nameserver 10.0.0.2
tred@home:~$ 
```

If you get a LAN IP by dhcp, then dhcp also sets up the nameserver in **/etc/resolv.conf** so you don't need to.

---

