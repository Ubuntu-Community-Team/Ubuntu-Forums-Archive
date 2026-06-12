---
title: "open ports?"
date: 2011-06-23
forum: Networking &amp; Wireless
---

### Post by Whatever212 on 2011-06-23
I am currently having an issue attempting to set up a dedicated server for source games (TF2, CS:S, L4D2). The required port (27015), along with most others, appears closed to the rest of the world and upon a port scan with DMZ hosting on (therefore no router interference between the internet and my computer) only a few ports are open (80, 139, 443, 445). My ISP does not block ports so therefore the only issue I can find is with my computer running Ubuntu 11.04. I have ensured that all traffic is allowed via iptables and I can't think of anything else that would have ports closed. Thanks for any help given.

---

### Post by Dangertux on 2011-06-23
Two suggestions off the top of my head.

The first are you scanning the right external IP address? If you are the second comes into play.

Is the right system in the DMZ?

The ports you listed by default are

80 - http/www server 
135 - MSRPC
139 & 445 are for netbios

You should not be seeing ports 135,139 , and 445 on a Ubuntu machine.  So my suspicion is that you're scanning a windows machine.

If you have multiple systems on your network make sure the correct system is in the DMZ (IE: the Ubuntu Server)

Oh yeah something else you need to keep in mind. If you are scanning the Ubuntu machine from inside your network you need to scan by local IP. If you scan your external IP address from behind a NAT router, Network Address Translation will make your results bogus. Also when connecting to your own game server you must use the local IP. That is just the magic of NAT.

Also make sure for testing purposes you disable ufw to ensure that the application you are serving successfully is binding to the port. Once you have connectivity that way punch a hole in ufw for the game server turn ufw on and rock out.

---

