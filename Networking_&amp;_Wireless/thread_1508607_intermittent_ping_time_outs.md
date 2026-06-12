---
title: "intermittent ping time outs"
date: 2010-06-13
forum: Networking &amp; Wireless
---

### Post by equick on 2010-06-13
Hi,

I am running a Lucid Ubuntu Server at home connected by wire to my router/modem. I usually ssh to the server from my laptop (wirelessly), but recently the connection stopped working. 

I tried pinging the server (192.168.0.20) but as you can see below most of these pings time out. I tried changing the network cable to my server but it made no difference, so I'm sure it's not that. If I connect my laptop to the server with a cable, I can reach it, and get through to the Internet.

I'm not really sure why this has started happening, possibly one of the automatic updates from ubuntu. Could you give me some tips on what to check please?

Thanks,

Ed.


Request timed out.
Request timed out.
Request timed out.
Reply from 192.168.0.20: bytes=32 time=52ms TTL=64
Request timed out.
Reply from 192.168.0.20: bytes=32 time=2ms TTL=64
Request timed out.
Request timed out.
Reply from 192.168.0.20: bytes=32 time=1ms TTL=64
Request timed out.
Request timed out.
Request timed out.
Request timed out.

---

### Post by equick on 2010-06-13
A bit more info on my set up. Still stuck on this.

ed@ubuntu:~$ uname -a
Linux ubuntu 2.6.32-22-server #36-Ubuntu SMP Thu Jun 3 20:38:33 UTC 2010 x86_64 GNU/Linux

ed@ubuntu:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"

ed@ubuntu:~$ ifconfig
br0       Link encap:Ethernet  HWaddr 00:1d:7d:03:4c:f5
          inet addr:192.168.0.20  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:7dff:fe03:4cf5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12602 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1170319 (1.1 MB)  TX bytes:598894 (598.8 KB)

eth0      Link encap:Ethernet  HWaddr 00:1d:7d:03:4c:f5
          inet6 addr: fe80::21d:7dff:fe03:4cf5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:730 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:781970 (781.9 KB)  TX bytes:181875 (181.8 KB)
          Interrupt:28 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4475 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4475 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:924686 (924.6 KB)  TX bytes:924686 (924.6 KB)

virbr0    Link encap:Ethernet  HWaddr 7a:cf:9a:9e:80:53
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::78cf:9aff:fe9e:8053/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:4871 (4.8 KB)

vnet0     Link encap:Ethernet  HWaddr 76:f9:bb:83:7e:ff
          inet6 addr: fe80::74f9:bbff:fe83:7eff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22309 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36783 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:6317742 (6.3 MB)  TX bytes:5682944 (5.6 MB)

vnet1     Link encap:Ethernet  HWaddr 4e:4d:96:2e:2e:3d
          inet6 addr: fe80::4c4d:96ff:fe2e:2e3d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1793 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7719 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:192445 (192.4 KB)  TX bytes:943086 (943.0 KB)

vnet2     Link encap:Ethernet  HWaddr 76:ae:47:e5:06:bf
          inet6 addr: fe80::74ae:47ff:fee5:6bf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39156 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33612 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:5698650 (5.6 MB)  TX bytes:7688008 (7.6 MB)


ed@ubuntu:~$ sudo iptables -L -n
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
        address 192.168.0.20
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        dns-nameservers 192.168.0.1
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

---

### Post by equick on 2010-06-13
ed@ubuntu:~$ brctl show
bridge name     bridge id               STP enabled     interfaces
br0             8000.001d7d034cf5       no              eth0
                                                        vnet0
                                                        vnet1
                                                        vnet2
virbr0          8000.000000000000       yes

---

### Post by bigmojo74 on 2010-06-13
To ask, you say your only having trouble connecting with your laptop when you're using wireless. When you say you connect to the server via ethernet, are you plugging directly into it - or plugging the laptop into the router via ethernet? Reason I ask is it doesn't seem like it'd necessarily be your server having trouble, if it's reachable over the wired of the network, it sounds more like an issue with your wireless connection.

