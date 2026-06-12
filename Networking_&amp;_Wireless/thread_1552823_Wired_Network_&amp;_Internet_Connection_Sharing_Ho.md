---
title: "Wired Network &amp; Internet Connection Sharing How To?"
date: 2010-08-14
forum: Networking &amp; Wireless
---

### Post by smiles on 2010-08-14
Hi everyone,

I'm extremely new to Ubuntu (as in this is the first time ever trying to USE it as my main OS) and am having some problems with networking and internet connection sharing on my **wired** home network. Now, I've tried various different versions of linux distros over the years but never could quite wrap my head around all the command line hacking needed to use most *nix based computers. So I've simply tested different versions that make the attempt to give you a windows-like interface and have found that ubuntu does the best job for me.

With that said, I downloaded, burned and installed the 10.04 desktop version about a week ago. The speed of Ubuntu is at least 10x that of WinXP on the SAME machine. That goes for booting up and browsing the internet. In fact, everything I have successfully tested in Ubuntu is at least 10x faster than XP on the same machine. Everything with the exception of networking and internet connection sharing.

For whatever reason I simply cannot get the network OR the internet connection sharing to work. Let me explain a bit...

When I first installed Ubuntu and booted into it, everything seemed to work out of the box. Internet and networking both worked on both PCs at first. However, at that time WinXP was on the second machine. But soon after my better half seen how fast everything was working on my Ubuntu installation, she wanted it too. So an hour or so later and she had a fresh copy of Ubuntu installed as well. That's when the network and the internet connection sharing began to fail. 

The weird thing is, I can get it working on one or the other PC, but not both at the same time. I can ping each PC and the router from either PC. But I cannot reach either PC through the networking interface and cannot reach the internet through the client PC.
I can see both PCs through the routers' web interface, but cannot reach either.

Since I do have a somewhat strange setup let me give you all some more details to help you to help me. :)

I have eth0 connected directly to my cable modem and eth1 connected to the first port on the router on the main PC. I then have eth0 of the client PC hooked into the 2nd port. 
The router itself is actually a DSL/wireless router combo (that I have left over from when I had to suffer the services of Verizon). 
It's the Actiontec GT704WG. Here's a link for reference:
[http://www.actiontec.com/products/product.php?pid=40](http://www.actiontec.com/products/product.php?pid=40)

I know this might not be the ideal solution but my gateway died and this is what I'm left with at the moment. In WinXP I was able to get it to work in several different ways:

1) I could bridge the internet connected ethernet to the LAN connected ethernet (bridge eth0 to eth1).

2) I could hook the cable modem itself into the routers 1st port and then everything else connected into the router also had internet access.

3) Run a proxy server and bind the proxy to the eth1 IP address using AnalogX Proxy. 
[http://www.analogx.com/contents/download/Network/proxy/Freeware.htm](http://www.analogx.com/contents/download/Network/proxy/Freeware.htm)

In WinXP, option 3 seemed to be the most reliable and very rarely failed, though the speed was slower than options 1 and 2. But with options 1 and 2 in XP, I would have to reconfigure the network on a regular basis.

Surely, if I can make it happen in WinXP and actually even as far back as Windows 95, there must be a way to do it in the far superior Ubuntu. I'm fairly certain it must be easier than I seem to be making it, but after literally days of researching, reading and testing, I'm just as lost now as I was when I started the search. In fact, I think I'm even more confused now. 

Most of the sources I've found point to installing a package that is no longer available. 
I think it was ipmasq. Here's a link to one of the source sites which seems to give the most popular way to configure the network (based on all the other sites I found with the exact same info).
[URL="http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html"] http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html
[/URL]
I've also tried using firestarter, but I'm not sure what I'm doing and when I enable firestarter it seems to boot my PC offline rather than providing access to the network.

My guess is that either I don't have the router configured correctly and/or don't have firestarter configured correctly.

BTW, I still have WindowsXP installed on both PCs and the network still works fine when BOTH machines are booted into XP. Sometimes, it also works even if the client machine is in Ubuntu and the gateway machine is in XP. But I simply cannot get it to work when BOTH PCs are booted into Ubuntu.

Here's my ifconfig info:

```

eth0      Link encap:Ethernet  HWaddr 00:04:5a:49:5c:19  
          inet addr:173.81.95.84  Bcast:173.81.95.255  Mask:255.255.252.0
          inet6 addr: fe80::204:5aff:fe49:5c19/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:299807 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24740 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:66668066 (66.6 MB)  TX bytes:2427584 (2.4 MB)
          Interrupt:16 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:11:d8:60:1b:5f  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:fe60:1b5f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2870 (2.8 KB)  TX bytes:17078 (17.0 KB)
          Interrupt:23 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:186 errors:0 dropped:0 overruns:0 frame:0
          TX packets:186 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15488 (15.4 KB)  TX bytes:15488 (15.4 KB)

```Any and all help will be greatly appreciated!

Thanks in Advance!

~smiles

P.S. Please remember that this is a WIRED network. I have found a wealth of information about wireless networking, but I need info about how to make a WIRED network work.

---

### Post by smiles on 2010-08-14
Can anyone help here or am I going to be forced to use Windows once again? Surely someone much smarter than myself could figure this out.

---

### Post by Iowan on 2010-08-14
Once/day is generally "polite" for bumping. ;)

