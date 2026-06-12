---
title: "Ping not working in the terminal"
date: 2012-03-06
forum: Networking &amp; Wireless
---

### Post by beto1211 on 2012-03-06
Hello friends, I need help

After changing the network configuration via "network connections" in the graphics mode from "manual" to "DHCP", my terminal, and the update manager, Synaptic package manager and FTP client, stopped from accessing Internet. All other programs (browsers, mainly), continue with normal access to the internet.

I tried to return to the IP configuration to "Manual", filling all the fields in the chart in the graphics mode, but the problem continued. The following is some information that may help to dispel doubts:

[B]When I ping to an address type [www.google.com.br](www.google.com.br), returns the message:
[/B]ping: unknown host [www.google.com.br](www.google.com.br)

[B]When I ping an IP address (64.233.161.13 ping), it appears:
[/B]PING 64.233.161.13 (64.233.161.13) 56 (84) bytes of data.
From 192.168.0.214 icmp_seq = 1 Destination Host Unreachable
From 192.168.0.214 icmp_seq = 2 Destination Host Unreachable
From 192.168.0.214 icmp_seq = 3 Destination Host Unreachable
From 192.168.0.214 icmp_seq = 4 Destination Host Unreachable
From 192.168.0.214 icmp_seq = 5 Destination Host Unreachable
From 192.168.0.214 icmp_seq = 6 Destination Host Unreachable
From 192.168.0.214 icmp_seq = 7 Destination Host Unreachable
From 192.168.0.214 icmp_seq = 8 Destination Host Unreachable
From 192.168.0.214 icmp_seq = 9 Destination Host Unreachable


[B]Below are some machine settings
[/B]
[B] ifconfig
[/ B]
eth0 Link encap: Ethernet HWaddr 00:1 e: c9: 1e: 65: ad
          inet end.: 192.168.0.214 Bcast: 192.168.0.255 Mask: 255.255.255.0
          inet6 addr: fe80 :: 21e: c9ff: fe1e: 65ad/64 Scope: Link
          UP BROADCAST RUNNING MULTICAST MTU: 1500 Metric: 1
          RX packets: 9886 errors: 0 dropped: 0 overruns: 0 frame: 0
          TX packets: 6229 errors: 0 dropped: 0 overruns: 0 carrier: 0
          collisions: 0 txqueuelen: 1000
          RX bytes: 5180372 (5.1 MB) TX bytes: 1487544 (1.4 MB)
          IRQ: 16

lo Link encap: Local Loopback
          inet end.: 127.0.0.1 Mask: 255.0.0.0
          inet6 addr ::: 1/128 Scope: Machine
          UP LOOPBACK RUNNING MTU: 16436 Metric: 1
          RX packets: 9482 errors: 0 dropped: 0 overruns: 0 frame: 0
          TX packets: 9482 errors: 0 dropped: 0 overruns: 0 carrier: 0
          collisions: txqueuelen 0: 0
          RX bytes: 749536 (749.5 KB) TX bytes: 749536 (749.5 KB)


[B] / etc / hosts file
[/ B] 192.168.0.214 roberto.roberto roberto

# The Following lines are desirable for IPv6 capable hosts
Localhost :: 1 ip6-localhost ip6-loopback
FE00 :: 0 ip6-localnet
FF00 :: 0 ip6-mcastprefix
ff02 :: 1 ip6-allnodes
ff02 :: 2 ip6-allrouters
ff02 :: 3 ip6-allhosts

[B] / etc / networks / interfaces file
[/ B]
auto eth0

Self it
inet loopback iface it

iface eth0 inet static
address 192.168.0.214
netmask 255.255.255.0
network 192.168.0.0
gateway 192.168.0.1

[B] The resolv.conf file is empty
[/ B]

Please help me

---

### Post by sanderj on 2012-03-06
post the output of:

```

ip route show

mtr -c4 -r -n 8.8.8.8

```

---

### Post by beto1211 on 2012-03-06
Hi, here it goes


ip route show:
192.168.0.0/24 dev eth0  proto kernel  scope link  src 192.168.0.214 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.168.0.1 dev eth0  metric 100 

mtr -c4 -r -n 8.8.8.8:
HOST: roberto                     Loss%   Snt   Last   Avg  Best  Wrst StDev

**********

Thanks in advance for your help

---

### Post by sanderj on 2012-03-06
> **beto1211 said:**
> Hi, here it goes


