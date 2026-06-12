---
title: "No wired internet from DSL."
date: 2009-05-19
forum: Networking &amp; Wireless
---

### Post by iamthemicrowave on 2009-05-19
Hi all.  I recently installed xubuntu 9.04 on an old microstar machine we have in my house.  Its a pentium 2 233 mhz, 196 mb RAM.  I recently installed a netgear fa311 v2 NIC.  Xubuntu reconginzes the card fine;  it is detected and set as eth0.  When I right click on the network icon, it attempts to connect for a while, and then quits.

ifconfig returns normal looking information, but it lists a weird IP address.  It is in hexadecimal format.  I don't know what to make of this.

sudo ifup eth0 returns something about eth0 = eth0.  I can't check now.

My house is on a DSL line with many other computers hooked up fine to our network.  This machine is plugged into the modem with a standard ethernet cable.  I know the cable works.

I think it might be a modem problem(since the card is recognized), but I don't know what to do.  It is a 2wire gateway(combination modem and router).  I restarted the modem, to no avail.  This computer does not show up on the network on the modem configuration page.

syslog shows the network card timing out, so I think it is not interacting correctly with the modem.

Could I have some troubleshooting steps and things to try please?  I will provide any more information requested.  I think the problem is the modem not assigning a proper IP address to this machine, but its just a hunch.

---

### Post by Alterax on 2009-05-19
Standard steps:

I actually think your network card is working okay, especially if it's trying to connect through network manager.  I don't recommend the ifup method if you are using network-manager, as the latter dynamically generates its own config files.

Try a different networking cable.  If that doesn't do it, try with a known working computer (friend's laptop comes in handy).  If that doesn't do it, right-click on network-manager, uncheck 'enable networking', then add the following lines:

to /etc/network/interfaces:
auto eth0
iface eth0 inet dhcp

to /etc/resolv.conf
nameserver 208.67.222.222

then do /etc/init.d/networking restart

Between those, that should get you up and going.  Usually the cable is the first to go, and since it's the easiest and cheapest to swap, I'd start there.  If none of these work, you may have a connector loose inside the card itself--and it's easier IMHO to cough up $20 for a new one than to try soldering those back into place.

---

### Post by superprash2003 on 2009-05-19
also , in your terminal type **sudo dhclient eth0** and post output

---

### Post by iamthemicrowave on 2009-05-19
I forgot to mention that my dad restarted this xubuntu machine 2 hours after I started installation.  I was away all day, and I assume it installed fine because everything else works, but I figured I should mention it.  I have considered reinstalling the system because I do not know if anything is messed up.  I may have to resort to that if the internet does not work.

Here is the info I did not post before:

```
$ ifconfig eth0
eth0   Link encap:Ethernet HWaddr 00:1e:2a:3e:d7:75
       inet6 addr: fe80::21e:2aff:fe3e:d775/64 Scope:Link
       UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
       RX packets:0 errors:826 dropped:1298 overruns:826 frame:0
       TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:1000
       RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
       interrupt:10 Base address:0xe800
```

```
$ sudo lspci -v
00:11.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
   Subsystem: Netgear Device f31d
   Flags: bus master, medium devsel, latency 64, IRQ 10
   I/O ports at e800 [size=256]
   Memory at ea010000 (32-bit, non-prefetchable) [size=256]
   Capabilities: [50] Power Management version 2
   Kernel driver in use: 8139too
   Kernel modules: 8139too, 8139cp

```



> **Alterax said:**
> Standard steps:

I actually think your network card is working okay, especially if it's trying to connect through network manager.  I don't recommend the ifup method if you are using network-manager, as the latter dynamically generates its own config files.

Try a different networking cable.  If that doesn't do it, try with a known working computer (friend's laptop comes in handy).  If that doesn't do it, right-click on network-manager, uncheck 'enable networking', then add the following lines:

to /etc/network/interfaces:
auto eth0
iface eth0 inet dhcp

to /etc/resolv.conf
nameserver 208.67.222.222

then do /etc/init.d/networking restart

Between those, that should get you up and going.  Usually the cable is the first to go, and since it's the easiest and cheapest to swap, I'd start there.  If none of these work, you may have a connector loose inside the card itself--and it's easier IMHO to cough up $20 for a new one than to try soldering those back into place.

I plugged the ethernet cable into my laptop(running Ubuntu 9.04), and the internet connected instantly with no problems.  Not a cable problem.

I added the lines to /etc/network/interfaces.  The file /etc/resolv.conf did not exist, so i created it and added that line.

```
$ sudo ./networking restart
*ISC junk posted below*
*same results as below call to sudo dhclient eth0, but with interval numbers of 4,4,8,15,19,11*

```

Still no internet.  I checked "enable networking", tried the script again, still nothing.  I tried to connect with network manager, nothing.

