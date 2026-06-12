---
title: "to fill or not to fill interfaces"
date: 2013-04-30
forum: Networking &amp; Wireless
---

### Post by clearski on 2013-04-30
During installation I let Ubuntu choose its way to configure Internet through a router running a DHCP server, so I'm basically getting my IP address from that router which was automatically discovered. But I recently read some docs about Networking and there was more info in a file than I actually have on my machine.

My /etc/network/interfaces file looks like this:

```
auto lo
iface lo inet loopback
```

Plus one iptables pre-up, which I added at some point.

Nothing about other interfaces: eth0 & wrl0 (my wireless interface). I am not using wrl0 now, but all my connections are going through eth0.

My guess is that all interfaces info must be must be written to the *interfaces* file in the case of a system running server services or not running any GUI, but for a basic workstation, which uses Network Manager, adding all interfaces to the file is not compulsory. However, I'm not sure about it and I'm wondering if it is recommended or wrong to add the interfaces myself after the lo.I know how to add all interfaces and all the details, but I'm not sure if there's anything to gain or any inconvenience because of this?

---

### Post by Hadaka on 2013-04-30
Hi, unless you are running a server and even then
depending on what you do with the server you dont
need to add anythinng to your current /etc/network/interfaces
nor do you need to add anyting to iptables. You have exactly
what you need for a stand alone computer using wired or wireless.
Here is mine...and i have 3 machines networked, via ssh for local
lan use only.
```
hadaka@the-beach:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
 
```
so you are fine, just the way you are.
hope that helps.

---

### Post by lisati on 2013-04-30
> **Hadaka said:**
> Hi, unless you are running a server and even then
depending on what you do with the server you dont
need to add anythinng to your current /etc/network/interfaces
nor do you need to add anyting to iptables. You have exactly
what you need for a stand alone computer using wired or wireless.
Here is mine...and i have 3 machines networked, via ssh for local
lan use only.
```
hadaka@the-beach:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
 
```
so you are fine, just the way you are.
hope that helps.
Agreed. 

One thing you might occasionally find in forums such as this one is people setting IP addresses in their interfaces file, and sometimes there's good reason to do so. My preference is to use my router to manage IP address allocation where possible. This can make it easier when connecting a portable device to someone else's network.

---

### Post by clearski on 2013-04-30
> **Hadaka said:**
> Hi, unless you are running a server and even then
depending on what you do with the server you dont
need to add anythinng to your current /etc/network/interfaces
nor do you need to add anyting to iptables. You have exactly
what you need for a stand alone computer using wired or wireless.
Here is mine...and i have 3 machines networked, via ssh for local
lan use only.
```
hadaka@the-beach:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
 
```
so you are fine, just the way you are.
hope that helps.

I'm fine, it works really great. I was just trying to understand when do I need to add interfaces.

Thanks!

---

### Post by Iowan on 2013-04-30
A machine without Network Manager (e.g. server) will probably use */etc/network/interfaces*. DHCP or static addresses can be configured  either way. Network Manager and  */etc/network/interfaces* do not play nicely together, so trying to referee can be tricky.

---

### Post by clearski on 2013-05-01
> **Iowan said:**
> A machine without Network Manager (e.g. server) will probably use */etc/network/interfaces*. DHCP or static addresses can be configured  either way. Network Manager and  */etc/network/interfaces* do not play nicely together, so trying to referee can be tricky.

Thank you, that answered not only the question I posted, but also a few which I also had in mind.

First of all, I understand that the server version of Ubuntu doesn't run Network Manager. So, that machine needs to have the interfaces configured, loaded and changed in a different way.

I guess that the word "auto" loads all interfaces (auto eth0, auto lo, auto wrl0) with the specific details mentioned afterwards (it can include different settings, DNS addresses for every interface etc).

I think that all interfaces could be active (responsive) at a time (at least lo, eth0 & wrl0), or could be disabled individually, but the traffic won't use them all. In my case, I can activate both Wireless connection and Cable connection with NM, but it doesn't mean that I am using both at the same time to connect to my router, so only one of them can be used at a moment.
 
I am not actually trying to referee a NM / etc/network/interfaces play, I'm trying to understand how things work. In case my GUI doesn't start or NM doesn't work or in case I decide to install a server edition on other computer, it's good to know how to do things and it's even better to understand them first. :)

---

### Post by bab1 on 2013-05-01
> **clearski said:**
> ...

First of all, I understand that the server version of Ubuntu doesn't run Network Manager. So, that machine needs to have the interfaces configured, loaded and changed in a different way.
Traditionally Linux TCP/IP networking was configured with 3 files.  These are: * /etc/network/interfaces, /etc/resolv.conf and /etc/hosts*.  Later there have been apps that help in configuring the networking (i.e. WICD and Network Manager)  These use different files to store the information needed.  It's the same info, just stored in a different place.  Either method will work.  You can't configure a specific interface with both methods at the same time however.> 

I guess that the word "auto" loads all interfaces (auto eth0, auto lo, auto wrl0) with the specific details mentioned afterwards (it can include different settings, DNS addresses for every interface etc).
Yes, auto does load the configuration for a specific interface at boot time.> 

