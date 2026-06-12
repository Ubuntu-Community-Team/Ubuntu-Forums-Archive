---
title: "ubuntu server setup"
date: 2012-09-08
forum: Networking &amp; Wireless
---

### Post by broecher on 2012-09-08
hi! i am trying to set up ubuntu server 9.04 in my home network for fun and my education. for now all i would really like to accomplish is being able to connect to the server from another computer in my network (i want to run it headless from my regular computer).  i have tried several things following some other threads and i am still not connected. here are the things i've done:

made a dhcp 'reservation' for 
192.168.0.169	ubuntuserver1	00:05:5d:50:0a:cc
i just picked a 169 from the available range.it shows up in 'lan computers' list now looking at my router(using another computer[that lacks capitol letter capabilities], d-link router btw).i accessed my router from: [http://192.168.0.1/](http://192.168.0.1/)

now on the server,
edited /etc/network/interfaces:
auto eth0
iface eth0 inet static
       address 192.168.0.169
       netmask 255.255.255.0
       gateway 192.168.0.1

edited resolve.conf:
nameserver 192.168.0.1

following the thread [http://ubuntuforums.org/showthread.php?t=1506854](http://ubuntuforums.org/showthread.php?t=1506854) 
i typed:
sudo ifconfig eth0 192.168.0.169 up
sudo route add default gw 192.168.0.1
ping -c3 192.168.0.1

result was 3 packets transmitted 0 received, 100% loss, time 2007ms
this means it failed right? i have also seen 'network unavailable' as a result earlier with a different configuration.

from the other computer:
me@mycomputer:~$ ssh 192.168.0.169
result:
ssh: connect to host 192.168.0.169 port 22: No route to host

i don't have the ability to copy and paste so this is a sumary:

ifconfig
eth0
link encap:ethernet hwaddress 00:05:5d:50:0a:cc
inet addr:192.168.0.169 bcast 192.168.0.255 mask 255.255.255.0
(everything else basically is zeros)
no listing for lo or others

ifconfig -a
same but now also
lo
link encap:local loopback
loopback mtu:16436 metric:1
...

---

### Post by 2F4U on 2012-09-08
I've setup static network adresses on 10.04 and 12.04 and it goes like this:

/etc/network/interfaces:

auto eth0
iface eth0 inet static
  address 192.168.0.169
  netmask 255.255.255.0
  gateway 192.168.0.1

Is there any reason why you use 9.04, since it seems a bit dated?

---

### Post by broecher on 2012-09-08
12 will not install on this machine, just went back to the first one i found. do you think there is much difference between 9 10 and 11 in this basic setup?

---

### Post by broecher on 2012-09-08
so in your case you just edited interfaces and that is all you did?

---

### Post by lisati on 2012-09-08
Editing the "interfaces" file is one way of doing it. Another way would be to reserve an IP address in your router. The procedure and what to look for on the router's browser-based control panel varies from router to router. There are pros and cons to each approach.

Edit: I'm just thinking that you might also want to look for a newer version of Ubuntu that will work on your system, so you can do things like install security updates and new software more easily.

---

### Post by broecher on 2012-09-08
i did both the static ip in interfaces and the router thing. was that wrong?

---

### Post by broecher on 2012-09-08
thanks gillychopra, its the computer, i forgot to use a computer! :) no i'm totally stumped still. i've followed tutorials like what you are talking about.

---

### Post by 2F4U on 2012-09-08
> **broecher said:**
> so in your case you just edited interfaces and that is all you did?

Yes, just the interfaces file. I did not make a reservation in my router except that I exclude a certain range of addresses from being handed out to dhcp clients, i. e. these addresses are reserved for fixed IP assignments.

---

### Post by broecher on 2012-09-08
yay!!!! i got it working!!! :)

I had tried several things editing different files and wasn't sure what all changes were hurting or helping so i just started over. i'll tell what happened in case some other poor soul reads this.

1) first i logged into my router from another computer ([http://192.168.0.1](http://192.168.0.1)) and went to dhcp server settings, changed the DHCP IP Address Range from 192.168.0.100 - 192.168.0.199 to 192.168.0.100 - 192.168.0.160. this is to prevent my desired address from being given to some other device.

2) installed ubuntu server again, this time when it said dhcp configuration not found(why it was not found im not sure), i selected manual configure. i entered my desired address 192.168.0.169, and the gateway and mask as it asked, the same numbers from above...

no editing of any files was needed. i went strait to the other linux computer and typed ssh 192.168.0.169 and voila! it was asking me to log in.

i unplugged the machine i was working on and plugged in another before trying this, and i noticed that the ethernet cord doesn't snap in, it just has to be pushed in firmly. this makes me wonder if the whole time the cord actually wasn't in far enough :p

---