ip route show:
192.168.0.0/24 dev eth0  proto kernel  scope link  src 192.168.0.214 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.168.0.1 dev eth0  metric 100 

mtr -c4 -r -n 8.8.8.8:
HOST: roberto                     Loss%   Snt   Last   Avg  Best  Wrst StDev

**********

Thanks in advance for your help

Can you "ping 192.168.0.1" ?

---

### Post by beto1211 on 2012-03-06
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.214 icmp_seq=1 Destination Host Unreachable
From 192.168.0.214 icmp_seq=2 Destination Host Unreachable
From 192.168.0.214 icmp_seq=3 Destination Host Unreachable
From 192.168.0.214 icmp_seq=4 Destination Host Unreachable
From 192.168.0.214 icmp_seq=5 Destination Host Unreachable
From 192.168.0.214 icmp_seq=6 Destination Host Unreachable

---

### Post by sanderj on 2012-03-06
And all this time your webbrowser is still reaching Internet?

If so, I can think of two causes:
- a firewall on your Linux system or on your LAN blocking ping, but not web-traffic. A way to check that: "wget www.google.com"
- your webbrowser is using a proxy. You can check that in the browser settings

If the above does not reveal the cause, I would boot from a Ubuntu live CD and see what works: web, ping, etc.

---

### Post by beto1211 on 2012-03-06
You are right


-the first check returned this:
roberto @ roberto: ~ $ wget [www.google.com](www.google.com)
- 06/03/2012 14:27:08 - [http://www.google.com/](http://www.google.com/)
Connecting to 192.168.0.2:3128 ... connected.
The Proxy request was sent, awaiting response ... 302 Moved Temporarily
Location: [http://www.google.com.br/](http://www.google.com.br/) [redirecting]
- 06/03/2012 14:27:08 - [http://www.google.com.br/](http://www.google.com.br/)
Connecting to 192.168.0.2:3128 ... connected.
The Proxy request was sent, awaiting response ... 200 OK
Size: unspecified [text / html]
Saving to: "index.html"

     [<=>] 11,710 -.-K / s in 0s
2012-03-06 14:27:08 (349 MB/s) - “index.html” salvo [11710]


-My web browser, indeed, uses a proxy: 192.168.0.2 port:3128

---

### Post by beto1211 on 2012-03-06
After your warning, I managed to make ftp work, as well as the synaptic package manager. I configured the proxy (192.168.0.2) and port 3128 and it worked (the same configuration that was in the browser). And now I can make apt-get in terminal.

The only thing that still does not work is the ping: (

Anyway, thanks a lot for your help!

---

### Post by gradinaruvasile on 2012-03-06
Your http proxy prevents other protocols and certain applications from working. You dont need that on your home computer only if you want to control your traffic for some reason.

You can put 

nameserver 8.8.8.8

in your resolv.conf.

---

### Post by beto1211 on 2012-03-06
But that's is my work PC, from the company I work. It's necessary to use proxy to access the internet ;)

---

### Post by sanderj on 2012-03-06
> **beto1211 said:**
> But that's is my work PC, from the company I work. It's necessary to use proxy to access the internet ;)

It would have helped if you had said that in your post; a corporate network with a proxy is quite something else than a home network.

Anyway: you could try to ping the proxy, thus 192.168.0.2

BTW: does your company provide Ubuntu systems, or is this your personal system?
And: did you configure the proxy setting on your Ubuntu system yourself, or did it happen automagically?

---

### Post by beto1211 on 2012-03-07
I forgot to mention that it was a computer on a corporate network. Sorry.

Ping at proxy:

PING 192.168.0.2 (192.168.0.2) 56 (84) bytes of data.
64 bytes from 192.168.0.2: icmp_req = 1 ttl = 64 time = 0243 ms
64 bytes from 192.168.0.2: icmp_req = 2 ttl = 64 time = 0216 ms
64 bytes from 192.168.0.2: icmp_req = 3 ttl = 64 time = 0196 ms
64 bytes from 192.168.0.2: icmp_req = 4 ttl = 64 time = 0236 ms
C ^
--- 192.168.0.2 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min / avg / max / mdev = 0.196/0.222/0.243/0.025 ms

Not all computers in my company use ubuntu. Only me and a few more, because I asked. The other option was the Win XP, that I had enough.

The proxy confuguration proxy on my machine (the proxy settings of the network) was made by my company's technical support. Currently, we are without a support person, so I am trying to solve the problem myself.

---

