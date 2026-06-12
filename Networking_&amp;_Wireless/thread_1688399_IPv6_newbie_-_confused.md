---
title: "IPv6 newbie - confused"
date: 2011-02-15
forum: Networking &amp; Wireless
---

### Post by ratcheer on 2011-02-15
I am a complete newbie with IPv6. This morning, I successfully set up an IPv6 tunnel with Hurricane Electric. Then I successfully completed their suggested host configuration commands for Linux. Of course, it doesn't work. Also, I can no longer access their website to ask for help.

My system now does worse at the ipv6 test site than it did, before. I.e., the dual stack test now fails, where it was successful before I created my tunnel.

I saw some similar threads, here, so here is my output from some of the requested commands.

```

ip address show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:30:1b:b5:9a:1d brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.18/24 brd 192.168.1.255 scope global eth0
    inet6 fe80::230:1bff:feb5:9a1d/64 scope link 
       valid_lft forever preferred_lft forever
3: sit0: <NOARP> mtu 1480 qdisc noop state DOWN 
    link/sit 0.0.0.0 brd 0.0.0.0
4: he-ipv6: <POINTOPOINT,NOARP,UP,LOWER_UP> mtu 1480 qdisc noqueue state UNKNOWN 
    link/sit 68.209.199.199 peer 216.66.22.2
    inet6 2001:470:7:b57::2/64 scope global 
       valid_lft forever preferred_lft forever
    inet6 fe80::44d1:c7c7/128 scope link 
       valid_lft forever preferred_lft forever

ip -4 route show
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.18  metric 1 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.168.1.254 dev eth0  proto static

ip -6 route show
2001:470:7:b57::/64 via :: dev he-ipv6  proto kernel  metric 256  mtu 1480 advmss 1420 hoplimit 0
fe80::/64 dev eth0  proto kernel  metric 256  mtu 1500 advmss 1440 hoplimit 0
fe80::/64 via :: dev he-ipv6  proto kernel  metric 256  mtu 1480 advmss 1420 hoplimit 0
default dev he-ipv6  metric 1024  mtu 1480 advmss 1420 hoplimit 0

```Any ideas what I have done wrong? Thanks.

Tim

---

### Post by ratcheer on 2011-02-15
Upon doing further research, the problem is probably something to do with my host being on a NAT LAN. Some suggestions were made for dealing with that, but I have no idea what they are talking about.

I do have a static WAN IP address.

Tim

---

### Post by SoftwareExplorer on 2011-02-15
The static address will probably make things simpler, but it probably isn't your problem.

If you do ```
ifconfig he-ipv6
```, does it show any traffic coming in on the traffic counters?
If not, your NAT is probably blocking it. Do you have access to the device doing NAT?
Also, does pinging an IPv6 address work?

I also wrote a [[COLOR="DeepSkyBlue"]how-to for HE tunnels and /etc/network/interfaces[/COLOR]]("https://erikbandersen.com/wordpress/?p=28") (which makes the tunnel come up automatically when you start your computer). You might have a look at it once you make sure that the tunnel is allowed through the NAT.

---

### Post by ratcheer on 2011-02-15
Thanks for your reply. No, there is no traffic at all.

ifconfig he-ipv6
he-ipv6   Link encap:IPv6-in-IPv4  
          inet6 addr: 2001:470:7:b57::2/64 Scope:Global
          inet6 addr: fe80::c0a8:112/128 Scope:Link
          UP POINTOPOINT RUNNING NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

However, since my OP, based on some info I found at the Hur Elec forums, I deleted he-ipv6 and re-added it using my LAN IP address instead of my public WAN IP. It still does not work, though.

Tim

---

### Post by ratcheer on 2011-02-15
I believe the problem is with my router, which probably does not support protocol41.

Tim

---

### Post by SoftwareExplorer on 2011-02-15
> **ratcheer said:**
> 
RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
Hm. If your NAT device was blocking it, I would expect to see 0 RX bytes, but some TX bytes from the tunnel trying to send stuff. Is this from right after you re-set it up? Do you get some TX bytes but not RX bytes after you do something like ```
ping6 ipv6.google.com
```?
> **ratcheer said:**
> 
However, since my OP, based on some info I found at the Hur Elec forums, I deleted he-ipv6 and re-added it using my LAN IP address instead of my public WAN IP. It still does not work, though.

