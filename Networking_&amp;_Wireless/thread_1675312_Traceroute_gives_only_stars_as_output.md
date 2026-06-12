---
title: "Traceroute gives only stars as output"
date: 2011-01-25
forum: Networking &amp; Wireless
---

### Post by amsterdamharu on 2011-01-25
When I try traceroute it only gives me stars as output. For example:
```
me@desk:/etc/udev/rules.d$ traceroute taobao.com
traceroute to taobao.com (121.14.24.241), 30 hops max, 60 byte packets
 1  * * *
 2  * * *
 3  * * *
......(more like this)
29  * * *
30  * * *
me@desk:/etc/udev/rules.d$ sudo traceroute taobao.com
traceroute to taobao.com (121.14.24.241), 30 hops max, 60 byte packets
 1  * * *
 2  * * *
 3  * * *
......(more like this)
29  * * *
30  * * *
```

It gives me some output when tracerouting to other computers within my network:

```
me@desk:/etc/udev/rules.d$ sudo traceroute 192.168.0.18
traceroute to 192.168.0.18 (192.168.0.18), 30 hops max, 60 byte packets
 1  192.168.0.18 (192.168.0.18)  207.785 ms  208.088 ms  208.335 ms
```

Is this because of my router you think?

---

### Post by amsterdamharu on 2011-01-25
Ah, me thinks is port forwarding. Let's try again.

Nope, can't get this to work with forwarded ports either.

---

### Post by amsterdamharu on 2011-01-26
I guess the port forwarding wasn't that well done, haven't tried forwarding all ports to my computer but with direct pppoe connection to the modem I get results back.

---

### Post by SpindizZzy on 2011-12-02
Well, I recently encountered this problem too. I rewired my LAN and now Traceroute gives only stars (***) as output from the second hop on...

Ping does work. I do not think that my ISP drops ICMP packets, because it used to work (before i upgraded my physical network)

What I did: 
- I added a router (TP-link TL-r402 M) behind my cablemodem, and attached one PC to it
- I plugged another router into this the first one, using another LAN-port. This is an old D-Link DI-604. I then attached 2 PC's to that one. **Ping from these two DOES work, but Traceroute doesn't... **

I'm guessing that the first router my traceroute-packets encounter (the D-Link) drops them (or 'camouflages' them), but i cannot find a setting to change this...

All help is appreciated !! :-)

Here's my output:
> root@bt:~# traceroute [www.google.be]("http://www.google.be")
traceroute to [www.google.be]("http://www.google.be") (173.194.65.106), 30 hops max, 60 byte packets
 1  192.168.0.1 (192.168.0.1)  1.739 ms  2.846 ms  20.984 ms
 2  * * *
 3  * * *
 .....
30  * * *


---

### Post by jonobr on 2011-12-02
Hello there,

Silly question,

Can you find out what your actual real internet address IP is from your device and ping that?

There could be a couple of things in play here.
Do you have a firewall blocking ICMP on your router?
Or have you changed your own router settings not to respond to ICMP requests?

Your ISP or service provider can always change how it responds to pings and traceroute so because it used to work, doesn't mean it will work that way now or in the future.


The second hop after your 192.168.0.1- I would have figured though, should return a response, and Im surprised it did not.
Thats what makes me think the settings on your internet gateway or router changed to not to respond to ICMP or ping request perhaps?

You will find not reporting of hops back is pretty common as it gives somebody wanting to snoop around a network an understanding of all the interfaces handling your traffic.

One way you can check whats going on is by doing a packet rtace using tcpdump

```
sudo tcpdump -vvv -i any -s 1600 icmp 
```
and then do your traceroute

Just to let you know how it works, (time to put you to sleep)

It uses the same approach as ping, sending out an echo request to the hops in a router,

If a device was to ping say google.com , the ping packet has to reach google.com in a default of 16 hops or jumps.

This way , it stops packets going around the internet forever, in routing loops.


The ping goes out with a hop limit of 16 and each router reduces that number by 1 as it tries to pass it on.
If a router receives an echo request with a value of 1, it reduces the count to zero, and reports back to the sender with its interface IP address and name saying the packet expired.