> **superprash2003 said:**
> also , in your terminal type **sudo dhclient eth0** and post output

This was done before I followed alterax's advice, with networking disabled.

```
$ sudo dhclient eth0

Internet Systems Consortium DHCP Client v3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp

Listening on LPF/eth0/00:1e:2a:3e:d7:75
Sending on LPF/eth0/00:1e:2a:3e:d7:75
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

I think I have tried everything suggested, with still no internet connection.  May I have more help please?  Should I post a syslog or something?

Only other thing I can think of is a driver problem.  I know the fa311 v2 is supported by linux, does anyone know about the 8139too driver I am using?  Should I try to use a different one?

Thank you for your help so far everyone.

---

### Post by superprash2003 on 2009-05-20
post the contents of the /etc/dhcp3/dhclient.conf file

---

### Post by dandnsmith on 2009-05-20
Can the router cope with IP6?
I see the assigned IP address looks like IP6, and not all will happily work with that - it seems significant that the PC can talk to another Ubuntu installation when plugged directly.

---

### Post by iamthemicrowave on 2009-05-25
I am sorry it took so long for the replies; I was out of town this past weekend.

> **superprash2003 said:**
> post the contents of the /etc/dhcp3/dhclient.conf file

```
option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers, domain-name, domain-name-servers, domain-search, host-name, netbios-name-servers, netbios-scope, interface-mtu, rfc3442-classless-static-routes, ntp-servers;
#requires subnet-mask, domain-namer-servers;
#timeout 60
#retry 60
#reboot 10
#select-timeout 5;
#initial-interval 2;
#script "/etch/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200
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
```

> **dandnsmith said:**
> Can the router cope with IP6?
I see the assigned IP address looks like IP6, and not all will happily work with that - it seems significant that the PC can talk to another Ubuntu installation when plugged directly.

I agree with your second statement.  How do I check to see if my router is IP6 compatible?

---

### Post by superprash2003 on 2009-05-26
try this [http://www.prash-babu.com/2009/05/how-to-fix-ip-by-dhcp-issue-in-ubuntu.html](http://www.prash-babu.com/2009/05/how-to-fix-ip-by-dhcp-issue-in-ubuntu.html)

---

### Post by dandnsmith on 2009-05-26
> **iamthemicrowave said:**
>   How do I check to see if my router is IP6 compatible?

Good question - I suspect that the answer is router/model dependent (I've no idea whether mine is)

I suspect that it may be more 'profitable' to discover how to constrain the PCs to use IPv4 - something to which I'm sure I've seen suggestions/fixes, but cannot remember where.

---

### Post by iamthemicrowave on 2009-05-26
> **superprash2003 said:**
> try this [http://www.prash-babu.com/2009/05/how-to-fix-ip-by-dhcp-issue-in-ubuntu.html](http://www.prash-babu.com/2009/05/how-to-fix-ip-by-dhcp-issue-in-ubuntu.html)

I tried your tutorial, and after I restarted networking, it still was not fixed.  I still get many lines of:

```
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval <random number>
```

and then:

```
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

I plugged the ethernet cable into my ubuntu jaunty laptop, and tried sudo dhclient eth0.  It worked fine, and I got an IP address.

Does anyone have any other suggestions? I am wondering if this is a hardware problem.  Perhaps I have just not tried the correct software fix yet.

---

### Post by zeedood on 2009-05-26
I too have run into the same issue noted here. I have vista set up on my box, and was going to set up dual boot once I saw that 9.04 ubuntu worked...so I have tried running it from the cd to start with and noted that it will not connect to the internet...the little icon in the upper right hand corner shows no network connection...
 
ifconfig shows inet6 addr with the next line showing 
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
 
if I try to ping the box with it's ip (192.168.1.97), it says connect: network is unreachable)
 
both netstat -r and route give a header line and that's it.
 
Changed the dhclient.conf as listed in one of the suggestions, restarted the network, but that didn't help either.
 
Tried setting up a static connection via netmanager...set the ip, netmask, gateway and dns server. with that, the network icon in the upper left corner showed it was connected. I can ping the local box with 192.168.1.97... but cannot ping the dns/gateway... validated the addresses by looking at the vista output for the nic card...
 
next tried setting the values in the /etc/network/interfaces file...
auto lo
iface lo inet loopback
auto eth1
iface eth1 inet static
address 192.168.1.97
netmask 255.255.255.0
gateway 192.168.1.254
restarted network again...still can't ping other than local box...
 
ifconfig now shows an inet address of 192.168.1.97, broadcast 192.168.1.255, and mask of 255.255.255.0...inet6 address still shows a hex address of some sort.
 
I know the right nic is being used as I checked the mac address...
not sure what else to try. any help would be greatly appreciated!

---

