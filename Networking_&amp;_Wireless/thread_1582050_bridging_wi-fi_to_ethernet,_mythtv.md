---
title: "bridging wi-fi to ethernet, mythtv"
date: 2010-09-25
forum: Networking &amp; Wireless
---

### Post by myth-eeebox-ben on 2010-09-25
Hi all, I'm new here.  I have made use of these forums before and found almost all my questions have been asked and answered already.  Thanks to the *buntu community.

This one has me stumped.  I'm trying to set up my myth box (frontend & backend) to do all of the networking that I require.  Here's my setup.

[B]
eeebox B202 running mythbuntu 10.04[/B]
[U]
eth0 static 192.168.1.10[/U]  
          this is started at boot through /etc/network/interfaces and my myth-backend resides here.
          dnsmasq takes care of ip addresses for anything connecting to the ethernet port
          no problems here (so far)

_wlan0 dhcp 192.168.0.10_ (IP assigned by my netcom wireless/3g router N3G007W)
          currently using NetManager to take care of the connection, but it may need to be disabled.......
          my router always gives it the same IP by the hardware address
          I can ssh into this address and access smb shares no problem.

**Wi-Fi Router 192.168.0.1**
          issues dhcp in the range 192.168.0.11-50
          provides internet access and ssh / smb to my private network
[B]
Laptop wi-fi dhcp 192.168.0.5x[/B]
          can ping, ssh, smb to 192.168.0.10
          myth-frontend  (cannot connect to 192.168.1.10 through wi-fi)

[I]
**now I have several interconnected questions**[/I]

it seems a simple bridge interface will not work for wlan0 <--> eth0 because wi-fi packets aren't the same as ethernet packets.  So I need to set up ip forwarding or routes.  But I can not get my head around iptables.

