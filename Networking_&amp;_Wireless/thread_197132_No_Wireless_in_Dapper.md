---
title: "No Wireless in Dapper"
date: 2006-06-15
forum: Networking &amp; Wireless
---

### Post by tc10b on 2006-06-15
Hi,

I have an IBM Thinkpad T23 and a 3 Com Office Connect PC card (3CRSHPW196) which worked straight out of the box with breezy, but following an upgrade to dapper it now no longer works.

I know it's not a problem with the card because it works fine under windows, but just refuses to work under dapper. It also ran in breezy really well. One of the things that made me choose linux over windows was the out of the box support.

It's a real shame as I rely on wireless quite heavily at uni and it worked fine under breezy :-({|= 

I've tried a few things such as installing wi fi radar and the atmeldrivers like it says in the wiki, but to no avail.

I'm really stumped, and this now leaves me with 2 options, downgrade back to breezy where I know it works. Or go back to windows, which I really don't want to have to do.

Does anyone have any ideas to help me get this sorted? I have seen a lot of posts about wireless in dapper, is it a release problem?

Thanks in advance.


Tom

---

### Post by stupidkid on 2006-06-15
Did you try ndiswrapper?

---

### Post by Lambert on 2006-06-15
See if you can find some help here.

[http://at76c503a.berlios.de/support.html#trouble](http://at76c503a.berlios.de/support.html#trouble)

Do you know where the problem is at? Driver not working? association problem between router and device?

If the driver is working you should be able to run the following commands from a terminal and get output on/from the device.

iwconfig
iwlist wlan0 scan

the second command may not work depending on the driver features. replace wlan0 if it's has a different identifier. You may also need to use sudo to run the commands.

---

### Post by tc10b on 2006-06-24
I have tried using ndiswrapper and it doesn't work. It tells me that the hardware the driver is for is not present. Which it is.

Thanks for the link, but I'm just not linux savvy enough to understand most of that.

iwconfig:
tc10b@tc10b-175-175:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"rdg.ac.uk"
          Mode:Managed  Frequency:2.427 GHz  Access Point: FF:00:00:00:00:00
          Bit Rate:11 Mb/s
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

iwlist eth1 scan:

tc10b@tc10b-175-175:~$ iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 0E:60:A8:0F:81:A2
                    ESSID:"rdg.ac.uk"
                    Mode:Ad-Hoc
                    Channel:1
                    Encryption key:off

Any ideas?

When I run WiFi Radar, it tells me it is able to connect to the Uni router, to which I have no access, but is unable to assign an ip address.

I don't understand why this is so. I'm using DHCP and it worked fine under breezy.

Thanks a lot guys.

---

### Post by tturrisi on 2006-06-24
You laptop has built in wireless.  Does it not work?  It also appears that the card is in adhoc mode instead of infrastructure mode.

btw, I presume in rdg.ac.uk that rdg = Reading?  I grew up in Reading, Penna, USA.

---

### Post by tc10b on 2006-06-25
[QUOTE=tturrisi]You laptop has built in wireless.  Does it not work?  It also appears that the card is in adhoc mode instead of infrastructure mode.

btw, I presume in rdg.ac.uk that rdg = Reading?  I grew up in Reading, Penna, USA.[/QUOTE]
No, no. I have a PCMCIA laptop card that I purchased on ebay, this time last year. It worked fine under breezy, straight out of the box, now it doesn't and I can't figure out why.

Yeah rdg.ac.uk = Reading University England :)

---

### Post by tc10b on 2006-09-20
Hi, I've been away for a while, I thought that there might be a solution by now so thought I would just bump the thread.

Just to make the problem clearer:

I'm using a PCMCIA wireless card, which worked 110% under breezy

I can find the card, use the card and connect to the router

I cannot gain an IP address, nor access the internet even sitting next to the router.

I'm really stumped, I know the card works under both breezy and windows and refuse to believe I have to go back to either to get wireless again.

Thanks again.

Tom

---

### Post by tc10b on 2006-10-05
Bump, I'm still having this trouble and I don't understand why. I would appreciate any help anyone can offer.

Thanks in advance.

Tom

---

### Post by dolphinsonar on 2006-10-05
If you want to try low-tech first, try wifi radar.  It solved all my problems with no tweaking...

---

### Post by tc10b on 2006-10-07
> **dolphinsonar said:**
> If you want to try low-tech first, try wifi radar.  It solved all my problems with no tweaking...

