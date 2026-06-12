---
title: "Ubuntu Server Static Networking"
date: 2011-06-15
forum: Networking &amp; Wireless
---

### Post by kroq-gar78 on 2011-06-15
To the Ubuntu Forums Community,

I'm using an Ubuntu server 10.04 that I set up on an external 2TB USB harddrive. I'm trying to get a static ip on it because I don't have to keep physically going to the computer to find the IP address so i can SSH and configure apache, mediawiki, and all the other cool stuff Ubuntu can do. I can't (aka really don't want to) use an Ethernet b/c its kinda far, but I don't think thats the problem - wifi vs. ethernet. It's connected to a laptop, so it has wifi built-in. I set up some static IP stuff in /etc/network/interfaces as posted here:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# eth1 with dhcp
auto eth1
iface eth1 inet dhcp

# eth1 with static IP
#auto eth1
#iface eth1 inet static
#    address 192.168.2.106
#    netmask 255.255.255.0
#    network 192.168.2.0
#    broadcast 192.168.2.255
#    gateway 192.168.2.200

# wlan0 base (don't comment out the line below)
auto wlan0
# wlan0 with DHCP
#iface wlan0 inet dhcp
# wlan0 with static IP
iface wlan0 inet static
    address 192.168.2.101
    netmask 255.255.0.0
    network 192.168.2.0
    broadcast 192.168.2.255
    gateway 192.168.2.200
wireless-essid *removed*
wireless-key *removed*
wireless-mode managed
```Where "*removed*" means that I have taken the text out of this post for security. At the top, I WAS going to do static ethernet, but I decided I wasn't really going to use and and set it back to DHCP (that what the commented part is).

My laptop (and all other computers, actually) are on DHCP and for some reason switch between 192.168.2.* and 192.168.1.* because some configuration is messed up in my router (I can't fix it; no permissions). Now, I'm pretty noobish when it comes to networking, so I was hoping that you guys here in the forums can help. I have a samba and apache server on the server and want full-time access to it without ssh-ing and changing the ip to the 192.168.1 or 192.168.2 networks every time my laptop switches networks, respectively. I can't access the server with my laptop when they're on different "networks". Can you please help? Post if you need clarification or something.

Thanks in advance.

Sincerely,
kroq-gar78

---

### Post by papibe on 2011-06-15
Before getting into details, What is your router brand and model?

The easiest way to set up an static IP for a machine in a LAN is to set it up on the router. Either using reservation or the static range. This way you don't need to modify anything in your computer.

Regards.

BTW, not all routers supports that.

---

### Post by kroq-gar78 on 2011-06-15
Its a Verizon one, but I can't do anything with it; I don't have permissions to modify it (aka no password). I really want to use WiFi ot do the static IP. Whenever my laptop goes to a different "network", I can't see the server anymore, so would broadcast or network have something to do with that?

---

### Post by crispy_420 on 2011-06-15
So Verizon locks you out of the router, that is no fun.

What do you mean you mean by you mean by when you leave your network you can't see your server anymore? Do you mean when you leave home you have no access?

---

### Post by papibe on 2011-06-15
According to the Verizon/FIOS support forums, their routers can be reset and after that it is the usual suspects:

> Upon reset, the user account will be "admin" and the password will be one of:
 
password
password1
the router's serial number (upper case)
 
You should change the password immediately upon login as there are several known security exploits associated with routers that use the default passwords.
 

---

### Post by kroq-gar78 on 2011-06-15
Nonononono, I don't think you understand what I mean. I don't manage my home network, and that person who does is currently away (and probably won't bother to do the static thing anyway); he won't give me the password/credentials required to loginto the router.

---

### Post by kroq-gar78 on 2011-06-15
> **crispy_420 said:**
> So Verizon locks you out of the router, that is no fun.

What do you mean you mean by you mean by when you leave your network you can't see your server anymore? Do you mean when you leave home you have no access?
yeah sorry, I'm not too good at explaining this.... When I say "network", I mean the 3rd byte in the IP address. So, when I switch from 192.168.2.* to 192.168.1.*, I call it "switching networks". I know, bad terminology, but I don't know what to call it otherwise :(

When my laptop (as in non-server) tries to log into the server when my toshiba (non-server) is on 192.168.1 and my server is on 192.168.2, I can't log in, and vice versa.

---

### Post by crispy_420 on 2011-06-15
What is you subnet? Most home setups are 255.255.255.0 so it would be impossible that 192.168.1.X and 192.168.2.X could ever connect anyway.

---

### Post by kroq-gar78 on 2011-06-15
oh, this I did not know...

Regardless - If by subnet you mean the subnet in my server's /etc/network/interfaces file, it's 255.255.0.0

---

### Post by dandnsmith on 2011-06-15
I think you need to make sure the netmasks are uniform for your local network at 255.255.0.0 rather than 255.255.255.0, then, if there are still problems it would be something in the routing.
However, getting the detail using DHCP may well set netmask to 255.255.255.0 automatically, as that is what it would expect as default setting.

---

### Post by kroq-gar78 on 2011-06-15
so do i change the netmask on every computer I want to use the server on? if so, how would I do it? sorry, I really don't know too much about networking...

---

### Post by capscrew on 2011-06-15
> **kroq-gar78 said:**
> so do i change the netmask on every computer I want to use the server on? if so, how would I do it? sorry, I really don't know too much about networking...

I have to assume you should use 255.255.255.0 for all of your subnet masks in your network.  Most folks do not need anything else.

The subnet mask *_defines the boundaries_* of the network.  By that I mean that is defines what is a network ID number (i.e **[COLOR="Blue"]192.168[/COLOR]**.0.0 (uses 255.255.0.0 or [COLOR="Green"]**192.168.0**[/COLOR].0  (uses 255.255.255.0).

The host number is those number that are NOT MASKED (i.e 192.168.**[COLOR="Blue"]0.1[/COLOR]** to 192.166.**[COLOR="Blue"]255.255[/COLOR]** (using 255.255.0.0) or 192.168.0.**[COLOR="Green"]1[/COLOR]** to 192.168.0.**[COLOR="Green"]255[/COLOR]** (using 255.255.255.0

This explains why it looks as if your server is switching networks -- It is not.  The network encompasses all of those hosts because the subnet mask is set at 255.255.0.0 (65534 hosts) instead of 255.255.255.0 (254 hosts).

Anther way to look at it is that a 255.255.255.0 subnet mask creates these subnets using 192.168 to start```

192.168.0.0
192.168.1.0
192.168.3.0
192.168.4.0
192.168.5.0
... to 
192.168.253.0
192.168.254.0
192.168.255.0

```

And a 255.255.0.0 subnet mask creates one network with 65534 hosts in it:
```
192.168.0.0
```

See [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://www.cisco.com/en/US/tech/tk365/technologies_tech_note09186a0080093f33.shtml") for all the gory details.

---

### Post by kroq-gar78 on 2011-06-15
I'm not exactly getting on what machine/device I have to set the subnet mask on: the router? the server? the clients (machines that I want to be able to access/see the server on/from)? I think I KIND OF understand what you're saying, capscrew - probably one of the best explanations on the internet, but is my client machine the problem? My computer has a subnet of 255.255.255.0, so is that why it can't see the server? So, theoretically, I CAN access the clients FROM my server (b/c 255.255.0.0 subnet in interfaces file), but not vice versa if they have a different 3rd byte (.1.* or .2.*)?

Thanks for all you guys' help so far.

---

### Post by capscrew on 2011-06-15
> **kroq-gar78 said:**
> I'm not exactly getting on what machine/device I have to set the subnet mask on: the router? the server? the clients (machines that I want to be able to access/see the server on/from)?
In your case you should set the subnet mask to 255.255.255.0 on all hosts (computers) in your local network (LAN).  They also should be members of the same network (i.e [COLOR="Purple"]192.168.0[/COLOR].[COLOR="DarkGreen"]0[/COLOR] or [COLOR="Purple"]192.168.1[/COLOR].[COLOR="DarkGreen"]0[/COLOR] or [COLOR="Purple"]192.168.2[/COLOR].[COLOR="DarkGreen"]0[/COLOR]).  Any of these have 253 usable IP addresses (.[COLOR="DarkGreen"]1 [/COLOR]to .[COLOR="DarkGreen"]254[/COLOR]). > 

 I think I KIND OF understand what you're saying, capscrew - probably one of the best explanations on the internet, but is my client machine the problem? My computer has a subnet of 255.255.255.0, so is that why it can't see the server? So, theoretically, I CAN access the clients FROM my server (b/c 255.255.0.0 subnet in interfaces file), but not vice versa if they have a different 3rd byte (.1.* or .2.*)?...
Just set 'em all to 255.255.255.0 and make the IP addresses in the same range ([COLOR="DarkGreen"]see above[/COLOR] (Notice the colors?)).

Edit:
> if they have a different 3rd byte (.1.* or .2.*)?
IPv4 networks and addresses are based on 8bit sections called octets.  So the section you are referring to is the 3rd octet.  The are really decimal representations of binary numbers.  In the case of 255.255.255.0 , there are 3 octets that have all the bits as 1 (on) and one octet with all bits a 0 (off).  it looks like this```
[COLOR="Purple"]11111111.11111111.11111111.[/COLOR][COLOR="DarkGreen"]00000000[/COLOR]
```

The on bits are the network and the off bits are the IP addresses for the hosts.  If you just count the bits there are 24 bits in the Network side (purple).  Another way to describe a network is this way```
192.168.1.0/24
``` The /24 is the subnet mask described as on bits.

---

### Post by kroq-gar78 on 2011-06-15
Ah, thanks for the extra info, clears up lots of stuff up for me. As I mentioned in one of the previous posts, my machines (non-server) strangely switch between .2.* and .1.* Is there any way to work around that? Currently, my machine is on the 192.168.2 "network", but it sometimes switches to 192.168.1 (i think when it requests for renewal or something like that on my router). Is there any way for my server to be accessible from either of those 2 "networks" while having one, static IP address?

---

### Post by capscrew on 2011-06-16
> **kroq-gar78 said:**
> Ah, thanks for the extra info, clears up lots of stuff up for me. As I mentioned in one of the previous posts, my machines (non-server) strangely switch between .2.* and .1.* Is there any way to work around that? Currently, my machine is on the 192.168.2 "network", but it sometimes switches to  (i think when it requests for renewal or something like that on my router). Is there any way for my server to be accessible from either of those 2 "networks" while having one, static IP address?

It appears that they are not on different networks, but without actually seeing the router configuration I cant be sure.  Here is how I see it.  The network is not *192.168.1* or *192.168.2* but rather, it is 192.168 (actually 192.168.0.0 /16 (255.255.0.0)).  This network described in binary as this 
```

[COLOR="Purple"]11000000.10101000[/COLOR].[COLOR="DarkGreen"]00000000.00000000[/COLOR] = 192.168.0.0
[COLOR="Purple"]11111111.11111111[/COLOR].[COLOR="DarkGreen"]00000000.00000000[/COLOR] = 255.255.0.0
```

All of the numbers that are in the green area are host numbers in the network. This means that 192.168.2.1 is in the same network as 192.168.1.1.  You can see this here

```

[COLOR="Purple"]11000000.10101000[/COLOR].[COLOR="DarkGreen"]000000[SIZE="3"]**[COLOR="Blue"]1[/COLOR]**[/SIZE]0.0000000**[COLOR="Navy"]1[/COLOR]**[/COLOR] = 192.168.[COLOR="Blue"]**2.1**[/COLOR]
[COLOR="Purple"]11111111.11111111[/COLOR].[COLOR="DarkGreen"]00000000.00000000[/COLOR] = 255.255.0.0

[COLOR="Purple"]11000000.10101000[/COLOR].[COLOR="DarkGreen"]0000000[SIZE="3"]**[COLOR="Blue"]1[/COLOR]**[/SIZE].0000000**[COLOR="Navy"]1[/COLOR]**[/COLOR] = 192.168.[COLOR="Blue"]**1.1**[/COLOR]
[COLOR="Purple"]11111111.11111111[/COLOR].[COLOR="DarkGreen"]00000000.00000000[/COLOR] = 255.255.0.0

```
Remember all the green numbers are for your computers while the purple describes the Network ID.  The subnet mask sets the boundary between the purple and green numbers.

To my way of thinking all you need to do is make all of you computers have a subnet mask of 255.255.0.0 and set the static IP of the server as a number that is **not part of the DHCP pool.**.  Do you know the range of numbers that are in the pool of numbers that DHCP hands out?  These are the IP addresses that the routers DHCP service hands out.  The reason to not use a number in the pool is that it will cause conflicts that you will see as errors.

As an **example**, I would try this on the wlan interface
```

# wlan0 base (don't comment out the line below)
auto wlan0 

wlan0 with static IP
iface wlan0 inet static
    address 192.168.[COLOR="DarkGreen"]200.101[/COLOR]
    netmask 255.255.0.0
    network 192.168.[COLOR="DarkRed"]**0.0**[/COLOR]
    broadcast 192.168.[COLOR="SeaGreen"]**255.255**[/COLOR]
    gateway 192.168.2.200


```

the interface wlan0 would look like this in binary
```

[COLOR="Purple"]11000000.10101000[/COLOR].[COLOR="DarkGreen"]1000[COLOR="Blue"]**1**[/COLOR]000.0**[COLOR="Blue"]11[/COLOR]**00**[COLOR="Blue"]1[/COLOR]**0[/COLOR][COLOR="Blue"]**1**[/COLOR] = 192.168.[COLOR="Blue"]**200.101**[/COLOR]
[COLOR="Purple"]11111111.11111111[/COLOR].[COLOR="DarkGreen"]00000000.00000000[/COLOR] = 255.255.0.0

```

See how even though we are using a number that ends in 200.101 that it still is a legitimate host number in the green.

---

### Post by kroq-gar78 on 2011-06-16
ok, so I know (I peeked at the router config while he was editing it ;)   ) that the DHCP rangeon 192.168.1 is somewhere from .2-.10, and the range of 192.168.2 is somewhere from .90 to .120. Is there a way that DOESN'T require me to set all my machines on 255.255.0.0? Sorry, I know that you can't do much w/o router info, but I won't be able to get my hands on it (MAYBE, at best) until mid July.

Anyway, I set my wlan0 interface config to this:
```
iface wlan0 inet static     address 192.168.**54**[COLOR=DarkGreen]**.78**
[/COLOR]    netmask 255.255.0.0     network 192.168.[COLOR=DarkRed]**0.0**[/COLOR]
broadcast 192.168.[COLOR=SeaGreen]**255.255**[/COLOR]
gateway 192.168.2.200
```but I still can't ping it or ssh into it (or web w/ apache); I'm assuming this is because my subnet mask on the client is still 255.255.255.0

Can I still have DHCP while using a manually configured subnet? I (sadly) am using mainly windows on the client b/c games, but all of my other computers use linux. Do you know how to do this (subnet change w/o removing DHCP), if it's even possible, on ubuntu?

Thanks for all your help.

---

### Post by capscrew on 2011-06-16
> **kroq-gar78 said:**
> ok, so I know (I peeked at the router config while he was editing it ;)   ) that the DHCP rangeon 192.168.1 is somewhere from .2-.10, and the range of 192.168.2 is somewhere from .90 to .120. Is there a way that DOESN'T require me to set all my machines on 255.255.0.0? Sorry, I know that you can't do much w/o router info, but I won't be able to get my hands on it (MAYBE, at best) until mid July.

Anyway, I set my wlan0 interface config to this:
```
iface wlan0 inet static     address 192.168.**54**[COLOR=DarkGreen]**.78**
[/COLOR]    netmask 255.255.0.0     network 192.168.[COLOR=DarkRed]**0.0**[/COLOR]
broadcast 192.168.[COLOR=SeaGreen]**255.255**[/COLOR]
gateway 192.168.2.200
```but I still can't ping it or ssh into it (or web w/ apache); I'm assuming this is because my subnet mask on the client is still 255.255.255.0

Can I still have DHCP while using a manually configured subnet? I (sadly) am using mainly windows on the client b/c games, but all of my other computers use linux. Do you know how to do this (subnet change w/o removing DHCP), if it's even possible, on ubuntu?

Thanks for all your help.
I would have to see the manual on this specific router (exact maker and model#) to understand how one is allowed set up to set up 2 conflicting DHCP pools.  In a sense 2 IP networks.  The only possible scenario I can see is that the router also handles the VOIP for the phones.

I'm not even going to guess on how to work around those issues.  Your question about using a manually set subnet mask is great.  The best answer I can give you is:  The dupal (pair) of IP address and Subnet mask define your hosts location on the network.  They tell other hosts what network is and specific host IP address in that network.  

It would be as if I gave you my address as: Broadway or 1256 or New York City.  None of those are enough to get you to the correct address, but 1255 Broadway, New York City does.

You could in theory separate the responsibility of IP address and subnet mask configuration, but as a practical matter I don't think it will happen.

---

### Post by kroq-gar78 on 2011-06-16
Thanks for the info. It does have a vonage modem (or whatever you call it) connected to it, in case you asked. So, it seems that w/o the router info/config I have to switch all of the subnets on the client machines to the same thing to make it work? How do I go about this w/o setting them all to stastic IP's?

Thanks for the help.

---

### Post by capscrew on 2011-06-17
> **kroq-gar78 said:**
> ... So, it seems that w/o the router info/config I have to switch all of the subnets on the client machines to the same thing to make it work? 
Like I told you before.  It is just a guess.  So the answer to the question is:  I guess so.> 

How do I go about this w/o setting them all to stastic IP's?

I can't really give you advice in this area non of my Linux machines use DHCP.  I would be an experiment for me as much as it is for you.

I don't even know that changing the subnet mask will work for you.  Remember we don't know the actual DHCP configuration on the router. 

I do know that the man page shows that you can force your DHCP client to request a specific subnet.  The file is located at ```
/etc/dhcp3/dhclient.conf
```  The instructions available here```
man dhclient.conf 
```  

Look in the section called *_lease_* The command you place in the dhclient.conf file is```
option subnet-mask 255.255.0.0;
```

---