[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

-or-

Because I have trouble applying settings with iwconfig (due to NetManager taking control) this bridge method could work but I need to remove NetManager completely and start my wlan0 with /etc/network/interfaces

[http://newyork.ubuntuforums.org/showthread.php?t=1015641]("http://newyork.ubuntuforums.org/showthread.php?t=1015641&highlight=rt2860+iwconfig+set+essid")

-or-

I'm attacking this the wrong way completely
or I need to use something like wicd


Any Ideas out there?

---

### Post by SeijiSensei on 2010-09-25
Personally I never use bridging; I use IP routing instead.  If you want the machine to route packets between interfaces, you'll need to check that IP forwarding is enabled in the Linux kernel, which by default it is not.

Try this.  First check to see if forwarding is enabled by typing the following in a Terminal:

sudo cat /proc/sys/net/ipv4/ip_forward

If you get a value of zero, forwarding is disabled.

Now try fixing it on the fly by running the command

sudo echo '1' > /proc/sys/net/ipv4/ip_forward

Can you ping 192.168.1.10 now from a machine in 192.168.0.0/24?

If that solves the problem, you can permanently enable forwarding by editing /etc/sysctl.conf.  Find the lines that read

```

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

```

and remove the hash mark (#) from the first column of the net.ipv4.ip_forward line, then save the file.

If that doesn't fix things, we'll need to probe deeper into things like your routing table, but let's try the simplest solution first.

---

### Post by myth-eeebox-ben on 2010-09-26
Thanks for the reply.  I'm following other issues on the forums.  My goal is similar to the "xbox through laptop wi-fi" setup

> **SeijiSensei said:**
> 
Try this.  First check to see if forwarding is enabled by typing the following in a Terminal:


Yes I have enabled IP forwarding

> **SeijiSensei said:**
> 
Can you ping 192.168.1.10 now from a machine in 192.168.0.0/24?


no, that's the problem.

> **SeijiSensei said:**
> 
If that doesn't fix things, we'll need to probe deeper into things like your routing table, but let's try the simplest solution first.


and that's the other problem; iptables is far from clear in my head.  I have copied some lines of code from other threads and stuck them in the console, but have no idea what I'm doing.

I think to make IP tables work properly I need to take control of my wlan0 and not let NetManager do it's thing.

Then we go into the next layer of my problem, I can't set essid (or anything else) with iwconfig because NetworkManager is handling it and I'm a bit scared to completely remove it.

---

### Post by myth-eeebox-ben on 2010-09-26
here's my settings


```
root@mythbox:~# sudo cat /proc/sys/net/ipv4/ip_forward
1
``````
root@mythbox:~# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination       
```so I have no active routes, correct?


so I do this

```
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```

and I end up with this
```
root@mythbox:~# iptables -t nat -L POSTROUTING
Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
MASQUERADE  all  --  anywhere             anywhere     

```

---

### Post by perspectoff on 2010-09-26
> **myth-eeebox-ben said:**
> 

it seems a simple bridge interface will not work for wlan0 <--> eth0 because wi-fi packets aren't the same as ethernet packets.  

Not true. 

A simple bridge interface works fine, and I am using it now. The packets are the same.

    * Install bridge-utils to be able to create network bridges: 

sudo apt-get install bridge-utils

    * Edit /etc/network/interfaces: 

sudo nano /etc/network/interfaces

The interfaces file should look like this after editing it:

auto eth0
iface eth0 inet manual
#
auto br0
iface br0 inet dhcp
#
bridge_ports eth0 wlan0
#
# The loopback network interface
auto lo
iface lo inet loopback

    * Restart networking with: 

sudo /etc/init.d/networking restart

From

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Network_Interfaces_Bridging](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Network_Interfaces_Bridging)

---

### Post by SeijiSensei on 2010-09-26
Iptables just filters packets according to rules; it doesn't set up any routes.  Your results show there are no filters in place.

To see the routing table, enter "route -n" at the commmand prompt.  My guess is that you have a route to the wifi router itself at 192.168.0.1, but no route to the 192.168.0.0/24 network.  Do you have a routing table entry like this one:

```

192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0

```

If not, try running the command 

sudo ip route add 192.168.0.0/24 via 192.168.0.1

and see if that helps.

---

### Post by myth-eeebox-ben on 2010-09-26
Firstly, thanks for the reply **perspectoff,** I was hoping a bridge would work, but it knocked out my eth0 static IP (which is essential for the mythbackend).  Then I read somewhere about the packet size and that a bridge can't simply pass on the packets, depending on how the wi-fi firmware handles them.

**SeijiSensei**
```
root@mythbox:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0

```

and I've added some other stuff to my previous post.

any clues?

---

### Post by SeijiSensei on 2010-09-26
> **myth-eeebox-ben said:**
> 
```
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```


Oh, you have a NAT rule?  That could be the problem.  You don't need to masquerade the packets if routing is set up correctly; in fact, it can break routing in many circumstances.

Try "flushing" the nat table like this:

sudo iptables -t nat -F

then try pinging again.

Masquerading is designed for situations where you want all the internal hosts on a network to appear as if their packets are all coming from a single address.  The most common application is on firewall routers; NAT is used to enable the internal hosts with private addresses to talk to external hosts on the Internet.  No matter which host you're using behind a NAT firewall, external hosts see your traffic as coming from the router's external address.  That's not the situation you have here.

---

### Post by myth-eeebox-ben on 2010-09-26
trying the bridge method with 


```

root@mythbox:~# cat /etc/network/interfaces 
auto lo

iface lo inet loopback

auto eth0

iface eth0 inet static
address 192.168.1.10
network 192.168.1.0
netmask 255.255.255.0
gateway 192.168.0.1
up dnsmasq


###### wi-fi adapter wlan0 ######################

auto wlan0
iface wlan0 inet dhcp
wireless-essid "benznet"
#wireless-key xxxxxxxxx
wireless-mode managed
address 192.168.0.10
netmask 255.255.255.0
gateway 192.168.0.1
up sh /etc/network/setwlan-post.sh
###########pre-up iptables-restore < /etc/iptables.rules

####### end of wi-fi ###################

auto br0
iface br0 inet dhcp
#address 192.168.0.2
#network 192.168.0.0
#netmask 255.255.255.0
#gateway 192.168.0.1
bridge_ports wlan0 eth0
#up \
#/sbin/iwconfig wlan0 essid benznet && \
#/sbin/iwconfig wlan0 mode managed

```



gives me
```
root@mythbox:~# ifconfig
br0       Link encap:Ethernet  HWaddr 00:22:43:45:67:5a  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::222:43ff:fe45:675a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7291 (7.2 KB)  TX bytes:9415 (9.4 KB)

eth0      Link encap:Ethernet  HWaddr 00:23:54:c1:f9:af  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:65684 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65684 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15317620 (15.3 MB)  TX bytes:15317620 (15.3 MB)

wlan0     Link encap:Ethernet  HWaddr 00:22:43:45:67:5a  
          inet6 addr: fe80::222:43ff:fe45:675a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31899 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4449 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6823233 (6.8 MB)  TX bytes:432947 (432.9 KB)
          Interrupt:17 

```

so it's knocked out the ip address on eth0 and wlan0, and has given 192.168.0.10 to br0
I can still ssh into 192.168.0.10 (eeebox in hosts) but now Myth can't connect to the backend.... not good.

---

### Post by myth-eeebox-ben on 2010-09-26
> **SeijiSensei said:**
> Oh, you have a NAT rule?  That could be the problem.


ok, I see that I don't need masquerading

so I've gotten rid of the br0 crap, fresh boot, and myth works again

now I do
```
sudo iptables -t nat -F

```
and 
```
sudo ip route add 192.168.0.0/24 via 192.168.0.1

```

and I can't ping 192.168.1.10 from wi-fi

I can't ping out using the eth0 interface
```
root@mythbox:~# ping -I 192.168.1.10 192.168.0.1
PING 192.168.0.1 (192.168.0.1) from 192.168.1.10 : 56(84) bytes of data.
^C
--- 192.168.0.1 ping statistics ---
7 packets transmitted, 0 received, 100% packet loss, time 5999ms

```

but i can ping out through wi-fi
```
oot@mythbox:~# ping -I 192.168.0.10 192.168.0.1
PING 192.168.0.1 (192.168.0.1) from 192.168.0.10 : 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=1.53 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=1.60 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=1.14 ms
^C


```

---

### Post by myth-eeebox-ben on 2010-09-26
now my routes look like this

```
root@mythbox:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.0.0     192.168.0.1     255.255.255.0   UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0

```

is the second line correct? how does traffic from  eth0 get to wlan0? I don't understand

---

### Post by SeijiSensei on 2010-09-26
I think the problem is actually a simple one -- your router.  You probably need to add a static route on it to the 192.168.1.0/24 network via 192.168.0.10.  

What's happening is that wifi hosts send traffic for 192.168.1.10 (and all other addresses) to the wifi router.  It doesn't have any special rule to handle that traffic, so it tries to send it out its external interface to the Internet.  It needs to know that traffic for the 192.168.1.0/24 network goes to the Linux box.

I bet you don't need that other route I suggested either.

---

### Post by myth-eeebox-ben on 2010-09-26
Thank you Sensei

Success!

I can access my mythbackend from my laptop now.  The only thing is I can't get to the internet from the ethernet on my mythbox.  This doesn't matter for what I'm doing, only if I was to plug an XBox or PS3 into the ethernet port it wouldn't get to the internet.

That's why I was going for a bridge so that traffic flowed both ways.

I'm sure one more rule would fix that.

---

### Post by myth-eeebox-ben on 2010-09-26
While I'm here, I'd better learn something about routes.

```
root@mythbox:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
root@mythbox:~# ping -I 192.168.1.10 192.168.0.1
PING 192.168.0.1 (192.168.0.1) from 192.168.1.10 : 56(84) bytes of data.
^C
--- 192.168.0.1 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 3999ms

```

so if I want to ping from eth0 to the router, I'll need to set wlan0 as my gateway right?
so the last line says that an outside address should go through the router to the internet.
and the second line should direct everything from the eth0 port to the wlan0 interface.
So it needs gateway set to 192.168.0.10.

is that right?

---

### Post by SeijiSensei on 2010-09-26
Let's start with a simple IP network with no routers; just a bunch of computers connected together via an old-fashioned ethernet hub.  If a machine at 192.168.0.1 has a packet it needs to send to 192.168.0.2, it just "broadcasts" that packet onto the network in hopes that the .2 machine will "hear" the broadcast and accept the packet.  In cases like these, there isn't any routing going on at all.  Since all the machines can see each other on the same wire, they all just babble away and hope things work out.  (Some services like mail and web use the Transmission Control Protocol, the "TCP" in "TCP/IP", as well to insure reliable transfers.  The receiving machine acknowledges the receipt of each packet.  Any that are missing are retransmitted.) 

In a routing table, this situation is represented by lines like the one for 192.168.0.0/255.255.255.0 on your machine.  The Linux box knows that if it has any packets for a machine in this network, it should broadcast them on the wlan0 interface.  Similarly if the eth0 interface were connected to other computers on its side via a hub, Linux would know to broadcast those packets for 192.168.1.0/24 on the eth0 interface.

So, in your case, there really isn't any need for another "gateway" address for packets to either of the 192.168 networks.  A machine in 192.168.1.0/24 would need to be configured with 192.168.1.10 as its default gateway, though, so it knows where to send traffic not destined for other machines in 192.168.1.0/24.

Packets that don't match any specified routes are governed by the final rule which applies to all other packets.  In your case the "default gateway" is your Internet router at 192.168.0.1.

None of this explains why you can't ping from 192.168.1.10 to 192.168.0.1, though.  I admit I'm stumped by that.  Someday, try connecting another computer to the eth0 side using either a hub or switch or a specialized "cross-over" Ethernet cable.  (Cross-over cables connect the transmit pins of one Ethernet adapter to the receive pins on the other and thus avoid the need for a hub.)  Give that computer an address in 192.168.1.0/24 and tell it to ping 192.168.0.1.  How does that work out?

You'll need to fix the route you entered in the router first.  It only routes to 192.168.1.10, not the entire 192.168.1.0/24 network.  Try replacing the .10 with .0 and make sure everything still works.  Otherwise the router will only be able to see the .10 machine and will send all other 192.168.1.x traffic to the Internet.

Finally, you might want to install the traceroute utility as well (sudo apt-get install traceroute).  Traceroute uses the same protocol as ping, but displays all the intermediate hops the packet traverses along its way.  For instance, tracing a route to [www.google.com](www.google.com) from my (Linux) external router shows the following:

```

$traceroute -n www.google.com
traceroute to www.google.com (173.194.35.104), 30 hops max, 40 byte packets
 1  xx.xxx.xx.x  3.324 ms  3.175 ms  5.482 ms
 2  130.81.49.228  5.450 ms  5.423 ms  5.377 ms
 3  130.81.29.172  5.343 ms  7.751 ms  7.735 ms
 4  152.63.16.137  14.954 ms  14.926 ms  17.438 ms
 5  152.63.16.221  17.412 ms  17.384 ms  17.336 ms
 6  152.63.21.117  67.097 ms  66.691 ms  64.081 ms
 7  152.179.72.62  14.500 ms  14.431 ms  16.815 ms
 8  216.239.43.114  16.783 ms  16.746 ms  14.627 ms
 9  216.239.48.92  16.940 ms  14.437 ms  14.343 ms
10  173.194.35.104  14.557 ms  14.449 ms  14.392 ms

```

Leaving off the "-n" option will resolve the addresses into host names; for instance, line 7 above would display with google-gw.customer.alter.net instead of 152.179.72.62.

Traceroute can be helpful in locating a routing problem if it occurs on an intermediate router.

Oh, and that entry for 169.254.0.0 is a kludge designed to support misconfigured Windows machines.  If a Windows machine has no static IP and can't obtain an address from a DHCP server, it's assigned an address in that range by the OS.  Linux distributions nowadays commonly add a route for that network automatically to avoid complaints that Linux doesn't work with Windows.

---

### Post by myth-eeebox-ben on 2010-09-29
Thanks again Sensei (you are my teacher!)

I wasn't expecting such a detailed reply. You've outdone yourself.....

I have connected my laptop with a crossover cable and can't ping out or get internet. That is why I have dnsmasq starting when eth0 comes up; to allow any laptop to connect and see my music, videos etc.  This gives me faster transfer rates than wireless. Eeebox has gigabit lan. I only use dnsmasq as a dhcp server (because it is shipped with ubuntu and i didn't have internet when I started setting up my myth-box)

I think I have a few things to try.  

Only one step away from calling this thread solved.

---