I think you can use 'any' for your local ipv4 tunnel endpoint. I doubt that's the problem though. Using your private address for the tunnel endpoint config on your end should work. 

If you have access to the NAT device, look for something called DMZ. It will point all incoming traffic to your NAT device (that is not associated with any outgoing connections) to the private IP you specify. So you would put your tunnel endpoint's private IP in for the DMZ, and your tunnel should get to your computer. If you tell me what model of router/modem you have, I might even be able to tell you specific instructions.

---

### Post by ratcheer on 2011-02-15
tim@tim-mav-prod:~$ sudo ping6 ipv6.google.com
[sudo] password for tim: 
PING ipv6.google.com(yi-in-x63.1e100.net) 56 data bytes
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
^C
--- ipv6.google.com ping statistics ---
10 packets transmitted, 0 received, 100% packet loss, time 9071ms

tim@tim-mav-prod:~$ ifconfig he-ipv6
he-ipv6   Link encap:IPv6-in-IPv4  
          inet6 addr: fe80::44d1:c7c7/128 Scope:Link
          inet6 addr: 2001:470:7:b57::2/64 Scope:Global
          UP POINTOPOINT RUNNING NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

tim@tim-mav-prod:~$

---

### Post by SoftwareExplorer on 2011-02-15
After googling, it looks like ping says that sometimes when iptables is misconfigured. What kind of firewall/rules are you running?

If you're running UFW, you can make it IPv6 aware by changing the file /etc/default/ufw to having the line IPv6=yes instead of IPv6=no.
From that file:> # Set to yes to apply rules to support IPv6 (no means only IPv6 on loopback
# accepted). You will need to 'disable' and then 'enable' the firewall for
# the changes to take affect.
IPV6=no


---

### Post by ratcheer on 2011-02-15
Thanks for the idea. Yours is the first mention I have seen about that in all my searching.

So, I made the edit, then "sudo service ufw stop", then "sudo service ufw start". Then, I surfed to ipv6.google.com **and it is working!**

Thanks very much!

Tim

---

### Post by SoftwareExplorer on 2011-02-15
> **ratcheer said:**
> So, I made the edit, then "sudo service ufw stop", then "sudo service ufw start". Then, I surfed to ipv6.google.com **and it is working!**
Glad you got it working! If you want to have your tunnel run on startup, you could use something like this in your /etc/network/interfaces:
```
auto he-ipv6
iface he-ipv6 inet6 v4tunnel
     endpoint 216.66.22.2
     address  2001:470:7:b57::2
     netmask  64
     ttl 64
     up ip -6 route add default dev he-ipv6
     down ip -6 route del default dev he-ipv6
```

---

### Post by ratcheer on 2011-02-15
Thank you, but I guess I spoke too soon. It did work with IP Passthrough set on my router, but when I disabled that, I could no longer connect to ipv6 sites.

I give up.

---

### Post by SoftwareExplorer on 2011-02-16
> **ratcheer said:**
> Thank you, but I guess I spoke too soon. It did work with IP Passthrough set on my router, but when I disabled that, I could no longer connect to ipv6 sites.