Old fall back from my ISP days, have you tried power cycling your network equipment?

---

### Post by equick on 2010-06-14
Thanks for your reply.
I have to plug my laptop directly into the ethernet port on my server to connect to it. Also if I check the attached devices on my router, I can't see the server listed there. I have tried cycling the router but to no avail.

---

### Post by tarsius4 on 2010-06-14
Hi,

I'm having a related problem, but it seems slightly different.  I have a desktop and a netbook that both connect to the Internet via wifi.  Both are configured with static IP addresses outside the range controlled by the DHCP server on the router.  At any given time, if I power them both on, I can easily ping, ssh, and rsync between them. However, generally after they've been on for a while (possibly over a period of days, during which they suspended several times), one or both of the machines "loses" the ability to communicate with the other.

Once a machine ("A") loses contact with the other ("B"), I can no longer ping, ssh, or rsync from machine A to the machine B, but often I am able to communicate from B to A.  Usually resetting solves this problem, but it has become very irritating over the past few months and I'd like to solve it once and for all. My problem differs from equick's problem because my pings are not intermittent... either the connection is made and all pings succeed or the connection is broken and all pings fail.

Also note that I can ALWAYS ping my router from each machine, and my current router has a feature that allows me to initiate pings and these pings ALWAYS succeed. I recently got a new router and this problem existed under BOTH routers. I have tried to disable and reconnect the wlan device on both machines to no avail--the only "solution" is a reboot.

I think this must be an individual configuration problem to each computer. I suspect that, after the "disconnection" occurs, packets that are addressed within my LAN (192.168.1.*) never actually leave the affected machine.

Hope we can help solve each others' problem,
Steve

---

### Post by bigmojo74 on 2010-06-14
tarsius - you could probably get away with just bouncing the interface(s) when they stop communicating:
sudo ifdown eth0 - interface down
sudo ifup eth0 - interface up

equick - I'm no guru, but I don't see anything wrong with the config or that jumps out to me in the scenario. I'd think perhaps it was a bad port on the network device but you say you can get to the internet fine from the server itself? If it only has one NIC a bad port would affect getting out from the server itself too, if you ping an external host (i.e. google.com) do you see the same packet loss? What about when the laptop is connected wirelessly, can it ping other hosts without seeing that kind of loss?

---

### Post by tarsius4 on 2010-06-19
Thanks for the response bigmojo. I actually wasn't able to do what you suggested because my USB wifi dongle isn't listed as a device in /etc/network/interfaces. However, I did "solve" my problem...

My particular wifi router supports broadcasting multiple SSIDs with different encryption settings, so I setup an additional "network" with AES instead of TKIP encryption. However, I think the real catalyst was connecting to a new network without an existing profile in nm-applet. My original connection was configured with static IPs and DNS through Google DNS. This time, I simply connected both computers to the new network and logged in with the proper key.  Everything just worked.

I'll have to go back and experiment with deleting my old network's profile and logging in from scratch to see if my computers can ping one another.

Thanks again,
Steve

---

### Post by equick on 2010-07-17
This turned out to be a problem with my router, not my ubuntu system. I switched back to my router and everything worked fine.

---

### Post by webwolf_3000 on 2010-09-08
seems to be a bug in the WiFi drivers, I reboot Ubuntu server 10 and I can ping everything on my network and the internet. after a minute or so, it all craps out.

I don't have to touch anything, it just stops pinging, Seems to have been an issues since somewhere around Ubuntu 8, I'm sure my Ubuntu server pre v8 was really stable and a lot faster when using SSH.

I'm thinking about giving up on this one, exactly the same setup worked fine for years without ever a hickup, seems to get worse with every new distro though. the last distro worked but it was a lot slower than the previous on SSH.

I'd use ethernet, but Vista/7's network stack doesn't play nice with the NIC on my old server, mapped drives time out, whereas a nice shiny new PCMCIA WiFi card has a nice stable connection on mapped drives ( or it did... )

---