I think that all interfaces could be active (responsive) at a time (at least lo, eth0 & wrl0), or could be disabled individually, but the traffic won't use them all. In my case, I can activate both Wireless connection and Cable connection with NM, but it doesn't mean that I am using both at the same time to connect to my router, so only one of them can be used at a moment.
You can have only one interface *active * per subnet at any one time.  The loopback adapter uses the 127.0.0.0/8 network and you can configure the **eth** and **wlan** adapters to the IP network of your choice.  If you configure the **eth** and **wlan** adapters to have IP addresses in the *same subnet*, the **eth** adapter will have precedence over the **wlan** adapter and will therefore be active.  In this scenario the **wlan** adapter will be configured but not active. > 

I am not actually trying to referee a NM / etc/network/interfaces play, I'm trying to understand how things work. In case my GUI doesn't start or NM doesn't work or in case I decide to install a server edition on other computer, it's good to know how to do things and it's even better to understand them first. :)
I don't think @iowan meant that literally.  Just that NM and using the interfaces file causes conflicts as they use different methods to achive the same goal.

FWIW -- Both methods (NM or interfaces) will configure either [COLOR="#FF0000"]DHCP[/COLOR] IP addressing *configuration parameters* or **[COLOR="#0000FF"]static[/COLOR]** (via the interfaces file)  IP addressing *configuration parameters*.

---

### Post by clearski on 2013-05-01
> **bab1 said:**
> Traditionally Linux TCP/IP networking was configured with 3 files.  These are: * /etc/network/interfaces, /etc/resolv.conf and /etc/hosts*.  Later there have been apps that help in configuring the networking (i.e. WICD and Network Manager)  These use different files to store the information needed.  It's the same info, just stored in a different place.  Either method will work.  You can't configure a specific interface with both methods at the same time however.Yes, auto does load the configuration for a specific interface at boot time.You can have only one interface *active * per subnet at any one time.  The loopback adapter uses the 127.0.0.0/8 network and you can configure the **eth** and **wlan** adapters to the IP network of your choice.  If you configure the **eth** and **wlan** adapters to have IP addresses in the *same subnet*, the **eth** adapter will have precedence over the **wlan** adapter and will therefore be active.  In this scenario the **wlan** adapter will be configured but not active. 
I don't think @iowan meant that literally.  Just that NM and using the interfaces file causes conflicts as they use different methods to achive the same goal.