### Post by Whatever212 on 2011-06-23
I disabled ufw and now status from [https://www.grc.com/x/portprobe=27015](https://www.grc.com/x/portprobe=27015) says stealthed however no connections can be made still. I don't think that NAT comes into play with DMZ on because (from my router) "DMZ hosting enables a LAN device to use the modem WAN IP address as its own. DMZ places the LAN device outside the firewall." I also made sure that it is the ubuntu machine that is using the DMZ hosting.

---

### Post by Dangertux on 2011-06-23
Well -- as I said previously it appears you have a Windows machine in the DMZ , your Ubuntu machine should not have RPC or Netbios open by default. 

As far as how DMZ routing  works it essentially places the IP address you specify "outside" of the NAT Firewall. 

If you type netstat -a in a terminal (on the machine running the server) and post the results as well as an ifconfig -a I can help you a little better.

For now I am standing by you have the wrong IP address in the DMZ. For more information about [DMZ and NAT routing check out the wiki.]("http://en.wikipedia.org/wiki/DMZ_%28computing%29")

Can you connect to the machine's address locally? If not then the gameserver has not bound to the port successfully this can be verified by the netstat -a command.

---

### Post by Whatever212 on 2011-06-23
Netstat -a output 
```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost.localdom:6502 *:*                     LISTEN     
tcp        0      0 localhost.localdo:27015 *:*                     LISTEN     
tcp        0      0 *:netbios-ssn           *:*                     LISTEN     
tcp        0      0 *:5900                  *:*                     LISTEN     
tcp        0      0 *:www                   *:*                     LISTEN     
tcp        0      0 *:5298                  *:*                     LISTEN     
tcp        0      0 localhost.localdoma:ipp *:*                     LISTEN     
tcp        0      0 *:31416                 *:*                     LISTEN     
tcp        0      0 *:17500                 *:*                     LISTEN     
tcp        0      0 *:microsoft-ds          *:*                     LISTEN     
tcp        0      0 FtKnox.local:51923      72-165-61-189.dia:27030 TIME_WAIT  
tcp        0      0 FtKnox.local:58525      www.sourcemod.net:www   TIME_WAIT  
tcp        0      0 FtKnox.local:49377      baymsg1020122.gate:msnp ESTABLISHED
```ifconfig -a output:
```
eth0      Link encap:Ethernet  HWaddr 70:5a:b6:36:dc:e3  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3441332 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6521317 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:258323034 (258.3 MB)  TX bytes:953074831 (953.0 MB)
          Interrupt:43 

eth1      Link encap:Ethernet  HWaddr c4:17:fe:b9:1f:fb  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:8630106 errors:35240 dropped:0 overruns:0 frame:29614917
          TX packets:5220038 errors:15 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3095144053 (3.0 GB)  TX bytes:847018733 (847.0 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6880 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6880 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:404695 (404.6 KB)  TX bytes:404695 (404.6 KB)
```I am using the Ethernet to connect to the network and I have re-entered 192.168.0.10 for the DMZ and the correct computer is further verified by the current computer name in the drop down box. I can connect using 192.168.0.10:27015.

---

### Post by Dangertux on 2011-06-23
Hmm... Ok -- well that verifies you are running a SMB server and a Webserver, it also shows that your game server is correctly bound.

So... Having said you re-entered the correct IP in the DMZ, on to the next line of questioning.

1 -- After doing all this do the ports still show up as closed?

2 -- Double check that UFW isn't running sudo ufw disable

3 -- Are you running any other ipchains rules such as bastille? 

4 -- Can anyone ELSE connect to your server? Again you're not going to be able to connect locally through your DNS or external IP. However , if someone else can connect you're golden.

EDIT: This will probably be my last post in this thread for tonight -- try to have someone login to the game server I would imagine they should be able to connect.

---

### Post by Whatever212 on 2011-06-23
I restarted the modem to see what would happen and upon modem restart with DMZ disabled I was unable to connect to any websites until I disabled DMZ. And since I am pretty much back to square one again (because port forwarding produces no results) I am just going to give up on this particular project. It would have been nice but its not mission critical. Thanks for the help.

---

### Post by Dangertux on 2011-06-24
Hmm...That's very odd, sorry I couldn't help you come to a resolution :-(

I would say just save the knowledge for the next go-round sooner or later I am sure you will take the project back up. That's how it always is with me at least. If I fail at something I'll take a break for a few days or weeks or even months, then give it another shot. 

Giving your mind time to breathe and look at it from a fresh perspective may help you see something you over looked.

Good luck :-)

---

### Post by doas777 on 2011-06-24
based on your netstat output, there is no service running on port 27015.

lets start with some terminology:
A **Blocked **port, is one that cannot be accessed (firewall, NAT, etc).
A **Closed **port is one that is accessible, but does not have a service listening on it.
An **Open **port is accessible, and has a service listening on it.

when you load a service, it **creates **a port and establishes a listener on it, so without a service running, you don't really have a port at all. the number is just an ID. a closed port is like an address that was never assigned to a house, or an unallocated phone number. the way networking is often taught, the port is emphasized over the service, but in reality it's the other way around. took me a while to realize it myself. when you focus on OSI layers 1-4, it looks like ports are always there, with or without a service installed, but that is not the case when you start looking up the stack. 

my advice is to restart your service, and then run:
```
dmesg | tail
``` to view the last 10 errors. if nothing comes up, make note of the time, restart the service again, and go to your log file viewer. look at kernel.log, messages, syslog, and debug.log for that time mark. with luck, that will provide info on why the service is not loading, and thus not opening the port.

once you have a service running, you may need to allow it through ufw,  but disabling ufw on a dmz server seems unwise, especially since you  have VNC listening globally. that would scare the pants off me. VNC should be allowed internally only. if you are looking for a secure form of remote  access, I suggest [freeNX]("https://help.ubuntu.com/community/FreeNX"). the samba is also quite worrisome.

---

### Post by Dangertux on 2011-06-24
> **doas777 said:**
> based on your netstat output, there is no service running on port 27015.

lets start with some terminology:
A **Blocked **port, is one that cannot be accessed (firewall, NAT, etc).
A **Closed **port is one that is accessible, but does not have a service listening on it.
An **Open **port is accessible, and has a service listening on it.

when you load a service, it **creates **a port and establishes a listener on it, so without a service running, you don't really have a port at all. the number is just an ID. a closed port is like an address that was never assigned to a house, or an unallocated phone number. the way networking is often taught, the port is emphasized over the service, but in reality it's the other way around. took me a while to realize it myself. when you focus on OSI layers 1-4, it looks like ports are always there, with or without a service installed, but that is not the case when you start looking up the stack. 

my advice is to restart your service, and then run:
```
dmesg | tail
``` to view the last 10 errors. if nothing comes up, make note of the time, restart the service again, and go to your log file viewer. look at kernel.log, messages, syslog, and debug.log for that time mark. with luck, that will provide info on why the service is not loading, and thus not opening the port.

once you have a service running, you may need to allow it through ufw,  but disabling ufw on a dmz server seems unwise, especially since you  have VNC listening globally. that would scare the pants off me. VNC should be allowed internally only. if you are looking for a secure form of remote  access, I suggest [freeNX]("https://help.ubuntu.com/community/FreeNX"). the samba is also quite worrisome.

Are you sure? I might be losing my mind but I'm pretty sure the second line of his netstat output shows localhost.localdomain is listening on 27015 tcp.

Like I said I might be off my rocker it's after 1 am lol

Also he noted that he could connect locally... Which indicates both a running service and an open port, prior to the external network , which is what had me on the DMZ for 3 posts lol.

>  I can connect using 192.168.0.10:27015.But yeah good catch on the VNC I didn't even see that earlier.

---

### Post by doas777 on 2011-06-24
> **Dangertux said:**
> Are you sure? I might be losing my mind but I'm pretty sure the second line of his netstat output shows localhost.localdomain is listening on 27015 tcp.

Like I said I might be off my rocker it's after 1 am lol

Also he noted that he could connect locally... Which indicates both a running service and an open port.

you are correct, it may be my eyes that are going. sry its late. the output does show the problem however:
```
tcp        0      0 **localhost.localdo**:27015 *:*                     LISTEN
```this listener will only take connections from 127.0.0.1 (note the local address column). this parameter is controlled by the service when it loads, so somewhere in the service config there should be a setting to listen globally on 0.0.0.0 (*) .

---

### Post by Dangertux on 2011-06-24
LOL YOU ROCK! You read my mind, this was driving me nuts, as soon as I read your post and looked back at his netstat output I thought the same thing about being bound to localhost, however...It is still confusing as to why he can connect to the 192.168.0.10 address if it is only bound locally, he shouldn't be able to connect on that interface... 

I vote we chaulk it up to magic lol.

EDIT...It is late I got way too excited about that lol...Meh eyes feel like bleeding, I'm going to bed good luck with this issue :-D

---

### Post by doas777 on 2011-06-24
> **Dangertux said:**
> 

I vote we chaulk it up to magic lol.

np yo.

my guess is that since the ip 192.168.0.10 has its shortest route over the loopback interface, so the packet appears to come from 127.0.x.x. the easiest test is to try to connect from a terminal inside the local network, hitting 192.168.0.10.

---

