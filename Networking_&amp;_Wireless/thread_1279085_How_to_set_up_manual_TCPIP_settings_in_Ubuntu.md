---
title: "How to set up manual TCP/IP settings in Ubuntu?"
date: 2009-09-30
forum: Networking &amp; Wireless
---

### Post by ekual on 2009-09-30
Hi 

I was wondering if someone can help me with a problem I am facing.

How do I manually set up TCP/IP settings in Ubuntu?

In windows it is done through IP4 properties on the particular card you are using whether it be Ethernet or Wireless. It looks like this:

[http://nsit.uchicago.edu/img/ucad/setup1.jpg](http://nsit.uchicago.edu/img/ucad/setup1.jpg)

^ Random image I got of it from the internet. It is sooooo easy to do in Windows but after hours of trying to work it in Ubuntu I can't seem to do it.

So why am trying to do this? Well to have a an IP stays perminant for torrents etc.

Is there a GUI way of doing it instead of through terminal. If not then that's life.

Thank you.

---

### Post by chili555 on 2009-09-30
> It is sooooo easy to do inSorry, I can't make my keyboard type the 'W' word. It is also so easy in Ubuntu. Please see Post #6 here: [http://ubuntuforums.org/showthread.php?t=1277315&highlight=IPv4](http://ubuntuforums.org/showthread.php?t=1277315&highlight=IPv4)

IMHO, if you are sure that you always, always want the same IP, it is better to remove Network Manager and edit */etc/network/interfaces* and be happy forever. Just one ape's opinion.

---

### Post by badger_fruit on 2009-09-30
> **chili555 said:**
> it is better to remove Network Manager and edit */etc/network/interfaces* and be happy forever. Just one ape's opinion.


Make that two
ook ook.

---

### Post by caddict on 2009-09-30
are yous saying that network manager can be a trouble maker? I'm having network troubles since upgrading and i like the idea of simplifying. is it better to manage networks from the command line?

---

### Post by chili555 on 2009-09-30
NM can certainly be troublesome; however, if you travel to the coffee shop, the university or the hotel with wifi, NM or its alternative Wicd makes things much easier. For me, it just connects without a hitch. If you read these forums, it's problematic for many. I am always distressed by the desktop machine owners that have a working wireless interface who can't connect using NM and conclude it's the *driver* and go to the far reaches of the internet to find a questionable driver that won't compile and then curse the wireless development in Ubuntu! In my opinion, NM, specifically in many cases, it's handling of encryption, was the culprit all along.

If, on the other hand, you have a stay at home desktop or server that will never go down to Starbucks, then it's easier to get a layer of complication out of the way, NM, and set up your details in */etc/network/interfaces* once and be connected reliably on boot every day. My stay at home machines are set up this way and my traveling laptop uses NM successfully.

---

### Post by Iowan on 2009-09-30
I guess I'm another who has had better-than-expected results with Network Manager on a laptop. On the other hand, this (ancient) Gutsy machine has little choice but to configure it's only interface via */etc/network/interfaces*.

---

### Post by ekual on 2009-10-01
So there isn't a way to manually configure without having to delete interfaces?

---

### Post by Iowan on 2009-10-01
Theoretically, you could use NM to configure/manage one interface, and use */etc/network/interfaces* to configure others.  Results may vary.

---

### Post by kevdog on 2009-10-01
There is a link in my signature how to configure wireless or wired cards manually at the command line if you are interested.  Hopefully this is what you are interested in.

---

### Post by ekual on 2009-10-02
Thanks for your reply's, I'll try it and let you know how I get on.

---

### Post by caddict on 2009-10-03
> If, on the other hand, you have a stay at home desktop or server that will never go down to Starbucks, then it's easier to get a layer of complication out of the way, NM, and set up your details in /etc/network/interfaces once and be connected reliably on boot every day

oh how i yearn for this.
i only have one interface, one connection, but i can't get it right!

i've disabled (feel nervous to uninstall) network-manager (system>prefs>startup apps) and changed ifupdown:managed from true to false in nm-settings.config

/etc/network/interfaces is looking pretty but still no connection. i have checked all my router settings, changed some, changed them back...all looks good. still no change

---

### Post by chili555 on 2009-10-03
> /etc/network/interfaces is looking prettyHow about letting us take a look. ```
cat /etc/network/interfaces
```Please post the result here.

---

### Post by caddict on 2009-10-03
> There is a link in my signature how to configure wireless or wired cards manually at the command line if you are interested. Hopefully this is what you are interested in.

kevdog, i have followed the steps in your how-to many times and in many ways without success. the how-to seems mainly to address wireless connections. mine should be trivial in comparison.

i have checked the driver is correct, even blacklisted some alternative driver.

i would post some command outputs but i can now no longer get eth0 up by any means, so i am on a different computer. if/when i get eth0 up i will post more details

---

### Post by caddict on 2009-10-03
thanks chili

i have another thread running here, which has some background

[http://ubuntuforums.org/showthread.php?t=1276981](http://ubuntuforums.org/showthread.php?t=1276981)

here is the interfaces file:

> auto lo
iface lo inet loopback
#address 127.0.0.1
#netmask 255.0.0.0

iface eth0 inet static
	address 10.1.1.4
	netmask 255.0.0.0
	gateway 10.1.1.1

auto eth0

---

### Post by chili555 on 2009-10-03
I would make it even prettier by changing it to:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.1.1.4
netmask [COLOR="Red"]255.255.255.0[/COLOR]
gateway 10.1.1.1
```Then please do:```
sudo ifdown eth0 && sudo ifup eth0
```Any errors or warnings? If not, please do:```
ping -c3 www.google.com
```Are you connected?

---

### Post by caddict on 2009-10-03
> I would make it even prettier by changing it to:

ok done that 

response to sudo ifdown eth0 is:

> interface eth0 not configured

and to sudo ifup eth0 is:

> cannot assign requested address

a question: on my router, the lan network mask is set to 255.0.0.0
shouldn't i stick to that?

---

### Post by chili555 on 2009-10-03
> a question: on my router, the lan network mask is set to 255,0,0,0
shouldn't i stick to that?I am no expert on netmasks, but I believe in an ordinary home network using a consumer router, the netmask should be 255.255.255.0, both in the router and specified in the computers. Here is an excerpt from: [http://en.wikipedia.org/wiki/Netmask](http://en.wikipedia.org/wiki/Netmask)> Suppose a home network consists of computers named Foo and Bar, connected to a router, and then via a cable modem to the Internet. The home network is configured as a subnet: address 17.76.99.1 is assigned to Foo, address 17.76.99.2 to Bar, and address 17.76.99.100 to the router. The subnet has been configured so that the first three octets of its members' addresses are all the same subnet id, 17.76.99, and this fact is expressed by the subnet mask 255.255.255.0 (binary 11111111 11111111 11111111 00000000) configured in the router.Do you have other computers working normally with your current setup?

---

### Post by caddict on 2009-10-03
yes...it's a long running network with three (sometimes four) computers; one running XP one vista (dare i say it) and one ubuntu jaunty. the jaunty computer was recently 8.04 and the network ran like clockwork. even after upgrading to 9.04. and the netmask has always been 255.0.0.0. i've seen other varieties of netmask here and there, but saw no reason to "fix what aint broke"

i have been using an unexplained workaround to connect the ubuntu computer to the network, because it has never connected at boot. it basically involves (i believe) spoofing the mac address of the ethernet card with

```
gksudo ifconfig eth0 up hw ether 00:00:00:00:00:00
```

then restarting the network.

no one has been able to explain why that works, but i've been using it to connect for over a year now. i just thought that i might be able to improve matters now that i'm using 9.04.

truth is, should have left well alone because now i can't connect at all:)

---

### Post by kevdog on 2009-10-03
Lets back track for a minute -- I have no idea why spoofing a MAC address would make your card work.

List for me the following:
lshw -C network
ifconfig


Thanks.

---

### Post by caddict on 2009-10-04
thanks kevdog!

here it is:

```
steve@foxy:~$ sudo lshw -C network
[sudo] password for steve: 
  *-network DISABLED      
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 10
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=10.1.1.4 latency=32 link=yes maxlatency=32 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 4a:0c:fd:ba:84:f1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
steve@foxy:~$
```

i have often wondered why that pan0 is there...i have no wireless devices...

maybe useful, some of the dmesg output:

```
    2.832246] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    2.832286] 8139cp 0000:02:05.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    2.837065] 8139too Fast Ethernet driver 0.9.28
