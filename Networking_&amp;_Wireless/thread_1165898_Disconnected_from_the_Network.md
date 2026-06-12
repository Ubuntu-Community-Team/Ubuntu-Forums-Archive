---
title: "Disconnected from the Network"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by Herstjori on 2009-05-21
Hi Guys,

I am unable to connect to the network since yesterday morning. 

1. Yesterday morning I created another user account called Internet without adjusting ANY 'privileges' (up until this moment I have only been using the single user account and root).
2. I logged on as 'Internet' user - Network Configuration - then set up a new wired network (I did select the "system settings" box).
3. Once selected to connect the network loading icon appeared in the top bar menu and after loading gave the result then (and on every attempt to connect since then) – 'The network connection has been disconnected'

I now can't seem to connect on any user.
I have gone to – Administration – User and Groups - and noticed that both boxes Privileges -  connecting to the Internet on modem - or - wireless and Ethernet networks was unselected? Not sure why?
I ticked both boxes and am still unable to connect!!!
Hardware testing gives me my network card and the Ethernet light on my DSL modem is on.

I am able to connect using my USB wireless modem still.

Any help please? 

Thanks.

---

### Post by superprash2003 on 2009-05-21
in your terminal type** ifconfig** and post output , you may not be getting an ip from your router..

---

### Post by Herstjori on 2009-05-22
Thanks Superprash2003 ifconfig below

