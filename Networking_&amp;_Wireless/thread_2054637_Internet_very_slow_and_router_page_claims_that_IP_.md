---
title: "Internet very slow and router page claims that IP is non-DHCP"
date: 2012-09-07
forum: Networking &amp; Wireless
---

### Post by Mahkoe on 2012-09-07
Before starting, I'd like to mention that I know *nothing* about networking.

I have recently upgraded to 12.04 and I really really like it. But there's one problem that I can't explain: the internet is unfathomably slow. I know it's not a problem with my ISP or my router because in Windoze it works fine, and it worked fine back when I had 10.10. I have already tried disabling ipv6 with no discernible results. Does anyone know what the problem is?

_Extra information:_

Here's the output from a ping command:
```
mahkoe@Terminator:~$ ping -c 3 xkcd.com
PING xkcd.com (107.6.106.82) 56(84) bytes of data.
64 bytes from 107.6.106.82: icmp_req=1 ttl=53 time=7372 ms
64 bytes from 107.6.106.82: icmp_req=2 ttl=53 time=8188 ms
64 bytes from 107.6.106.82: icmp_req=3 ttl=53 time=8017 ms

--- xkcd.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 7372.157/7859.308/8188.450/351.481 ms, pipe 3
```

I recently went on my router page to see if there were any outstanding errors and here are two things I've read that may or may not be the cause of this unfortunate problem:
1: It seems my laptop is connected to the router with a non-DHCP IP (whatever that means)
2: I have no idea what this is supposed to mean, but here's a copy paste from the router log:
```
Time:07/03/12 23:04:37, Level:critical, Content:SYNC Timing Synchronization failure - Failed to acquire QAM/QPSK symbol timing
Time:07/03/12 23:09:19, Level:critical, Content:No Ranging Response received - T3 time-out
Time:07/03/12 23:09:58, Level:critical, Content:SYNC Timing Synchronization failure - Failed to acquire QAM/QPSK symbol timing
Time:07/03/12 23:12:24, Level:critical, Content:No Ranging Response received - T3 time-out
Time:07/03/12 23:13:07, Level:critical, Content:SYNC Timing Synchronization failure - Failed to acquire QAM/QPSK symbol timing
Time:07/03/12 23:14:40, Level:critical, Content:No Ranging Response received - T3 time-out
Time:07/03/12 23:15:15, Level:critical, Content:SYNC Timing Synchronization failure - Failed to acquire QAM/QPSK symbol timing
Time:07/03/12 23:25:36, Level:critical, Content:No Ranging Response received - T3 time-out
Time:07/03/12 23:25:48, Level:critical, Content:Started Unicast Maintenance Ranging - No Response received - T3 time-out
Time:07/04/12 13:21:40, Level:critical, Content:Received Response to Broadcast Maintenance Request, but no Unicast Maintenance opportunities received - T4 timeout
Time:07/04/12 13:23:43, Level:critical, Content:No Ranging Response received - T3 time-out
Time:07/14/12 03:16:32, Level:critical, Content:Unicast Ranging Received Abort Response - Re-initializing MAC
Time:07/14/12 03:16:51, Level:critical, Content:No Ranging Response received - T3 time-out
Time:07/14/12 03:17:10, Level:critical, Content:UCD invalid or channel unusable
Time:07/14/12 03:17:25, Level:critical, Content:No Ranging Response received - T3 time-out
Time:07/14/12 03:18:17, Level:critical, Content:Started Unicast Maintenance Ranging - No Response received - T3 time-out
Time:08/04/12 21:12:46, Level:critical, Content:No Ranging Response received - T3 time-out
Time:08/09/12 07:05:16, Level:critical, Content:Received Response to Broadcast Maintenance Request, but no Unicast Maintenance opportunities received - T4 timeout
Time:08/29/12 01:33:45, Level:critical, Content:No Ranging Response received - T3 time-out
Time:09/06/12 20:47:16, Level:warning, Content:DHCP WARNING - Non-critical field invalid in response

```

---

### Post by troffasky on 2012-09-08
What's the output of 'ip route' and 'ip addr'? 

Can you provide the output of a ping to the IP listed on the line that starts "default via ..."?

---

