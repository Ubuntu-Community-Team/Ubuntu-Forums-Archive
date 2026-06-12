---
title: "Problem connecting with Timewarner Cable Modem"
date: 2006-07-09
forum: Networking &amp; Wireless
---

### Post by venkataramanam on 2006-07-09
Hi, I am an absolute newbie to Ubuntu. I have installed Ubuntu 6.06 freshly on one of the machines (HP nc6000) on ebay. I have a cable model internet connection from TimeWarner (RoadRunner). I am not able to connect to internet. Network adapter is from Broadcom (NetXtreme BCM5705M_2 Gigabit). When I checked the Networking GUI, Ethernet Connection:etho is active and it has been setup to use DHCP. That is the only connection enabled (I have a wireless adapter also, but I have turned it off in the Networking GUI).

On suggestions from some posts, I have disabled IPv6 by changing an entry in the file /etc/modprobe.d/aliases (the line "alias net-pf-10 ipv6" changed to "alias net-pf-10 off") and then rebooting the system. That hasn't worked.

Could you please suggest any ways to rectify. I have been fighting a lot to resolve this. Please suggest any diagnostic tools as well to check internet connection statistics. Basically I am not a Linux guy other than a good user of vi editor.

Thanks
Venkat

---

### Post by mips on 2006-07-09
My standard response follows:

What hardware are you using, modem/router model etc ???
How is the above hardware configured ???

