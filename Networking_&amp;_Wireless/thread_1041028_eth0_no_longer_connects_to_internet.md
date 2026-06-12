---
title: "eth0 no longer connects to internet"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by jpaugh64 on 2009-01-16
Hello. I have Ubuntu 8.10 amd64 installed on my laptop. I connect to the internet via a proxy server. My ethernet connection used to work, but now I can only connect to localhost when I boot up from my hard disk; however when I use the live cd, and set up the proxy, everything works fine. 
   I suspect that some package went haywire while being installed, but I don't think my last installs were related to networking. I have run some Windows applications (using Wine) that may have tried to use the network.
   I just looked at another thread and tried one fix (haven't rebooted yet): adding "auto eth0" to /etc/network. I hope that works, but I don't think it will. Ubuntu recognizes the connection "auto eth0" and says it's connected, but it doesn't work.

Any help is appreciated :p. I'm comfortable with the terminal, I just don't know many commands yet; I'm a semi-noob.

---

### Post by stefangr1 on 2009-01-16
Can you post the output of ifconfig?

You connect trough a proxyserver using the firefox options?

---

### Post by jpaugh64 on 2009-01-16
I leave firefox set to "Use system settings" and then use System-->Preferences-->Network Proxy to change the proxy. I set it to use the http:// proxy for all protocols, and it worked before. One moment while I reboot to run ifconfig from the installed system. Here's the ouput from the live system to compare. If I recall correctly, these are identical.

```

jpaugh64@live-cd:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:1e:33:61:b5:3c  
          inet addr:10.26.0.210  Bcast:10.26.7.255  Mask:255.255.248.0
          inet6 addr: fe80::21e:33ff:fe61:b53c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17222 errors:0 dropped:8752689206 overruns:0 frame:0
          TX packets:8501 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10657987 (10.6 MB)  TX bytes:1702365 (1.7 MB)
          Interrupt:252 Base address:0x2000 

```

<edit>
and here's the output from the installed system:
```

jpaugh64@brokenSystem:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:1e:33:61:b5:3c  
          inet addr:10.26.0.210  Bcast:10.26.7.255  Mask:255.255.248.0
          inet6 addr: fe80::21e:33ff:fe61:b53c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:198 errors:0 dropped:10809766534 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18490 (18.4 KB)  TX bytes:1152 (1.1 KB)
          Interrupt:252 

```
The fix I tried before in /etc/network didn't work, either.

---

### Post by superprash2003 on 2009-01-16
are you able to ping your router or other machines?

---

### Post by Dennis Schulmeister on 2009-01-16
Hi,

imho this is a serious bug because since yesterday I get the very same behaviour. (After installing updates) DHCP works fine but otherwise you can't send packages through the network interface. DNS-lookups fail and pinging the router says:

> sendmsg: Operation not permitted

There's a [bug rebort on launchpad.net]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/315370") on this topic. But it seems like Canonical is not much of a help there. :(

Best, Dennis

---

### Post by jpaugh64 on 2009-01-16
I cannot ping anything other than localhost. As a matter of fact, this occurred soon after installing updates. It would be REALLY nice to figure out which package was causing all of this trouble. I don't know enough about package managers or linux to know, but I would guess that the problem is simply an altered configuration file.

---

### Post by Dennis Schulmeister on 2009-01-16
Hi,

now I got the very same problem on the 3rd installation in a row. But at least I was able to find a fix. Please try the following:

```
cd /etc/init.d
sudo ./ipmasq stop
ping ubuntu.com
```

Some package must have pulled in ipmasq. But the ipmasq description says that you need it on firewalls exclusively not on regular clients like your all-day computer. So it should be safe to remove it

```
sudo apt-get remove ipmasq
```

HTH,
Dennis

---

### Post by jpaugh64 on 2009-01-16
Thanks, Dennis, I'll try that in a few minutes. Here's to hoping.

---

### Post by jpaugh64 on 2009-01-16
Wonderful! It worked. Than you Dennis, and all who replied. :D

I had no /etc/init.d/ directory, however, so I first had to run this
```

jpaugh64@brokenSystem:~$ whereis ipmasq

```to find its directory listing. It was actually listed in three places: 
/usr/sbin/ipmasq 
/etc/ipmasq 
/usr/share/ipmasq

So I just cded to one of the directories and stopped the service. Voila!
```

jpaugh64@brokenSystem:~$ cd /etc
jpaugh64@brokenSystem:/etc$ sudo ipmasq stop
[sudo] password for jpaugh64: 
jpaugh64@brokenNoMore!!:/etc$ ping www.ubuntu.com
PING www.ubuntu.com (91.189.94.8) 56(84) bytes of data.
64 bytes from jujube.canonical.com (91.189.94.8): icmp_seq=1 ttl=42 time=115 ms
...
^C
--- www.ubuntu.com ping statistics ---
8 packets transmitted, 8 received, 0% packet loss, time 7033ms
rtt min/avg/max/mdev = 112.269/113.983/117.527/1.712 ms

```

EDIT: Thank you SO much for helping me take yet another step from Windows to Linux. Hopefully soon I'll be able to give back to this community.

---