Cheers for the reply, I have tried Wifi radar it finds the router, but there is no signal, even sitting next to it! And it won't connect to it and find an ip.
](*,)

---

### Post by tc10b on 2006-10-17
Well I've looked on google and various other threads, one which was dealing with a very similar card to the one I am using.

I am using the 3 Com 3CRSHPW196 Wireless LAN PC Card

Here is what I have tried and failed:

Using wifi-radar:

Error for wireless request "Set Nickname" (8B1C) :
SET failed on device eth1 ; Operation not supported.
eth1 Failed to read scan data : Resource temporarily unavailable

??

tc10b@tc10b-175-175:~$ sudo ifconfig eth1 up
tc10b@tc10b-175-175:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.

Listening on LPF/eth1/00:04:75:9a:3d:51
Sending on LPF/eth1/00:04:75:9a:3d:51
Sending on Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

tc10b@tc10b-175-175:~$ sudo iwconfig eth1 essid linksys
tc10b@tc10b-175-175:~$ sudo iwconfig eth1 mode managed
tc10b@tc10b-175-175:~$ sudo dhcpcd -t 10 -d eth1
dhcpcd: MAC address = 00:04:75:9a:3d:51

(at this point the card light comes on, which means the card is down)

tc10b@tc10b-175-175:~$ sudo ifconfig eth1 up

tc10b@tc10b-175-175:~$ sudo dhcpcd eth1 linksys

This just hangs the system for about a minute and then switches the light on the card on, which is rather odd as it means the card has been unloaded.

I'm going to try and compile the drivers again to see if that makes a difference

tc10b@tc10b-175-175:~$ cardctl ident
Socket 0:
product info: "3Com", "3CRSHPW_96 Wireless LAN PC Card"
manfid: 0x0101, 0x0696
function: 6 (network)
Socket 1:
no product info available

So it's already recognising it correctly.

OK I reinstalled the latest drivers, and still no luck:

tc10b@tc10b-175-175:~/Downloads/atmelwlandriver$ sudo make install
pcmcia directory already exists
usb directory already exists
pci directory already exists
bin directory already exists
x11r6 bin directory already exists
Run #depmod -aeq after installation.
OK
tc10b@tc10b-175-175:~/Downloads/atmelwlandriver$ sudo depmod -aeq

Now when I run dmesg, it reads it as an atmel card and not as a 3com card:

[17184059.696000] pccard: card ejected from slot 0
[17184063.896000] pccard: PCMCIA card inserted into slot 0
[17184063.896000] pcmcia: registering new device pcmcia0.0
[17184064.472000] eth1: Atmel at76c50x. Version 0.98. MAC 00:04:75:9a:3d:51
[17184064.928000] ADDRCONF(NETDEV_UP): eth1: link is not ready

I don't know what the last line means, can anyone shed some light?

tc10b@tc10b-175-175:~$ ifconfig
eth0 ommitted

eth1 Link encap:Ethernet HWaddr 00:04:75:9A:3D:51
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:11 errors:1 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:660 (660.0 b) TX bytes:0 (0.0 b)
Interrupt:3 Base address:0x2100

tc10b@tc10b-175-175:~$ iwconfig

eth1 IEEE 802.11-DS ESSID:"linksys"
Mode:Managed Frequency:2.437 GHz Access Point: 00:06:25:78:63:0F
Bit Rate:11 Mb/s
Retry min limit:7 RTS thrff Fragment thrff
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

I'm now completely lost, and at my wits end I have a reliable wired connection but I would like to go wireless.

If anyone can help it would be very much appreciated.


Can anyone help?

Thanks


Tom

---

### Post by tc10b on 2006-11-11
Any ideas from anyone? I really want to get my wireless back.

Cheers.

Tom

---

### Post by tc10b on 2006-11-12
OK, so now I have a full signal bar when I use my wireless card and a static IP address.
I can live with this provided it works, however it won't send or recieve data from the router so I can't ping anything or go online.
I dunno how I can fix this, I tried deleting the DNS servers as restarting , I saw this on a website and thought it would help.

Any help would be gratefully recieved.

Cheers

Tom

---

### Post by GB_Joe on 2008-07-07
Tom - I know this is a long shot as the last post was ages ago, but I have the exact same card and problem with Hardy. It's my first go on Linux and I'm struggling! I've read about this kind of problem in various places, but I've not seen a solution yet, or at least not one that makes any sense to me!

Would be great to hear from you... or anyone...?

---

### Post by tturrisi on 2008-07-07
uninstall Network-Manager

---

