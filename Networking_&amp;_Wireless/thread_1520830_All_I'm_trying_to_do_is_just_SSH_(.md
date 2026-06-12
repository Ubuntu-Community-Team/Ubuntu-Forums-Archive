---
title: "All I'm trying to do is just SSH :("
date: 2010-06-30
forum: Networking &amp; Wireless
---

### Post by joebobjoe on 2010-06-30
Hello, I cannot connect to my Ubuntu Server. Currently I'm trying via my MacBook through ethernet. A physical connection is apparent; however, the computers cannot communicate.

To resolve this problem is important because I just need basic SSH functionality.

While connected through ethernet, my MacBook cannot ping my Ubuntu box.

Here is a screen shot of the Mac's network setup, a ping attempt, the ifconfig's of both machines.

[http://cl.ly/11ecb4bf7a02020222a5]("http://cl.ly/11ecb4bf7a02020222a5") (screenshot)

```
macbook:~ andrew$ ping 192.168.122.1
PING 192.168.122.1 (192.168.122.1): 56 data bytes
Request timeout for icmp_seq 0
Request timeout for icmp_seq 1
Request timeout for icmp_seq 2
Request timeout for icmp_seq 3
ping: sendto: No route to host
Request timeout for icmp_seq 4
ping: sendto: Host is down
Request timeout for icmp_seq 5
ping: sendto: Host is down
Request timeout for icmp_seq 6
^C
--- 192.168.122.1 ping statistics ---
8 packets transmitted, 0 packets received, 100.0% packet loss
macbook:~ andrew$ 

```

ifconfig on the MacBook gives me:

```
macbook:~ andrew$ ifconfig
en0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
	ether <MAC address hidden>
	inet 192.168.122.2 netmask 0xffffff00 broadcast 192.168.122.255
	media: autoselect (100baseTX <full-duplex>)
	status: active
```

ifconfig on the Ubuntu box gives me (yes, hand-copied):

```
andrew@elephant:/$ifconfig
virbr0	Lin encap:Ethernet  HWaddr <MAC address hidden>
	inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
	inet6 addr: <MAC address hidden> Scope:Link
	UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
	RX packets:0 errors:0 dropped:0 overruns:0 frame:0
	TX packets:59 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:0
	RX bytes:0 (0.0 B)  TX bytes:6813 (6.8 KB)
```

Could anyone give me some troubleshooting pointers?

---

### Post by pedro_orange on 2010-06-30
Hi.

Can you ping the Mac from the Ubuntu machine? 
Can you ping the router from either of the machines?

Do you have a firewall or something on the Ubuntu machine that may be stopping the ping? Check your iptables.

Is there anything on the router that may also do this?

Also, are you DHCP or static?

---

### Post by iponeverything on 2010-06-30
> andrew@elephant:/$ifconfig
virbr0	Lin encap:Ethernet  HWaddr <MAC address hidden>
	inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.255.0
	inet6 addr: <MAC address hidden> Scope:Link
	UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
	[COLOR="Red"]**RX packets:0**[/COLOR] errors:0 dropped:0 overruns:0 frame:0
	TX packets:59 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:0
	RX bytes:0 (0.0 B)  TX bytes:6813 (6.8 KB)

Check to make sure you don't have a bad cable and as mentioned by @pedro_orange check that you are not filtering the traffic.

This will print your packet filtering rules:
```
sudo iptables -L -n 
```

This will flush your packet filtering rules:
```
sudo iptables -F
```

---

### Post by joebobjoe on 2010-06-30
Thanks for the replies guys.

> **pedro_orange said:**
> Can you ping the Mac from the Ubuntu machine?
No.

> **pedro_orange said:**
> Can you ping the router from either of the machines?
There is only a router connected to the MacBook via wireless. The ethernet connection between the MacBook and the Ubuntu is ad-hoc.

> **pedro_orange said:**
> Do you have a firewall or something on the Ubuntu machine that may be stopping the ping? Check your iptables.
The Ubuntu Server 10.04 LTS is a fresh install, so whatever came with the system I have.

> **pedro_orange said:**
> Is there anything on the router that may also do this?
Yes, but they're not connected via a router.

> **pedro_orange said:**
> Also, are you DHCP or static?
There should be no DHCP server on either machines, which are connected directly.

> **iponeverything said:**
> Check to make sure you don't have a bad cable and as mentioned by @pedro_orange check that you are not filtering the traffic.

This will print your packet filtering rules:
```
sudo iptables -L -n 
```

This will flush your packet filtering rules:
```
sudo iptables -F
```
I flushed the rules, restarted my machine, but still cannot ping in either way. There were a couple of REJECT rules in the FORWARD chain; however, there was an encompassing ACCEPT rule before it.

This is truly a debacle, I've tried another LAN cable and I get the same result.

Also, why is my built in ethernet on the Ubuntu box virbr0 and not eth0? Could that have something to do with it?

Any advice on more troubleshooting would be great.

---

### Post by mattborn on 2010-06-30
I'm encountering similar problems.  I have a machine which has a known good router, known good cable, known good network card.  I took it offline for an OS upgrade, dropped x86-64 10.04 server on there, and the problems started.

Sometimes there are network failures when logged in locally and attempting to look out at the world.  Usually if you even look at eth0, these are resolved (sudo ifconfig eth0), and suddenly you can ping and ssh and wget.

Logging in remotely is problematic, as the machine frequently responds to pings but not to ssh.  If, however, you've recently performed an operation from a local shell which used the network, you can often log in remotely, but shortly thereafter your connection gets terminated when the networking decides to go AWOL again.

These problems didn't exist previously, when the machine was running 32 bit 9.10.  Some configuration may have changed, but I'm not sure what would cause _this_.

---

### Post by endotherm on 2010-06-30
> 
inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.255.0
it looks like your subnet masks are wrong on elephant.
one is 32bit, the other 24 (on the macbook; ffffff00 => 24bits). i think the problem is with '255.255.255.255.0'. should be "Mask:255.255.255.0". a mask of 32 bits (255.255.255.255) is basically a network with 1 host on it. or mabey it's no hosts. either way, your netmask must be less than or equal to 255.255.255.252.

---

### Post by lastavim on 2010-06-30
> **endotherm said:**
> it looks like your subnet masks are wrong on elephant.
one is 32bit, the other 24 (on the macbook; ffffff00 => 24bits). i think the problem is with '255.255.255.255.0'. should be "Mask:255.255.255.0". a mask of 32 bits (255.255.255.255) is basically a network with 1 host on it. or mabey it's no hosts. either way, your netmask must be less than or equal to 255.255.255.252.

Yes, the netmask is wrong, but I believe this could be just typing mistake in joebobjoe post... I doubt ifconfig or other tool would allow to enter invalid netmask.

What kind of network cable are you using to connect both computers? Is it cross-over?

---

### Post by joebobjoe on 2010-06-30
> **lastavim said:**
> Yes, the netmask is wrong, but I believe this could be just typing mistake in joebobjoe post... I doubt ifconfig or other tool would allow to enter invalid netmask.

What kind of network cable are you using to connect both computers? Is it cross-over?
Yes, sorry it was just a typing mistake. It has been fixed now. The cable I've been using is an ethernet cable I've used successfully to connect my router to my modem.

---

### Post by joebobjoe on 2010-06-30
> **endotherm said:**
> it looks like your subnet masks are wrong on elephant.
one is 32bit, the other 24 (on the macbook; ffffff00 => 24bits). i think the problem is with '255.255.255.255.0'. should be "Mask:255.255.255.0". a mask of 32 bits (255.255.255.255) is basically a network with 1 host on it. or mabey it's no hosts. either way, your netmask must be less than or equal to 255.255.255.252.
It was a typing mistake. Sorry.

---

### Post by joebobjoe on 2010-06-30
Hmmm. It seems as though eth0 was down. I don't think virbr0 was my ethernet connection.

When I did "ifconfig -a" I found eth0 that was unlisted with "ifconfig."

I did "ifconfig eth0 up" and edited the "/etc/network/interfaces" file and added eth0. Unfortunately, now Ubuntu load. I'm getting "init: network-interface (eth0) pre-start process (495) terminated with status 1" and four similar lines including the lo interface. Did I just mess everything up by screwing around in the "/etc/network/interfaces" file?

---

### Post by joebobjoe on 2010-06-30
Guys I've got this problem solves. Virbr0 was the wrong interface. Since network wasn't automatically installed during Ubuntu installation, Ubuntu decided not to put my eth0 interface up. Now it's up and running. Thanks for all the help!

---

