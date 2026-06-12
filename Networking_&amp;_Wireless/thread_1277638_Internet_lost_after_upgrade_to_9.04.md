---
title: "Internet lost after upgrade to 9.04"
date: 2009-09-28
forum: Networking &amp; Wireless
---

### Post by Evelien on 2009-09-28
Today I managed to get Ubuntu 8.10 working on my system. Everything seemed to work, except accessing shared drives on a Vista machine on my LAN.
 
Then I upgraded to 9.04. And now I have lost connection to the Internet! (Ironically the shared drive on the Vista machine is now accessible in File browser and in Firefox... )
 
I can ping with the Vista machine, I can ping with my router. Trying a ping to outside the house fails (both using a hostname and using an ip-address...)
 
The response I get is:
connect: Network is unreachable
 
My networking icon at the top of the screen says "connection 'Auto eth0' active"...

---

### Post by Iowan on 2009-09-28
What are results of **route -n**? It (*should* have your gateway as the default on the last line. You can also edit the (NM) connection to verify gateway is properly set in IPv4 settings.

---

### Post by Evelien on 2009-09-28
Hmm, route -n gives an unusual result:
 
Destination  Gateway   Genmask  Flags Metric Ref  Use Iface
192.168.1.0   0.0.0.0   255.255.255.0   U  1     0      0  eth0
169.254.0.0   0.0.0.0   255.255.0.0       U  1000 0    0  eth0
 
192.168.1.0 is my gateway.
I have no idea who/what 169.254.0.0 is???

---

### Post by Evelien on 2009-09-28
I happen to have a Ubuntu 8.10 installation still on another partition.
I tried that again and it still has Internet connection.
It also has one additional line in the route -n output:
 
0.0.0.0   192.168.1.254   0.0.0.0   UG   0  0  0  eth0
 
This line is at the bottom, the other lines are the same as above
 
And this installation works...

---

### Post by Evelien on 2009-09-29
I am still without Internet. I have tried millions of things.
 
I tried to edit the connection as suggested by Iowan. I can add a gateway there, but it disappears: When I go into the edit box again, my changes are gone. (And it DID prompt me for authorization when I edited...)
 
Most notably, I have tried to add the missing line in the route table myself:
[php]
evelien@UbuntuHQ:~$ sudo route add default gw 192.168.1.0 eth0
SIOCADDRT: No such process
[/php]
Then I learned that "route add" is kind of old-fashioned, so I tried:
[php]
evelien@UbuntuHQ:~$ sudo ip route add default gw 192.168.1.0 eth0
Error: either "to" is duplicate, or "gw" is garbage.
[/php]
 
I also learned that 169.254.*.* is not a real IP-address at all, but something that is used when DHCP fails. I even saw my spouses wireless laptop that is on the same router got an address of 169.254.77.209 yesterday. At first I thought our wireless had been hacked, or the laptop had logged on to the neigbour's wireless by mistake, but now I think Ubuntu even manages to get our router confused in some way...
:confused:
Can anyone please give me a clue?

---

### Post by Evelien on 2009-09-29
Yay! My connection is back!
 
I did what Iowan suggested in this thread [http://ubuntuforums.org/showthread.php?t=1156441](http://ubuntuforums.org/showthread.php?t=1156441):
I commented out the "option rfc3442" line in /etc/dhcp3/dhclient.conf
 
So... Am I happy now?
A bit, because I can use my system.
But I always like to know WHY things work and that is not (yet) the case here....
 
Anyway, many thanks to Iowan!!

---

### Post by Iowan on 2009-09-29
I'm glad that thread *finally* helped someone else... 
It seems odd that a DHCP server would not simply ignore something it did not understand, but mine (apparently your's, too) simply gave up and did *nothing* - meaning it didn't return an IP address. I haven't tried it since I upgraded the server to Hardy (from Breezy) and substituted DNSMasq for dhcp3-server.

---