[    2.837107] 8139too 0000:02:05.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.838739] eth0: RealTek RTL8139 at 0xa000, 00:00:00:00:00:00, IRQ 23
[    2.838743] eth0:  Identified 8139 chip type 'RTL-8101'
[  292.912869] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  303.040013] eth0: no IPv6 routers present
[  304.868064] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  315.792009] eth0: no IPv6 routers present
```

ifconfig right now only shows lo

> steve@foxy:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:293 errors:0 dropped:0 overruns:0 frame:0
          TX packets:293 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:25262 (25.2 KB)  TX bytes:25262 (25.2 KB)

---

### Post by caddict on 2009-10-04
@chili
from the description you posted 255.255.255.0 does make more sense than 255.0.0.0, so i changed the netmask accordingly on the router and the other computers. sadly, no difference. actually even when some computers had a different mask from the router, it didn't seem to matter

---

### Post by chili555 on 2009-10-04
Please let us see the result of:```
sudo ifconfig eth0 down && sudo ifconfig eth0 up
ping -c3 10.1.1.1
cat /etc/resov.conf
```Thanks.

---

### Post by kevdog on 2009-10-04
The first problem is with the line that states:

*-network DISABLED      


As chili suggested if you do a
sudo ifconfig eth0 up

Then repost 
lshw -C network

You should get anything stating anything about DISABLED -- b/c if you do something isn't working right -- possibly the driver.

---

### Post by chili555 on 2009-10-04
> The first problem is with the line that states:

*-network DISABLED Or, if it's a laptop, it could mean that the wireless switch or key combination has the wireless radio disabled. Please check.

---

### Post by caddict on 2009-10-04
really appreciate the input guys! couldn't do this alone

ok things have changed a little here. for some reason i decided to change the network to dhcp...just to see what would happen.

still no connection at boot.

dhclient -r eth0
ifconfig eth0 up

does nothing. also:
```
steve@foxy:~$ sudo ifconfig eth0 down
steve@foxy:~$ sudo ifconfig eth0 up
SIOCSIFFLAGS: Cannot assign requested address
steve@foxy:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=32 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 52:27:24:e5:30:3c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```

on the positive side:
```
steve@foxy:~$ sudo ifup eth0
ifup: interface eth0 already configured
steve@foxy:~$ 
```

after trying a lot of things (many of which i can't remember) i spotted some hw address associated with pan0 (what is pan0?). so i tried the old trick again:
```
steve@foxy:~$ gksudo ifconfig eth0 up hw ether ee:34:b0:23:6c:34
SIOCSIFFLAGS: Cannot assign requested addresssteve@foxy:~$ 
steve@foxy:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 4156
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/ee:34:b0:23:6c:34
Sending on   LPF/eth0/ee:34:b0:23:6c:34
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 10.1.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/ee:34:b0:23:6c:34
Sending on   LPF/eth0/ee:34:b0:23:6c:34
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPOFFER of 10.1.1.4 from 10.1.1.1
DHCPREQUEST of 10.1.1.4 on eth0 to 255.255.255.255 port 67
DHCPACK of 10.1.1.4 from 10.1.1.1
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
bound to 10.1.1.4 -- renewal in 1500 seconds.
                                                                         [ OK ]