I give up.
(I'm assuming that IP passthrough is like or almost like DMZ, and not some type of bridging mode for the modem)
Does IP passthrough keep other stuff on your network from working, or are you just worried about security?
If it's security you're worried about, it would be easy to fix with UFW. If IP passthrough is a kind of bridging (where you would have to put in ISP credentials on your computer) you would have to set up a lot of stuff to do what your router used to do.

---

### Post by SoftwareExplorer on 2011-02-16
Another option would be to get a tunnel from sixxs.net. They use UDP tunneling with the AICCU client, which should get through NAT just fine (a router that can't NAT udp right would be pretty broken).

---

### Post by ratcheer on 2011-02-16
> **SoftwareExplorer said:**
> (I'm assuming that IP passthrough is like or almost like DMZ, and not some type of bridging mode for the modem)
Does IP passthrough keep other stuff on your network from working, or are you just worried about security?
If it's security you're worried about, it would be easy to fix with UFW. If IP passthrough is a kind of bridging (where you would have to put in ISP credentials on your computer) you would have to set up a lot of stuff to do what your router used to do.

Yes, it simply assigns one computer on the LAN to the external WAN IP, removing it from NAT. The rest of the LAN is still behind NAT. Security is my worry about doing that. And I would have to learn a lot more about ufw before feeling comfortable with that.

There is no compelling reason for me to use ipv6, I just thought it would be cool to play around with it. In the long range, I think the best solution will be a new router that handles ipv6, natively.

I really appreciate all your help. I have learned a lot.

Tim

---

### Post by lemming465 on 2011-02-16
FYI for folks doing ping6 tests: I have better luck with that when I specify the *-I xxx* option with the interface I want to use.

---

### Post by ratcheer on 2011-02-17
I installed miredo, last night. It works with no other muss or fuss. I can ping6 or surf to ipv6-only sites.

However, the ipv6 test sites report that my system cannot. Why is this?

Tim

---

### Post by lemming465 on 2011-02-17
Which IPv6 test sites, specifically?  There are multiple RFC's with many complicated rules about how to pick between IPv4 and IPv6 addresses, particularly different kinds of IPv6 addresses.  In general:
(1) If a site only has one kind of address, use that
(2) If a site has both v4 and v6, but one pair involves native transport and one tunneled, prefer native.  So your v4+miredo client will talk to a dual-stack site with v4, not v6.
(3) If it's dual-stack native all around, believe in the future and prefer v6.

---

### Post by ratcheer on 2011-02-17
The one I can think of offhand is [http://ipv6-test.com](http://ipv6-test.com) I just now reran it and it scored me 10/10 on ipv4 and dual ipv4/ipv6 connectivity but 0/10 on ipv6 only connectivity. However, I can surf to ipv6.google.com and I can ping6 it.

Tim

---

### Post by lemming465 on 2011-02-17
Did you mean [www.test-ipv6.com](www.test-ipv6.com), a completely different site?  If not give it a try, the *technical info* page there has really good interpretations.

---

### Post by ratcheer on 2011-02-18
> **lemming465 said:**
> Did you mean [www.test-ipv6.com]("http://www.test-ipv6.com"), a completely different site?  If not give it a try, the *technical info* page there has really good interpretations.

Yes, you are right. I have tried both of those sites, but the one you cited is the one I have used the most.

Tim

---

### Post by ratcheer on 2011-02-18
Ok, several new developments.

I was researching how to find an  IPv6 capable router and I found out that my current wireless router can  be flashed to DD-WRT. So, I have done that. This is supposed to handle  IPv6.

But, while I was doing it, I found out that, apparently,   the video card in my Windows PC has died. Unfortunately, there is no  phone line in the room where my Linux PC is, so I cannot just move the  modem to that room. I now have the major task of swapping PC's  (including monitors, external drives, and speaker systems).  [IMG]http://i.dslr.net/v2/lite/confused.gif[/IMG]

If  I ever get all that finished, I will have to bridge my modem and see if  the newly flashed router will handle the PPPoE connection. If I get  that working, I will then have to reset or reconfigure every node on my  LAN (two PC's that still work plus numerous game systems). Joy, joy,  joy....

I am wondering if I even want to pursue all this?

Tim

---

### Post by ratcheer on 2011-02-18
I made all the changes and everything worked. However, I still do not have ipv6 support in the router. I will try a different dd-wrt firmware revision, next week.

Tim

---

### Post by ratcheer on 2011-02-19
I found another version of dd-wrt for my router that supports ipv6, and installed it.

DD-WRT v24-sp2 (09/18/10) std-nokaid-nohot-nostore - build 15230M NEWD Eko

So,  that should be a big step in the right direction. Now, all I should  have to do is figure out how to configure everything so it will work.

Tim

---

### Post by ratcheer on 2011-02-19
Ok, it is all working, now. The final change I made to fix it was to redefine the link on the client-side to refer to my NAT address instead of my WAN address. It doesn't really make sense to me, but that seems to be how it works.

Thanks to everyone for your input!

Tim

---

