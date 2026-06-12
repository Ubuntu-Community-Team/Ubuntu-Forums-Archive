---
title: "Odd networking problem"
date: 2006-07-12
forum: Networking &amp; Wireless
---

### Post by neilp85 on 2006-07-12
I just got a 3 yr old Dell desktop from a friend that I'm trying to put Ubuntu on. I wouldn't label myself a linux noob but I'm far from a veteran. 

Here's my setup: 
I'm using Ethernet to connect this computer to my home network. The router I've got is the Linksys WRT54GL with the default firmware and very liberal firewall settings. According to lspci my network card is Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31).

The problem is I'm unable to connect this computer to the network. The symptoms seem odd to me. On the first boot I was notified about all the updates I needed apply but was unable to download any of the packages. That lead me to believe I must have some degree of connectivity.

I checked ifconfig and the eth0 interface was given a proper IP address. I was recieving packets but at a ratio of for every packet recieved there were 10 packets with errors. When I try to ping the router itself I get the 'Destination host unreachable' message. If I try to ping something like google it hangs and eventually quits after 30+ seconds, sometimes with an unknown host message and other time with no message at all.

I also looked at the routing table and everything looks ok there. I've got a route to the local network and a path to the internet with the router as the gateway. When I try to manually restart the interface with ifup it continuously sends DHCPDISCOVER messages and is never given an IP address. If I restart the computer though the interface seems to get configured properly and given an IP.

This problem has got me stumped. As I've said, I've got some linux experience but I've already tried all the network troubleshooting I know. Some help here would be great.

---

### Post by NathanClayton on 2006-07-12
Have you checked the network cables? It sounds almost as if there's a bad connection between your computer and the router. Maybe try plugging it into one of the cables that you know work - i.e. that of another computer.

---

### Post by neilp85 on 2006-07-12
I didn't think it was a problem with the cables because I had recently used it with a different computer on the same port without any problems. I went ahead and switched it anyway and I'm having the same problems. The only difference now is that the number of errors is less than the number of recieved packets.

---

### Post by neilp85 on 2006-07-12
I just tried a live CD of DSL and was able to connect to my local network and the internet just fine so this problem isn't with my router setup or ethernet cables.

---

### Post by aminoz on 2006-07-13
I think I have a similar problem,possibly related.  I'm using a Dell 1300 with a D-link DSL-G604T ADSL router, which I am connecting to by ethernet not wireless.  
I assumed everything was ok because I can access the web ok with firefox, but when I tried to use Update Manager or the synaptic package manager, they stall and I can't download anything. I took my laptop to work, where we have a Netgear ADSL router (don't have the model details here) and are also using the same ISP.-- Everything works ok! I was able to download updates and stuff via the package manager.  But still the same result at home.  Obviously there is a difference somewhere but I can't think what.

---

### Post by neilp85 on 2006-07-13
After my first post I did some more research to try and find a solution. I had read about disabling IPv6 and did that to no avail. I then booted the Dapper live CD and my network connection worked just fine. At this point I was stumped. With no connectivity I decided to try more drastic measures.

For those of you willing to freshly install Ubuntu I have a hacked solution that may work. I found an old Breezy install CD that I had and installed it. That went smoothly and I my eth0 connection worked perfectly. I then updated my repo lists to the dapper ones and did a dist-upgrade. After the upgrade was finished everything seemed to still be working great. I could connect to the internet, download all the new packages I needed, etc. I know this isn't an optimal solution but it worked for me so give it a try if you're desperate.

---

### Post by mips on 2006-07-13
There are know issues with the Tulip chipset. Just do a search here for 'tulip' and you will find a lot of threads. Someone even wrote a howto for Davicom Tulip  or something in that order.

---

### Post by neilp85 on 2006-07-13
Thanks, I guess reinstalling from Breezy may not have been necassary.

---

