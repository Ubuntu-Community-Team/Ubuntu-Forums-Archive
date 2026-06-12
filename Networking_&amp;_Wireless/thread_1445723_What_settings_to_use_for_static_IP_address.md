---
title: "What settings to use for static IP address?"
date: 2010-04-03
forum: Networking &amp; Wireless
---

### Post by mjpatey on 2010-04-03
Hi, all-

Been around the block a few times, but never have gotten the hang of the deeper things of networking in Karmic.  This never seemed to be an issue in some earlier versions of Ubuntu (I got on board at 6.06).  I've tried editing /etc/network/interfaces in the past, but it's led to disaster every time, doubtless due to my lack of understanding.  I've also tried using wicd, and don't remember how I screwed that one up, but I managed to!  :-)

So I'm trying to get it done right now using Network Manager.  Its GUI has the following standard list of fields for me to fill out:

- Address, Netmask and Gateway (all particular to the connection, in this case eth0)

- DNS servers and Search Domains (which presumably apply to all connections)

So... I check ifconfig to get the basic values I'm looking for.  It gives me the following for eth0:

> eth0      Link encap:Ethernet  HWaddr yo:uc:an:tr:ea:dme  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4dff:fe96:98f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:930753 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1217500 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:490218875 (490.2 MB)  TX bytes:1276388509 (1.2 GB)
          Interrupt:29 Base address:0x4000 
Of course, I want to change the 192.168.1.102 to a static value, so I put my desired value (192.168.1.111) in Network Manager's "Address" field.

In its "Netmask" field, I copied the value listed in ifconfig as "Mask" (255.255.255.0).

In the "Gateway" field, I copied the value from ifconfig's "Broadcast" parameter, which I assume is where I went wrong (192.168.1.255).  I don't know what else to put there... any ideas?

Then in Network Manager's "DNS Servers" field, I gave it 192.168.1.1 (the address of my router).

In the "Search Domains" field I simply typed google.com.  Is this the sort of thing it's looking for here?

The above values, my best shot, result in no Internet for me.  I've tried to understand this in the past and have failed miserably.  So thanks in advance for any light you may be able to shed!

-Mark

---

### Post by capscrew on 2010-04-03
```

```> **mjpatey said:**
> ...

So I'm trying to get it done right now using Network Manager.  Its GUI has the following standard list of fields for me to fill out:

- Address, Netmask and Gateway (all particular to the connection, in this case eth0)

- DNS servers and Search Domains (which presumably apply to all connections)

So... I check ifconfig to get the basic values I'm looking for.  It gives me the following for eth0:



Of course, I want to change the 192.168.1.102 to a static value, so I put my desired value (192.168.1.111) in Network Manager's "Address" field.

In its "Netmask" field, I copied the value listed in ifconfig as "Mask" (255.255.255.0).

In the "Gateway" field, I copied the value from ifconfig's "Broadcast" parameter, which I assume is where I went wrong (192.168.1.255).  I don't know what else to put there... any ideas?

[COLOR="Blue"]Typically the gateway is the route out of the network.  This should be the nearside interface address of the router (i.e. 192.168.1.1) [/COLOR]> 

Then in Network Manager's "DNS Servers" field, I gave it 192.168.1.1 (the address of my router).

In the "Search Domains" field I simply typed google.com.  Is this the sort of thing it's looking for here?
[COLOR="Blue"]Nope.  This is the domain of your network.  It is added to the end of your hostname if you do not specifically add it.[/COLOR]> 

The above values, my best shot, result in no Internet for me.  I've tried to understand this in the past and have failed miserably.  So thanks in advance for any light you may be able to shed!

-Mark
[COLOR="Blue"]So you need```
IP address = 192.168.1.111
Subnet Mask = 255.255.255.0
Gateway= 192.168.1.1

``` 

Optionally: if you have set up a DNS domain that you want suffixed to your DNS search (resolution) of hostname you can add a "search domain".

[/COLOR]

---

### Post by dineshs on 2010-04-03
Also if you are using network manager,your /etc/network/interfaces should contain only this```
auto lo
iface lo inet loopback
```

---

### Post by mjpatey on 2010-04-03
Thanks, both of you!  Capscrew, I will try those settings when I get home.  Thanks for the explanation!  Dineshs, that's exactly what mine says.  Thank you!

-Mark

---

### Post by oldfred on 2010-04-03
I also tried to use a address that was within the range that DHCP was using and it did not work.
I also would go back and edit out your HWaddr. I actually spoofed mine when I switched computers and then when I got my router I used the same HW address.

This worked:

---

### Post by 98cwitr on 2010-04-03
if you to 192.168.1.1 in a browser does it pull up your router? If not try 192.168.1.100 or 192.168.1.254 <--- these will be your gateway address if they work

I bet your router is set to use a starting IP 192.168.1.100 - 254, might want to use that for your host address(es).

---

### Post by capscrew on 2010-04-03
> **98cwitr said:**
> if you to 192.168.1.1 in a browser does it pull up your router? If not try 192.168.1.100 or 192.168.1.254 <--- these will be your gateway address if they work

I bet your router is set to use a starting IP 192.168.1.100 - 254, might want to use that for your host address(es).

The OP stated that he was configuring a static IP address.  This means he wants to use an address that is within the range of addresses defined by the combination of the network ID (192.168.1.0) and the subnet mask (255.255.255.0), ***[COLOR="DarkSlateGray"]but not within the DHCP pool[/COLOR]***.  The router uses part of the network range for the pool, but not all of it.

