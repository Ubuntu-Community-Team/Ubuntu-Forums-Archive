---
title: "Lucid Live Cd network dosen't work. Why?"
date: 2010-05-21
forum: Networking &amp; Wireless
---

### Post by skew on 2010-05-21
I'm running two live Lucid 10.04 cd's on two separate machines connected with a twisted cable directly (no hud, switches or routers) ifconfig confirms both NIC cards on eth0 are UP and recognized. example of one machine below. The other NIC says basically the same thing with, of course a different MAC address.


eth0      Link encap:Ethernet  HWaddr 00:e0:b8:b8:cd:7e  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:b8ff:feb8:cd7e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 



running dhclient eth0 on both machines say basically the same thing. 
Example of one machine:


Listening on LPF/eth0/00:e0:b8:b8:cd:7e
Sending on   LPF/eth0/00:e0:b8:b8:cd:7e
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


What's going on here? Why no network on this basic system? Is this a bug in Lucid?

A previous two machine network with Intrepid worked perfectly. I use to be able to just unplug the network cable at will and intrepid would automatically reestablish a connection when I reconnected the cable. 

Any assistance with this matter, or at the least confirmation of a existing bug in Lucids network system would be helpful. 

Thanks!

---

### Post by skew on 2010-05-21
Should I assume from the lack of even one reply that lucid is broken? I had left a question such as the post above earlier in the week and it too was left unanswered. 

   What surprises me is that "Ubuntu's Lucid" can't even cope with a straight and simple computer to computer Ethernet connection.

   I'll change my question instead.  Which Linux distro should I switch to which will currently provide the best network support and usability?  Or, HEAVEN FORBID! Would I be better off going with Windows 7 after five happy years with Ubuntu?  It's simple actually, a properly functioning OS with network functionality is more important to me at this time then beta testing a new OS.

---

### Post by Iowan on 2010-05-21
> **skew said:**
> Should I assume from the lack of even one reply that lucid is broken? Perhaps 3 hours isn't enough time for the person with your answer to check in - some may still be at work.

I had some [similar]("http://ubuntuforums.org/showthread.php?t=1156441") issues with my Jaunty laptop, but Karmic and Lucid worked on a desktop machine. That was trying to get a DHCP address from my server.

Is there a DHCP server on one of the machines? Otherwise, no DHCP adddress will be offered. *Ordinarily*, a switch, hub, router, or crossover cable is required - although some of the newer (than I have) cards can autoconfigure.

Any luck with pings?

---

### Post by skew on 2010-05-21
Thanks for replying Iowan.  More info on my working network system, which is the one that I am really hoping to get fixed can be found in this post.

[http://ubuntuforums.org/showthread.php?t=1487221]("http://ubuntuforums.org/showthread.php?t=1487221")

I originally made that plea for assistance post on a twin issue three days ago.  No one replied to that call for help so I may have been a little impatient tonight, my apologies.

---

### Post by Iowan on 2010-05-21
I was gone last week - but I'm certainly not the only person who should have been able to help... Your other thread mentions that ping worked between the two... sorta? You could ping computer two (192.168.1.4) from computer one (192.168.1.3) - what about the other way around? Could you ping computer1 from computer2?

---

### Post by skew on 2010-05-22
Good morning. 

Two things.  

  First in reply to your earlier question. I have installed dhserver on either one or the other machines at some point, even both at the same time during my weeks of trying to remedy this network failure. Ping works exactly the same on both machines under dhcp. There is no ping return as wicd says no IP has been assigned by the dhcp server. I've changed the interfaces file in both systems from 

[B]auto lo
iface lo inet loopback[/B]

**to**

[B]auto lo
iface lo inet loopback

auto eth0
iface lo inet dhcp[/B]

and back again...

FWIW; My wireless interface eth1 on my laptop works perfectly. eth1 has never been assigned anything in the interfaces file. I don't have a wireless card on the second machine. I only know the laptops wirelesss card works as it connects correctly to an unconnected stand alone WRT54G. The WRT54G acting correctly as the dhserver and assigning the laptop an IP address. I think I mentioned in the linked post that I can also connect wired to the WRT54G through both machines perfectly. Just not karmic to lucid(laptop).
 
 When I've attempted using a separate static IP addresses for both machines in the interfaces file the ping appears to work, but incorrectly as it strangely loops back and appears to ping itself even though I'm pinging the second computers IP address. This strange behavior occurs on both machines. I've checked this several times and each machine is assigned a separate IP address 192.168.1.3 on one and 192.168.1.4  on the other. Both netmasks are 255.255.255.0  I have no gateway needed so have either left that blank in the interfaces file, assigned it 0.0.0.0 and 192.168.1.1 on occasion, usually when connected to the WRT54G. 

That help? The million dollar question now is what do I try next?  
Thanks again!

---

