---
title: "Internet at school"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by Rahk on 2008-12-04
Hello there,

Sorry if this has been in countless posts, but I just couldn't find anything that solves my problem.

Anyway, my problem is that I can't connect to my wireless at school. It works fine where ever I try but there. What it does is that it finds the Connection, tries to connect to it, both bubbles go green, and then it just disconnects after giving up trying to get an address. I've pretty much tried everything I can come up with, which basically is just creating a new connection type, set the IP Gateway DNS etc, but it still just wont work.

I am using 8.1 and my  Network controller: Intel Corporation Wireless WiFi Link 5100

Thanks for any help provided

---

### Post by superprash2003 on 2008-12-04
post output of /etc/network/interfaces and output of iwconfig

---

### Post by razy60 on 2008-12-04
Do you need any special permissions from the school, passwords etc to enable a connection.

Raz

---

### Post by Rahk on 2008-12-04
output for /etc/network/interfaces: 
auto lo
iface lo inet loopback

and for iwconfig;

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"linksys"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1D:7E:2C:1C:6C   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2352 B   
          Power Management: off
          Link Quality=97/100  Signal level:-48 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


But i am currently at home posting this, so it might not help the actual problem?

Also to razy; no its a completely unsecured internet.... Should work right away with DHCP... but it just wont with this ubuntu instalation

---

### Post by razy60 on 2008-12-04
Should imagine that you need to be at the school,
From what i have heard from friends who are uni the wireless signals are allways rubbish so if you have even the smallest error it can cause problems.

---

### Post by timcredible on 2008-12-04
some schools are moving to certificates for wireless access, which will require more effort on your part, or they may have purposely disabled non-windows machines with nac and cisco clean access.  you need to open a helpdesk ticket with your school and get with the network guys to find out the problem.

---

### Post by superprash2003 on 2008-12-05
well what you could do , is setup static ip when connecting to school network.. set those ips in the /etc/network/interfaces file.. it seems to connect to the network but not get an ip.. so then you specify the iop

---

