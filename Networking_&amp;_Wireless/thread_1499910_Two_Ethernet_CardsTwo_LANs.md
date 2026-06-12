---
title: "Two Ethernet Cards/Two LANs"
date: 2010-05-26
forum: Networking &amp; Wireless
---

### Post by jondavidf on 2010-05-26
Hello all,

I am trying to get two network cards configured correctly.  Right now they are both set up on DHCP and are given a permanent IP address from two different routers.

I have an Ubuntu Server with 2 network cards installed.  Each is connected to a separate LAN.  I have Samba set up to share files from server attached external drives to the two separate LAN's.  That part seems to be working okay, other than file transfer is extremely slow (about 8 MB/s) even with all Gigabit components in the LAN and the drives connected via e-Sata.

I am running Squid on the Server also, and am using it as a proxy server for the 1st LAN.

Once I connected the cable to the 2nd LAN (without Squid as a proxy) I am no longer able to connect to the Internet from my clients through the proxy.  I am not sure how I tell (or if I need to) the Server that only the 1st network card is connected to the Internet.

Thanks for the help.

---

### Post by -humanaut- on 2010-05-26
Whichever ones not connected to the internet you could try disabling DHCP on it. That's really all I can think of to tell the server its not "online"

---

### Post by jondavidf on 2010-05-26
Update:
 
How do I tell one network card to access the Internet and the other network card that it's local only?  I'm thinking that will solve my problem.

---

### Post by -humanaut- on 2010-05-27
/etc/network/interfaces

You can setup your interfaces from there. can you post back the result of: cat /etc/network/interfaces

---

### Post by jondavidf on 2010-06-02
First, the basics.  I have:

2 - Satellite Provided Internet Systems
2 - Routers
1 - Ubuntu Server w/2 network cards
48 - Clients on LAN1
22 - Clients on LAN2
4TB - Of shared media on server

I am very new to Ubuntu and somewhat new to networking.  I know the basics of MAC addresses, IP addresses, etc. but not so much about port redirecting, port forwarding, etc.

Where I'm at right now:

I took a desktop computer, installed a second network card, reformatted the hard drive and installed Ubuntu Server 64 bit, installed Samba and Squid (more on those later).

My biggest problem seems to be configuring the network cards.  They are both set to DHCP.  They are both given a strict IP address from it's own router.  They can both ping locally and client PC's can see the server (sometimes) on the network and connect always; except one guy but I think it's a problem on his end.  The router on LAN2 is set to block Internet access to the server.  That is fine because I want Internet traffic from the server to go through LAN2's router anyway.  So DHCP seems to be working fine, but still no Internet connection to the server.

What I've done to try to fix the problem:

I tried creating an IP Table file, iptables.conf, that told all outbound traffic to eth1 (LAN2) to DROP.  It was told to allow all incoming data from both cards and allow outgoing data to eth0 (LAN1) to be allowed.  I inserted a pre-up statement into the /etc/network/interfaces file that said -

pre-up iptables-restore > /etc/iptables.conf

The only thing this did was made my attempted connection to the Internet from the server fail immediately.

What I'd like to do is configure the cards so that the LAN2 card (eth1) is local only on the server side, ie the clients will have a direct connection to the Internet through Router 2, but will be able to access the shares on the server.  I'd like the LAN1 card (eth0) to be able to access the Internet.  Do you know how to do this?  I'm thinking that it's through iptable setup but I'm not 100% positive, as I've only been using Ubuntu for two weeks or less.

The funny thing is when I do sudo /etc/init.d/networking restart I get a slow Internet connection for just a few moments.  I tried pinging Google and it got a response.  Then shortly after it is gone.

Once I get the cards configured I'd like to use Squid as a proxy server.  I believe Squid works fine because once LAN2 is disconnected the proxy works as advertised.  An ideal situation would be where Squid could cache for both LAN's but I'd be happy with just one for now.

My final issue right now is with Samba.  About 99% of the clients can connect to the shared folders on the server, but the connection is much slower than it was with Windows Server 2008.  The gear is all gigabit ethernet and eSata drives so I believe steady transfer rates of 75+mb/s are realistic.  We are averaging about 8-10mb/s now.  Also, I administer the files from a Windows 7 machine and it seems to route all data that I move through my ethernet connection.  Most of the shares are on one hard drive, but even moving data from one share to another share on the same drive the transfer rate is the same (8-10mb/s).  Shouldn't it be almost instantaneous since it's just changing which directory it's in?  Do you know how to configure the network/Samba so that it's optimum for sharing data from eSata external drives to all the clients?

Once I complete these things my server will be completely operational.  I can post code if needed, just wasn't sure which code to post yet.

Thanks for the help.

---

### Post by Iowan on 2010-06-02
Threads merged.

---

### Post by jondavidf on 2010-06-13
Any idea how to make a LAN Card access local only?  No internet....  I'm thinking it has to do with routing or iptables, but I'm very new to Ubuntu so I'm not exactly sure.

---

### Post by gsgleason on 2010-06-13
The issue is likely that each is acquiring a default route via DHCP.

Show the output of netstat -nr when just the one is connected and it works, and also when both are connected and it's not working.

---

### Post by gsgleason on 2010-06-13
> **jondavidf said:**
> Any idea how to make a LAN Card access local only?  No internet....  I'm thinking it has to do with routing or iptables, but I'm very new to Ubuntu so I'm not exactly sure.


Use static addressing on the second interface (or both) instead of DHCP.

---

### Post by jondavidf on 2010-06-14
I tried changing to static IP address.  I still couldn't ping router of LAN2 from server.  So I changed to auto eth1 and dhcp.  Then I edited the resolv.conf file by deleting the info for the LAN2 router and edited the routing table by removing the default gateway for eth1. The system appears to be working now with the changes below.

