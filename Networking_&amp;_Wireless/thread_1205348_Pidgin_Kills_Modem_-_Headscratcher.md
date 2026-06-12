---
title: "Pidgin Kills Modem - Headscratcher"
date: 2009-07-05
forum: Networking &amp; Wireless
---

### Post by publicurinal598 on 2009-07-05
I simply cannot explain any rationale for this behavior, and don't know where to begin.

Problem: When running Pidgin, everything works great. However, when someone using Pidgin sends me a message (not the other way around, and not when the other person uses another client), my DSL modem crashes. All access to the internet is lost until the modem is reset.

Scenario: Currently running Ubuntu 9.04 (Jaunty). Pidgin version is 2.5.5. Connected to the DSL modem via wireless G, using WEP encryption.

Additional information: This behavior has occurred on both previous versions of Ubuntu (8.04 confirmed), and of Pidgin (dating back at least to last summer, likely longer). Problem does not occur when running Kopete. The behavior does not occur under the same scenario if Pidgin is run on Windows. Additionally, this was not an issue using a wired connection with another router/modem (have not attempted this with the present wireless).

Hardware Info: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05) -- Kernel driver in use: ipw2200.

Anybody care to toss their hat in as to possible solutions? Thanks.

---

### Post by computer13137 on 2009-07-05
I find this very unusual.  Are you sure it's stopping the modem, and not like - Ubuntu networking?

Once the Internet is disabled, try pinging the IP address of your router, or another computer on the network.  Are those able to get through?

