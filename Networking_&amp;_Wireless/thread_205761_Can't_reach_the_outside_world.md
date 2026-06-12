---
title: "Can't reach the outside world"
date: 2006-06-28
forum: Networking &amp; Wireless
---

### Post by skerg on 2006-06-28
I installed ubuntu on one of my machines the other day, everything went smooth, I was able to get updates from the web, I played around with some settings to let my machine have a static ip. But recently the machine can't see the outside world:

ping: unknown host [www.google.com](www.google.com)

Also if I try to ping a local machine on the network it will just hang and not give me anything back. But I'm able to ping the ubuntu machine from another on the network and it responds, I'm actually ssh'd into the machine since I don't currently have a monitor hooked up.

Here's what my /etc/network/interfaces looks like:

auto eth0
iface eth0 inet static
address 192.168.1.105
netmask 255.255.255.0
gateway 192.168.1.1

ifconfig eth0 returns:

eth0      Link encap:Ethernet  HWaddr 00:01:02:02:EF:8F
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:2ff:fe02:ef8f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3440816 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1867298 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:527940018 (503.4 MiB)  TX bytes:331296020 (315.9 MiB)
          Interrupt:3 Base address:0xef80

I'm not sure what else would be helpful to solve the problem, if anyone has some ideas let me know. Thanks.

---

### Post by falcon15500 on 2006-06-29
What's in your **/etc/resolv.conf**  ?  Try pinging an external IP address directly (rather than the host name).  

falc

---

### Post by skerg on 2006-06-29
My /etc/resolv.conf is empty, and when I ping an external ip, I get a response.

---

### Post by skerg on 2006-06-30
Is there a way to rewrite the resolv.conf file?

---

### Post by takakia on 2006-06-30
Even I am facing exactly the same problem !

---

### Post by f00buntu on 2006-06-30
[QUOTE=skerg]
iface eth0 inet static
[/QUOTE]

if you're using a static ip address you should add your dns server(s) to /etc/resolv.conf

gksudo gedit /etc/resolv.conf

you can probably use your router as a dns proxy so add the following line:

nameserver 192.168.1.1

...and save changes

if this doesn't work you can put your ISP's dns servers in your resolv.conf

---