FWIW -- Both methods (NM or interfaces) will configure either [COLOR=#FF0000]DHCP[/COLOR] IP addressing *configuration parameters* or **[COLOR=#0000FF]static[/COLOR]** (via the interfaces file)  IP addressing *configuration parameters*.

Thank you, the way you explained makes things very clear!

It also pointed out that there's one more important reality (which I was overlooking): **the subnet**.

What I understand now (and I hope it's correct) is that if I have two Ethernet adapters I can have a different subnet (but only one, not two) for each adapter and both could be loaded at boot time and even accept different connections at the same time, but only one subnet / interface.

For example, I can have two LANs (each with 4-5 workstations) and just one server machine with two ethernet adapters serving both LANs. Some services could be provided to localhost only, some to the first LAN via one ethernet adapter (one subnet), and some to the second LAN via the second ethernet adapter (second subnet). Some services could also be routed in various ways between these three interfaces through the server which also does the routing. But if all I got is an ethernet adapter and a wireless adapter, and if they are both on the same subnet, they can't be loaded both at the same time, because there'll be a conflict of addresses.

By different subnets I understand addresses like:

192.168.3.x (where x is a 1 to 255 number assigned to computers with the specified prefix 192.168.3.)
192.168.100.x (where x is a 1 to 255 number assigned to computers with the specified prefix 192.168.100.)

I think that both these subnets belong to the network 192.168.0.0 and they both should have 255.255.0.0 netmask. But I'm not pretty sure about these subnet numbers.

---

### Post by bab1 on 2013-05-01
> **clearski said:**
> Thank you, the way you explained makes things very clear!

It also pointed out that there's one more important reality (which I was overlooking): **the subnet**.

What I understand now (and I hope it's correct) is that if I have two Ethernet adapters I can have a different subnet (but only one, not two) for each adapter and both could be loaded at boot time and even accept different connections at the same time, but only one subnet / interface.
This is almost correct.  You don't assign a subnet to a specific adapter.  It might be helpful to think of each adapters configuration permitting the host to communicate with its peers in a specific subnet.   > 
For example, I can have two LANs (each with 4-5 workstations) and just one server machine with two ethernet adapters serving both LANs. 
It would be called a host participating in 2 LANS.  And when you configure forwarding it becomes a router (passing traffic between the 2 networks.  The term server at this level of discussion is not the physical hadware, but rather the services available.  To put it another way; A server is a process that is always running, waiting to provide services to the requesting client (e.g HTTP or DNS or SSH or smbd (Samba) of NFS).  > 
Some services could be provided to localhost only, some to the first LAN via one ethernet adapter (one subnet), and some to the second LAN via the second ethernet adapter (second subnet). Some services could also be routed in various ways between these three interfaces through the server which also does the routing. But if all I got is an ethernet adapter and a wireless adapter, and if they are both on the same subnet, they can't be loaded both at the same time, because there'll be a conflict of addresses.
Yes.> 

By different subnets I understand addresses like:

192.168.3.x (where x is a 1 to 255 number assigned to computers with the specified prefix 192.168.3.)
192.168.100.x (where x is a 1 to 255 number assigned to computers with the specified prefix 192.168.100.)

I think that both these subnets belong to the network 192.168.0.0 and they both should have 255.255.0.0 netmask. But I'm not pretty sure about these subnet numbers.
But not necessarily.  The terms subnet and network have changed slightly over the years.  But for the most part a *network * is a block of IP addresses that you control (administer).  One persons network is most likely another persons subnet.  For example the network 3.0.0.0 /8 (3.0.0.0 with a subnet mask of 255.0.0.0) is owned by G.E..  The administrator could create a subnet of 3.0.0.0/24 (a subnet of 255.255.255.0) and assign a person to manage this sub network.  All of this is much clearer if you look at the numbering of the network as the OS sees it; in a binary fashion.```

[COLOR="#FF0000"]00000011[/COLOR][COLOR="#0000FF"]000000000000000000000000[/COLOR] <--3.0.0.0 /8 network (8 bits of mask)
[COLOR="#800080"]11111111[/COLOR][COLOR="#0000FF"]000000000000000000000000[/COLOR]  <--255.0.0.0 netmask that defines the network boundries

[COLOR="#FF0000"]000000110000000000000000[/COLOR][COLOR="#0000FF"]00000000[/COLOR]  <--3.0.0.0 /24 network (24 bits of mask)
[COLOR="#800080"]111111111111111111111111[/COLOR][COLOR="#0000FF"]00000000[/COLOR]  <--255.255.255.0 netmask that defines the network boundries

```

Clearly the second network is a subset of the first.  This means that any network that you control can be called a network and you may subnet it if you wish.  The only limitation is that you need at least a network ID and a broadcast address and at least 2 host IP addresses to have a functioning network.

I'm sure you have more questions now.  ;-)

---

### Post by clearski on 2013-05-01
You almost killed me with those 0s and 1s. :)

By looking at your binary representation, I think that any address is seen (by the machine) as a group of 4 x 8 bits, which makes it a 32-bits address. As far as I remember, I think I read somewhere that IPV4 addresses are 32 bits and IPV6 are 128 bits.

From your example, it is clear that the more we mask the network, the less "space" is has for a subnet (which is also logical).

If my address is 192.168.5.1 and my netmask is 255.255.255.0, then my network could be written as 192.168.5.0 / 24, because I have the first 24 bits masking the address. It means that I could only use the last 8 bits (the free ones, which are not masked) of the network address for my router, computers from LAN etc. And if my address is 192.168.5.13 with a netmask 255.255.0.0, the network is  192.168.0.0 /16.

If everything I wrote above is correct, I have three more questions. :)

1. It is obvious that 00000000 = 0 and 11111111 = 255, but I can't figure out how did you know that 00000011 is the binary representation for number 3. Is there any formula or trick to find out what's the binary for 142, for example? :)

2. I've only got two computers connected through a router. Let's say that my network is 192.168.1.0 and my netmask 255.255.255.0 (or 192.168.1.0 /24, to speak a more advanced language now :) ). With the current netmask I have 254 remaining addresses for my computers or any other network devices. If I change my netmask to 255.255.255.251, does it mean that the only addresses available on this network would be 192.168.1.252 (let's say for the router) and 192.168.1.253 (computer 1) and 192.168.1.254 (computer 2)?

3. Can I also do my netmasking like this: 255.255.0.255 ? Is this still a 0.0.0.0 /24 masking?

This is very interesting and very useful. I cannot thank you enough for your time and help.

---

### Post by bab1 on 2013-05-01
> **clearski said:**
> You almost killed me with those 0s and 1s. :)
That's why you write it in decimal but it really is a stream of on/off bits.> 

By looking at your binary representation, I think that any address is seen (by the machine) as a group of 4 x 8 bits, which makes it a 32-bits address. As far as I remember, I think I read somewhere that IPV4 addresses are 32 bits and IPV6 are 128 bits.

From your example, it is clear that the more we mask the network, the less "space" is has for a subnet (which is also logical).

If my address is 192.168.5.1 and my netmask is 255.255.255.0, then my network could be written as 192.168.5.0 / 24, because I have the first 24 bits masking the address. It means that I could only use the last 8 bits (the free ones, which are not masked) of the network address for my router, computers from LAN etc. And if my address is 192.168.5.13 with a netmask 255.255.0.0, the network is  192.168.0.0 /16.

This is  more properly stated as:  The subnet mask defines the Network ID and the rest is left to assign to the hosts in the network.  As the netmask defines the Network ID, this also defines the boundaries of the network in question.  Using the network of 192.168.0.0 you can tell what is network and what is the host IP address space.  If we say /24 we mean the first 24 *contiguous *bits are the network ID.  The last 8 bits minus 2 are used for the hosts (routers/printers/workstations/laptops).  The first address ( e.g .0) is reserved for the network ID ( in this case [COLOR="#FF0000"]192.168.0.[/COLOR][COLOR="#0000FF"]**0**[/COLOR]).  The last number is reserved for broadcasts to the entire network (as in [COLOR="#FF0000"]192.168.0[/COLOR].[COLOR="#0000FF"]**255**[/COLOR]).
> 
If everything I wrote above is correct, I have three more questions. :)

