---
title: "Static IP and different subnet gateway"
date: 2010-07-09
forum: Networking &amp; Wireless
---

### Post by sammer021486 on 2010-07-09
I have Ubuntu 10.04 Desktop running as a testing web server, but I am having issues giving the server a static IP and to add to the matter the Default Gateway is on another subnet.

I do not have network-manager or network-manager-gnome installed

To set the static IP I entered the following into /etc/network/interfaces
```

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 172.16.213.25
netmask 255.255.255.0
network 172.16.213.0
broadcast 172.16.213.255
gateway 172.16.212.1

```the DNS /etc/resolv.conf file already has the servers entered in it from when the server was getting its IP dynamically

I have to restart the box to apply the new IP address because sudo ifup eth0 and sudo /etc/init.d/networking restart both return errors for eth0

After restarting eth0 shows all of the correct information for the interface and after adding 172.16.212.1 to the route table as the default gateway, I am unable to connect to the internet and am unable to ping the default gateway.

If I change the address from 172.16.213.25 to 172.16.212.25 I am able to ping the gateway but still not able to connect to the internet.

---

### Post by jonobr on 2010-07-09
Maybe Im missing something obvious here, but your ip address should be in the same subnet as the gateway,


Again, I must be missing something obvious here

---

### Post by Iowan on 2010-07-09
There was another thread a while back about a working machine with gateway outside the subnet - but I still don't understand why it would work. 