Traceroute uses this method to determine paths. It also explains why it takes a bit of time to map a path.

Tracertoue will send an ICMP request out from your host with a hop limit of 1,
The next router sees that,  sets the count to zero and responds to you with a count of 0 and its info saying the destination is unreachable.

Traceroute now knows the first hop IP address.
Next , it sends out a second packet with a hop count of 2.
The router that responded the first time, takes that request,
subtracts 1 from the hop limit, and passes to the next router. 
The next router reduces the hop count to zero and reports back name and IP to the sender indicating that the packet expired.

A new request is sent with a hop count of 3 so it will get to the next router and so on.

---

### Post by haqking on 2011-12-02
* * * means filtered, most likely a firewall

---

### Post by SpindizZzy on 2011-12-03
Ok, i checked (ande RE-checked) both of the routers, and I'm pretty sure that there is no ICMP-blocking or firewall active. BUt, if this were the case, my hops would need to be visible, so stuff is still not right ](*,)

Here's my TCP-dump:
> root@bt:~# sudo tcpdump -vvv -i any -s 1600 icmp
tcpdump: listening on any, link-type LINUX_SLL (Linux cooked), capture size 1600 bytes
12:23:19.051229 IP (tos 0x0, ttl 64, id 43264, offset 0, flags [none], proto ICMP (1), length 56)
    192.168.0.1 > 192.168.0.135: ICMP time exceeded in-transit, length 36
    IP (tos 0x0, ttl 1, id 2991, offset 0, flags [none], proto TCP (6), length 60)
    192.168.0.135.60414 > ee-in-f99.1e100.net.www:  tcp 40 [bad hdr length 0 - too short, < 20]
12:23:19.054276 IP (tos 0x0, ttl 64, id 43520, offset 0, flags [none], proto ICMP (1), length 56)
    192.168.0.1 > 192.168.0.135: ICMP time exceeded in-transit, length 36
    IP (tos 0x0, ttl 1, id 2992, offset 0, flags [none], proto TCP (6), length 60)
    192.168.0.135.48804 > ee-in-f99.1e100.net.www:  tcp 40 [bad hdr length 0 - too short, < 20]
12:23:19.093792 IP (tos 0x0, ttl 64, id 43776, offset 0, flags [none], proto ICMP (1), length 56)
    192.168.0.1 > 192.168.0.135: ICMP time exceeded in-transit, length 36
    IP (tos 0x0, ttl 1, id 2993, offset 0, flags [none], proto TCP (6), length 60)
    192.168.0.135.39080 > ee-in-f99.1e100.net.www:  tcp 40 [bad hdr length 0 - too short, < 20]
^C
3 packets captured
3 packets received by filter
0 packets dropped by kernel
The fact that it says 'ICMP time exceeded' makes me believe that the packets are still dropped by my first (D-Link) router.  I surfed around to find if this is standard in this kind of router, but found no info... I also tried to upgrade the firmware, but apparantely D-link stopped support for this model. Any suggestions ? Should i try without that first router to see if the hops go through then ?

BTW: thanks jonobr for the clear visualisation of Ping / Traceroute :p

[COLOR=Red]_**UPDATE:**_[/COLOR]
[COLOR=Black]I fooled around with cables for a while and discovered that everything works just fine when i physically remove the TP-link (ie the second) router from the chain. I then googled around a little and found out (through other forums) that this particular type of brand/model DOES NOT allow traceroute to travel through. There's also no setting to change this. :(

**So, new question:** Is there another way to see the results of Traceroute ? Another command or flag ? Maybe software that does this with a different protocol ? :?: :?:[/COLOR]

---

### Post by aldin on 2012-09-30
> **SpindizZzy said:**
> 
**So, new question:** Is there another way to see the results of Traceroute ? Another command or flag ? Maybe software that does this with a different protocol ? :?: :?:[/COLOR]

try this:
traceroute -I -n 8.8.8.8

(-I argument)


man traceroute

-I     Use ICMP ECHO for probes

---