1. It is obvious that 00000000 = 0 and 11111111 = 255, but I can't figure out how did you know that 00000011 is the binary representation for number 3. Is there any formula or trick to find out what's the binary for 142, for example? :)
Binary notation is pretty simple.  TCP/IP addressing adds a little to the straight math.  First the TCP/IP part:  We are talking about IPv4 here only.  The 32 bit address space is as you noted, comprised of four 8 bit sections (called octets).  Each octet is the same as the other as to the numbering.  This means that the entire octet has the max value of 255 and a minimum value of 0.  Lets start with one octet. Obviously the number 0 is represented like this```
00000000
```
The number 1 looks like this```
00000001
```
Since we can't create a number larger than 1 in any position, we move to the left just as we would do with decimal after the 9th number.  So the number 2 would look like this in binary```
00000010
``` ...and 3 would be ```
00000011
```

So the binary progression is 0 or 1, 2, 4, 8, 16, 32, 64, 128 and you can think of the 8 slots as one of  0 or 1, one of 2, one of 4, one of 8, one of 16, one of 32, one of 64, one of 128.  And if you add up any of these you have a number between 0 and 255 decimal.  There are calculators on the internet to do this but you should learn this if you are going to be involved with IT in any serious manner.> 

2. I've only got two computers connected through a router. Let's say that my network is 192.168.1.0 and my netmask 255.255.255.0 (or 192.168.1.0 /24, to speak a more advanced language now :) ). With the current netmask I have 254 remaining addresses for my computers or any other network devices. If I change my netmask to 255.255.255.251, does it mean that the only addresses available on this network would be 192.168.1.252 (let's say for the router) and 192.168.1.253 (computer 1) and 192.168.1.254 (computer 2)?
The simple answer to this is:  You change the host address space address space by increasing or decreasing the bits devoted to the Netmask.  192.168.1.0 /25 takes 1 bit away from the host addressing making it 7 bits instead of 8.  This gives you 2 networks, each with half the number of host addresses minus 2  for each subnet (Net ID and b'cast)  if you add up the bits we defined above leaving off the left most (e.g. 128) you have the maximum 127 -2 usable addresses for each subnet.  The /24 network has 255 minus 2.  > 

3. Can I also do my netmasking like this: 255.255.0.255 ? Is this still a 0.0.0.0 /24 masking?
No you can't do that.  The subnet mask must hold contiguous flipped bits (a 1) moving from left to right.  This is how the end of the network ID and the start of the host IP addressing is determined. Look back at the O's and 1's in the last post. > 

This is very interesting and very useful. I cannot thank you enough for your time and help.

I'm sure that this will bring more questions.  It's fine by me.   We'll have a mini IP addressing tutorial when we are done.

---

### Post by clearski on 2013-05-02
> **bab1 said:**
> That's why you write it in decimal but it really is a stream of on/off bits.
This is  more properly stated as:  The subnet mask defines the Network ID and the rest is left to assign to the hosts in the network.  As the netmask defines the Network ID, this also defines the boundaries of the network in question.  Using the network of 192.168.0.0 you can tell what is network and what is the host IP address space.  If we say /24 we mean the first 24 *contiguous *bits are the network ID.  The last 8 bits minus 2 are used for the hosts (routers/printers/workstations/laptops).  The first address ( e.g .0) is reserved for the network ID ( in this case [COLOR=#FF0000]192.168.0.[/COLOR][COLOR=#0000FF]**0**[/COLOR]).  The last number is reserved for broadcasts to the entire network (as in [COLOR=#FF0000]192.168.0[/COLOR].[COLOR=#0000FF]**255**[/COLOR]). 

It seems that what I was thinking of when I said "my network is 192.168.0.0" was in fact referred to as a Network-ID. It's good to know because I found this term when I read some howtos, but I really didn't know what they mean.

> **bab1 said:**
> Binary notation is pretty simple.  [...] 

If I understand correctly, the conversion goes like this (the following two lines are meant just to help doing the conversion, and not a result in any direction):

```

(128)     (64)      (32)     (16)     (8)     (4)     (2)    (1)   [human decimal notation]
  0         0         0        0       0       0       0      0     [computer binary notation] 