```
network now looks like this:
```
steve@foxy:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 10
       serial: ee:34:b0:23:6c:34
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=10.1.1.6 latency=32 maxlatency=32 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 52:27:24:e5:30:3c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
steve@foxy:~$ 

```

at least i have a connection again. maybe there is a problem with the card. maybe i should just be happy that i can connect at all!

do you think it may be possible to run these lines at bootup?

---

### Post by kevdog on 2009-10-04
That might be the strangest series of events Ive seen.

You can run the commands at startup if you put them in the rc.local file above the exit 0 command.  You do not need to prefix the commands with sudo since the file is run as root.  You need to edit the file as root also.

---

### Post by chili555 on 2009-10-04
Strange indeed!> bound to 10.1.1.[COLOR="Red"]4[/COLOR]> driver=8139too driverversion=0.9.28 ip=10.1.1.[COLOR="Red"]6[/COLOR]Will the weirdness ever stop or will my head explode?

---

### Post by caddict on 2009-10-04
glad to be able to provide something different! it looks like this is the only way i can get connected, so better stick to it!

chili are you saying
> bound to 10.1.1.4
should rather be
> bound to 10.1.1.1
seeing that 10.1.1.1 is the router?

if it makes you feel better, network output now says:

> driver=8139too driverversion=0.9.28 ip=10.1.1.4

@kevdog
> put them in the rc.local file
i will do this soon

i'm wondering is there any reason to choose dhcp over static? it's been static ip for a while now...can't see why i should leave it as dynamic...

---

### Post by caddict on 2009-10-05
ok now the computer connects to the network automatically (and automagically). the method may defy explanation, but it works!

these two lines are in the rc.local file and all is well

```
ifconfig eth0 up hw ether ee:34:b0:23:6c:34
/etc/init.d/networking restart
```

huge thanks for the ideas and support!

---

