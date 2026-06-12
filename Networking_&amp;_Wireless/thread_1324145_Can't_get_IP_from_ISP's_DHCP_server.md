---
title: "Can't get IP from ISP's DHCP server"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by Curtis.Everingham on 2009-11-12
I posted this question on another similar thread as well:
[http://ubuntuforums.org/showthread.php?t=1312614](http://ubuntuforums.org/showthread.php?t=1312614)

My problem is that I am unable to get my ISP's DHCP server to give ubuntu an IP address. I do not have a router. This machine is set up to dual boot with windows XP. on windows, I get the external IP, so I know that in ubuntu, im looking to get my IP address from the ISP. I know basic networking in Ubuntu, but thats about it.

Here is my /etc/networking/interfaces file:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

I cant get a copy of ifconfig output at this moment, but I'll post it when I can. I do remember that there is no IP address.

Any help would be greatly appreciated, and if theres anything i could clarify to help, please let me know.

---

### Post by lensman3 on 2009-11-12
Is your firewall blocking the dhcp requests?  I think, that 0.0.0.0 is the address a dhcp server listens on.  Check to see if iptables is blocking.

---

### Post by alkatron on 2009-11-12
check /etc/dhcp3/dhclient.conf or post it here.

---

### Post by Curtis.Everingham on 2009-11-12
to Lensman3:
Im a bit confused about the iptables command... what arguments would get the info you want? as far as i know, there is no firewall enables. But I am a bit of a Ubuntu noob, so as far as I know isnt saying much.

to Alkatron:

```
# Configuration file for /sbin/dhclient, which is included in Debian's
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

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;
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
```

Thats my /etc/dhcp3/dhclient.conf file.

Thanks very much for your help, both of you.

---

### Post by Iowan on 2009-11-12
Which version are you running - I haven't seen Karmic, but dhclient.conf looks pre-Jaunty. I didn't see (or at least recognize) your other post.

---

### Post by Curtis.Everingham on 2009-11-12
Heh... a rather old version, though I'm not sure which. I'm actually trying to help my sister set up an old desktop of mine so I can log in remotely, and that installation of linux is rather old (though I hadn't really considered the version until you mentioned it, thanks for the reminder :D). I'll try and get ahold of her, and figure out what version it is/what options we have to get the new version on there. That computer is quite old (1999-2000-ish), so I dont know what kind of disc burning hardware there is. Will post more info when I get it.

---

### Post by Iowan on 2009-11-12
System>About Ubuntu should provide answers. If you're not using router, what kind of connection does ISP provide? (Cable, DSL, dialup)

---

### Post by Curtis.Everingham on 2009-11-12
Ubuntu version is 6.06 Dapper Drake, though I am looking to see if I can get a newer version installed, though I dont think that computer has a disc burning drive.

Internet type is Cable, No router, just the modem.

---

### Post by Curtis.Everingham on 2009-11-21
I am having the same problem with the automatic network configuration during the Karmic installation process (Server edition). the ISP's DHCP is just not giving me an IP. Internet works correctly on windows installed on the same machine. Any ideas would be greatly appreciated.

---

### Post by Flecko on 2009-11-21
I'm having the same issue with Ubuntu Server Edition 9.10. The same hardware works under the desktop edition, but for some reason when I put the server edition on, the network DHCP config barfs.

I can trace my problem a little more closely though...the DHCPDISCOVER requests go out correctly to 255.255.255.255 and my router see's them and sends back DHCPOFFERs, but for some reason the computer ignore's them. I've found this by checking the routers logs.

Very odd behavior, considering the same exact hardware works under Ubuntu 9.10 desktop edition.

I've tried all the potential fixes, including doing a static route, or modifying dhcpclient.conf to include the dhcp-client-identifier trick, and nothing works.

This is a real pisser considering Karmic already has a bad reputation for being buggy. I've never had a problem with an ethernet connection in Linux...and thats going all the way back to 1998.

Any ideas?

---

### Post by Iowan on 2009-11-21
Does ISP issue DHCP address - or is that a function of the modem? Only reason I ask is that my DSL modem also serves as firewall and DHCP server.

---

