---
title: "No Internet Full stop"
date: 2009-03-05
forum: Networking &amp; Wireless
---

### Post by siggy421 on 2009-03-05
Okay this is really annoying me, second install of ubunto and same problem.

I have no internet and i really mean no internet, no network connection no nothing. 

Now i know i need drivers for my wirless card, so ive been trying to use a wired card. Ive checked with ifconfig, and yes its up runnign and installed fine.

However it fails to get an Ip address from my router, if i manually set it, it tells me its connected but it isn;t.

So yeah im utterly stumped, i can;t seem to run half the commands because nothing installed and i can't get any applications/drivers not inthe original package.

To top it off, i managed to get the wireless working once, and then after a restart it won't connect, and i seem unable to get it to kick start either. To top it off i can't reinstall the drivers because i just get errors in recompiling.

---

### Post by Crafty Kisses on 2009-03-05
Hey there siggy! What are the results of this command?
```
route
```
I also have another question, can you actually ping a website and receive any data? You can ping a website by running the following command:
```
ping websitename
```
Then see if you are receiving any data. I'd also suggest connecting to the wireless connection via Terminal, which can be done fairly easy:
```
iwconfig eth1 essid <your_accesspoint_essid_here>
```
If you have an encryption on your router, you can alternatively run the following:
```
iwconfig eth1 key <your_key_here>
```
It also wouldn't hurt seeing what kind of ethernet/wireless card you have so post the results of these commands:
```
lshw -C network
lspci
```

---

### Post by codya517 on 2009-03-05
I seem to have the same issue here.

---

### Post by prshah on 2009-03-05
> **siggy421 said:**
> ive been trying to use a wired card. Ive checked with ifconfig, and yes its up runnign and installed fine.

However it fails to get an Ip address from my router, if i manually set it, it tells me its connected but it isn;t.


Sometimes, doing things manually from the command line will show us where the problems lie; try the below:

a) Check if the wired connection is "alive"```
sudo mii-tool eth0
```

b) Check if it can get an IP address dynamically (automatically) ```
sudo dhclient eth0
```

If you get no errors from the above two, your Internet should work fine now. Otherwise, post back the errors and/or output of the above two commands for analysis, along with the output of ```
ifconfig
```

---

### Post by codya517 on 2009-03-05
tried what the above stated in the terminal.(this is on a different comp, yay usb drive)

sudo mii-tool eth0 and sudo dhclient eth0...

eth0: negotiated 100baseTx-FD, link ok
****@****:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1f:d0:d3:fa:69
Sending on   LPF/eth0/00:1f:d0:d3:fa:69
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


and with ifconfig...

eth0      Link encap:Ethernet  HWaddr 00:1f:d0:d3:fa:69  
          inet6 addr: fe80::21f:d0ff:fed3:fa69/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7512 errors:0 dropped:3809830009 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:450720 (450.7 KB)  TX bytes:10793 (10.7 KB)
          Interrupt:219 Base address:0x8000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1f:d0:d3:fa:69  
          inet addr:169.254.10.46  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:219 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:486 errors:0 dropped:0 overruns:0 frame:0
          TX packets:486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30448 (30.4 KB)  TX bytes:30448 (30.4 KB)

didn't work, and the modem is shared with this computer (windows, stock intel network card) and i had to restart the modem for the connection on this one to work.

---

### Post by strife242 on 2009-03-05
> **codya517 said:**
> 
Listening on LPF/eth0/00:1f:d0:d3:fa:69
Sending on   LPF/eth0/00:1f:d0:d3:fa:69
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

You are not getting a response from the DHCP server on your DHCP Discover packets at all.


> **codya517 said:**
> 
eth0:avahi Link encap:Ethernet  HWaddr 00:1f:d0:d3:fa:69  
          inet addr:169.254.10.46  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:219 Base address:0x8000 


Thus your NIC stick to the default address (169.254.x.x).

You can try to define a static IP from your LAN (or public pool if that is a possibility in your scenario).

Edit /etc/network/interfaces
using vi, nano or one of the GUI editors,

Add the following:
iface eth0 inet static
address xxx.xxx.xxx.xxx(enter your ip here)
netmask xxx.xxx.xxx.xxx
gateway xxx.xxx.xxx.xxx(enter gateway ip here)

and be sure to save your changes.

Then edit /etc/resolv.conf
and add your DNS servers manually:
nameserver xxx.xxx.xxx.xxx(enter your dns server ip)