> eth0      Link encap:Ethernet  HWaddr 00:10:c6:a8:a5:17  
          inet6 addr: fe80::210:c6ff:fea8:a517/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1236 (1.2 KB)  TX bytes:6758 (6.7 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:180 errors:0 dropped:0 overruns:0 frame:0
          TX packets:180 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11932 (11.9 KB)  TX bytes:11932 (11.9 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:114.73.129.190  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:787 errors:0 dropped:0 overruns:0 frame:0
          TX packets:633 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:886735 (886.7 KB)  TX bytes:66280 (66.2 KB)

I also ran this - dhclient.conf /etc/dhcp3
and this - gksudo gedit /etc/resolv.conf
and this - ROUTE

Not sure if they are needed but I have them anyhow.

Thanks dude much appreciated.

---

### Post by superprash2003 on 2009-05-22
in your terminal type **sudo dhclient eth0** and post output.. is 114.x.x.x your WAN IP?

---

### Post by Herstjori on 2009-05-22
> Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:10:c6:a8:a5:17
Sending on   LPF/eth0/00:10:c6:a8:a5:17
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

WAN meaning wireless network?

I am connected via a cat5 cable so would that make it a LAN?

Thanks Superprash2003 - sorry I am a bit a newbie to Ubuntu

---

### Post by superprash2003 on 2009-05-22
post contents of your /etc/dhcp3/dhclient.conf file .. by WAN i mean your internet ip.. when you go to [www.whatismyip.com](www.whatismyip.com) do you see the same 114.x.x.x ip?

---

### Post by Iowan on 2009-05-22
Running Intrepid?

---

### Post by Herstjori on 2009-05-22
Hi guys,

Iowan - yes I am running intrepid....I was considering upgrading to Januty but Microsoft NEW software that never works when it first comes out has sulled my opinion of upgrades!

Superprash2003 - can I apoligise please I have made a silly mistake. All terminal commands that I ran were done while the wireless modem was plugged in so you are quite correct it was a WAN IP - the WAN IP is 114.x.x.x - correct.

So I have posted below the ifconfig run without the Wireless in but with the CAT5 LAN still plugged in

> eth0      Link encap:Ethernet  HWaddr 00:10:c6:a8:a5:17  
          inet6 addr: fe80::210:c6ff:fea8:a517/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:128 (128.0 B)  TX bytes:6028 (6.0 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:476 (476.0 B)  TX bytes:476 (476.0 B)

Now as mentioned I ran the /etc/dhcp3/dhclient.conf through terminal the other day while the WAN was in but now I can't seem to do it - terminal gives 'command not found' result

For what its worth this is the result I got with the WAN and LAN in

> # Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, domain-search, host-name,
	netbios-name-servers, netbios-scope, interface-mtu;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}

Again sorry I missed the obvious WAN/LAN

---

### Post by Iowan on 2009-05-22
> **Herstjori said:**
> WAN meaning wireless network?
I am connected via a cat5 cable so would that make it a LAN?WAN generally means "Wide Area Network" as opposed to Local Area Network.  When referring to a home network, the LAN refers to the local machines, the WAN refers to the Internet.

---

### Post by superprash2003 on 2009-05-23
ok , so i guess your problem comes down to this . you have internet access.. but no network access, primarily because your eth0 isnt getting an ip address.. you've tried the dhclient command to ask for an ip from the router , but no DHCP offers . So this could mean that your router has DHCP disabled.. So firstly check your router's settings to see if DHCP is enabled..If you still dont get an ip address,, you would have to go with static ip ..here's a tutorial on that.. [http://www.prash-babu.com/2008/11/how-to-setup-static-ip-address-in-linux.html](http://www.prash-babu.com/2008/11/how-to-setup-static-ip-address-in-linux.html)

---

### Post by Herstjori on 2009-05-23
Thanks Superprash2003

A whole bunch of things have just happened 

1. the network/infaces file opended didn't mention dhcp it said loopback
2. the ifdown gave the result ifdown: failed to open statefile /var/run/network/ifstate: Permission denied

As I have been unbale to connect to the router (even though the connected lights were on both the pc and the router)
 Frustrated I changed the cat5 cable and unplugged the phone jack - for the first time in a couple of days I was able to access the router.

I moved the pc into the bedroom as  to try using my other cable which is like 3 feet long - I suspected that maybe all this time it was the cat5 I was using ( again - even though the connected lights were on both the pc and the router) 

now in the bedroom - the network icon in the top bar tells me that - wired networks .. device is unmanaged

system - admin - network tools only (lo) Loopback interface is now showing I did have another there I think it was the ethernet

thanks for your help dude

---

### Post by superprash2003 on 2009-05-24
well you would have to create an eth0 , like shown in the post..

---

### Post by Herstjori on 2009-05-24
Sorry I don't understand what I haven't done I followed the link you gave to the letter and have just done so again

> portal@portal-desktop:~$ sudo gedit /etc/network/interfaces
[sudo] password for portal: 
portal@portal-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface ppp0=ppp0.
                                                                         [ OK ]
portal@portal-desktop:~$ sudo ifdown eth0
ifdown: interface eth0 not configured
portal@portal-desktop:~$ sudo ifup eth0
 * if-up.d/mountnfs[eth0]: waiting for interface lo before doing NFS mounts
portal@portal-desktop:~$ 

This is the result in terminal after again replacing the  'sudo gedit /etc/network/interfaces' file

I can't see where to create an eth0?

---

### Post by Herstjori on 2009-05-24
Superprash2003 I still cant access anything

Wired Networks - device is unmanaged ........can you please tell me how to manage the device?

System - Admin - Network Tools - did show for about 10 minutes an eth0 device but now it has dissappeared again

If I go to edit connections there are 3 wired connections 

Auto Ethernet
Wired Connection 1
Wired Connection 2

the /etc/network/interfaces hasn't changed from the static address

I am thinking that I am either going to buy a rj45/cat5 to usb converter or go back to Windows as Ubuntu seems to have too many issues

---

### Post by Iowan on 2009-05-24
I've been using Gutsy on this machine since I upgraded it from Feisty.  My laptop has fresh install of Jaunty - NM seems to work well.  I missed the interim period (Hardy and Intrepid) when NM started evolving (but I didn't miss it much ;) ). 
The "unmanaged" message is *probably* because NM ignores interfaces defined in */etc/network/interfaces*.

---

### Post by Herstjori on 2009-05-24
Thanks Iowan - any advice on any other ways to 'start' a network connection? other than NM?

---

### Post by Iowan on 2009-05-24
I've lost track of the thread, but there was a post that suggested un-installing NM and replacing it with older version. [This]("https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager") one just disables NM - dunno if that lets /etc/network/interfaces file work as before. 
One would like to think that if the new NM has fixed previous problems, that it would be backported to Intrepid and Hardy (maybe not as easy as it sounds).

---

### Post by Herstjori on 2009-05-25
Iowan - my thanks to you!!!!

Superprash2003 thanks also for your help

This is how it was fixed

I followed the link Iowan posted about how to disable NM

I changed the /etc/network/interface back to the loopback and removed the static ip that Superprash2003 gave
I then noticed the NetworkAdmin article it gave the instrustions to start NM [here]("https://help.ubuntu.com/community/NetworkAdmin")
Terminal stated that NM was NOT installed once installed I am now able to once again connect via my wired connection

What I am both curious and extremely frustrated with is how on earth did NM uninstall itself!?!?!!?

---

