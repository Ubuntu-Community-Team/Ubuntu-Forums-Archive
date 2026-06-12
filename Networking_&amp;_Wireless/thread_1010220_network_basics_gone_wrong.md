---
title: "network basics gone wrong"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by Richard-g8jvm on 2008-12-13
Hi

I need to move a massive amount of data between two computers both 64 bit both running 8.10.
tried the obvious which I've always done, assign both static addresses and assign static routes to both.
turn the firewall off with lokkit, still blocked.
gut feeling that lokkit tells lies and the firewall still up.
open port 21 on both machines, udp and tcp, still blocked.open port 22, to try scp. still blocked.
the routes are OK as I can ping both ways.

next step install dhcp3 server on my main machine.

eth0 is assigned a dynamic address so only want to have the dchp3 server listening on eth3.
I moved from mandriva due to poor audio support, but I could have had this up and running in minutes with MDV.
I've been through the help files and no avail there.
how do I tell dchpd3 only to listen on eth3 and how to open port 21 with 
it telling lies and saying its open when it clearly isn't


TIA

Richard

---

### Post by cmnorton on 2008-12-13
What is telling you you are blocked?

Do you have an ftp server running on one of the hosts? Or, are you using SAMBA?

---

### Post by Richard-g8jvm on 2008-12-13
on two machines its any attempt to gain access to either ports 20 or 21.


UFW just tell blatant lies , its saying ports 20 & 21 both udp and tcp are open.
I just port scanned this machine from an external source and all ports  up to 128 there is no response.

on the other machine, which has to be sorted as its a Christmas present, 
I am also getting gconf errors due to secure policy blocked the reply..
I really feel this is a bit of a joke.
on the other machine lokkit was used to turn the firewall off, but it didnt.

This must be some daft ides of a developer somewhere to protect the little kiddies from someone getting in to their machine.

my current ip address is 77.98.119.154, both 20 and 21 should be open , but they aren't

Hosts.allow is set to ALL:ALL


have I got to burn 50 DVDs to move this data block ?,,,,its crazy


Richard

---

### Post by The Cog on 2008-12-13
If you don't trust what the firewall GUI says, go underneath and get to the truth. The command **sudo iptables -nvL** will tell you what the current policies and rules are for real. These commands should clear all your firewall rules, but a firewall configuring service might put them back again after a while:
```
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -X
sudo iptables -F
```

---

### Post by Richard-g8jvm on 2008-12-13
Thanks

I ran sudo iptables -nvL and now its doing what it should.
I've completely uninstalled lokkit and ufw and installed Firestarter, which
is a much nicer front end to iptables.
I did in the end get scp to run between the two machines then got gftp running.


I get the impression there is another layer of security still in play,
I've gone back to static addressing between the two machines, but I've noticed there is still something tearing down the ifconfig and routing , or it maybe something on a auto conf on a timer thats retrying to do something once every 10 mins or so..


thanks for the help


Richard

---

### Post by The Cog on 2008-12-14
I have seen reports that network manager interferes wth static IP addresses, so it may be worth uninstalling that for a while to see if that helps.

---

### Post by Richard-g8jvm on 2008-12-14
I agree with what I've seen, its near impossible to use the network manager to use a static address.

I've cludged around the problem by running a dhcp3 server on the main machine and letting the network manage do its own thing dynamically.
setting both as static addresses works for a while, you can ping for about 180 pings then a message sendmessg not allowed.
At that point the interface goes deaf,you can run tcpdump and see the replies to the ping and the outgoing,
But nothing is shown on the CLI.

For the user who just wants to connect to a modem or what ever with a single machine, it works very well, but to use as a router its been made a pig to get going.

the develppers really need to have a look at the way other distros do networking.
Mandriva's drakconf makes it very easy, a mix of the two would be very nice.


Richard

---

### Post by The Cog on 2008-12-14
Try wicd [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) if network manager is the problem - I am very happy with it. It allows static address configuration, and you can choose between different profiles for the wired connection. Wicd also works when no-one is logged in.

---

### Post by Richard-g8jvm on 2008-12-14
Thanks I'll make a note of it.
As soon as I've finish loading everything on it and handed to its new owner, it will be using a wireless router so I can reinstall the network manager again then..

Thanks
Richard

---