If you change the address, it messes up the network address, which (I've read) is optional. a subnet of 255.255.254.0 would put the gateway in the network... but all associated machines would need to be changed. 

Can you ping the internet by IP address (74.125.95.147)?

---

### Post by sammer021486 on 2010-07-09
I wonder if this is the thread you are referring to [COLOR=Red][http://ubuntuforums.org/showthread.php?t=1510986](http://ubuntuforums.org/showthread.php?t=1510986)[/COLOR] I tried to set up the route [COLOR=Black]to[/COLOR] do this, before posting my thread, but had no luck.  


I can only access the internet when DHCP is enabled and I setup DHCP by the /etc/network/interfaces file, like so 
```
 auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
```If I use a static IP on the 172.16.212.0/24 subnet I have no access to the internet, but can see the computer listed in "The Dude" network mapping tool and can ping any other PC on the network.  Try to ping [www.google.com]("http://www.google.com") and get no reply.  I cannot try it tonight, but probably tomorrow, to ping a web address by its IP address instead of name.

I wish I had paid more attention in school and this was fresh in my mind, because I did this in school in my network security course.

---

### Post by bab1 on 2010-07-10
> **Iowan said:**
> There was another thread a while back about a working machine with gateway outside the subnet - but I still don't understand why it would work. 

If you change the address, it messes up the network address, which (I've read) is optional. a subnet of 255.255.254.0 would put the gateway in the network... but all associated machines would need to be changed. 

Can you ping the internet by IP address (74.125.95.147)?

@Iowan,

I'll bet you meant [_[COLOR="Blue"]this thread[/COLOR]_]("http://art.ubuntuforums.org/showthread.php?t=1510986&page=3").  I've not looked at this guy's issues.  I hope this helps out.

@jonobr,

The default gateway does not need to be in the same subnet.  You are correct that, typically the setup is: the nearside interface (inside nic) of the **directly connected** router, but it does not always have to be so.  If you declare a route and then make that route the default gateway it will work.

I guess you need to think of what a "route" is.  It really just states: if you have traffic for this IP send it to that IP via this interface (nearside router interface).  Once you have that in place you just declare the gateway as: any traffic that we don't explicitly know where it goes send it to the above "route"

It should be noted: you need to know that the "route" IP in this case must be a gateway device.  You can't just send it anywhere.  In the thread above.  The ISP explicitly defined the gateway IP address that was not part of the users subnet.  In other words: you need to know the upstream gateway IP address.

---

### Post by bab1 on 2010-07-10
> **sammer021486 said:**
> I wonder if this is the thread you are referring to [COLOR=Red][http://ubuntuforums.org/showthread.php?t=1510986](http://ubuntuforums.org/showthread.php?t=1510986)[/COLOR] I tried to set up the route [COLOR=Black]to[/COLOR] do this, before posting my thread, but had no luck.

I'm sure it is.  :-)

We can talk about it tomorrow.

---

### Post by sammer021486 on 2010-07-12
When the linux box is running DHCP these are the settings

```

administrator@ServerLinux:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          inet addr:172.16.212.52  Bcast:172.16.212.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:719 errors:0 dropped:0 overruns:0 frame:0
          TX packets:685 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:330593 (330.5 KB)  TX bytes:94742 (94.7 KB)
          Interrupt:20

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:300 (300.0 B)  TX bytes:300 (300.0 B)

administrator@ServerLinux:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.212.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         172.16.212.1    0.0.0.0         UG    100    0        0 eth0
administrator@ServerLinux:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp


administrator@ServerLinux:~$ cat /etc/resolv.conf
nameserver 8.8.8.8
nameserver 8.8.4.4
administrator@ServerLinux:~$

```When I switch the box over to STATIC these are the settings

```

administrator@ServerLinux:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          inet addr:172.16.212.62  Bcast:172.16.212.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:356 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34260 (34.2 KB)  TX bytes:2106 (2.1 KB)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 B)  TX bytes:300 (300.0 B)

administrator@ServerLinux:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.212.1    0.0.0.0         255.255.255.255 UH    0      0        0 eth0
172.16.212.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         172.16.212.1    0.0.0.0         UG    0      0        0 eth0
0.0.0.0         172.16.212.1    0.0.0.0         UG    100    0        0 eth0
administrator@ServerLinux:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 172.16.212.62
netmask 255.255.255.0
netwok 172.16.212.0
broadcast 172.16.212.255
gateway 172.16.212.1


administrator@ServerLinux:~$ cat /etc/resolv.conf
nameserver 8.8.8.8
nameserver 8.8.4.4
administrator@ServerLinux:~$ 

```When the box is set to DHCP I have no problems accessing the internet or pinging other computers.  Switch over to STATIC and I can still ping, but no internet connection

Once I have this working for the xxx.xxx.212.xxx network I have to switch the box over to the xxx.xxx.213.xxx network, but the gateway will be located on the xxx.xxx.212.xxx network.

---

### Post by bab1 on 2010-07-12
> **sammer021486 said:**
> ...When the box is set to DHCP I have no problems accessing the internet or pinging other computers.  Switch over to STATIC and I can still ping, but no internet connection.

Ping what; just the local LAN hosts?  How did you configure the static settings?  Where are the static settings set?  Can you post those settings.> 

Once I have this working for the xxx.xxx.212.xxx network I have to switch the box over to the xxx.xxx.213.xxx network, but the gateway will be located on the xxx.xxx.212.xxx network.

I think if we figure out how to set the static settings above we will have no problems moving to another subnet and using the original gateway.

Why do you need to do this?  Can you explain the network topology a bit?

---

### Post by sammer021486 on 2010-07-12
> **bab1 said:**
> Ping what; just the local LAN hosts?  
I can still ping other computers in the same subnet.  

> How did you configure the static settings?  Where are the static settings set?  Can you post those settings.
Static settings are all configured through the /etc/network/interfaces file.  I concatenated my settings in the code boxes above.  The code boxes show the settings while in dynamic mode and then static mode

Other than the above settings that I posted I am not sure what else you are looking for


> 
Why do you need to do this?  Can you explain the network topology a bit?
The topology is modem > watch guard router > switch > linux box

router has DHCP starting at xxx.xxx.xxx.50 - xxx.xxx.xxx.199, first part of my error today I tried to issue ip xxx.xxx.xxx.62

The xxx.xxx.213.xxx subnet is the web server portion of the router.  The router has the option of running two networks protected and unprotected.

---

### Post by bab1 on 2010-07-12
> **sammer021486 said:**
> I can still ping other computers in the same subnet.  


Static settings are all configured through the /etc/network/interfaces file.  I concatenated my settings in the code boxes above.  The code boxes show the settings while in dynamic mode and then static mode.

I see it now.  I missed the static part.  :-(> 

Other than the above settings that I posted I am not sure what else you are looking for



The topology is modem > watch guard router > switch > linux box

router has DHCP starting at xxx.xxx.xxx.50 - xxx.xxx.xxx.199, first part of my error today I tried to issue ip xxx.xxx.xxx.62

The xxx.xxx.213.xxx subnet is the web server portion of the router.  The router has the option of running two networks protected and unprotected.

What you are telling me is that you are setting up a separate DMZ subnet for the web server.  What I also noticed was that this is a private range of IP subnets and therefore you are using NAT.  This means you need to forward port 80 to the web server for it to work.

Can you point me to a location that has the manual for the Watch Guard router you are using?  I want to see how they suggest you configure the DMZ.

---

### Post by sammer021486 on 2010-07-13
> **bab1 said:**
> 
What you are telling me is that you are setting up a separate DMZ subnet for the web server.  What I also noticed was that this is a private range of IP subnets and therefore you are using NAT.  This means you need to forward port 80 to the web server for it to work.

I kind of have two things going at once.  

The first and most important is to get this linux box setup with a static IP and working.  Right now when given a static IP I have no internet on the box, but I can ping any other computer in the subnet.  I even tried putting the default route right into the /etc/network/interfaces file.  I can not however ping any web address.  Switch the box back to DHCP and restart the services and I can surf the internet, no problem.

The second task, after I get the box setup with a STATIC IP and working properly, the IP will be switched from xxx.xxx.212.xxx to xxx.xxx.213.xxx which is the DMZ side of the router.  

> 
Can you point me to a location that has the manual for the Watch Guard router you are using?  I want to see how they suggest you configure the DMZ.
I could not find a model number on the router, but if you go to [www.watchguard.com](www.watchguard.com) and look for the wireless routers you will find a manual for them.

Their set up is almost like any other router, specify address range, DHCP, gateway, etc, but they have two branches to connect to.  There is the private side that connects your internal network and then there is the optional, which is also configured the same way as any other router, but

---

### Post by bab1 on 2010-07-13
> **sammer021486 said:**
> I kind of have two things going at once.  

Yes you do.> 

The first and most important is to get this linux box setup with a static IP and working.  Right now when given a static IP I have no internet on the box, but I can ping any other computer in the subnet.  I even tried putting the default route right into the /etc/network/interfaces file.  I can not however ping any web address.  Switch the box back to DHCP and restart the services and I can surf the internet, no problem.

The second task, after I get the box setup with a STATIC IP and working properly, the IP will be switched from xxx.xxx.212.xxx to xxx.xxx.213.xxx which is the DMZ side of the router.  


I could not find a model number on the router, but if you go to [www.watchguard.com](www.watchguard.com) and look for the wireless routers you will find a manual for them.

Nope.  You have to be the lead on this.  I'm not going to hunt for you.  I'll help you but I won't work harder than you on your problem.  I'll bet if you look on the config page you can figure it out.   Let me know when you do.> 

Their set up is almost like any other router, specify address range, DHCP, gateway, etc, but they have two branches to connect to.  There is the private side that connects your internal network and then there is the optional, which is also configured the same way as any other router, but

**[COLOR="Red"]Almost [/COLOR]**can mean big differences.  I understand more than you think I do, but I need specifics.

Let me know and we can proceed tomorrow.

---

### Post by sammer021486 on 2010-07-13
Found the help file for the Firebox X Edge [http://www.watchguard.com/help/docs/edge/10/en-US/index.html](http://www.watchguard.com/help/docs/edge/10/en-US/index.html) 

I do not have administrative rights to the watchguard router, so nothing can be changed by me or screen captured for specifics.   

This router is currently setup though with the mailservers (Win 2003) and all of the computers and networked printers in the trusted zone, there is no MAC filtering.  The IP address available for DHCP is from xxx.xxx.xxx.50-xxx.xxx.xxx.199 on the trusted network.  

On the Optional network, there is a web server (win 2003) hosting the companies website.  Currently the server is connected directly to the router through the Optional port.  Once this Linux server is up and running static ip, the two servers will be connected through a switch to the router.  


External Addressing is setup by the ISP through PPPoE

Trusted is the xxx.xxx.212.xxx 

Optional is the DMZ xxx.xxx.213.xxx


This problem is not isolated to the watchguard router, I am having the same problem behind a Linksys WRT54G2 router, running cisco's software.  DHCP works fine, but as soon as I switch over to STATIC, no more internet connection.

---

### Post by bab1 on 2010-07-13
> **sammer021486 said:**
> Found the help file for the Firebox X Edge [http://www.watchguard.com/help/docs/edge/10/en-US/index.html](http://www.watchguard.com/help/docs/edge/10/en-US/index.html) 

I do not have administrative rights to the watchguard router, so nothing can be changed by me or screen captured for specifics. 

Very interesting.  Do you the right to be attempting this configuration? Does management know what you are doing in this area?>   

This router is currently setup though with the mailservers (Win 2003) and all of the computers and networked printers in the trusted zone, there is no MAC filtering.  The IP address available for DHCP is from xxx.xxx.xxx.50-xxx.xxx.xxx.199 on the trusted network.  

On the Optional network, there is a web server (win 2003) hosting the companies website.  Currently the server is connected directly to the router through the Optional port.  Once this Linux server is up and running static ip, the two servers will be connected through a switch to the router. 

I have just skimmed the manual and my impression is that the 2 subnets are on different ports at the WatchGuard device.  Just changing the IP address is not enough.  The host has to be connected to the correct port.  Do you have physical access to the WatchGuard and the blessing of your company's management to mess with it.> 


External Addressing is setup by the ISP through PPPoE

Irrelevant in this context.> 


Trusted is the xxx.xxx.212.xxx 
One physical port (i.e. like a NIC) in the WatchGuard.> 

Optional is the DMZ xxx.xxx.213.xxx
A separate physical port (a second NIC). > 


This problem is not isolated to the watchguard router, I am having the same problem behind a Linksys WRT54G2 router, running cisco's software.  DHCP works fine, but as soon as I switch over to STATIC, no more internet connection.
Where are you pluging the Linksys into the network (topology please)

If the watchguard works as I suspect it does the ports on the device are routed and not switched.  Therefore you can't just add a switch to one of the ports and have access to both subnets.  

At this point access to the Optional network is is not really important.  What is interesting is the *static *IP restriction.  It is possible to restrict internet access (via the WatchGuard rules) to only those who have an IP address in the DHCP pool.  I don't know that for a fact so lets try this again.

Post the following outputs **and your results **for both static and DHCP config.  Make sure you do not use an IP that is part of the DHCP pool (but must be part of the 172.16.212.0/24 subnet)```
ifconfig -a
route
route -n
```

---

### Post by sammer021486 on 2010-07-13
> **bab1 said:**
> Very interesting.  Do you the right to be attempting this configuration? Does management know what you are doing in this area?
Yep, IT manager was the one that asked me to configure a linux box for a testing web server, he has no knowledge of how to work in Linux.  If I really need access to the router he will log me in so that I may make the changes required, but as it stands it should be a simple change from DHCP to STATIC and then switch the linux box over to the DMZ network.  He would prefer that this be done without any changes to the router, if possible.

> 
I have just skimmed the manual and my impression is that the 2 subnets are on different ports at the WatchGuard device.  Just changing the IP address is not enough.  The host has to be connected to the correct port. Correct, there is 4 NICs on the Trusted side of the router and 1 NIC on the Optional side.   The 4 NICs on the Trusted side are switched while the Optional NIC is routed so that the Trusted may access it, but nothing may enter from the Optional side.

Once the linux box is working in STATIC mode on the Trusted network it will be added to the Optional network via switch.

I have a diagram of the network that I will post at the bottom of this post to help you visualize the network.

> 
Do you have physical access to the WatchGuard and the blessing of your company's management to mess with it.Yes, full physical access.  The only limitations I have is Admin rights to the router, but can gain them if really required.


> 
One physical port (i.e. like a NIC) in the WatchGuard.
4 Trusted ports
> 
A separate physical port (a second NIC). 
1 Optional port

> 
Where are you pluging the Linksys into the network (topology please)
To test to see if it was the watchguard, I took the Linux Box home and connected it to my network, which is a simple modem > WRT54G2 setup.  I assigned it an IP outside of my DHCP and had no internet connection, yet I can take a windows PC and configure it with a different STATIC IP, and still have internet connection, while the Linux box is sitting there with no internet.

> If the watchguard works as I suspect it does the ports on the device are routed and not switched.  Therefore you can't just add a switch to one of the ports and have access to both subnets.  Hopefully my diagram will help explain the setup better

> 
At this point access to the Optional network is is not really important.  What is interesting is the *static *IP restriction.  It is possible to restrict internet access (via the WatchGuard rules) to only those who have an IP address in the DHCP pool.  I don't know that for a fact so lets try this again.I asked our IT manager the same question, if the WatchGuard was configured to only allow certain IPs on the Trusted network, but he said that both servers currently on the network are Static IP addresses and that I should be able to assign any IP and it will allow the new STATIC IP.  But now that you mention it, the two servers are xxx.xxx.212.80 and xxx.xxx.212.81, which are both inside of the DHCP range of xxx.xxx.212.50-199.  

From my understanding all that was done prior to my employment with the company was to assign the servers a STATIC IP and that was it, instant success.  

I will have to get the IT manager to give me access to the router to see what is currently set up for the two servers, maybe the answer is just assigning the router to remember the MAC of the Linux NIC and always reserve the same IP to the Linux box.


> 
Post the following outputs **and your results **for both static and DHCP config.  Make sure you do not use an IP that is part of the DHCP pool (but must be part of the 172.16.212.0/24 subnet)```
ifconfig -a
route
route -n
```I will have to do that tomorrow as I am currently at home


While I was typing this post, I was also configuring a Ubuntu 10.04 Guest in Virtual Box with my NIC for the Guest set to Bridge mode to allow the virtual machine to get one of my WRT54G2 IP addresses.  Configured the image the same way as I am with the box at the office and it has taken the STATIC IP and I am surfing the net.  

Yet I was unable to configure the Linux Box from the office, last night to do the same on my home network, maybe the install on the Linux box is corrupt, the only difference between the one at the office and the virtual one is that I have removed the network-manager and network-manager-gnome from the Office box.  The Office box was installed using Universal USB Installer and the same ISO used to install the virtual guest.  

If needed I can format and reinstall Ubuntu on the Office box, there is nothing on it at the moment.

Another issue that was noticed today while I was trying to configure the Linux Box at the office, was that pinging out was disabled, that is a new development within the past few days, as we were able to ping out before, to external addresses.


The Red connection is the current connection to the Web server, once this Linux Box is up and running the dotted connection will be used.  The Blue connection shows the current location of the Linux Box in the Trusted Network right now, this is not to scale, but just an image to help you visualize the current network topology
[IMG]http://sphotos.ak.fbcdn.net/hphotos-ak-ash2/hs019.ash2/34316_408549973299_505568299_4527304_2626045_n.jpg[/IMG]

---

### Post by bab1 on 2010-07-14
> **sammer021486 said:**
> Yep, IT manager was the one that asked me to configure a linux box for a testing web server, he has no knowledge of how to work in Linux.  If I really need access to the router he will log me in so that I may make the changes required, but as it stands it should be a simple change from DHCP to STATIC and then switch the linux box over to the DMZ network.  He would prefer that this be done without any changes to the router, if possible.

I agree the less we mess with the WatchGuard the better off you are.  There is nothing worse that trying to figure out what someone did in the past, but failed to document.  
> 

Correct, there is 4 NICs on the Trusted side of the router and 1 NIC on the Optional side.   The 4 NICs on the Trusted side are switched while the Optional NIC is routed so that the Trusted may access it, but nothing may enter from the Optional side.

Just being picky here -- when you are talking about a switched (Ethernet/Layer2) connection, the cable connects via a port.  If it is routed then you need a NIC.  So what we really have is a 4 port switch integrated into a device with for one of the NIC's while the other NIC has only one port (e.g. the Trusted and Optional subnets).
> 

Once the linux box is working in STATIC mode on the Trusted network it will be added to the Optional network via switch.

As I thought so,  Once done it just needs you to make a cable switch from the Trusted switch to the Optional switch and a retest.> 

I have a diagram of the network that I will post at the bottom of this post to help you visualize the network.

I see it.  It makes sense to me. > 

Yes, full physical access.  The only limitations I have is Admin rights to the router, but can gain them if really required.

If we do this correctly then your boss can take care of the incidentals. This is better for you.  He can't point to you and say "you messed it up", or worse, make you fix it.  Not a pretty thought.> 

To test to see if it was the watchguard, I took the Linux Box home and connected it to my network, which is a simple modem > WRT54G2 setup.  I assigned it an IP outside of my DHCP and had no internet connection, yet I can take a windows PC and configure it with a different STATIC IP, and still have internet connection, while the Linux box is sitting there with no internet.


My impression is that the OS install is flawed.  You should reinstall
> 

I asked our IT manager the same question, if the WatchGuard was configured to only allow certain IPs on the Trusted network, but he said that both servers currently on the network are Static IP addresses and that I should be able to assign any IP and it will allow the new STATIC IP.  But now that you mention it, the two servers are xxx.xxx.212.80 and xxx.xxx.212.81, which are both inside of the DHCP range of xxx.xxx.212.50-199.


If the servers are using IP addresses that are inside of the pool then they need to be reserved, not static addresses.  This means the DHCP server still hands them out but on a reserved basis.

In the past I have tried to make users aware of the differences between STATIC and DYNAMIC IP addressing.  Here is my take on it ```

Dynamic = An IP address assigned by a DHCP server
  Additional configuration can be delivered this way

Static  = An IP address configured via config files
  In Ubuntu/Debian this means /etc/network/interfaces and
  /etc/resolv.conf

Reserved = This is how you provide a immutable (unchanging) IP address via DHCP.  
It is still a dynamically assigned address. There is still a lease but the 
IP address stays the same.  The host is ID'd via the MAC address.

```
>   

From my understanding all that was done prior to my employment with the company was to assign the servers a STATIC IP and that was it, instant success.  

I will have to get the IT manager to give me access to the router to see what is currently set up for the two servers, maybe the answer is just assigning the router to remember the MAC of the Linux NIC and always reserve the same IP to the Linux box.

As I said a RESERVED IP address.  If it is truly a static address AND it is in the DHCP pool of addresses you would have conflict errors.> 


While I was typing this post, I was also configuring a Ubuntu 10.04 Guest in Virtual Box with my NIC for the Guest set to Bridge mode to allow the virtual machine to get one of my WRT54G2 IP addresses.  Configured the image the same way as I am with the box at the office and it has taken the STATIC IP and I am surfing the net.


Still more evidence that the install has gone wrong and we need to reinstall the OS.
>   

Yet I was unable to configure the Linux Box from the office, last night to do the same on my home network, maybe the install on the Linux box is corrupt, the only difference between the one at the office and the virtual one is that I have removed the network-manager and network-manager-gnome from the Office box.

This kinda cinches it.  If you are using a desktop OS and network-manager is involved and anything is possible.  Do you need the GUI to manage this server?

I have a desktop that has no network-manager involvement that is statically configured.  When I installed it I declined to automatically set up DHCP.  It works fine.

I have another server here that I manage from the CLI through SSH  from another host.  Sometimes I use my Vista laptop to connect to the server.  It also works.   
> 

The Office box was installed using Universal USB Installer and the same ISO used to install the virtual guest.  

If needed I can format and reinstall Ubuntu on the Office box, there is nothing on it at the moment.
I would do this first thing.  Do you have a DVD or CD drive on this host?  I would d/l the iso and burn a CD of the  version you want.  I still use 8.04 LTS (Hardy).  I know it and it provides me with the server software I need.  As a proof of concept (testing) host I would use hardy instead of Lucid.  You could use later versions but they are not supported as long as Hardy is.> 

Another issue that was noticed today while I was trying to configure the Linux Box at the office, was that pinging out was disabled, that is a new development within the past few days, as we were able to ping out before, to external addresses.
Are you saying the the Linux host ONLY can't ping externally or all host have lost this ability?

Indeed you are having too many problems with the Ubuntu install.  Once again I would reinstall and test this again.

This is not you making a mistake -- this is just a bad install.  It happens every once in a while.  

One last thing -- do this without going to the IT manager's help.  He'll love you for it.  Test at home or whatever.  Trust me as a manager I love it when someone "just makes it work".  Don't forget to document what you have done.

---

### Post by sammer021486 on 2010-07-14
> **bab1 said:**
> Indeed you are having too many problems with the Ubuntu install.  Once again I would reinstall and test this again.

This is not you making a mistake -- this is just a bad install.  It happens every once in a while.  

Reinstalled and its working now.

There is an odd catch though, to get the STATIC IP to work, it has to be first assigned dynamically.  

I was trying to set the STATIC IP and was running into the same problems. 

So on a whim I decided to try an IP that had already been assigned through DHCP, success.  I do not know why this works, but it does.  I took the DHCP IP address I had been issued on my windows PC, entered it into the Linux Box, now I am surfing the net on the Linux Box.  The Linux Box steals the IP address and now my Windows PC has no IP address, the Linux Box is holding onto that address and when I try to ipconfig /renew on the Windows PC I get the error that the IP is in use.  

I configured the Linux to get a new IP address dynamically, then took the new dynamically assigned IP address and assigned it to the Linux Box as a STATIC IP and it is working fine.

I looked into the servers too, they are both assigned STATIC IPs in the DHCP range.

> 
One last thing -- do this without going to the IT manager's help.  He'll love you for it.  Test at home or whatever.  Trust me as a manager I love it when someone "just makes it work".  Don't forget to document what you have done.

Still have to get the manager to let me into the router, I have not had a chance to see the configuration of the router yet to see if the current servers have be issued RESERVED IPs or if they just work by giving them STATIC IPs.

Most likely reason they have had no issue with the servers set up the way they are is that they are always on and never lose their DHCP assigned IP address.

I will post back when I have a chance to see how the router is setup, now its time to test this weird IP address setup and install the needed software.

---

### Post by bab1 on 2010-07-14
> **sammer021486 said:**
> Reinstalled and its working now.

There is an odd catch though, to get the STATIC IP to work, it has to be first assigned dynamically.  

That's odd.  I have NO DHCP on my home network.  My static configuration has always worked.

But if it works for you then document your observations.  That way if it comes up again you will know what to do.

Please post back her with your progress I am interested in the final results.

---

### Post by sammer021486 on 2010-07-14
> **bab1 said:**
> But if it works for you then document your observations.  That way if it comes up again you will know what to do.
First thing I was taught in school, document all progress so you can go back and see what worked and what didn't and to have a copy of the work you have done.

This has been a good exercise for me, my schooling for network security was a little too fast for me to take in everything.  I did a third year program with no real prior knowledge to networking, other than setting up a networked printer or a SOHO network.  So I was playing catch up to everyone else in my courses, except for the first year classes I was enrolled in.

> 
Please post back her with your progress I am interested in the final results.
I'll be sure to do that, maybe a few days, as it is busy here and my manager and I both need to sit down to finish the setup as he will also need to know how everything works.

Thank you for your help bab1

---

### Post by betlog on 2010-07-16
address 172.16.213.25
netmask 255.255.255.0[FONT=Verdana]  <<<---- [/FONT]er... 
...don't you want a valid 20 bit block address there?
172.16.0.0 &#8211; 172.31.255.255
172.16.0.0/12 (255.240.0.0) <<<--- ?

[http://en.wikipedia.org/wiki/Private_network](http://en.wikipedia.org/wiki/Private_network)

---

### Post by sammer021486 on 2010-07-16
> **betlog said:**
> address 172.16.213.25
netmask 255.255.255.0[FONT=Verdana]  <<<---- [/FONT]er... 
...don't you want a valid 20 bit block address there?
172.16.0.0 – 172.31.255.255
172.16.0.0/12 (255.240.0.0) <<<--- ?

[http://en.wikipedia.org/wiki/Private_network](http://en.wikipedia.org/wiki/Private_network)
We are using Classless Inter-Domain Routing (CIDR), so we can take the 172.16.0.0-172.31.255.255 address range and divide it into smaller subnets.

---

### Post by sammer021486 on 2010-07-29
> **bab1 said:**
> That's odd.  I have NO DHCP on my home network.  My static configuration has always worked.

But if it works for you then document your observations.  That way if it comes up again you will know what to do.

Please post back her with your progress I am interested in the final results.

Because of so many issues going on with our network and computers not being able to access the internet.  The manager allowed me to have a look at the router's configuration and that is where I learned that the router is limited to only allowing 12 IP addresses to access the internet.  

So that solves the issue I was having with the Linux Box.  The one Linux install was corrupt and not configuring correctly, but once I got the new install working in STATIC mode; but because the 12 IP address rule, I was not able to get access to the internet unless I stole an IP that already had internet access.  

The router is not configured to worry about the MAC address of the computer, only the IP address that is why I was successful at stealing another computer's IP address and then being able to surf the internet.  

Will maybe have to look into setting up a time out for inactive computers or certain IP addresses on the network so that we do not run into this issue again.

The server is up and running right now on the trusted network, whether or not it will be migrated over to the optional network I do not know, those details have not been released to me.  

Thank you again for your help Bab1

---

### Post by bab1 on 2010-07-29
> **sammer021486 said:**
> Because of so many issues going on with our network and computers not being able to access the internet.  The manager allowed me to have a look at the router's configuration and that is where I learned that the router is limited to only allowing 12 IP addresses to access the internet.  

So that solves the issue I was having with the Linux Box.  The one Linux install was corrupt and not configuring correctly, but once I got the new install working in STATIC mode; but because the 12 IP address rule, I was not able to get access to the internet unless I stole an IP that already had internet access.  

The router is not configured to worry about the MAC address of the computer, only the IP address that is why I was successful at stealing another computer's IP address and then being able to surf the internet.  

Will maybe have to look into setting up a time out for inactive computers or certain IP addresses on the network so that we do not run into this issue again.

The server is up and running right now on the trusted network, whether or not it will be migrated over to the optional network I do not know, those details have not been released to me.  

Thank you again for your help Bab1

You are welcome.  I see a lot of paranoid thinking in the setup.  But as we can't control it, the best thing is to understand and live with the rules.

---