The only reason I could see for a modem to 'lock up' with Pidgin would involve IM protocols or ports.  (Shouldn't happen at all, so this is a hypothetical diagnosis).  The fact that the problem doesn't occur with the same software on Windows on the same network leads me to believe that it's something with your Ubuntu box, and not your modem or local area network.

If you have no idea how your network is setup, paste the output of the following command so we can help you further.
```
ifconfig
```If you know the IP of your router, try running the following command after the "modem crashes".

```
ping -c 4 192.168.1.1
```Where 192.168.1.1 is the IP of your router.

You could also try pinging another system on the network.  You can get the IP of your Windows box by typing "ipconfig" into a command prompt.  Run a 'ping -c 4' to it as well for us.  (Sidenote, Windows firewall may block ICMP pings, so don't jump to any conclusions, unless the ping responds when the modem is "not crashed".)

I'd be really surprised if the modem ended up being the problem.

Cheers,
Kirk

---

### Post by publicurinal598 on 2009-07-06
I'll try and re-create the behavior next time I catch my Pidgin-using friends online. However, in the meantime, a response to a couple of your questions:

1. I'm fairly certain that it is the modem, because upon the connection dropping, all I have to do is reset the modem (not the router, so the wireless connection is not reset). Additionally, I vaguely recall the problem affecting all computers on the network.

2. As for the Windows versus Linux issue, they are being dual-booted on the same computer (so same hardware). The Windows boot does have a fairly restricted firewall rule set (although localhost and network are fully unblocked), the Ubuntu one does not.

3. My first thought was akin to yours, that Pidgin attempts to connect to other Pidgin clients differently, and that's the culprit. As to why only in Ubuntu, and why it confuses the modem, I cannot explain; and I could not find a setting resembling this.

4. Here's the result from ifconfig:

```
:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:43:70:fc:a6  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:12:f0:38:79:77  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fe38:7977/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:138987 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76036 errors:0 dropped:6 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3366139766 (3.3 GB)  TX bytes:88485302 (88.4 MB)
          Interrupt:17 Memory:dfcfd000-dfcfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2480 (2.4 KB)  TX bytes:2480 (2.4 KB)
```

I noticed a similar unresolved issue on the bottom of this thread: [http://ubuntuforums.org/archive/index.php/t-724803.html]("http://ubuntuforums.org/archive/index.php/t-724803.html") (I too have an Inspiron 6000 with the same network card). However, while his seemingly requires a router reset, mine does not. The issue has occurred on two Netgear routers (different models).

Again, I'll try and run a few more of these tests when I see the couple of Pidgin-using folks I know online. Until then, I hope this is helpful.

---

### Post by Crafty Kisses on 2009-07-06
So you say you have to restart your Modem every time this issue occurs? Does it ever reconnect to the Internet by itself? When the Internet actually goes down I want you to run a command, don't restart the modem when you run this command, leave it alone:
```
ping google.com
```
See if you get any replies from Google. You can also try once your Internet drops is to scan from the Terminal and see if anything shows up and see if you can reconnect without restarting your Modem. I'd also like to see your routing table, post the results of the following command:
```
route
```
As stated the routing table should be a little helpful for me. It also appears you're going through wireless, so if this is the case, you can also try something else. When the Internet drops, try scanning for Wireless networks and see if you can connect to them, you can do that by running:
```
iwlist scan
```
Then if you don't see anything, you can run:
```
ifconfig eth0 down
```
That will bring the interface down, you can bring it up (I'm just guessing your DHCP):
```
dhcpcd  -d -h <hostname> eth0
```
Try the things I mentioned and see if anything changes. The logs would also be helpful to post so I or somebody else can look at them and help you further in your networking problem.

---

### Post by publicurinal598 on 2009-07-07
Sorry for the late reply, computer13137 and Codename. Here are the results pre- and post-connection crashing. I also made backups of the /var/log directories pre- and post-failure, so if there are any specific logs that would be helpful, just let me know which.

That said, I noticed that if I waited it out (about 60s or so), the connection would in fact re-establish itself, so it is not necessary to restart the modem after all. I also forgot to ping the modem on the post-failure test, and the pidgin-using buddy I used to help me test it had signed off before I was able to do it again. I'm hoping having the logs will help. Without further ado:

**Pre-Failure:**

```
user@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:43:70:fc:a6  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:12:f0:38:79:77  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fe38:7977/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7163 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6729 errors:0 dropped:6 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5494325 (5.4 MB)  TX bytes:1176113 (1.1 MB)
          Interrupt:17 Base address:0xc000 Memory:dfcfd000-dfcfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)


user@ubuntu:~$ ping -c 10 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=5.09 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=1.52 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=1.48 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=64 time=0.771 ms
64 bytes from 192.168.0.1: icmp_seq=5 ttl=64 time=1.48 ms
64 bytes from 192.168.0.1: icmp_seq=6 ttl=64 time=1.52 ms
64 bytes from 192.168.0.1: icmp_seq=7 ttl=64 time=1.47 ms
64 bytes from 192.168.0.1: icmp_seq=8 ttl=64 time=1.50 ms
64 bytes from 192.168.0.1: icmp_seq=9 ttl=64 time=1.47 ms
64 bytes from 192.168.0.1: icmp_seq=10 ttl=64 time=3.90 ms

--- 192.168.0.1 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9012ms
rtt min/avg/max/mdev = 0.771/2.022/5.090/1.283 ms


user@ubuntu:~$ ping -c 10 google.com
PING google.com (74.125.45.100) 56(84) bytes of data.
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=1 ttl=53 time=55.5 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=2 ttl=53 time=55.1 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=3 ttl=53 time=55.2 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=4 ttl=53 time=54.8 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=5 ttl=53 time=54.9 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=6 ttl=53 time=54.4 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=7 ttl=53 time=54.7 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=8 ttl=53 time=55.9 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=9 ttl=53 time=54.1 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=10 ttl=53 time=54.5 ms

--- google.com ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9013ms
rtt min/avg/max/mdev = 54.186/54.982/55.999/0.506 ms


user@ubuntu:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     2      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth1
user@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:14:D1:5B:35:AD
                    ESSID:"SAMBA"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=76/100  Signal level=-52 dBm  
                    Extra: Last beacon: 4832ms ago
```

**Post-Connection Failure**
```
user@ubuntu:~$ ping -c 10 google.com
ping: unknown host google.com

user@ubuntu:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     2      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth1

user@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:14:D1:5B:35:AD
                    ESSID:"SAMBA"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=75/100  Signal level=-54 dBm  
                    Extra: Last beacon: 1784ms ago
```

Let me know how I can be of further help.

---

### Post by publicurinal598 on 2009-07-12
Bumpity bump?

---

### Post by publicurinal598 on 2009-07-20
Another attempt at revival?

---

