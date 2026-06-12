---
title: "Networ interface name eth1 vs eth0"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by iKevin on 2008-12-13
Hi All

I have a crazy problem.  I am running a commercial program that require a license manager.  Everything is normally fine but once in a while my network interface gets named eth1 instead of eth0.  This isn't an issue for me except that the license manager requires eth0.

This all has to do with (I think) something that I did a while back when trying to get my network card to work.  I have a realtek card and it eventually worked when there was a kernel update.  I was running 8.04 and the card worked when 8.04.1 came out.  I did a lot of tinkering using google to get it to work and I can't recall what I did.  

Using the forums, I think it has something to with with 70-persistent-net.rules which I am showing below:

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="XX:XX:XX:XX:XX:XX", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="XX:XX:XX:XX:XX:XX", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

I keep on deleting the eth1 line thinking that it will fix thing but it keeps coming back after rebooting.  Is there a way to make eth1 go away?  Also, what could I have done to cause this in the first place?

---

### Post by Wisp2006 on 2008-12-13
You delete it through network manager? If so, I think he is the problem. Try to remove it, and manually edit the network interfaces. eth0, 1, 2, as far as i know, it's just a name,just like "Network Connection" in Win. The device is the same i guess, so for an odd reason, the manager consider you still have an eth0. BTW, the software uses FLEXLM?

---

### Post by iKevin on 2008-12-13
Yes, the software uses flexlm.  Part of the problem is that I run it about once per month. So, I never notice the "eth1" until that time.  I will run out to lunch and try the network manager and get back to the forum.

-Thanks

---

### Post by iKevin on 2008-12-13
OK.  I have to ask a dumb question.  By network manager, I am guessing you mean the network tool on the tool bar.  When I open it and "unlock" it and try to delete the Wired Network, it doesn't do anything.  Is there a different tool that I am supposed to use?  I don't see anything there about eth1.

Thanks

---

### Post by zika on 2008-12-13
post Your /etc/network/interfaces file.

---

### Post by iKevin on 2008-12-13
Here you go!

$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

---

### Post by zika on 2008-12-13
try with ```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface DHCP
auto eth0
iface eth0 inet dhcp
```

---

### Post by iKevin on 2008-12-13
I tried that and eth1 is back.  I also deleted the eth1 line in 70-persistent-net.rules and the network is still named eth1.  I rechecked 70-persistent-net.rules and that darn eth1 line is back after rebooting.  It seems that once you have eth1, udev wants to make it come back.

---

### Post by zika on 2008-12-13
what ifconfig gives?

---

### Post by iKevin on 2008-12-13
Well, I rebooted a second time and everything seems to have worked.  I have eth0 back and it persisted after a third reboot.  So, somehow it is solved.

Thanks

---

### Post by kutturuvan on 2008-12-24
Hello,

I've been trying to get my NIC behave the way I want, for the last few weeks. Its a much similar to the above one, but i'm unable to solve it as per the above guidelines.
Here's my situation:

I've a Desktop with Ubuntu Intrepid installed, which has an ethernet card, detected by the Ubuntu. I don't have internet/LAN connection to this PC. But the catch is that, I need the NIC to be active for I run a proprietary design software, which requires the NIC MAC address for the flexlm license server.
The result of "ifconfig" gives the following:
/*
eth4      Link encap:Ethernet  HWaddr 00:0b:2b:0c:ea:bb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0xb800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 B)  TX bytes:200 (200.0 B)
*/

(I wonder why its "eth4", rather than "eth0"). 
But my /etc/network/interfaces file has only the entry corresponding to the loopback interface. 

When I run the flexlm server, it reports that the hostid (MAC address of NIC) is not matching. The funny thing is that some time back, it was working properly.  I tried setting up the NIC with the network tool GUI, but the same result. 

Is it a problem with the network manager or has it some thing to do with the flexlm server? Even after entering the details manually in /etc/network/interfaces file and restarting the network services, "ifconfig" returns the same details plus the newly assigned IP address, but the problem remains.

I also have Windows XP in the same machine, which has no problems with the NIC. 

I would like to know whether the interface will become active only after we connect the Ethernet cable or not. If so, what I should do to make it visible even when there is no active connection?

Any help would be greatly appreciated.

---