```


  0      1     0     0    0     0   0    0
  #That would be a binary representation for number 64 in a single octet of a TCP/IP address

  0      1     0     0    1     1    0    1 
  #That would be a binary representation for number 77 in a single octet of a TCP/IP address

  11000000.10101000.00000000.00000000
  #And that would be the representation for the Network-ID 192.168.0.0


> **bab1 said:**
> The simple answer to this is:  You change the host address space address space by increasing or decreasing the bits devoted to the Netmask.  192.168.1.0 /25 takes 1 bit away from the host addressing making it 7 bits instead of 8.  This gives you 2 networks, each with half the number of host addresses minus 2  for each subnet (Net ID and b'cast)  if you add up the bits we defined above leaving off the left most (e.g. 128) you have the maximum 127 -2 usable addresses for each subnet.  The /24 network has 255 minus 2.  No you can't do that.  The subnet mask must hold contiguous flipped bits (a 1) moving from left to right.  This is how the end of the network ID and the start of the host IP addressing is determined. Look back at the O's and 1's in the last post.

Strange, but now it comes easier to have a binary representation for this, and more difficult to have a  human notation :)

  a) 192.168.1.0 / 24 -> our netmask is [11111111111111111111111100000000] in binary

  b) 192.168.1.0 / 25 -> our netmask is [111111111111111111111111[COLOR=#ff0000]**1**[/COLOR]0000000] in binary

  Basically we took (masked) the first bit (the bold & red one, which represents 128 in decimal) from the last octet of our netmask.

But now I'm unable to write the two networks I have for /25 in decimals. I think that netmask is 255.255.255.127 for both, because there's the first bit missing in both cases, but I can't imagine how to write the network hosts addresses.
  
One could be 192.168.1.0 / 255.255.255.127 (which allows addressing from 0 to 127, of which one is reserved for broadcast and one for NetworkID)
The second could be 192.168.1.255 / 255.255.255.127 (which allows addressing from 128 to 255, of which one is reserved for broadcast and one for NetworkID)

However, I am not sure about these two networks...

> **bab1 said:**
> I'm sure that this will bring more questions.  It's fine by me.   We'll have a mini IP addressing tutorial when we are done.

That would be great and will help others, too. 

I think it'd be also great to have a title for a recommended reading, too, which will discuss TCP/IP Networking from the very basic to some intermediate level. What title do you recommend?

Thank you very much.

---

### Post by bab1 on 2013-05-02
> **clearski said:**
> It seems that what I was thinking of when I said "my network is 192.168.0.0" was in fact referred to as a Network-ID. It's good to know because I found this term when I read some howtos, but I really didn't know what they mean.

If I understand correctly, the conversion goes like this (the following two lines are meant just to help doing the conversion, and not a result in any direction):

```

(128)     (64)      (32)     (16)     (8)     (4)     (2)    (1)   [human decimal notation]
  0         0         0        0       0       0       0      0     [computer binary notation] 
```


  0      1     0     0    0     0   0    0
  #That would be a binary representation for number 64 in a single octet of a TCP/IP address

  0      1     0     0    1     1    0    1 
  #That would be a binary representation for number 77 in a single octet of a TCP/IP address

  11000000.10101000.00000000.00000000
  #And that would be the representation for the Network-ID 192.168.0.0
Yes, all of the above is correct.> 

Strange, but now it comes easier to have a binary representation for this, and more difficult to have a  human notation :)

  a) 192.168.1.0 / 24 -> our netmask is [11111111111111111111111100000000] in binary

  b) 192.168.1.0 / 25 -> our netmask is [111111111111111111111111[COLOR=#ff0000]**1**[/COLOR]0000000] in binary

Indeed this is true.  So far we have only talked about how the OS *views* the bit stream, but not how the OS  uses (manipulates) the bit stream  > 

Basically we took (masked) the first bit (the bold & red one, which represents 128 in decimal) from the last octet of our netmask.

But now I'm unable to write the two networks I have for /25 in decimals. I think that netmask is 255.255.255.127 for both, because there's the first bit missing in both cases, but I can't imagine how to write the network hosts addresses.
This is not the correct way to view this.  The OS needs a way to separate the Network ID ***bit space** from the host addressing**[I] bit space***[/I].  At its essence the netmask defines the size (in bits) of these two spaces.  This means that using a 32 bit address space and a 24 bit netmask we have 24 bits reserved for the Network ID and 8 bits reserved for Host ID's (IP addresses).   The question really is;  How is the netmask used?

The OS uses a method called anding.  This is NOT a cumulative adding of the numbers. but rather a comparison of the numbers.  It works like this:  From left to right, but only **contiguously**, where the mask bit is flipped (a 1) include that in the Network ID space.  When these contiguous flipped bits end we have the boundary between the Network ID space and the Host ID space.  In other words you can't tell the Network ID without both the IP address number and the Netmask.  This means this is just an IP address: 192.168.0.128, but this is a Network ID: 192.168.0.128 /24 when we humans read it. > 
  
One could be 192.168.1.0 / 255.255.255.127 (which allows addressing from 0 to 127, of which one is reserved for broadcast and one for NetworkID)

The second could be 192.168.1.255 / 255.255.255.127 (which allows addressing from 128 to 255, of which one is reserved for broadcast and one for NetworkID)

However, I am not sure about these two networks...
Neither are correct.  The subnet mask for a /25 bit network is 255.255.255.128 (decimal).  The masking is from left to right.  If we add the octet separator to the notation we have```
11111111.11111111.11111111.1000000
``` .... See the end of the flipped bits.  To the left is the Network ID space (25 bits) to the right is the Host ID space (7 bits).  The host ID range for addressing is either 0 to 127 minus the Network ID (0) and the B'cast (127) or from 128 to 255 minus the Network ID (128) and the B'cast (255).  Remember you have created 2 subnets out of  1 network.> 


That would be great and will help others, too. 

I think it'd be also great to have a title for a recommended reading, too, which will discuss TCP/IP Networking from the very basic to some intermediate level. What title do you recommend? 

IP addressing info is all over the Internet.  We're not breaking any new ground here. It's only one small part of the TCP/IP networking protocol.  Most of the time it is not stated in quite the terms we have been using So I don't mind restating it here.  I don't see any reason to formalize it.  I realize it is new to you so we will continue until you are comfortable with IP addressing.

Keep asking questions on the points you don't understand.

---

### Post by clearski on 2013-05-02
Now I realise that we can only tell the Network ID, broadcast and host ID range if we have **both** an IP address and a netmask address. The Network ID is given by anding the bits of the mask with the bits of the IP address. In our case (/25) we only anded the first bit of the last octet, because it was only one bit taken to the netmask address from the host range addresses.

Since I didn't understand your point from the start, I read some more docs on the Internet and I think that everything is clear now.

Below are three studies. The first two with the /25 netmask, and one more difficult case I imagined.

**[EXAMPLE 1]**

```
Binary netmask                        Octal
11111111 11111111 11111111 10000000 : 255.255.255.128