[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)
[http://www.ubuntuforums.org/showthread.php?t=78337](http://www.ubuntuforums.org/showthread.php?t=78337) 

1. Please post output of **ifconfig eth0**  (Depends on your interface number)
2. Please post output of **lspci | grep Eth**
3. Please post output of **route -n**
4. Please post output of **cat /etc/resolv.conf**
5. Please post output of **cat /etc/network/interfaces**
6. Please post output of **cat /etc/dhcp3/dhclient.conf**
7. Please copy **entire** output of windows **ipconfig /all** command here
8. Who is your ISP and provide a web link.

Can you ping your gateway IP address, can you ping 198.133.219.25 ?

---

### Post by MrHorus on 2006-07-09
In what way can you not connect?

Do you get an IP address?
Do you get an IP address but no connectivity at all?
Do you get an IP but no address resolution?

Most cable modems are merely glorified ethernet, so what to do is:

'sudo ifconfig eth0' which should show if you have an IP address assigned.

If you don't then try 'sudo dhclient' to try issueing a DHCP request to be assigned an IP.

If you have an IP address assigned then try 'ping -c 5 64.233.187.99' to try pinging Google and if this works, then try 'ping -c ww.google.com' and if that does NOT work then you have DNS problems.

Alternatively, some ISPs only allow specific computers to connect to their cable modem system and they filter this via the MAC address, so this is something that you will want to check with your ISP. If they do and you have changed ethernet interfaces at all then you can see the MAC address to give them from 'sudo ifconfig eth0' and it should be down as hardware address or physical address.

Let us know how you get on.

---

### Post by venkataramanam on 2006-07-09
> **mips said:**
> My standard response follows:

What hardware are you using, modem/router model etc ???
How is the above hardware configured ???

[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)
[http://www.ubuntuforums.org/showthread.php?t=78337](http://www.ubuntuforums.org/showthread.php?t=78337) 

1. Please post output of **ifconfig eth0**  (Depends on your interface number)
2. Please post output of **lspci | grep Eth**
3. Please post output of **route -n**
4. Please post output of **cat /etc/resolv.conf**
5. Please post output of **cat /etc/network/interfaces**
6. Please post output of **cat /etc/dhcp3/dhclient.conf**
7. Please copy **entire** output of windows **ipconfig /all** command here
8. Who is your ISP and provide a web link.

Can you ping your gateway IP address, can you ping 198.133.219.25 ?

Thanks a lot for your comprehensive reply.

I have tried disabling IPv6 as mentioned by you in the links above. That is by turning off in /etc/modprobe.b/aliases and as well as in FireFox (about:config typed in URL and changed ipv6 disable entry to true). Rebooted, but that hasn't worked for my machine.

Here is the output of the diagnostic commands that you had asked for...

UBUNTU DIAGNOSTICS:
-------------------

1. ifconfig eth0
----------------

eth0      Link encap:Ethernet  HWaddr 00:08:02:D9:EC:7E
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4642 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:297924 (290.9 KiB)  TX bytes:2076 (2.0 KiB)
          Interrupt:11

2. lspci | grep Eth
--------------------
0000:02:04.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 

01)
0000:02:0e.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M_2 Gigabit 

Ethernet (rev 03)


3. route -n
------------
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

4. cat /etc/resolv.conf
-----------------------

Blank output


5. cat /etc/network/interfaces
-------------------------------
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp


iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


6. cat /etc/dhcp3/dhclient.conf
-------------------------------

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
#prepend domain-name-servers 24.93.41.125, 24.93.41.126;
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


WINDOWS DIAGNOSTICS: (NOTE: THIS IS ON A DIFFERENT MACHINE CONNECTED TO SAME ISP. I DONT HAVE WINDOWS INSTALLED ALONGSIDE UBUNTU.)
--------------------------------------------------------

Windows IP Configuration

        Host Name . . . . . . . . . . . . : venkatm
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : satx.rr.com

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : satx.rr.com
        Description . . . . . . . . . . . : Realtek RTL8139/810x Family Fast Ethernet NIC
	Physical Address. . . . . . . . . : 00-C0-9F-95-79-BA
	Dhcp Enabled. . . . . . . . . . . : Yes
	Autoconfiguration Enabled . . . . : Yes
	IP Address. . . . . . . . . . . . : 70.114.30.16
	Subnet Mask . . . . . . . . . . . : 255.255.255.0
	Default Gateway . . . . . . . . . : 70.114.30.1
	DHCP Server . . . . . . . . . . . : 10.46.0.1
	DNS Servers . . . . . . . . . . . : 24.93.41.125
                                    24.93.41.126
	Lease Obtained. . . . . . . . . . : Sunday, July 09, 2006 12:38:52 P
	Lease Expires . . . . . . . . . . : Monday, July 10, 2006 3:11:11 AM

My ISP is TimeWarnerCable (RoadRunner). [http://www.timewarnercable.com/SanAntonio/Products/Internet/default.html](http://www.timewarnercable.com/SanAntonio/Products/Internet/default.html)

I dont have a router of my own. ISP has given a device which is connected to cable wire. It serves as a modem, phone can be connected, tv-tuner can also be connected. The device is from ARRIS Intnl (Model: TM402P/110).

When I ping my gateway (as listed in Windows), network is unreachable. Also when I ping 198.133.219.25 (what is this?), network is unreachable. (This has been done on Ubuntu)

Probably now you can suggest a simple way to get it working.

FYI: On a Windows machine, connecting with Cable Modem needs no settings to be done. Plugin network cable and start.

Thanks again for so many tips on network diagnostics.
~Venkat

---

### Post by venkataramanam on 2006-07-09
> **MrHorus said:**
> In what way can you not connect?

Do you get an IP address?
Do you get an IP address but no connectivity at all?
Do you get an IP but no address resolution?

Most cable modems are merely glorified ethernet, so what to do is:

'sudo ifconfig eth0' which should show if you have an IP address assigned.

If you don't then try 'sudo dhclient' to try issueing a DHCP request to be assigned an IP.

If you have an IP address assigned then try 'ping -c 5 64.233.187.99' to try pinging Google and if this works, then try 'ping -c ww.google.com' and if that does NOT work then you have DNS problems.

Alternatively, some ISPs only allow specific computers to connect to their cable modem system and they filter this via the MAC address, so this is something that you will want to check with your ISP. If they do and you have changed ethernet interfaces at all then you can see the MAC address to give them from 'sudo ifconfig eth0' and it should be down as hardware address or physical address.

Let us know how you get on.

Thanks very much for your suggestions.

Honestely, I dont know how to verify if I get an IP address.
I have copied the output of "iconfig etho" and "dhclient" commands here. Probably you can determine if I have an IP address assigned.

1. ifconfig eth0
-----------------

eth0      Link encap:Ethernet  HWaddr 00:08:02:D9:EC:7E  
          inet6 addr: fe80::208:2ff:fed9:ec7e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14507 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:938990 (916.9 KiB)  TX bytes:8104 (7.9 KiB)
          Interrupt:11 

2. dhclient
-----------

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/ath0/00:0b:cd:59:98:af
Sending on   LPF/ath0/00:0b:cd:59:98:af
Listening on LPF/eth0/00:08:02:d9:ec:7e
Sending on   LPF/eth0/00:08:02:d9:ec:7e
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

When I do "ping -c 5 64.233.187.99", it says "Network is unreachable" and when I do "ping -c www.google.com", it says bad number of packets to transmit.

Probably now you will some more to suggest.

Thanks
Venkat

---

### Post by mips on 2006-07-10
Power the cable modem off and then on again, read somewhere here that this might help.

Does not look like DHCP is working in your case from the dhcp logs & ifconfig output. Could I suggest a static config to see if you can then connect ? We can always go back to dhcp and try and figure it out.

---

### Post by venkataramanam on 2006-07-12
> **mips said:**
> Power the cable modem off and then on again, read somewhere here that this might help.

Does not look like DHCP is working in your case from the dhcp logs & ifconfig output. Could I suggest a static config to see if you can then connect ? We can always go back to dhcp and try and figure it out.

Guys, Finally things are working to the extent: wireless is working :-)

My laptop supports wireless as well..but I didn't have a router to make use of that. So bought a new wirless router from LinkSys. But before giving wireless a shot, I connected through ethernet cable. Things worked magically without any change. So probably somehow my laptop didn't get to understand the modem from TimeWarnerCable ( RoadRunner for that matter). After routing the modem through the friendly LinkSys router, everything looked bright. Became a little bit greedy after that. Tried to configure wireless on Ubuntu. Some initial hiccups, but finally the culprit was ...I had set up wireless data encryption (or some other key encryption) mode as WPA-PSK...But Ubuntu had a single encryption choice: WEP....So generated a new key with WEP and fed it to Ubuntu. Things didn't work first time though network signal indicator turned green with soome 70% strength. Then gave it a Cure-For-All Reboot remedy :-). Things started working.

So morale of the story...If an ISP supplied modem does not work, take a longer path with an attached router.

But, listening to all of you guys taught me all that is necessary to diagonize(spelled correctly !) networking. Thanks a lot guys.

Thanks
Venkat

---

### Post by blu.gecko on 2006-07-12
Dude, TimeWarner BrightHouse, must be from Indy, can you ping your loopback ip address your LAN. try that before you try to ping the outside world WAN. If all else fails call Tier3 and ask them if your modem is online and ask for the 10.0.0.0 ip address that brighthouse has assigned to the modem.

are you on a router by chance?
](*,)

---

### Post by mips on 2006-07-12
> **blu.gecko said:**
> Dude, TimeWarner BrightHouse, must be from Indy, can you ping your loopback ip address your LAN. try that before you try to ping the outside world WAN. If all else fails call Tier3 and ask them if your modem is online and ask for the 10.0.0.0 ip address that brighthouse has assigned to the modem.

are you on a router by chance?
](*,)

hmm, he said it is working...

---