### Post by ffxx68 on 2011-10-19
Hi all. 

I'm also experiencing a similar problem, altough within a different setup. I'm trying to ping from my laptop an Android tablet over a WiFi local network. Yes, I know Android is not Ubuntu, but it still has a Linux kernel (2.6.29) and the network layer is very similar to any other Linux. Sorry if it's a bit off-topic, but I hope you understand, as I'm desperately looking for hints...

 This is a typical ping session, from laptop to tablet:

```
> ping  -n 100 192.168.0.100

Pinging 192.168.0.100 with 32 bytes of  data:
Reply from 192.168.0.101: Destination host unreachable.
Reply  from 192.168.0.101: Destination host unreachable.
Reply from  192.168.0.101: Destination host unreachable.
Reply from  192.168.0.101: Destination host unreachable.

<<  WiFi  Deactivated and re-activated on tablet >>

Reply from  192.168.0.100: bytes=32 time=2015ms TTL=64
Reply from 192.168.0.100:  bytes=32 time=8ms TTL=64
Reply from 192.168.0.100: bytes=32 time=7ms  TTL=64
Request timed out.
Request timed out.
Request timed out.
Request  timed out.
Request timed out.
Reply from 192.168.0.100: bytes=32  time=7ms TTL=64
Reply from 192.168.0.100: bytes=32 time=5ms TTL=64
Reply  from 192.168.0.100: bytes=32 time=3ms TTL=64
Request timed out.
Request  timed out.
Request timed out.
Request timed out.
Request timed  out.
Request timed out.
Request timed out.
Request timed out.
Request  timed out.
Reply from 192.168.0.100: bytes=32 time=7ms TTL=64
Request  timed out.
Reply from 192.168.0.100: bytes=32 time=8ms TTL=64
Request  timed out.
Request timed out.
Reply from 192.168.0.100: bytes=32  time=7ms TTL=64
Reply from 192.168.0.100: bytes=32 time=6ms TTL=64
Request  timed out.
Request timed out.
Reply from 192.168.0.100: bytes=32  time=13ms TTL=64
Reply from 192.168.0.100: bytes=32 time=11ms TTL=64
Request  timed out.
Request timed out.
Request timed out.
Request timed  out.
...
```Looks like the ping service is kept active for  just a few seconds after I cycle WiFi on the tablet (from the system  settings), then it becomes very unstable.

Note how the tablet on  the other hand is perfectly logged onto the WiFi net and I can use it  without issues to browse the Internet, for example. The tablet is the  only device showing this problem in my home net. I can have another PC  and a netbook in the same net and they don't suffer any such trouble.  Already checked for duplicate IP addresses.

But it isn't only  ping. If I try to use a SSH deamon app (QuickSSHd) it starts  successfully, but I can't connect a terminal client from my PC.

At  least, I can't anymore... It used to work, just once (I own the tablet  only since a few days), until (I think) I installed the "Cisco  AnyConnect Rooted" VPN app. That's the only operation I have done on the  tablet, before I had this issue. Cisco AnyConnect installed sucesfully a  but it never succeeded to start, because it required root privileges  (which I haven't given to the tablet yet). Well, infact, as I received the device just a week a go I had a  chance to  test ping or SSHd just once before, so I suspect the issue  has always been there. The issue is still  there even after un-installing Cisco VPN. Of course I will post this same request  for  help on a Cisco, and tablet-expert forums as well, but how does it  come that installing an app may have changed system services, without a  root  access?

Tablet is still with its factory  firmware. As a reference, these are the firmware details:

Android: 2.2.1
Baseband: BD_P678A1V1.0.2B09
Kernel:  2.6.29 hengai@and-ser2#11020
Build: renesas_emev-eng 2.2.1 MASTER  eng.hengai.20110729.172420 test-keys

(my tablet is a Renesas  dual-core A9, with 3G; but I'm not using 3G...)

Even if I get root access to the tablet, what else  should I collect to debug this issue? 

Any help, suggestion, clue, hint  welcome ! Thanks

---

