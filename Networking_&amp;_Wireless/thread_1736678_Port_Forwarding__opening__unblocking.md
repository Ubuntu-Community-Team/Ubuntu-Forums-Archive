---
title: "Port Forwarding / opening / unblocking"
date: 2011-04-22
forum: Networking &amp; Wireless
---

### Post by j.piotr on 2011-04-22
Hi!
I have recently installed ubuntu 10.10 and managed to finally make Minecraft to work. 
Today i tried to connect to my friend's server, but it failed : java.net.noroutetohostexception no route to host.
After trying few things, trying to forward ports in "firestarter", forwarding on router(pirelli DRG A223G - same forwarding as [http://portforward.com/english/routers/port_forwarding/Pirelli/DRG-A226G/Minecraft_Server.htm](http://portforward.com/english/routers/port_forwarding/Pirelli/DRG-A226G/Minecraft_Server.htm)) and trying to connect again, message : connecting for like few minutes and then : timeout (no connection)
Single player works fine
We connect through Hamachi (that was another problem on Linux, but i managed to make it work and joined his network, so i think it's working)
What should i do to make it work?
Minecraft 1.4
DRG A223G
Ubuntu 10.10
Hamachi
The port for minecraft is probably 25565(that's what suggests port-forwarding and few ppl on minecraft forum).

I tried checking port on canyouseeme.org, but none (even 80) is visible.
Also i am not 100% sure i forwarded ports on linux properly(nor on router...) and i am not sure about static IP. I am connected through LAN, so 1 problem less. I made "static" IP connection and i got internet, so i think it's working
i set IPv4 settings like this :
Method : Manual
Address
192.168.1.34
Netmask
255.255.255.0
Gateway
192.168.1.254
DNS servers
192.168.1.254
search domains
192.168.1.254

I spent nearly whole day today on it, and only thing i managed to get is working Minecraft in single player and i think working Hamachi.
Any ideas?

---

### Post by Fire_Chief on 2011-04-22
What IP address did you attempt to connect to (your friend's Hamachi IP)?
With Hamachi, I think you don't need to open any firewall ports.

---

### Post by j.piotr on 2011-04-22
I tried to join 5.84.29.57. A few other ppl play at his server as well( he's on win7 others as well on windows)
Update:
my nick is properly seen by others on hamachi, no longer the java error. just connecting to the server... for like 10 mins and then "timeout"
It looks like ports are blocked, but are they blocked in linux or router? I made a port-forward, but i'm not sure if it's working(it looks like so, made like in guide)

---

### Post by j.piotr on 2011-04-23
Up? Will someone help me, please?

---

### Post by Ropes on 2011-04-23
I'm confused, why are you using hamachi? Minecraft supports networked play..

If you seem to drop after an amount of time, I'd think it comes from hamachi's instability, not your port forwarding. 

Another issue to consider is Minecraft's instability on Ubuntu, I'm on 10.10 and there are way more bugs and glitches than on Win7 for me(mostly graphics though).

I'd like to help if I can, but you need to give a little more info.   If you followed the instructions for port forwarding on your router, you've done all you can do in that area, which leaves your network settings.
What is your network config? Are you running static or DHCP?
Run this in the terminal and show the results:
```
ifconfig
```
And what are your interface settings?
```
cat /etc/network/interfaces
```

I've been dealing with a whole mess of networking problems lately so I'm rather sympathetic and will try to help if I can.

---

### Post by j.piotr on 2011-04-23
I'm confused, why are you using hamachi? Minecraft supports networked play...
[COLOR=Lime]I do not know, my friends play together on a hamachi server hosted by one of them (he has dynamic ip, maybe that's the reason? i do not know)[/COLOR]

If you seem to drop after an amount of time, I'd think it comes from hamachi's instability, not your port forwarding. 
[COLOR=Lime]The problem is i cant get IN, even for a second. If i play single-player it works perfectly(picking up, placing cubes etc etc etc, even achievements).[/COLOR]

Another issue to consider is Minecraft's instability on Ubuntu, I'm on 10.10 and there are way more bugs and glitches than on Win7 for me(mostly graphics though).
[COLOR=Lime]As i said i think i achieved stable Minecraft[/COLOR]

I'd like to help if I can, but you need to give a little more info.   If you followed the instructions for port forwarding on your router, you've done all you can do in that area, which leaves your network settings.
[COLOR=Lime]I've done just like said for DRG A226G(cause it has same layout of firmware, looks exacly the same). I remember i had problems with 6112 for starcraft and problems with Warcraft 3 as well as Utorrent, i solved those problems b4 but i truly do not remember how - i am not good at it)[/COLOR]

What is your network config? Are you running static or DHCP?
i have dynamic IP from my internet provider, but i settled static-ip "inside" the network(so i always get 192.168.1.31, i think it's proper, and i settled all port forwarder for 192.168.1.31)

Run this in the terminal and show the results:
```
ifconfig
```And what are your interface settings?
[COLOR=Lime]```
eth0      Link encap:Ethernet  HWaddr 00:24:1d:ce:e2:44  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:46 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:24:1d:ce:e2:34  
          inet addr:192.168.1.34  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1dff:fece:e234/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:260178 errors:0 dropped:0 overruns:0 frame:0
          TX packets:189109 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:356756792 (356.7 MB)  TX bytes:19190928 (19.1 MB)
          Interrupt:47 Base address:0xc000 

eth2      Link encap:Ethernet  HWaddr 00:e0:4c:bf:2b:ac  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0x9800 

ham0      Link encap:Ethernet  HWaddr f2:72:72:80:6c:54  
          inet addr:5.100.212.48  Bcast:5.255.255.255  Mask:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1200  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:6470 (6.4 KB)  TX bytes:1900 (1.9 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1664 (1.6 KB)  TX bytes:1664 (1.6 KB)

```[/COLOR]I do not know what you mean by interface settings, i have Ubuntu 10.10 for 3 or 4 days now :(
```
cat /etc/network/interfaces
```I've been dealing with a whole mess of networking problems lately so I'm rather sympathetic and will try to help if I can.
[COLOR=Lime]```
edvin@Edvin:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
```[/COLOR]
I tried to answer to each part of what you've said

---

### Post by j.piotr on 2011-04-23
Anyone, please help?
I am not even 100% sure how to settle this static-ip I would be really glad to get help with setting this to work.

---

### Post by Ropes on 2011-04-23
I would strongly recommend you setting up your static IP.  You'll have to make sure that your router is set up first, I'm sure there will be plenty of tutorials with the proper googling. Your static IP for your computer will probably wind up being something like 192.168.0.1xx

Once you have the IP associated with your computer's MAC, you'll need to setup your network interfaces.  This tutorial guided me through the process: [http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)

Once your IP is static you'll have at least one less cause which may be the problem, DHCP networks can be rather glitchy.

---

### Post by j.piotr on 2011-04-24
this site gives sample settings but doesnt say how to PROPERLY acquire them. I found mine in there:

---

### Post by Ropes on 2011-04-24
> **j.piotr said:**
> this site gives sample settings but doesnt say how to PROPERLY acquire them. I found mine in there:
I'm assuming that that's your router setup page.  I'd guess in the "IP Address Distribution" section you'll need to change the DHCP drop-down option to a Static one, maybe, again I can't see it so I don't know.

Am I correct in assuming that your router's IP is 192.168.1.254? If so, you'll need to pick your computer's IP static address something in this range: 192.168.1.[1-253]
Once you've picked that you can use the tutorial I sent you to figure out the rest, here's my interface file if it helps.

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.0.101 #This is my static IP, choose yours and use it here
        netmask 255.255.255.0  #Sets you Subnet mask, this should be roughly the same for you
        network 192.168.0.0   #Not sure on this one, Use Google to figure it out, i think yours will be 192.168.1.0
        gateway 192.168.0.1   #This needs to be your routers address for you i think it should be 192.168.1.254

```Other than that, I've told you most all I know with what you've given me.  Good luck!

---

### Post by j.piotr on 2011-04-24
> **Ropes said:**
> I'm assuming that that's your router setup page.  I'd guess in the "IP Address Distribution" section you'll need to change the DHCP drop-down option to a Static one, maybe, again I can't see it so I don't know.

Am I correct in assuming that your router's IP is 192.168.1.254? If so, you'll need to pick your computer's IP static address something in this range: 192.168.1.[1-253]
Once you've picked that you can use the tutorial I sent you to figure out the rest, here's my interface file if it helps.

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.0.101 #This is my static IP, choose yours and use it here
        netmask 255.255.255.0  #Sets you Subnet mask, this should be roughly the same for you
        network 192.168.0.0   #Not sure on this one, Use Google to figure it out, i think yours will be 192.168.1.0
        gateway 192.168.0.1   #This needs to be your routers address for you i think it should be 192.168.1.254

```Other than that, I've told you most all I know with what you've given me.  Good luck!
I can only select: "disable", "DHCP server", "DHCP Relay"
You're right with the router address.
I can't set it up with those "commands" through terminal, it's just a bit too hard 4 me. I settled the static IP b4 through right clicking on the network icon on tray and selecting edit connections.
After typing sudo nano /etc/network/interfaces i see:
```
auto lo
iface lo inet loopback
```changed to :
```

auto lo
iface lo inet loopback

auto eth1 - i have my internet connection on "auto eth1"
iface eth1 inet static
        adress 192.168.1.31            i have xxx.xxx.x.31, i added also 1 instead of 0, cause my router gives IP adresses with 1 in there
        netmask 255.255.255.0       i think it's ok
        network 192.168.10.0         Here i do not know    
        gateway 192.168.1.254       Here the screen says 0.0.0.0....
        broadcast ????? i dont need any?
``````
edvin@Edvin:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                                            SIOCDELRT: No such process
Don't seem to have all the variables for eth1/inet.
Failed to bring up eth1.
``````
sudo vi /etc/resolv.conf 
# Generated by NetworkManager
domain home
search home
nameserver 192.168.1.254
~                                                                                                                                                                                 
~                                                                                                                                                                                 
~                                                                                                                                                                                 
~                                                                                                                                                                                 
~                                                                                                                                                                                 
~                                                                                                                                                                                 
~                                                                                                                                                                                 
~                                                                                                                                                                                 
~ What should i delete in here? everything?                           
``````
edvin@Edvin:~$ host cyberciti.biz
cyberciti.biz has address 75.126.153.206
cyberciti.biz has IPv6 address 2607:f0d0:1002:51::4
cyberciti.biz mail is handled by 20 CYBERCITI.BIZ.S9A2.PSMTP.COM.
cyberciti.biz mail is handled by 30 CYBERCITI.BIZ.S9B1.PSMTP.COM.
cyberciti.biz mail is handled by 40 CYBERCITI.BIZ.S9B2.PSMTP.COM.
cyberciti.biz mail is handled by 10 CYBERCITI.BIZ.S9A1.PSMTP.COM.

```
```
edvin@Edvin:~$ ping cyberciti.biz
PING cyberciti.biz (75.126.153.206) 56(84) bytes of data.
64 bytes from www.cyberciti.biz (75.126.153.206): icmp_req=1 ttl=54 time=144 ms
64 bytes from www.cyberciti.biz (75.126.153.206): icmp_req=2 ttl=54 time=145 ms
64 bytes from www.cyberciti.biz (75.126.153.206): icmp_req=3 ttl=54 time=145 ms
64 bytes from www.cyberciti.biz (75.126.153.206): icmp_req=4 ttl=54 time=144 ms
64 bytes from www.cyberciti.biz (75.126.153.206): icmp_req=5 ttl=54 time=145 ms
64 bytes from www.cyberciti.biz (75.126.153.206): icmp_req=6 ttl=54 time=145 ms
^Z
[2]+  Stopped                 ping cyberciti.biz
edvin@Edvin:~$ ping 192.168.1.254
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.
64 bytes from 192.168.1.254: icmp_req=1 ttl=64 time=0.350 ms
64 bytes from 192.168.1.254: icmp_req=2 ttl=64 time=0.352 ms
64 bytes from 192.168.1.254: icmp_req=3 ttl=64 time=0.336 ms
64 bytes from 192.168.1.254: icmp_req=4 ttl=64 time=0.389 ms
64 bytes from 192.168.1.254: icmp_req=5 ttl=64 time=0.575 ms
64 bytes from 192.168.1.254: icmp_req=6 ttl=64 time=0.330 ms
^Z
[3]+  Stopped                 ping 192.168.1.254

```Thanks a lot for help:) i nearly thought that noone cares:(

---

### Post by Fire_Chief on 2011-04-25
Just curious, are you able to connect to other public Minecraft servers? For example, there are servers at mcserverlist.net.

If so, then is it possible your friend is running his private server on a non-default port? Try to include the port when you connect to his server.

You can also test a raw connection to his server using telnet
```
telnet 5.84.29.57 *serverportnumber*
```

Cheers!

---

