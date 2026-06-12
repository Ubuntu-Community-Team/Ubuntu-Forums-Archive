---
title: "Port forwarding, reconfiguring my home network."
date: 2009-06-11
forum: Networking &amp; Wireless
---

### Post by gordonsowner on 2009-06-11
Hi,

I want to be able to access my ubuntu 8.04 server externally via ssh and such.  So I think I need to do port forwarding.  Further, I think I need to reconfigure my network so that the ubuntu server keeps a static IP, and I need to simplify/change my topology.

My current setup is a ADSL modem, LAN side plugged into the WAN port of a linksys WRT54G.  The linksys is my DHCP server for ~5 devices, 2 wired, 3 wireless.  This works.  However, to port forward, I see that I have to make some static addresses and port forward through the modem and the linksys.

I found a thread that said that this could be made simpler by plugging the modem into the LAN port of the linksys and making the linksys into a wired switch.  Then I can use the modem as my DHCP server (plus assign some static routes).  The thread that I followed was at: [http://www.velocityreviews.com/forums/t310908-port-forwarding-with-two-routers.html](http://www.velocityreviews.com/forums/t310908-port-forwarding-with-two-routers.html)

I'm not getting this to work.  I set my linksys to address 192.168.1.1, my modem to 192.168.1.2, and dhcp addresses from 192.168.1.100 to 150.  When I plug it in, I can administer both the modem and the linksys via their IP addresses on a web interface, but I cannot access external websites.  I can if i plug this computer directly into the LAN port of the modem (after disconnecting the linksys, because there is just one port).

So I'm stuck.  I would think that if I can reach the modem from my server (administering and pinging), that I should be able to access the whole internet.  Can someone help?

tia,
matt

---

### Post by redmk2 on 2009-06-11
> **gordonsowner said:**
> ...I think I need to reconfigure my network so that the ubuntu server keeps a static IP, and I need to simplify/change my topology.

...  I'm not getting this to work.  I set my linksys to address 192.168.1.1, my modem to 192.168.1.2, and dhcp addresses from 192.168.1.100 to 150.  When I plug it in, I can administer both the modem and the linksys via their IP addresses on a web interface, but I cannot access external websites.  I can if i plug this computer directly into the LAN port of the modem (after disconnecting the linksys, because there is just one port).

So I'm stuck.  I would think that if I can reach the modem from my server (administering and pinging), that I should be able to access the whole internet.  Can someone help?

tia,
matt

Matt,

When you reconfigured your setup, did you reconfigure the gateway?  As you have it now, it should be 192.16.1.2.  Try it and see if it works.

As I see it, the modem is working as a router.  As long as you have NAT and can port forward it is doing the job performed by a router.  What you need is a switch, a wireless AP and DHCP.  I believe you have that in the Linksys.  The Ethernet ports are the switch.  Look at the manual and see if it can be setup as a wireless AP.  We know it will do DHCP.  Don't use the WAN port on the Linksys.  it expects to be on different network.

If the Linksys can't be setup as the AP then you need to get a switch and see about providing DHCP services or provide static IP addressing.  Does the ADSL modem have DHCP.  Sometimes they do.

---

### Post by cariboo on 2009-06-11
Setting up port forwarding on the Linksys WRT54G is easy. 

The first thing I would suggest you do is reset the router backt to factory default, that way any changes you have made will be undone, and you should be able to access the internet again.

You didn't say what version you are using, I would suggest you uninstall newtork-manager-gnome and install gnome network-admin, that way you can set a static ip address. Access Network Manager by going to System-->Administration-->Network, choose you network interface and set a static ip address. Set an ip address outside your dhcp range, if you are using 1921.69.1.100 to 192.168.1.150, then set the static ip address to something like 192.168.1.200.

To port forward to the router see the screenshot to see what I set up for port forwarding. I don't have anything enable at the moment, but to enable it just make sure there is a checkmark in the box at the extreme right.

---

### Post by gordonsowner on 2009-06-11
Thank you both,

redmk2:

I did not set the gateway, but the gateway IP showed up in the 'Status > Router' page.  What I did was follow the directions given at: [http://keystoneisit.blogspot.com/2008/03/how-to-set-up-wrt54g-as-switchbridge.html](http://keystoneisit.blogspot.com/2008/03/how-to-set-up-wrt54g-as-switchbridge.html) to turn this into a switch.  No luck.  My settings are (in the working, non-switch form, link from modem LAN to linksys WAN):

modem: Actiontec Gt701
DHCP: on
IP: 192.168.0.1

router: linksys WRT54G
Internet IP: 192.168.0.3
Local IP: 192.168.1.1
Default Gateway: 192.168.0.1
DHCP: on

When I follow the directions in the link above, and I reset/renew my DHCP settings on linksys, I cannot obtain any IP address from the modem.  The 'Status > Router' info is missing or all '0.0.0.0'.  So I'm not sure what step I'm missing there...

cariboo907:
Thanks!  once I get the setup working, I'll follow your pic for port forwarding...

Matt

---

### Post by superprash2003 on 2009-06-11
i dont think you need to change your setup, your previous setup was fine 
> My current setup is a ADSL modem, LAN side plugged into the WAN port of a linksys WRT54G 
from here , you just need to worry about the linksys , as the ADSL is in bridged mode which will forward all traffic..so what i suggest is , move back to the original setup , and in the linksys port forwarding page , enter the ip you see funder hte ifconfig output from the ubuntu terminal , it would be 192.168.0.x .. and you should have your ports open

---

### Post by gordonsowner on 2009-06-11
Thanks superprash2003, I'll try it tonight.

---

### Post by gordonsowner on 2009-06-14
UPDATE: Solved.

Ok, it looks like I was missing the last step -- restarting the network:

```
/etc/init.d/networking restart

```

Found this at: [http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p3](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p3).

So, between linksys portion is solved... now I will try to make the linksys address static relative to my DSL router...


Hi,

Working on this network again... trying baby steps.  Trying to first assign a static IP from my linksys router wrt54g v2.0 (which is behind my DSL modem ActionTec GT701) to my ubuntu computer.  Using DHCP with linksys to my computer (dynamic IPs between 192.168.1.100 and 192.168.1.149), this is the output of 'ifconfig':

```
eth0      Link encap:Ethernet  HWaddr 00:c0:49:f6:cc:e3  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:49ff:fef6:cce3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10289 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9377 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3877166 (3.6 MB)  TX bytes:984411 (961.3 KB)
          Interrupt:9 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1640 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1640 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:82000 (80.0 KB)  TX bytes:82000 (80.0 KB)

```
so then I change '/etc/network/interfaces' to:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.1.200
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

```

when I do, I wait moment and try the browser/curl of google.com, which fails because the site cannot be reached.  The 'ifconfig' output of the ubuntu box is:

```
eth0      Link encap:Ethernet  HWaddr 00:c0:49:f6:cc:e3  
          inet6 addr: fe80::2c0:49ff:fef6:cce3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10422 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9433 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3898010 (3.7 MB)  TX bytes:991321 (968.0 KB)
          Interrupt:9 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1640 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1640 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:82000 (80.0 KB)  TX bytes:82000 (80.0 KB)

```
note that conspicuously missing is the eth0 inet addr line from when I was running DHCP.  I see cariboo907 has helped other people besides me on this in the forums, and I looked at one of the old posts and saw that the same advice was given: [http://ubuntuforums.org/archive/index.php/t-1054410.html](http://ubuntuforums.org/archive/index.php/t-1054410.html).  Any idea what's going wrong in my setup?

Thanks,

---

