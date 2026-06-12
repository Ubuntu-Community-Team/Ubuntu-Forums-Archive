---
title: "What applications are connecting to the network?"
date: 2009-06-12
forum: Networking &amp; Wireless
---

### Post by jjalocha on 2009-06-12
I would like to know what application(s) is/are using my network interface (desktop PC, eth0).

I installed the XFCE Network Monitor applet yesterday, and it displays constant network activity, even when I shut down all obvious network applications. I never saw that behaviour on previous installations (on the same and different computers).

So I would like to know how to discover what applications are accessing the network. I have been reading about network monitoring/analyzing tools, but I got completely lost. All these tools seem to be for monitoring large networks, and bandwith usage... I have no idea, if I need packet sniffing or not...

I was simply thinking about something like top. I found atop, but I this requires me to patch the kernel!

Does anyone know of a simple tool that shows the network use on one single computer?

BTW: I installed/configured conky, but that doesn't seem to do the job, either.

---

### Post by puppywhacker on 2009-06-12
my favorite troubleshooting tools/commands are:

wireshark will look at the traffic on the network, netstat will show the established connections, lsof will show which programs are listening to ports and which pid's are using which ports.

```
wireshark
netstat -na
lsof i:22
lsof p:1234

```

---

### Post by jjalocha on 2009-06-13
Thank you very much, puppywhacker, with the help of lsof, I disabled network-manager (which brought down wpa_supplicant also), and avahi-daemon. I am running on a slow stand-alone desktop PC, so I don't need these.

But all this incoming traffic is still there, and I don't understand what it is doing.

---

### Post by puppywhacker on 2009-06-13
then tcpdump can give you a hint on which port the incoming traffic is directed to. for instance my trace below shows ssh traffic between the remote and the local computer

```
tcpdump -i eth0
19:46:09.259376 IP remote.host.com.59395 > closeby.host.com.ssh:

```

wireshark can graphically show you through the traces, and I know it isn't really a point and click type of application, but experts like it

---

### Post by jjalocha on 2009-06-13
I am literally flooded here:
```
$ sudo tcpdump -i eth0
13:53:54.410337 IP pc-166-230-241-201.cm.vtr.net.59719 > resolver01.vtr.net.domain: 61393+ PTR? 99.199.161.190.in-addr.arpa. (45)
13:53:54.426432 arp who-has pc-220-75-120-200.cm.vtr.net tell pc-1-75-120-200.cm.vtr.net
13:53:54.431311 IP resolver01.vtr.net.domain > pc-166-230-241-201.cm.vtr.net.59719: 61393 1/3/2 (176)
13:53:54.443964 arp who-has pc-189-231-241-201.cm.vtr.net tell pc-1-231-241-201.cm.vtr.net
13:53:54.446426 arp who-has pc-240-199-161-190.cm.vtr.net tell pc-1-196-161-190.cm.vtr.net
13:53:54.464982 arp who-has pc-67-30-120-200.cm.vtr.net tell pc-1-30-120-200.cm.vtr.net
13:53:54.465269 IP pc-166-230-241-201.cm.vtr.net.34737 > resolver01.vtr.net.domain: 58340+ PTR? 67.30.120.200.in-addr.arpa. (44)
13:53:54.476395 IP resolver01.vtr.net.domain > pc-166-230-241-201.cm.vtr.net.34737: 58340 1/3/2 (174)
13:53:54.502246 arp who-has pc-159-8-163-190.cm.vtr.net tell pc-1-8-163-190.cm.vtr.net
13:53:54.534606 arp who-has pc-47-9-163-190.cm.vtr.net tell pc-1-8-163-190.cm.vtr.net
13:53:54.534920 IP pc-166-230-241-201.cm.vtr.net.44485 > resolver01.vtr.net.domain: 22625+ PTR? 47.9.163.190.in-addr.arpa. (43)
13:53:54.545103 arp who-has pc-64-9-163-190.cm.vtr.net tell pc-1-8-163-190.cm.vtr.net
13:53:54.547098 IP resolver01.vtr.net.domain > pc-166-230-241-201.cm.vtr.net.44485: 22625 1/3/2 (172)
13:53:54.581691 arp who-has pc-196-41-120-200.cm.vtr.net tell pc-1-40-120-200.cm.vtr.net
13:53:54.602227 arp who-has pc-137-11-163-190.cm.vtr.net tell pc-1-8-163-190.cm.vtr.net
13:53:54.602408 arp who-has pc-119-75-120-200.cm.vtr.net tell pc-1-75-120-200.cm.vtr.net
13:53:54.611221 arp who-has pc-87-75-120-200.cm.vtr.net tell pc-1-75-120-200.cm.vtr.net
13:53:54.611400 arp who-has pc-25-2-163-190.cm.vtr.net tell pc-1-0-163-190.cm.vtr.net
13:53:54.611539 IP pc-166-230-241-201.cm.vtr.net.33533 > resolver01.vtr.net.domain: 12533+ PTR? 87.75.120.200.in-addr.arpa. (44)
13:53:54.619750 arp who-has pc-52-5-163-190.cm.vtr.net tell pc-1-4-163-190.cm.vtr.net
13:53:54.623613 IP resolver01.vtr.net.domain > pc-166-230-241-201.cm.vtr.net.33533: 12533 1/3/2 (174)
13:53:54.624196 arp who-has pc-80-75-120-200.cm.vtr.net tell pc-1-75-120-200.cm.vtr.net
13:53:54.625182 arp who-has pc-247-1-163-190.cm.vtr.net tell pc-1-0-163-190.cm.vtr.net
13:53:54.637792 arp who-has pc-50-9-163-190.cm.vtr.net tell pc-1-8-163-190.cm.vtr.net

```

VTR is our internet provider here...

---

### Post by Brandon Williams on 2009-06-13
arp stands for Address Resolution Protocol. Those packets are from machines on your local network segment trying to find the ethernet addresses for other machines on your local network segment.

All the other packets are reverse DNS lookups, probably as a result of tcpdump itself performing reverse DNS lookups so that it can show you hostnames. If you run tcpdump with the -n flag, those will go away and you'll only see the arp requests.

---

### Post by puppywhacker on 2009-06-14
your provider is broadcasting arp requests to you which shouldn't have been reaching you. broadcasting from one customer shouldn't reach the others. send a complaint to your provider if it persists

---

### Post by jjalocha on 2009-06-14
Thank you very much for the clear description. I'll contact them.

---

