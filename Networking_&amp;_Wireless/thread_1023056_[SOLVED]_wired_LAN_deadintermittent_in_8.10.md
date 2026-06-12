---
title: "[SOLVED] wired LAN dead/intermittent in 8.10"
date: 2008-12-27
forum: Networking &amp; Wireless
---

### Post by MTisza on 2008-12-27
I've seen dozens of threads regarding how wired connections are screwed up in 8.10, but none of the symptoms match what I'm having exactly, and more importantly none of the fixes work either.

My network setup: Router <---> SwitchA <---> SwitchB <---> 8.10PC

Router: Snapgear SG530 (Currently maintained by securecomputing.com) This is my DHCP server as well. SW Version 3.1.6 
SwitchA: Linksys 24-Port 10/100
SwitchB: Netgear 8-port 10/100/1000
8.10PC: I've tried more than one motherboard and this problem is consistant on all of them.  Currently an ABIT F-I90HD.  I'm using the built-in GigE port. (FYI the other motherboard that also fails is an ASUS PQ5-EM.)

Symptom:
After starting up the PC I can use the network fully for ~1 minute.  Then I loose the ability to communicate with the router (and therefore the internet as well).  I can still ping anybody else inside the subnet, but not the router.  If I reboot the router the internet works again, until I reboot Ubuntu 8.10.

I ran tcpdump on the router, and wireshark on the PC and it confirms that the echo requests are being sent by the PC and somehow dropped by the router.  When I ping in the reverse direction i.e. from the router to the PC, I see that the echo request reaches the PC fine and it replies fine, but again the response is dropped in the router (i.e. tcpdump shows the packet, but the ping command says 100% packet loss).

Observations:
I see how one might be tempted to say my router is at fault ( and likely my next step is to purchase a replacement at some retail store so I can test and optionally return one) but this only appear when I'm using 8.10.  I have tied numerous times to use 8.04 and it works, then 8.10 and it doesn't.  I've tried 9.04 alpha2 and it also doesn't work.

My current install has all default settings for networking, except I blacklisted the ipv6 module since that has always been a problem in my network.  Disabling it is SOP for me.

---

### Post by MTisza on 2008-12-27
SOLVED!!!

Yes it was my router.  It has an intrusion detection and blocking feature it calls IDB.  It was setup by default to disable communications to and from any device that triggers the IDB feature.

What was triggering it is an SNMP broadcast (to 192.168.2.255) of a get-request for OID : 1.3.6.1.2.1.25.3.2.1.2.1

I don't know what this is for, but it must be new in ubuntu 8.10.  Google search shows that this OID might have something to do with discovering printers or maybe other devices in the network.

---

### Post by ispy on 2008-12-27
Don't forget to mark the thread as solved...

---

### Post by MTisza on 2008-12-27
Done, thanks for the reminder.

---

### Post by jkounis on 2009-01-01
I'm having the same problem as you. The network works fine with a BEFSX41 Router/Firewall, intermittently with a Netgear FVS114 router, and it doesn't work at all with a DLink DIR-655 router. 

The behavior with the DIR-655 is exactly as you describe. It works for a few seconds and then loses all Internet connectivity through the router. However, connectivity within the network remains just fine. Also, other machines on the network are unaffected.

Could you tell us what you did to solve the problem? That might help my troubleshooting. I can't seem to find any description in the DIR-655 documentation about how to disable the Intrusion Detection System. Or did you have to replace your router?

Thanks!

---

### Post by MTisza on 2009-01-01
I was able to see on my router that the IDB feature (which my be named differently on your router) detected suspicious traffic from and therefore blocked the IP of the Ubuntu PC.  I then added that IP as a trusted IP, and the problem went away.

I'm not too familiar with your firewall/router but I did take a quick look at a dummy configuration console that Netgear has on their website for your router.

[http://tools.netgear.com/landing/gui/security/fvs114/simulators/FVS114/default.htm](http://tools.netgear.com/landing/gui/security/fvs114/simulators/FVS114/default.htm)

I recommend you log into your router's web based management console and first take a look at the log (on the left under security is the link).  If you see your Ubuntu PC's IP there, then that should give you a clue as to what the real problem is.  Post that info here and I'll help if needed.

If the log shows nothing try to add your Ubuntu PC's IP address as a trusted IP on the "Block Sites" page. (also linked on the left under the security heading).

Please report back if this works or not.

---

### Post by MTisza on 2009-01-01
I just realized you seem to more interested in the DLINK router.  I know even less about that one, but again I went to the DLINK emulator site for this.

Here I don't see any features related to intrusion detection, just as you wrote.  But you can try to view the log, and then also play with the settings under the Advanced->Firewall Settings.

I don't know the difference between the options for the UDP Endpoint Filtering, but for me the culprit was SNMP traffic form Ubuntu which uses UDP Port 161 by default.

Let me know how it goes.

---

### Post by jkounis on 2009-01-05
The problem was more involved than I thought. I couldn't figure out how to force my machine to be "trusted" by any of the routers I purchased. However, the problem seemed to be related to the fact tat I had two IP addresses on the same network (a configuration that worked fine in Ubuntu 6 and 7.. but not in 8.10 Intrepid Ibex).

Either disabling one of the adapters, or bonding the two together with the same IP address solved the problem. In the end, I bonded the two using a procedure I found at [http://www.astroshapes.com/information-technology/blog/archives/21-port-bonding-with-linux-ubuntu-server.html?/archives/21-port-bonding-with-linux-ubuntu-server.html]("http://www.astroshapes.com/information-technology/blog/archives/21-port-bonding-with-linux-ubuntu-server.html?/archives/21-port-bonding-with-linux-ubuntu-server.html").

I posted a detailed report of my tests at [http://ubuntuforums.org/showthread.php?t=1031164]("http://ubuntuforums.org/showthread.php?t=1031164") ([SOLVED] Internet Connectivity Problems with Static IPs/2 network adapters).

---