Binary IP address
11000000 10101000 00000001 00010001 : 192.168.1.17

------------------------------------ (Bitwise AND operation 1 and 1 = 1; any other combination is 0)

The Network ID:
11000000 10101000 00000001 00000000 : 192.168.1.0 (Network ID)
```



**[EXAMPLE 2]**

```
Binary netmask                        Octal
11111111 11111111 11111111 [COLOR=#ff0000]1[/COLOR]0000000 : 255.255.255.128

Binary IP address
11000000 10101000 00000001 [COLOR=#ff0000]1[/COLOR]0101101 : 192.168.1.173

------------------------------------ (Bitwise AND operation 1 and 1 = 1; any other combination is 0)

The result:
11000000 10101000 00000001 [COLOR=#ff0000]1[/COLOR]0000000 : 192.168.1.128 (Network ID)
```


**[EXAMPLE 1] **A /25 bit mask address (255.255.255.128) anded to an IP address 192.168.1.17 reveals a Network ID 192.168.1.0, because the flipped bit of the netmask anded with the corresponding bit of the IP address is 0 (1 and 0 = 0), which is 0 in octal representation.

**[EXAMPLE 2]** The same /25 bit mask address (255.255.255.128) anded to an IP address 192.168.1.173 reveals a Network ID 192.168.1.128, because the flipped bit of the netmask anded with the corresponding bit of the IP address is 1 (1 and 1 = 1), which is 128 in octal representation.

Below I tried a more difficult calculation:

**[EXAMPLE 3]**

We have an IP address 144.18.166.15 and a netmask 255.255.255.248. We have to find the Network ID, b'cast and host range addresses.

```
Binary netmask:                       Octal
11111111 11111111 11111111 1111[COLOR=#ff0000]1[/COLOR]000 : 255.255.255.248

Binary IP address
10010000 00010010 10100110 0000[COLOR=#ff0000]1[/COLOR]111 : 144.18.166.15

----------------------------------- (Bitwise AND operation 1 and 1 = 1; any other combination is 0)

The result:
10010000 00010010 10100110 0000[COLOR=#ff0000]1[/COLOR]000 : 144.18.166.8 (Network ID)
```


The number of available host addresses on this subnet is* 2^n - 2* (where *'n' *is the number of 0 bits counted from right to left in the last octet of the netmask, and 2 is substracted because of the two addresses we have to reserve: Network ID and b'cast).

In this case, we have three 0 bits, so the number of possible hosts addresses is 2^3 - 2 = 6.

The Network ID is 144.18.166.8, the b'cast is 144.18.166.15, and the the range of available hosts addresses is from 144.18.166.9 to 144.18.166.14.

For all three examples above, I could have used only the last octet for calculations (anding), because the first three octets of the netmask were 255.255.255, so the first three octets of the IP address were not affected by masking in any way.

I've never thought I would do these binary and octal calculations, in fact I have to say that I didn't like these in school. :)

---

### Post by bab1 on 2013-05-02
> For all three examples above, I could have used only the last octet for calculations (anding), because the first three octets of the netmask were 255.255.255, so the first three octets of the IP address were not affected by masking in any way.
They are part of the netmask.  They are part of the contiguous flipped bits of the mask starting from the farthest left position..  Remember, from left to right the bits march.  The computer can't see what you see.  It just computes the flow of bits from some stop mark  that is defined int he protocol.

Try using 255.255.240.0 for a subnet mask.  How many bits are in this subnet mask?  How may hosts are there in the network?  Try it with a 16 bit mask or a 8 bit mask.  If you had a /16 bit network how many subnets can you make.  Consider that they all don't need to to have 255 addresses.

---

### Post by bab1 on 2013-05-02
> **clearski said:**
> Now I realise that we can only tell the Network ID, broadcast and host ID range if we have **both** an IP address and a netmask address. The Network ID is given by anding the bits of the mask with the bits of the IP address. In our case (/25) we only anded the first bit of the last octet, because it was only one bit taken to the netmask address from the host range addresses.

Since I didn't understand your point from the start, I read some more docs on the Internet and I think that everything is clear now.

Below are three studies. The first two with the /25 netmask, and one more difficult case I imagined.

**[EXAMPLE 1]**

```
Binary netmask                        Octal
11111111 11111111 11111111 10000000 : 255.255.255.128

Binary IP address
11000000 10101000 00000001 00010001 : 192.168.1.17

------------------------------------ (Bitwise AND operation 1 and 1 = 1; any other combination is 0)

The Network ID:
11000000 10101000 00000001 00000000 : 192.168.1.0 (Network ID)
```



**[EXAMPLE 2]**

```
Binary netmask                        Octal
11111111 11111111 11111111 [COLOR=#ff0000]1[/COLOR]0000000 : 255.255.255.128

Binary IP address
11000000 10101000 00000001 [COLOR=#ff0000]1[/COLOR]0101101 : 192.168.1.173

------------------------------------ (Bitwise AND operation 1 and 1 = 1; any other combination is 0)

The result:
11000000 10101000 00000001 [COLOR=#ff0000]1[/COLOR]0000000 : 192.168.1.128 (Network ID)
```


**[EXAMPLE 1] **A /25 bit mask address (255.255.255.128) anded to an IP address 192.168.1.17 reveals a Network ID 192.168.1.0, because the flipped bit of the netmask anded with the corresponding bit of the IP address is 0 (1 and 0 = 0), which is 0 in octal representation.
Because ***all the contiguous bits*** mask the IP address and reveal the NetID. > 

**[EXAMPLE 2]** The same /25 bit mask address (255.255.255.128) anded to an IP address 192.168.1.173 reveals a Network ID 192.168.1.128, because the flipped bit of the netmask anded with the corresponding bit of the IP address is 1 (1 and 1 = 1), which is 128 in octal representation.
Not really.  The .17 can only exist in the 192.168.1.0 /25 network ( as the range is 0 to 127).  The same is true for the .173 address. It can only exist in the 192.168.1.128 /25 network (as the range is  to 128 to 255), minus of course the 2 non-valid addresses that are part of any network.(subnet).> 

Below I tried a more difficult calculation:

**[EXAMPLE 3]**

We have an IP address 144.18.166.15 and a netmask 255.255.255.248. We have to find the Network ID, b'cast and host range addresses.

```
Binary netmask:                       Octal
11111111 11111111 11111111 1111[COLOR=#ff0000]1[/COLOR]000 : 255.255.255.248

Binary IP address
10010000 00010010 10100110 0000[COLOR=#ff0000]1[/COLOR]111 : 144.18.166.15

----------------------------------- (Bitwise AND operation 1 and 1 = 1; any other combination is 0)

The result:
10010000 00010010 10100110 0000[COLOR=#ff0000]1[/COLOR]000 : 144.18.166.8 (Network ID)
```


The number of available host addresses on this subnet is* 2^n - 2* (where *'n' *is the number of 0 bits counted from right to left in the last octet of the netmask, and 2 is substracted because of the two addresses we have to reserve: Network ID and b'cast).



Not always the last octet.  The bits available for the hosts IP addressing (Host ID) is **_all the available bits after the mask boundary._**  For example, if we have 16 bits of mask (NetID) then we have 16 bit of range for Host ID.  If we have a network of 192.168.0.0 /16 then we could conceivably have a legitimate IP address of 192.168.4.128 in the same network as the IP address of  192.168.0.15.  They are both in the same network.  There are 65534 legitimate IP addresses in that network.  So you can have very small or very large IP networks.  The range is all defined by the subnet mask.   > 

In this case, we have three 0 bits, so the number of possible hosts addresses is 2^3 - 2 = 6.

The Network ID is 144.18.166.8, the b'cast is 144.18.166.15, and the the range of available hosts addresses is from 144.18.166.9 to 144.18.166.14.

For all three examples above, I could have used only the last octet for calculations (anding), because the first three octets of the netmask were 255.255.255, so the first three octets of the IP address were not affected by masking in any way.

I've never thought I would do these binary and octal calculations, in fact I have to say that I didn't like these in school. :)

Maybe it will help you to see this with a calculator.  Here is the one I use [**_[COLOR="#0000FF"]http://www.subnet-calculator.com/cidr.php[/COLOR]_**]("http://www.subnet-calculator.com/cidr.php")

get lazy and use it after you understand it all.  ;-)

---

### Post by clearski on 2013-05-03
I am now able to tell the Network ID, host address range & broadcast with the IP and masks bits.

All calculations below were done on paper and verified with CIDR Calculator.

192.168.14.24 /11 : 192.160.0.0 (Network ID); Range from: 192.160.0.0 to 192.191.255.255

44.87.112.25 /20:  44.87.112.0 (Network ID); Range from: 44.87.112.0 to 44.87.127.255

16.87.55.94 /17:   16.87.0.0 (Network ID); Range from: 16.87.0.0 to 16.87.127.255
 
125.14.1.123 /9 :   125.0.0.0 (Network ID); Range from: 125.0.0.0 to 125.127.255.255

204.222.144.15 /29:  204.222.144.8 (Network ID); Range from: 204.222.144.8 to 204.222.144.15  

111.111.2.243 /14:  111.108.0.0 (Network ID); Range from: 111.108.0.0 to 111.111.255.255


But I have to say that I can't do it without a paper and a pen (in my case, that is GEdit and my keyboard) and I'm not sure I do it the way you do.


Example: 11.67.89.123 /11

/11 means 8+3, so we have three flipped bits in the second octet, followed by five 0s.

I pull the second octet away from the netmask and write its mask, and underneath the second octet from the IP address.

11100000 (second octet of netmask)
01000011 (second octet of the IP address)

I compare the numbers and see that the 2nd bit from left to right is common. This gives the NetworkID number in decimals (64) for the second octet. The Network ID is 11.64.0.0

Then I see that the second octet has five 0 bits (that is 16+8+4+2+1 = 31 in decimals), it means that the end range is 11.95 (64+31).255.255. The broadcast is 11.95.255.255.

Maybe its somehow twisted, but it's the only way I can do these calculations now. I verified them all with CIDR and all were correct. I think I have a problem with seeing these as a computer does. Yet... I just can't imagine how I can see these easier...

---

### Post by bab1 on 2013-05-03
> **clearski said:**
> I am now able to tell the Network ID, host address range & broadcast with the IP and masks bits.

All calculations below were done on paper and verified with CIDR Calculator.

```
192.168.14.24 /11 : 192.160.0.0 (Network ID); Range from: 192.160.0.0 to 192.191.255.255

44.87.112.25 /20:  44.87.112.0 (Network ID); Range from: 44.87.112.0 to 44.87.127.255

16.87.55.94 /17:   16.87.0.0 (Network ID); Range from: 16.87.0.0 to 16.87.127.255
 
125.14.1.123 /9 :   125.0.0.0 (Network ID); Range from: 125.0.0.0 to 125.127.255.255

204.222.144.15 /29:  204.222.144.8 (Network ID); Range from: 204.222.144.8 to 204.222.144.15  

111.111.2.243 /14:  111.108.0.0 (Network ID); Range from: 111.108.0.0 to 111.111.255.255

```

But I have to say that I can't do it without a paper and a pen (in my case, that is GEdit and my keyboard) and I'm not sure I do it the way you do.

Example: 11.67.89.123 /11

/11 means 8+3, so we have three flipped bits in the second octet, followed by five 0s.

I pull the second octet away from the netmask and write its mask, and underneath the second octet from the IP address.

11100000 (second octet of netmask)
01000011 (second octet of the IP address)

I compare the numbers and see that the 2nd bit from left to right is common. This gives the NetworkID number in decimals (64) for the second octet. The Network ID is 11.64.0.0

Then I see that the second octet has five 0 bits (that is 16+8+4+2+1 = 31 in decimals), it means that the end range is 11.95 (64+31).255.255. The broadcast is 11.95.255.255.

Maybe its somehow twisted, but it's the only way I can do these calculations now. I verified them all with CIDR and all were correct. I think I have a problem with seeing these as a computer does. Yet... I just can't imagine how I can see these easier...

We have progressed from *what* is it to *how* it works.  Now we look at **why**.  ;-)

In the above examples you have taken an individual host's IP address and applied a subnet mask to derive the Net ID and Host ID range.  While you can do that, it serves no purpose in the real world.  All of this is sub-netting is really for a network administrator to manage the network(s) they control.  

An example here might help you understand.  Let's say you work for a business that is assigned a /20 network.  How many sub-networks can you create to provide sub-networks for all the various departments you will have in the overall network?  As the network manager your interest is in overall network allocation (IP ranges) not in individual IP addresses.

When you calculate these, you would start with the range (255, or 2048 or 4096 addresses) needed and assign the particular range to a department arbitrarily from the network you control.  The thing to bear in mind is to not assign a range that is overlapping with another (remember boundaries).

The network 172.16.0.0 /20 has a range of 172.16.0.0 to 172.31.255 (4096 hosts).  It can be sub-netted in this manner```

2 subnets with a range of 2048 addresses in each (/21)
4 subnets with a range of 1024 addresses in each (/22)
8  subnets with a range of 512 addresses in each (/23)
16 subnets with a range of 256 addresses in each (/24)
32 subnets with a range of 128 addresses in each (/25)
and so on ... 

```...or any combination of subnets.  You could have four /24 nets, two /23 nets and one /21 subnet if you wanted to.

Since we know the starting and ending addresses of the main network we can determine how all these subnets will fit in to the overall picture.  When  IP address assigned   to an individual host the subnet mask has been determined already by this method.  The end user just needs to accept it (via DHCP) or configure the individual host with the IP/mask pair.

In short you look at sub-netting from the network down, rather than from the individual host up.  If the truth be told; I use the calculator now when doing the calculations for any network I design.

---

### Post by clearski on 2013-05-03
> **bab1 said:**
> In the above examples you have taken an individual host's IP address and applied a subnet mask to derive the Net ID and Host ID range.  While you can do that, it serves no purpose in the real world.  All of this is sub-netting is really for a network administrator to manage the network(s) they control. 

Yes, it is true. I know that mastering subnetting would a great step forward and what I've done was just a warm-up. :)

I'll stop here with my network (IP) related questions for the moment. I've found some Cisco training docs on IP subnetting, I'll try to take as much as I can from there. I've seen they are taking the bit masking thing to a higher level. They also discuss classes, private / public / reserved addresses etc. Not very detailed, but enough to progress (hopefully).

I'll take a few days off for Easter, so I'll be back on the forums next week. The Ubuntu Unleashed book will be ordered and will arrive soon, but even though I'm sure there will be questions. :) Hundreds of pages of golden guides and info. :) Can't wait!

Thank you very, very much for your time and help and we keep in touch! :)

---