The netstat -nr now shows:

Kernel IP routing table
Destination          ..... Gateway          ..... Genmask          ..... Flags     ..... MSS ..... Window     ..... irtt  .....Iface
192.168.1.0    .... 0.0.0.0             ........ 255.255.255.0   U              ......... 0 ......... 0                  ................0 .......eth0
192.168.0.0    .... 0.0.0.0             ........ 255.255.255.0   U              ......... 0 ......... 0                  ................0 .......eth1
0.0.0.0           ........... 192.168.1.1      . 0.0.0.0             .......... UG            ....... 0 ......... 0                  ................0 .......eth0

/etc/resolv.conf shows:

nameserver 192.168.1.1

The /etc/network/interfaces shows:

       [FONT=Verdana][SIZE=2][FONT=&quot]auto lo[/FONT][/SIZE][/FONT]
    [FONT=Verdana][SIZE=2][FONT=&quot]iface lo inet loopback[/FONT][/SIZE][/FONT]
  [FONT=Verdana][SIZE=2][FONT=&quot]
[/FONT][/SIZE][/FONT]
[FONT=Verdana][SIZE=2][FONT=&quot]auto eth0[/FONT][/SIZE][/FONT]
    [FONT=Verdana][SIZE=2][FONT=&quot]iface eth0 inet dhcp[/FONT][/SIZE][/FONT]
    [FONT=Verdana][SIZE=2][FONT=&quot]   hwaddress ether 00:50:43:00:9c:7d[/FONT][/SIZE][/FONT]
        

[FONT=Verdana][SIZE=2][FONT=&quot]auto eth1[/FONT][/SIZE][/FONT]
    [FONT=Verdana][SIZE=2][FONT=&quot]iface eth1 inet dhcp[/FONT][/SIZE][/FONT]
    [FONT=Verdana][SIZE=2][FONT=&quot]   hwaddress ether 00:26:2d:1f:0e:09

Are there any other adjustments that I should make to optimize performance?
[/FONT][/SIZE][/FONT]

---

### Post by Iowan on 2010-06-14
I suppose the question remains - does each interface get an appropriate DHCP address so the routing table works? (eth0 in 192.168.1.X and eth1 in 192.168.0.X)

---

### Post by jondavidf on 2010-06-15
I believe the answer to your question is yes.  Each router gives a strict bind (permanent IP) to each interface.  The IP address for eth0 is 192.168.1.49 and the IP address for eth1 is 192.168.0.155.  Whenever the DHCP lease expires, it just renews to the same address.

---

### Post by Iowan on 2010-06-15
I probably just missed it, but which card has internet access? The routing table looks like it should be eth0.

---

### Post by jondavidf on 2010-06-15
That is correct. eth0 is the interface that has Internet access.  I will probably try setting eth1 to static again, as I believe DHCP from LAN2's router is making the server drop off the Network Places list once it reassigns the IP address to eth1.  The server was showing up on Network Places when I connected LAN2 but has now disappeared.

---

### Post by jondavidf on 2010-06-17
Update:
 
Everything now works!  Samba works for both LANs and Squid works for LAN1.  
 
The only thing that I still need to tweak is server share access speed for LAN2 and making the Ubuntu machine visible in the Network or Network Places on the client machines.  The server can be accessed by IP address or even typing the hostname into the address bar, but it is still not showing up in Network Places or Network.  
 
The other thing that I still need to do is tweak Squid to make sure I have optimal setting for speed.

---

### Post by Wastrelway on 2012-06-25
I had a similar problem that I just fixed and I want to share my solution for the good of everyone.  I've seen other posts about similar problems.  The original poster here seems to have gotten it working but he's using dhcp for both cards.  One of my cards (eth0) gets an IP address from the internet and the other (eth1) is on my LAN and has a static address.

What seems to happen is both cards come up according to /etc/network/interfaces, but then eth0 gets an address by dhcp and that brings eth1 down.

My solution was to add a script in rc.local that brings eth1 back up.  Because it may take some time for dhcp to work, I had to put in delays.

I edited rc.local this way:
#get this machine on the local
sleep 10                               #this delay may not be needed
hosed=`ifconfig | grep --count "10.10.10.1"`  #10.10.10.1 is the static address for eth1
while [ $hosed -eq 0 ]
do
sleep 60                                #this time might be tweakable
ifconfig eth1 down
ifconfig eth1 10.10.10.1 up
sleep 60                                #this time mighrt be tweakable
hosed=`ifconfig | grep --count "10.10.10.1"`
done

I hope this helps someone.

---

### Post by sffvba[e0rt on 2012-06-25
> **Wastrelway said:**
> I had a similar problem that I just fixed and I want to share my solution for the good of everyone.  I've seen other posts about similar problems.  The original poster here seems to have gotten it working but he's using dhcp for both cards.  One of my cards (eth0) gets an IP address from the internet and the other (eth1) is on my LAN and has a static address.

What seems to happen is both cards come up according to /etc/network/interfaces, but then eth0 gets an address by dhcp and that brings eth1 down.

My solution was to add a script in rc.local that brings eth1 back up.  Because it may take some time for dhcp to work, I had to put in delays.

I edited rc.local this way:
#get this machine on the local
sleep 10                               #this delay may not be needed
hosed=`ifconfig | grep --count "10.10.10.1"`  #10.10.10.1 is the static address for eth1
while [ $hosed -eq 0 ]
do
sleep 60                                #this time might be tweakable
ifconfig eth1 down
ifconfig eth1 10.10.10.1 up
sleep 60                                #this time mighrt be tweakable
hosed=`ifconfig | grep --count "10.10.10.1"`
done

I hope this helps someone.


Thanks for sharing.

*Thread **closed**.*


404

---

