---
title: "Wired Ethernet not being detected.."
date: 2009-02-03
forum: Networking &amp; Wireless
---

### Post by suffer1989 on 2009-02-03
Hey, i Have a laptop, and i mainly use a wireless connection to browse the web, ETC. ETC. I have also assigned it a static IP Address. However, when i plug in an ethernet cable, UBUNTU doesnt recognise it ?

Here is my /etc/network/interfaces:

```
# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.4
network 192.168.0.1
netmask 255.255.0.0
broadcast 169.254.255.255 
gateway 192.168.0.1
```

As you can see, i like to keep my Ip at 192.168.0.4. However, I cant use the ethernet. What do I have to change, what am I doing wrong ?

---

### Post by sedawk on 2009-02-03
What is the output of "sudo ifconfig eth0"?

Is it possible that your wireless uses an IP in the same network
(e.g. 192.168.0.3). In that case it is most likely that your default
route will route all traffic via the wireless and ignore your
wired network.
In that case you have to change the default route to use eth0, not
the wireless.

---

### Post by suffer1989 on 2009-02-04
Here is the result:

```
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:99:7e:9c  
          inet addr:192.168.0.4  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 
```

so, how do i place priorityfor Wired ethernet ? Also, the IP address isnt taken. I wouldnt care what the IP address is when Im connected Via ethernet...

Any Ideas ?

---

### Post by suffer1989 on 2009-02-04
I installed WICD and everything is ok
Problem resolved...

---

### Post by tednumber8 on 2009-02-04
I can't figure out how to install WICD on Intrepid otherwise I would hvae doen it long ago.

---

