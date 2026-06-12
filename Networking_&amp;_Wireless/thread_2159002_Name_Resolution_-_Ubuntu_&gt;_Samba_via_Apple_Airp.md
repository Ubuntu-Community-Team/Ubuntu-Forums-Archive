---
title: "Name Resolution - Ubuntu &gt; Samba via Apple Airport Extreme"
date: 2013-07-01
forum: Networking &amp; Wireless
---

### Post by amtrakuk on 2013-07-01
Hi there.

Something that has been puzzing me for months.

I have a small home network with a mix of Samba on the FreeBSD server, Ubuntu, Mac and the others as devices (including smart phones).  I'm using Virgin Media so I 'have' to use their supplied router - although in bridge mode.

I'm using the Airport Extreme as it is able to run BG on one channel and N on a seperate channel simataniously.  Dispite the Virgin media router being BGN compatable obviously the WiFi speed keeps dropping as and when the slowest wireless device accesses the network - something the Airport extreme doesn't suffer with.

I'm stuck between a rock and a hard place!  Everything is fine with the Airport extreme but one thing - Browsing the network.  If I use the Virgin Media Router, Clicking on "Home Folder" then "Browse the Network", the Samba server appears in the list - Thumbs up there.   If I use the Virgin router in bridge mode with the Airport extreme clicking on "Browse Network", all thats displayed is "Windows Network".  If I double click on that I get "Workgroup", double clicking on that I get a long wait and a dialoge box saying 'Opening "Workgroup"' followed but the "Unable to mount location - Failed to retrieve share list from server".  It seems that a broadcast port is being blocked?

I am able to ping the Samba server and even mount it manually (Using IP address) using the Go>Location route.

I suceeed in resolving the servers name in a terminal;

ajh@ajh-ESPRIMO-Mobile-D9510:~$ nmblookup leopard
querying leopard on 192.168.2.255
192.168.2.2 leopard<00>

But Ping seems to go via the ISP?

ajh@ajh-ESPRIMO-Mobile-D9510:~$ ping leopard
PING leopard.cable.virginmedia.net (81.200.64.50) 56(84) bytes of data.
64 bytes from advancedsearch.virginmedia.com (81.200.64.50): icmp_req=1 ttl=56 time=16.7 ms
64 bytes from advancedsearch.virginmedia.com (81.200.64.50): icmp_req=2 ttl=56 time=13.0 ms
64 bytes from advancedsearch.virginmedia.com (81.200.64.50): icmp_req=3 ttl=56 time=13.2 ms
^C
--- leopard.cable.virginmedia.net ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 13.003/14.318/16.704/1.690 ms

Would this be the cause of the problem?  If so how can it be resolved?  Any ideas would be welcome.

As I say Ive been puzzling over this for months, Ive lost count of the number of things I've tried, ususally resorting back to the Virgin Media router but suffering dipping Wireless thoughput even disconnections at times when the WLAN card briefly switches from N back to G so ideally like to use the airport extreme for a more reliable and fast connection.

---