Save that file as well 

Then restart the NIC using:

sudo /etc/init.d/networking restart

Now you should be able to reach other devices on the network.

---

### Post by codya517 on 2009-03-05
I can't save the file after editing it.

"you do not have the permissions etc.."

Even though my user profile is admin. And I tried accessing it through the terminal as superuser and i get

:su - Permission Denied

makes no sense...

---

### Post by codya517 on 2009-03-05
okay. got the edit to save and take.

problem is it didn't change anything. Still the same issue.
and tried restarting the network before and after connecting. after connecting i got some type of error.

SIOCDELRT: No Such Process

---

### Post by codya517 on 2009-03-05
and a restart of ubuntu has resulted in the network being changed some how. it went from auto eth0 to ifupdown(eth0) and won't connect or show up at all now.

and ifconfig resulted in showing only an "lo" output and no eth0 output at all...

sudo nano /etc/network/interfaces

reveals that the interface addition of eth0 was still there and intact, as well as the etc/resolv.conf was also unchanged.

When trying to manually connect (without term) ifupdown(eth0) it said that it could not connect and that ifupdown is not supported.

Latest version of Ubuntu btw.

---

### Post by codya517 on 2009-03-06
had to reinstall ubuntu.

and tried just about everything.
Nothing seems to work with Linux on this connection ordeal...

---

### Post by rabidpuffin on 2009-03-29
I am having the exact same issue on 8.10.  

I am trying to connect via ethernet to a Linksys router.

I've tried auto dhcp, static dhcp on the client, static dhcp from the router.  Nothing seems to be working.

/etc/network/interfaces
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.xxx.xxx
netmask 255.255.255.0
gateway 192.168.x.x

```

/etc/resolv.conf
```

#Generated by NetworkManager
nameserver 192.168.x.x

```

sudo dhclient:
```
No DHCPOFFERS received.
```

So far I have seen a few posts with this issue but I have yet to find a solution.

Thanks in advance for any help.

---

### Post by rabidpuffin on 2009-03-29
A little more info

The results of lspci contains
00:13.0 Ethernet Controller: Realtek SemiConductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

ifconfig shows
eth0, lo, pan0, pan0:avahi
eth0 has the static address that was assigned to it 

pinging the router 
shows destination host unreachable

---

### Post by shane2peru on 2009-03-29
hmm, this sounds really familiar to what I went through.  The difference is that I have a Marvell ethernet card, which turns out it isn't supported by linux, and I had to come up with a patch job to get it working.  First time I ever had this problem and I have used Ubuntu for quite some time.  Realtek should be supported, however you should google the specs of your machine and make sure that is indeed the network card, and then make sure there isn't any glitches in the drivers and google for some hacks to make it work.  I did a quick google on your card, but didn't see anything super relevant.  Also are you 100% sure that this network card is working?  Are you dual booting and able to confirm it works with windows?  Does it work with another distro?  Just a few thoughts.

Shane

---

### Post by rabidpuffin on 2009-03-29
Thanks for your reply I'm going to start looking into those card specs, etc.

To answer your question, I can get this card working with win2000 and win2k server.  

I have installed 8.04.2 and 8.10 with no luck.  I ran 9.04 beta from a live CD and was unable to get that working. 

I would like to try an original 8.04 (original) distro.  Is it possible to get archived releases?

---

### Post by rabidpuffin on 2009-03-29
In case it helps, this is my board.

[http://www.gigabyte.com.tw/Support/Motherboard/BIOS_Model.aspx?ProductID=1762](http://www.gigabyte.com.tw/Support/Motherboard/BIOS_Model.aspx?ProductID=1762)

I'm using the onboard NIC

---

### Post by rabidpuffin on 2009-03-30
Sweet!

With a little help from google and numerous forum threads I have solved my issue.  This thread specifically addresses the known issues with Realtek

[http://ubuntuforums.org/showthread.php?t=538448&highlight=noapic](http://ubuntuforums.org/showthread.php?t=538448&highlight=noapic)

I solved it by changing a setting in the BIOS: I changed the Interrupt Mode from APIC to PIC.

I do not know what the side effects (if any) are but I now have a network connection.  

Thanks

---

### Post by shane2peru on 2009-03-30
glad you got it!  Google is a great resource especially when you know what you are looking for. :D  Glad to hear it was a simple setting.

Shane

---