My own home network uses 192.168.1.0 (255.255.255.0).  I have a DHCP pool of .100 to .125.  I have my printers in the .200 range and my servers in the .10 to .19 range.  My static hosts (desktops) are .50 to .59 range.

---

### Post by capscrew on 2010-04-03
> **oldfred said:**
> I also tried to use a address that was within the range that DHCP was using and it did not work.

No static IP addresses (manually configured) should be using the DHCP pool addresses.  An address that does not change does not define a static IP address.  A DHCP served IP address that does not change (reserved) is still a DHCP address (a lease).  A static IP address is always manually configured.  Most of the time this used to mean in the /etc/network/intervaces file.  Network Manager now stores this info elsewhere.  There are some subtle changes using NM.  The interface does not active until you log in.  To me this is unacceptable for a server.  I still configure using the /etc/network/interfaces file.  > 
I also would go back and edit out your HWaddr. I actually spoofed mine when I switched computers and then when I got my router I used the same HW address.

I would not mess with the MAC address when configuring the interface on the host.  It's not needed to successfully configure the address.

---

### Post by oldfred on 2010-04-03
Sorry, I did not mean for the OP to edit his HW address on his computer but in his post. 

I only spoofed mine before I had a router and comcast would make me wait 20 minutes when I plugged in a different computer. When I make the HW address the same I was immediately online.

---

### Post by mjpatey on 2010-04-03
Capscrew, you make a good point... I may delve into editing /etc/network/interfaces again soon.

The DHCP addresses begin for me in the 192.168.1.100 range, and I have 9 devices that might vie for an address at any given time (including phones and handheld gaming devices).  So what I like to do is assign my 2 always-on desktops a static IP address if possible, and I like to call them .111 and .222... easy to remember, and not likely to interfere with any of the dynamically-assigned devices.  I've never known if that's a problem or not, but .111 makes it so that I don't really need to care, I guess!

Is there a reason I should try numbers outside the range where DHCP assigns addresses, like .11 and .22, maybe?

Thanks to everybody for the great information and discussion, and I wish I were home to try all this out!  I'll report back as soon as I do.

-Mark

---

### Post by oldfred on 2010-04-03
Its is not the range within DHCP you use but the range that the router has defined for DHCP. You have to assign your manual setting outside the defined range, You may be able to set that in your router but on mine I think it is fixed.

---

### Post by mjpatey on 2010-04-03
Thanks, oldfred, I'll try that.

---

### Post by capscrew on 2010-04-03
> **mjpatey said:**
> Capscrew, you make a good point... I may delve into editing /etc/network/interfaces again soon.

The DHCP addresses begin for me in the 192.168.1.100 range, and I have 9 devices that might vie for an address at any given time (including phones and handheld gaming devices).  So what I like to do is assign my 2 always-on desktops a static IP address if possible, and I like to call them .111 and .222... easy to remember, and not likely to interfere with any of the dynamically-assigned devices.  I've never known if that's a problem or not, but .111 makes it so that I don't really need to care, I guess!

Is there a reason I should try numbers outside the range where DHCP assigns addresses, like .11 and .22, maybe?

Yes!  If you assign static addresses to DHCP numbers you create errors and conflicts.  See below.> 


Thanks to everybody for the great information and discussion, and I wish I were home to try all this out!  I'll report back as soon as I do.

-Mark

Mark,

The DHCP pool of addresses should be used *only *by the DHCP server.  This means that if you provide the range of .100 to .199 for use by the DHCP server you (as the administrator) *should not* use those addresses for any other configuration (i.e as a static address).

Remember you have 254 host numbers in you subnet available.  No number is better than any other.  Your choice of using the numbers is entirely arbitrary.  To put it another way the router (default gateway can be any of those 254 addresses.  192.168.1.1 is no better than 192.168.1.254 or 192.168.1.225 for that matter.

I would limit the amount of the DHCP pool addresses to what you need +5 (about 14 numbers in you case?) and make sure that it did not include your .111 or .222 addresses that you want to use as static addresses.

It might help if you look at the numbering from the point of view of the bitstream (as the router sees it).  Here are a few numbers, see if you can tell the difference?

```

192.168.1.1   = 11000000101010000000000100000001
192.168.1.2   = 11000000101010000000000100000010
...
192.168.1.200 = 11000000101010000000000111001000
192.168.1.254 = 11000000101010000000000111111110

```

---

### Post by mjpatey on 2010-04-03
It's starting to come back to me... I think the last time I did this I must have known that, and used .11 and .22, not .111 and .222.

That's what I'll try this time.

Edit:  Regarding the Default Gateway... so that's something that I'm *setting* when I do this, not something that I'm hoping I type the right number for?  I can set it to 192.168.1.46 and then that will be the new address for my router?

---

### Post by capscrew on 2010-04-03
> **oldfred said:**
> Its is not the range within DHCP you use but the range that the router has defined for DHCP. You have to assign your manual setting outside the defined range, You may be able to set that in your router but on mine I think it is fixed.

To be more specific:  The range of the network is 254 hosts.  The range that the DHCP server uses is ***part ***of that range.

```

[COLOR="Blue"]192.168.1.0 = network[/COLOR]
192.168.1.**1** = 1st host in network
...
192.168.1.**254** = last host in network
[COLOR="Red"]192.168.1.255  = broadcast (to all in the network)
[/COLOR]
The dhcp pool is somewhere in the above range.


```

It should be a definable configuration, but I have not looked at every router made.  :-)

---