### Post by Mahkoe on 2012-09-08
Certainly.
ip route:
```
mahkoe@Terminator:~$ ip route
default via 192.168.0.1 dev wlan0  proto static 
169.254.0.0/16 dev wlan0  scope link  metric 1000 
192.168.0.0/24 dev wlan0  proto kernel  scope link  src 192.168.0.177  metric 2 
```
ip addr:
```

mahkoe@Terminator:~$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN qlen 1000
    link/ether 88:ae:1d:90:c1:87 brd ff:ff:ff:ff:ff:ff
3: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP qlen 1000
    link/ether 18:f4:6a:1a:ae:5d brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.177/24 brd 192.168.0.255 scope global wlan0

```
ping -c 3 192.168.0.1
```
mahkoe@Terminator:~$ ping -c 3 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_req=1 ttl=64 time=4.46 ms
64 bytes from 192.168.0.1: icmp_req=2 ttl=64 time=2.38 ms
64 bytes from 192.168.0.1: icmp_req=3 ttl=64 time=2.37 ms

--- 192.168.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 2.373/3.072/4.465/0.986 ms

```
Thank you for the reply

---

### Post by troffasky on 2012-09-08
A few thoughts:

[LIST]Those router logs look like cable modem logs to me, and are probably more concerned with your cable WAN connection than your client machine.
[/LIST]
[LIST]Try 'dhclient -v wlan0', but personally I can't think how your address and gateway were assigned would affect ping time and throughput, unless you've got a complicated LAN with multiple gateways and you've picked the wrong one [but I'm sure you would have mentioned that if it were the case].
[/LIST]
[LIST]
I tried pinging xkcd.com from here and while the ping time was nowhere near 8s, the total time for 3 pings was still 10s as there seemed to be a delay in resolving the reverse DNS of the IPs responding. Try pinging 8.8.8.8 instead.[/LIST]
```
$ ping -c 3 xkcd.com
PING xkcd.com (107.6.106.82) 56(84) bytes of data.
64 bytes from 107.6.106.82: icmp_req=1 ttl=50 time=89.5 ms
64 bytes from 107.6.106.82: icmp_req=2 ttl=50 time=89.9 ms
64 bytes from 107.6.106.82: icmp_req=3 ttl=50 time=90.0 ms

--- xkcd.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time [COLOR="Red"]10230ms[/COLOR]
rtt min/avg/max/mdev = 89.508/89.820/90.041/0.413 ms
```
[LIST]That ping time to your gateway looks totally normal to me, for wireless. So it looks to me like it's not a problem on your machine but actually on the gateway or the link to the internet [which you've already proved off with a different client]. How about DNS? Try using 8.8.8.8, see if it has any effect.
[/LIST]

---

### Post by steeldriver on 2012-09-08
^^^ all good advice from troffasky there I think

I agree that the router logs all look like modem <-> ISP negotiations (channel bonding) and since they only occur a couple of times a month they're probably normal - some may even be when the ISP takes the service down in their 'maintenance windows'

Definitely try pings by IP as well as name as that will help decide whether it's a routing problem or a DNS problem.

---

### Post by Mahkoe on 2012-09-08
I'm not sure what any of that means, to be honest, but here's the ping command:
```


pinc: command not found
mahkoe@Terminator:~$ ping -c 3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=53 time=5591 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=53 time=5462 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=53 time=5522 ms

```
 Here's the ping time for xkcd by using the ip address:
```

mahkoe@Terminator:~$ ping -c 3 107.6.106.82
PING 107.6.106.82 (107.6.106.82) 56(84) bytes of data.
64 bytes from 107.6.106.82: icmp_req=1 ttl=55 time=4704 ms
64 bytes from 107.6.106.82: icmp_req=2 ttl=55 time=4857 ms
64 bytes from 107.6.106.82: icmp_req=3 ttl=55 time=5736 ms

```
Sometimes my internet goes faster and sometimes it stops altogether. Those ping times are the average, I would say.

---

### Post by steeldriver on 2012-09-08
You could try

```
tracepath -b 8.8.8.8
```which will give you a bit more detail than ping - tbh I'm not sure how to interpret the results but I *think* it breaks down the response times by hop

You can kill it with Ctrl-C once it gets down into 'no reply no reply no reply...'

---

### Post by troffasky on 2012-09-08
Can you try the same ping tests in Windows?

When you say 'works in Windows', is this on a different PC or are you dual booting [or even it in a VM]? If you've got a separate PC with Windows on, you could try a speed test between the two PCs with iperf. 

And finally, is any of this behaviour reproducible on your *buntu machine using wired ethernet rather than wireless?

---

### Post by Mahkoe on 2012-09-09
I am running a dual boot, and I don't have a usable ethernet cable to try out a wired connection. I know that the actual connection between me and the router is fine because for every device (such as smartphones) that has ever used the wireless showed that it had three bars (out of three) and I've always have five bars on my laptop (out of five). The only difference I've noted between my ubuntu machine and all the others is that the router says it is connected without DHCP.

---

