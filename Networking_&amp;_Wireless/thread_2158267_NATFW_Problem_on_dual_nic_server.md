---
title: "NAT/FW Problem on dual nic server"
date: 2013-06-28
forum: Networking &amp; Wireless
---

### Post by jedediahgoodson on 2013-06-28
Can someone help me resolve this port/firewall issue?


I had this working for a year.  Our business moved and we got some new IP's from our ISP, and we upgraded the firewall on this machine.


Here's my setup:


1. my server (ubuntu 11) has two nics on different subnets with different WAN ip's
2. I use a sonicwall tz-215
3. I have external dns and static ips.



pretty basic I guess.


Symptoms: 


* I am not able to get an SSH or HTTP/S from the outside world.  I can get to the same internally with no problems.
* external port scan tools show these ports as STEALTH (grc.com).


What I have done:


1. swapped firewalls (no change in symptoms)
2. ensured ufw is disabled (and "ufw status" reports inactive)
3. I have light up a test web server on another box, mapped ports to that and that is accessible from the outside world.
4. internal port scan shows all the ports in question as open.


What has changed is basically the new firewall.  The internal network configuration has not changed.


When I started the server at the new location, eth1 picked up a different ip than the one I wanted.  I used a DHCP reservation on the FW to make sure I had the correct one that I had before.  I had to release and renew eth1 to get the correct local address but that did seem to work.

I used static for eth0 and dhcp for eth1 because I would get errors when using two static gateways.  Putting eth1 on DHCP worked fine previously.  My thoughts at this time is that the dual-nic nature of this machine is behind the problem somehow.  Is it possible NAT from the FW is failing because of this.  I am stuck because this worked before and it's not now.

Like I said, I changed firewalls, back to the one I used before the move, and the symptom remains the same.  

Can anyone suggest what I've done wrong here?


Here is my network configuration:


eth0      Link encap:Ethernet  HWaddr 00:0c:29:05:7e:18
          inet addr:10.10.0.64  Bcast:0.0.0.0  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe05:7e18/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7534193 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7496845 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:710779070 (710.7 MB)  TX bytes:917138974 (917.1 MB)


eth1      Link encap:Ethernet  HWaddr 00:0c:29:05:7e:22
          inet addr:10.10.1.5  Bcast:10.10.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe05:7e22/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40930 errors:0 dropped:1 overruns:0 frame:0
          TX packets:27771 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4194492 (4.1 MB)  TX bytes:7619785 (7.6 MB)


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:924521 errors:0 dropped:0 overruns:0 frame:0
          TX packets:924521 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:298377854 (298.3 MB)  TX bytes:298377854 (298.3 MB)
		  
		  
Contents of /etc/network/interfaces


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet static
address 10.10.0.64
netmask 255.255.255.0
gateway 10.10.0.1


# secondary network card
auto eth1
iface eth1 inet dhcp


There is nothing in resolv.conf or hosts that is not default.

---

### Post by jedediahgoodson on 2013-06-28
I've solved this.  The problem is you can't have two gateways on a multihomed machine when you are doing NAT.

I removed this and restarted networking.  It works now.

# The primary network interface
auto eth0
iface eth0 inet static
address 10.10.0.64
netmask 255.255.255.0
**gateway 10.10.0.1 << remove**


# secondary network card
auto eth1
iface eth1 inet dhcp

---

