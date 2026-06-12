---
title: "bridge-utils -- what am I missing here?"
date: 2010-03-23
forum: Networking &amp; Wireless
---

### Post by oospill on 2010-03-23
okay .. here's what I've got so far: 3 NICs.  cable modem into eth0, eth1 to internet port on wireless router, wireless router (port #1) to eth2.

ifconfig -- verified that I have 3 NICs.

installed bridge-utils .. 
'sudo brctl addbr br0' .. 
'sudo brctl addif br0 eth0'
'sudo brctl addif br0 eth1' 

sudo /etc/init.d/networking restart

I'm supposed to have a bridge now, right?

thanks for any help!!

---

### Post by capscrew on 2010-03-23
> **oospill said:**
> okay .. here's what I've got so far: 3 NICs.  cable modem into eth0, eth1 to internet port on wireless router, wireless router (port #1) to eth2.

ifconfig -- verified that I have 3 NICs.

installed bridge-utils .. 
'sudo brctl addbr br0' .. 
'sudo brctl addif br0 eth0'
'sudo brctl addif br0 eth1' 

sudo /etc/init.d/networking restart

I'm supposed to have a bridge now, right?

thanks for any help!!

Why do you feel you need to create a bridge?  What is the intended purpose (e.g. end result)?

---

### Post by oospill on 2010-03-23
great question.  thanks.  I grabbed several d-link nics for five bucks a pop..

I've got a desktop, and a laptop w/built in wireless.  current setup: cable > cable modem > wireless router (w/4 rj45s) > port 1 to desktop; laptop is wireless

works great for all-around internet surfing on either comp.  I would *like* to see what goes between the cable modem and the wireless router by having two more nics on my desktop.

the question of why is another great question.  I haven't gotten that far, yet.

but, really.  I have googled the heck out of 'bridge-utils ubuntu', etc..  everything is a little different.  I noticed some how-tos modified a file, '/etc/network/interfaces' I believe it was.

thanks for any input!!

---

### Post by capscrew on 2010-03-24
> **oospill said:**
> great question.  thanks.  I grabbed several d-link nics for five bucks a pop..

I've got a desktop, and a laptop w/built in wireless.  current setup: cable > cable modem > wireless router (w/4 rj45s) > port 1 to desktop; laptop is wireless

works great for all-around internet surfing on either comp.  I would *like* to see what goes between the cable modem and the wireless router by having two more nics on my desktop.

The flow of data does not work as I think you envision it.  The theoretical is based on a layered approach.  First we have to physically connect the machines (devices).  The spec's are considered **[COLOR="Red"]Layer 1[/COLOR]**.  

Then we have to recognize the flow of bits (e.g. bitstream) from the physical to the logical (hardware to software) this is [COLOR="Blue"]**Layer 2**[/COLOR].  This is actually split between 2 subsections.  This first being the chip that holds the MAC (Media Access Control) address and the Link Layer that defines the ***frame ***that holds the data.  These days it is all Ethernet (802) If it is wired then the spec is [**_802.3_**]("http://en.wikipedia.org/wiki/IEEE_802.3").  If it is wireless it is [**_802.11_**]("http://searchmobilecomputing.techtarget.com/definition/IEEE-802-Wireless-Standards-Fast-Reference").  Either way it is 802 and that uses The MAC address for ID.

[COLOR="Green"]**Layer 3**[/COLOR] where your data gets its IP address.  The data (frame) is encapsulated in a packet and given an IP address.

It is only when data *leaves the local segment* (subnet) that [COLOR="Purple"]**Layer 4**[/COLOR] networking protocols  (TCP) are employed.  

All of the above is described [**_here_**]("http://en.wikipedia.org/wiki/TCP/IP_model").

Why is this important to you.  All your wireless and wired connections are connected at layer 2 only If all of the NIC's that you have *are in the same IP subnet*.  They will then communicate via the MAC address. They will NEED NO BRIDGING.  Bridging is a method to associate hosts via MAC address when the IP address is NOT in the same subnet (i.e. 129.168.1.1 and 10.0.22.36).

But you will not be able have 3 NIC's in the same subnet if they are all controlled (installed) with one OS.  This is because there is a protocol (Spanning Tree) which prevents multiple links to the same subnet built into the kernel.  This is to stop routing loops.  You only need one address per host per subnet.

The bottom line is: you can't do what you wanted to.  There is no reason or method.

> 
the question of why is another great question.  I haven't gotten that far, yet.


As a start you can install Wireshark on the Ubuntu host and watch all the traffic that comes to the NIC you leave operational.

---

### Post by oospill on 2010-03-24
thanks bottle dude

hmm.. something to ponder.  I could've sworn that when setup correctly, a bridge could be completely invisible .. jsut kinda like a little relay.

---

### Post by capscrew on 2010-03-24
> **oospill said:**
> thanks bottle dude

hmm.. something to ponder.  I could've sworn that when setup correctly, a bridge could be completely invisible .. jsut kinda like a little relay.

There is nothing to ponder.  It is what it is.

Your bridge was probably for a virtual host.  This is how one connects a virtual NIC to a real NIC on the same host.

---

