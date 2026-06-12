---
title: "Trying to set up a static ip address in 9.10"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by wickedcultgod on 2009-11-02
Hello all. Well I've decided to try Ubuntu out once again. I love it but can not for the life of me figure out how to set up a working static ip address on Ubuntu. I got it to work once on my mac, but now have no idea how I did it! I have searched the web and these forums and have not found anything comprehensive. I know where to manually enter in the fields in network manager but have no idea how to find the following:
the ip address, (I got the subnet mask), or the default gateway or DNS Server info. I'm just really confused. I can not for the life of me figure out how to do this outside OS X. I'd appreciate any help.

---

### Post by irishbreakfast on 2009-11-02
I am not sure this will answer your question, but this is my experience.

All we did was 
1) add them to our router
2) edit /etc/hosts to add a line, x.x.x.x machine-name, for each machine. 

As I recall, my partner got the range of numbers to use from our router. And I just did a whois on our DNS and it looks like it was given to us by our provider.

---

### Post by wickedcultgod on 2009-11-02
I tried using that but I don't think I'm doing it right. Thank you though for the reply.

---

### Post by t0mppa on 2009-11-02
> **wickedcultgod said:**
> I know where to manually enter in the fields in network manager but have no idea how to find the following:
the ip address, (I got the subnet mask), or the default gateway or DNS Server info. I'm just really confused. I can not for the life of me figure out how to do this outside OS X. I'd appreciate any help.

For IP address, you can use any IP, that is not already taken, in the subnetwork created by your router. Without knowing what the network address is (subnet mask determines the range), it's rather hard to say what addresses are in the subnet. You'd have to check it from either the router configuration or from a device that is connected to the router already just to be sure.

Default gateway is the routers IP address, as you will be sending all traffic going outside of your local network through it. For DNS server, you can either use that of your ISP, which would also be your routers IP address or then [OpenDNS]("http://www.opendns.com/"), i.e., 208.67.222.222 or 208.67.220.220. Once again, you'd have to check the info just like above.

So, bottom line is that you'll either have to access the routers configuration or establish a connection through DHCP once to determine the details. On a Linux system connected to a router, you can grab the required info with the following terminal commands:[LIST]
[*]**netstat -r**, example output:```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
[COLOR="Lime"]192.168.0.0[/COLOR]     *               255.255.255.0   U         0 0          0 wlan0
link-local      *               255.255.0.0     U         0 0          0 wlan0
default         [COLOR="Red"]192.168.0.254[/COLOR]   0.0.0.0         UG        0 0          0 wlan0

```
The green part is the beginning of the local subnet range and the red part is the IP of your router.
 
[*]**ifconfig**, example output:```
wlan0     Link encap:Ethernet  HWaddr 00:22:44:66:88:aa  
          inet addr:192.168.0.100  [COLOR="Blue"]Bcast:192.168.0.255[/COLOR]  Mask:255.255.255.0
          inet6 addr: fe80::222:68ff:fea0:33c8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5622 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5326 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4810822 (4.8 MB)  TX bytes:1208534 (1.2 MB)

```
The blue part is the end of the local subnet range.
[/LIST]

The first and last address of a network are reserved as the Network and Broadcast address (as you can see from above). So, in my case, I could use 192.168.0.x as my IP address, where x can be anything from 1 to 253 (router has taken the 254 already).

---

### Post by wickedcultgod on 2009-11-02
Now that is some info. I believe I understand some. I'm going to try this. I'll post my results. Thank you guys so much. The Ubuntu community is amazing.

---

### Post by wickedcultgod on 2009-11-02
THANK YOU SO F----ING MUCH!!!! I did it. I can forward ports now!!!! This is amazing. Domo Arigato Gozaimasu!!!!

---