[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is a help page for Internet/Connection Sharing.

---

### Post by uptime365 on 2010-08-14
Hi,

You network is like the below right ?

||Cable-Modem||------eth0-||MainPC||-eth1------P0-||Router||-P1------eth0-||ClientPC||

Can you ping 192.168.1.2 from ClientPC and what is the ifconfig and /etc/network/interfaces setup on ClientPC.

Also one more question can't you connect MainPC directly to ClientPC like below ?

 ||Cable-Modem||------eth0-||MainPC||-eth1------------eth0-||ClientPC||

Uptime

---

### Post by Keskasidvar on 2010-08-14
I'm having a problem similar to this, except I'm dual-booting with Win7 and the internet never worked.

---

### Post by smiles on 2010-08-14
Hi Iowan,

Ok, well, I've only bumped the post once today after it seemed to drop off the first page, so my bump is used up for the day. 

Thanks for the link. However, I've already been there and tried following the steps well in advance of posting here. I didn't simply install Ubuntu, get frustrated and come straight here to post my questions. I've been fighting with this problem for about a week now and have sadly come to a dead end. 

It's really frustrating because I can get networking & ICS to work on BOTH machines as long as I have ONE of them logged into Windows (doesn't even matter which machine either). It's only when I log BOTH machines onto Ubuntu that I run into the Networking and ICS problems. 

I'm not very well versed in using the command line and fear I may have made a mistake over the last week or so trying to configure the network in the terminal. In fact, I'm quite sure I've made mistakes and ended up reinstalling Ubuntu from scratch after some of the advice I've attempted to follow. 

Just today alone I've been working on this problem for a good 6 solid hours with absolutely no luck. It seems the more I mess with the networking, the more problems I end up having.... i.e. screwing up the internet connection for both PCs rather than just the one. I've completely lost the ability to see either PC from the other, but can ping with no problem. 

So once again, anyone that can offer some advice to a newbie Ubuntu user would be great.  

I'm going to go through and follow the instructions from the ICS link provided once again but I'm not getting my hopes up too high as I've been through this at least 3 times already with seemingly no effect (aside from losing the ability to see the other PC in the Windows Shares networking interface). Before trying to configure ICS (following the directions in your link), I could connect to the other PC, access files, copy, paste,  and create files w/o problems as soon as I finished installing Ubuntu.

I lost that ability after trying to share the internet connection and can't seem to get it back.

I haven't given up yet, but after a week with no luck my patience with Ubuntu is wearing thin. 
I was hoping someone more knowledgeable than myself might be able to shed some light in my direction. 

~smiles

---

### Post by smiles on 2010-08-14
> **uptime365 said:**
> Hi,

You network is like the below right ?

||Cable-Modem||------eth0-||MainPC||-eth1------P0-||Router||-P1------eth0-||ClientPC||


Yes the above is correct.


> **uptime365 said:**
> Can you ping 192.168.1.2 from ClientPC and what is the ifconfig and /etc/network/interfaces setup on ClientPC.

leslie@leslie:~$ ping -c3 192.168.1.2
PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.
64 bytes from 192.168.1.2: icmp_seq=1 ttl=64 time=1.78 ms
64 bytes from 192.168.1.2: icmp_seq=2 ttl=64 time=0.204 ms
64 bytes from 192.168.1.2: icmp_seq=3 ttl=64 time=0.205 ms

--- 192.168.1.2 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 0.204/0.731/1.784/0.744 ms

eth0      Link encap:Ethernet  HWaddr 00:16:ec:74:a5:8f  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ecff:fe74:a58f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6842 (6.8 KB)  TX bytes:12936 (12.9 KB)
          Interrupt:23 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:125 errors:0 dropped:0 overruns:0 frame:0
          TX packets:125 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10076 (10.0 KB)  TX bytes:10076 (10.0 KB)


> **uptime365 said:**
> and /etc/network/interfaces setup on ClientPC

How do I pull this information? As I said, I'm extremely new to Ubuntu and much of this is like a foreign language to me. LOL

> **uptime365 said:**
> Also one more question can't you connect MainPC directly to ClientPC like below ?

 ||Cable-Modem||------eth0-||MainPC||-eth1------------eth0-||ClientPC||

Uptime

Maybe I'm just a moron, but I have never been able to connect the network that way and get it to work. On my machines, when I try connecting them directly as above both ethernet cards seem to quit responding (lights quit working and neither machine sees either card). Do I need a special cable or something for it to work that way?

Thanks for all your help!

~smiles

---

### Post by Iowan on 2010-08-14
> **smiles said:**
>  On my machines, when I try connecting them directly as above both ethernet cards seem to quit responding (lights quit working and neither machine sees either card). Do I need a special cable or something for it to work that way?
Depending on the NIC's... gigabit cards can (sometimes) auto-configure, but the 10/100 cards I use require a crossover cable to go machine-machine. A hub or switch (or router?) between them would use straight cables.

---

### Post by smiles on 2010-08-14
> **Iowan said:**
> Depending on the NIC's... gigabit cards can (sometimes) auto-configure, but the 10/100 cards I use require a crossover cable to go machine-machine. A hub or switch (or router?) between them would use straight cables.


Thanks Iowan. That makes sense and is now clear to me. All my ethernet cards are the 10/100 variety -- no gigabits here. So I would need the crossover cable (thinking about going to find one today just to see if it will speed up this networking issue I'm having). 

I'm currently connecting the PCs through a router. I've made a little progress (though couldn't tell you how) as I can now connect to the other PC through Places >> Connect to Server... by entering the IP address of the client machine. At least I can when it is logged into Windows...haven't tried when it's logged into Ubuntu yet, just got this working when logged into XP on the client machine.

Still no internet yet, but I'm still working on it. :)

I finally got it working on BOTH machines while BOTH are logged into Ubuntu. :)

I did some more digging here in the forum and found a link which seems to have solved my problem.

[Here's the link]("http://bigbrovar.wordpress.com/2008/12/18/how-to-share-your-internet-connection-on-ubuntu/") for anyone else that may be having a similar problem.

---

