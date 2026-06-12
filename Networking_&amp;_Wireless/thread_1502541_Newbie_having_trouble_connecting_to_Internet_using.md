---
title: "Newbie having trouble connecting to Internet using Ubuntu 10.04"
date: 2010-06-05
forum: Networking &amp; Wireless
---

### Post by Yolo on 2010-06-05
Hello everyone,

I just recently installed Ubuntu 10.04 on my Desktop computer. 

Processor- Intel Core 2 Quad CPU Q6600 2.40 GHZ
RAM- 4.00 GB
System type- 32-Bit OS

I usually connect on Windows through an Ethernet cable connected directly to my router which is a: Linksys wireless G Broadband router 802.11 G 2.4 GHZ 

I also using a Killer K1 network card.

My problem, basically, is that I am unable to connect to the internet.

I tried following the help button but to no avail.

I plugged in my computers IP address, the Subnet Address, Gateway and the two DNS address I have and clicked apply and it still won't pick it up.

I am a complete Newb when it comes to Linux so I really would appreciate all the help you could give me. I really want to see what Ubuntu can do but I can't even get on the internet! lol

I will be awaiting your replies! Thank you!

---

### Post by Yolo on 2010-06-05
Hello again,

I just wanted to add that I tried pinging my router using terminal.

My routers Ip is 192.168.1.108 and I got the response "Network is unreachable" 

I don't know if that helps.

thanks again i will be awaiting replies!

---

### Post by Darktrax on 2010-06-05
Yolo,

I have just solved exactly this problem on my PC.
Can you hang in there a bit while I work up some text?

This is because I have had this network pain for days, and I am thinking maybe some others have encountered it.

Back soon..
BTW - please mention if the total number of available network ports is more than one, and if there are any on the motherboard.

---

### Post by Darktrax on 2010-06-05
OK - at least on this boot-up, I SOLVED this one for myself, and I am hoping the set-up will stick for a re-boot. Given that you are using the Killer K1 network card, I am speculating that you have at least **two** physical network ports. Either one is on the PC motherboard, and then at least one on the network card, or maybe none at all on the motherboard, and perhaps more than one on the network card.

Keep in mind also that I am writing this for others too. Please forgive if I end up telling you stuff you already know, or consider a bit basic.
You can figure that "miranda" is the hostname on my PC. Mine has two built in Realtek interfaces. Also, I am describing getting the network up to a **CABLE** interface.

**The SYMPTOMS:** (as I find it)
Previous versions 8.10, 9.10 etc. work OK, but as soon as you try the new Lucid Lynx 10.04, you cannot get on the internet, the System => Administration => Network Tools just gives lots of information about how non-working it is, and the Network Tools does not actually seem to work.

It seems that the setup scripting can default to the wrong ethernet socket, if there happens to be more than one. I have no idea how eth0 and eth1 are assigned to the physical ports, or even if what one distro thinks is eth0 is eth1 on another release. I always thought eth0 was the default.

I know this seems a bit obvious, but the fix may be as simple as **TRY THE CABLE IN THE OTHER AVAILABLE NETWORK PORTS**. :)
If its broke - then we need to first wring out some information. 

**My SOLUTION:**
First step is to get yourself a root terminal. (OR, you can prefix every command with sudo, and offer a password every time, this can get tedious)
Example: Use Menu => Accessories => Terminal <RIGHT CLICK>
Select to add the terminal to the panel or desktop (your choice).
Open the terminal **and give it sudo as the code below, using your username instead.
```
darktrax@miranda:~$ sudo su
[sudo] password for <your username>:
```
Do it all again for another couple of times. Have some terminals open.
Stretch them a bit wider than the 80 lines default.
Use ONE of the terminals for the commands to figure this out. Use the other two for looking at help. (Its possible they don't have to be root terminals for this - but I did't care!)

Now - find out what is going on. Try the following command ***ifconfig -a*** Also, in the other terminal, type ***ifconfig --help***. In yet another terminal, type ***info ifconfig*** and keep in mind to navigate what arrives with up/down arrow  and Page keys, and you need ***q*** to quit it. The ***ifconfig*** command by itself will show network interfaces that are default, and the ***-a*** argument added will display all the ports.
 
Example: (From my PC right now that I have got this to work)
```
root@miranda:/home/darktrax# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:24:1d:7f:2a:7c  
          inet addr:192.168.0.20  Bcast:192.168.0.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:35 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:24:1d:7f:2a:7e  
          inet addr:192.168.0.24  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1dff:fe7f:2a7e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2555 (2.5 KB)  TX bytes:8897 (8.8 KB)
          Interrupt:36 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:497 errors:0 dropped:0 overruns:0 frame:0
          TX packets:497 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:46182 (46.1 KB)  TX bytes:46182 (46.1 KB)
```
OK - look at the above carefully. Notice that eth0 is not **UP**, unlike eth1, which says "**UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1**"
Notice also there are inet addr: addresses 192.168.0.20 for eth0, and 192.168.0.24 for eth1. I chose these arbitrarily myself, since my ADSL router is configured to offer DHCP automatic service to anything in the range 192.168.0.x, with 192.168.0.1 being reserved for itself, and 192.168.0.255 reserved for broadcast. **YOUR broadband router norms may be different!** Check the info that it comes with. Many use 192.168.1.1 and some use yet other addresses.
**CHECK THE HARDWARE:** Use ***lspci***. It will tell you what is there.

The command ***eth0 up*** will turn network interface eth0 on.
Similarly ***eth0 down*** will turn it off.
I use this to discover which one has the cable to the modem router.
**Know the ADDRESS OF THE ROUTER!**
In my case, 192.168.0.1
We test the setup using ***ping*** See this example..
```
root@miranda:/home/darktrax# ping -c 4 192.168.0.1
connect: Network is unreachable
```
Now look at what you get when it works
```
root@miranda:/home/darktrax# ifconfig eth1 up
root@miranda:/home/darktrax# ping -c 4 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=3.05 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=0.734 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=0.711 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=64 time=0.684 ms

```
**FIRST - SET UP A GOOD IP ADDRESS**
This is where 10.04 Lucid Lynx was in a problem. The eth0 address was 192.168.0.1, **which was the ADDRESS OF THE ROUTER - not the PC!**. The ping command was pinging itself! duh? I have no idea how it got that way. Also, eth1 did not have an address at all, and that was the one that turned out to have the cable in it. If its not right, fix it with ***ifconfig eth0 192.168.0.x where x is in the range 2-253***. You can choose.
Here is what I did. You can see me assigning addresses to eth0 and eth1.

```
root@miranda:/home/darktrax# ifconfig eth0 down
root@miranda:/home/darktrax# ifconfig eth1 down
root@miranda:/home/darktrax# ifconfig eth1 192.168.0.20
root@miranda:/home/darktrax# ifconfig eth1 192.168.0.24

```
Next is to **TURN THEM ON ONE AT A TIME, AND TEST THEM WITH PING**
Notice that the localhost lo is 127.0.0. This is the ***loopback*** address.

```
root@miranda:/home/darktrax# ifconfig lo up
root@miranda:/home/darktrax# ifconfig eth1 up
root@miranda:/home/darktrax# ping -c 4 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=3.05 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=0.734 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=0.711 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=64 time=0.684 ms
```

Thats what it looks like when it works :)
If you get "connect: Network is unreachable", then switch that port off, and turn on another. Alternatively, you can move the cable to another hole, and try again.
When you get the connect, there are some things left - the GATEWAY, and the DNS server information. DNS may be automatic on some routers. My service provider information has 2 addresses. If you like, you can use available DNS server adresses from anywhere. there are many.
FireFox and other internet-using programs need to know that your broadband  router address is the gateway

**TEACH IT THE GATEWAY:** Obviously edit it to suit your setup, now you know what hole the cable is in. In my case ..
```
root@miranda:/home/darktrax# route add default gw 192.168.0.1 eth1
```

Nearly there. You will find the regular Network Tool setup does allow you to set DNS addresses OK. There may be a ifconfig command that does it, but I was tired. It may even be possible to set the whole thing, broadcast, gateway, everything, in a single line command. This I just don't know.

Finally. Will it remember all this for the next re-boot, or will some faulty script have us back in a mess? Do we have to edit stuff to ensure this? I just do not know. I guess I will find out soon. 10.04 is a frustrating disappointment for me, because it looks so pretty, and seems very good. Unfortunately, if the network setup is in a mess, and hard to fix, then it stays out of my PC. At least, with the above, you can get the browser working, go for updates, install video hardware drivers, etc.
Hope this helps

---

### Post by linprob on 2010-06-05
> **Darktrax said:**
> Yolo,

I have just solved exactly this problem on my PC.
Can you hang in there a bit while I work up some text?

This is because I have had this network pain for days, and I am thinking maybe some others have encountered it.

Back soon..
BTW - please mention if the total number of available network ports is more than one, and if there are any on the motherboard.
Have 4 ports on my modum, one port on wireless router, one port on computer. No sign of a connection                                         linprob

---

### Post by Darktrax on 2010-06-05
OK - back again after a re-boot

**THIS PROCEDURE DOES NOT STICK DURING A RE-BOOT** :(

To get the network up again, I had to re-assign the addresses.
Make sure only one was UP.
Then teach it the GATEWAY

```
ifconfig eth0 192.168.0.20
ifconfig eth1 192.168.0.24
ifconfig eth0 down
route add default gw 192.168.0.1 eth1
```
Then it works.
At least now the NVidia driver is in. We need to know what scripts to edit, or how to launch some setup tool that works!

We need some help here guys! Yolo and me are suffering a bit :(

---

### Post by dineshs on 2010-06-05
Yolo,
please run this command in a terminal ```
sudo dhclient
```
and post the output of
```
ifconfig -a
```
Darktrax,
Have you tried configuring NM?
Right-click on the NM icon(two opposite arrows on top right) and then click on Edit Connections. 
Select the tab, wired 
select the ethernet connection you want and click edit(you can add the ethernet connection if not listed) 
select ipv4 
method-manual 
click add 
address 192.168.1.100 
mask 255.255.255.0 
gateway 192.168.1.1 
then hit enter 
DNS 4.2.2.1
then click apply 
ref:[https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7) 
Note :The IP addresses are examples.Substitute your values

---

### Post by Yolo on 2010-06-06
Hey guys,

Thank you for your replies.

I'm using the internet on windows since my ubuntu doesn't work so it will take me some time to reply with terminal stuff.

Here is what i got in terminal for ipconfig -a

steven@ubuntu:~$ ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 00:04:4b:0a:48:5f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:25 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:04:4b:0a:48:5e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:26 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:6080 (6.0 KB)  TX bytes:6080 (6.0 KB) 



I have no idea what any of that means lol. Once again I am completely newb at this. Thank you so much for your help!

---

### Post by Yolo on 2010-06-06
Bump. lol

---

### Post by Darktrax on 2010-06-06
Yolo,

We both have to do as dineshs suggests (if the network manager will let us)

The output from your ifconfig -a shows inet addresses have not been assigned.

I have been trying to use the Network Manager from the beginning.
There are only 3 tabs, "General, DNS, and Hosts"
There is NO "Connections" tab as shown in the "Help"
There seems NO way to modify the settings, choose "auto" whatever.

Why are we in this place? I can seen lots of postings from folk failing to get networked.

---

### Post by pr0t3g3 on 2010-06-06
Ubuntu continues to have problems with networks 'n stuff... 10.04 is not a stable version in itself.. You might have better luck switching to an earlier more stable release, if your problem does not get resolved.

---

### Post by Yolo on 2010-06-06
Ya,

I've tried using the network manager as stated and i get to the point where it asks for my password but it no avail. It does not change anything, I'm still not connecting. What do you guys suggest I do? Where can I find a more stable version of Ubuntu?

---

### Post by Yolo on 2010-06-06
Also,

I dont know if this helps or not but I just don't understand why I'm not connecting. I have a PHYSICAL connection to the router, not wireless which is more stable, I connect fine when I'm on my Windows OS and my BROTHER who also runs Ubuntu on his desktop runs it perfectly fine and connects perfectly fine. The only difference between him and I is that he is connected DIRECTLY to the modem and not the router like myself. Could this have anything to do with it?

---

### Post by Yolo on 2010-06-06
Here is my BROTHERS INFORMATION FROM IFCONFIG -A



davidluengo@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:19:d1:03:5e:bf  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d1ff:fe03:5ebf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3178 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3067 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:2775455 (2.7 MB)  TX bytes:540203 (540.2 KB)
          Memory:dffe0000-e0000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)


Also, I looked at his network manager and he did not have to go through the process that I am having to go through. His connection connected automatically when he got ubuntu. I looked in his NM and it saids AUTO eth0, Unlike mine which saids eth1 and eth0.  What could this all mean?

---

### Post by Yolo on 2010-06-06
Bump.

Any insight to my problem would be greatly appreciated, thank you once again for your time ! =D

---

### Post by Yolo on 2010-06-06
Bump. =( I really need help guys

---

### Post by medad on 2010-06-06
Hi Yolo,

I see that you have two ethernet cards.  Is one of them actually part of the motherboard or are they both PCI cards?  If you are able to, disable the ethernet plug-in that is part of your motherboard.  This will at least allow you to verify if there is a communication problem due to having two ethernet plug-ins activated at the same time.

I say this as your brother only shows that he has one ethernet card attached and his connection works fine.

Good Luck,

Medad

---

### Post by Yolo on 2010-06-06
Hello Medad,

I have to go out for a few but do you know how I would go about disabling the Ethernet port in my motherboard? Im a complete newb dude lol. Thank you bro!

Yolo

---

### Post by medad on 2010-06-06
I don't have an Intel Core 2 Quad so I am unsure how the bios is set up.  The only way I learned is to go to each page and see what each one does first.  Hopefully somebody else can reply to you. The only other suggestion that I can give you is to pull out the PCI ethernet card, but if you are a newbie...  

Sorry...

---

### Post by Yolo on 2010-06-06
Its ok, thank you!

Does anyone else have any insight into this problem or should I just delete 10.04 and try version 9.10 of ubuntu?

Once again this is what I got for the command ipconfig -a

steven@ubuntu:~$ ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 00:04:4b:0a:48:5f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:25 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:04:4b:0a:48:5e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:26 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:6080 (6.0 KB)  TX bytes:6080 (6.0 KB) 


Thank you for your help so far and ill be looking forward to more =/. I really want this to work

---

### Post by dineshs on 2010-06-07
Yolo,
please run this in a terminal 
```
sudo dhclient
```
and post the result of ```
ifconfig -a
```
If it doesnt show a valid IP you can change your ethernet cable to the other port and repeat the same.

darktrax,
I think NM is not running in your machine.You can try configuring /etc/network/interfaces
```
sudo gedit /etc/network/interfaces
```
and edit the file as follows
```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
    address 192.168.0.24
    netmask 255.255.255.0
    broadcast 192.168.0.255
    gateway 192.168.0.1

```
Please substitute your IP values.You can also do this refering this site
[https://help.ubuntu.com/community/NetworkAdmin](https://help.ubuntu.com/community/NetworkAdmin)
After doing this restart network
```
sudo /etc/init.d/networking restart 
```

---

### Post by Yolo on 2010-06-07
steven@ubuntu:~$ ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 00:04:4b:0a:48:5f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:25 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:04:4b:0a:48:5e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:26 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:6080 (6.0 KB)  TX bytes:6080 (6.0 KB) 


this is the reslut of the code dineshs. What does this mean?

---

### Post by dineshs on 2010-06-07
You are not getting a valid IP.
Can you connect your machine directly to the modem and post the output of ifconfig -a?
BTW what did you get for
```
sudo dhclient
```

---

### Post by Yolo on 2010-06-07
Hey dineshs,

Im sorry for not responding to you last night but I had to go to sleep b/c i had class in the morning, Which I'm going to  now.  I will post the output of the code "sudo dhclient" as soon as I get home and also link up to the modem and post the other output as well. Thank you so much for your help! I really hope we can solve this problem.

Yolo

---

### Post by Yolo on 2010-06-07
OK I got some new information.

Here is the output for CODE: sudo dhclient:

steven@ubuntu:~$ sudo dhclient 
[sudo] password for steven: 
Internet Systems Consortium DHCP Client V3.1.3 
Copyright 2004-2009 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/) 

Listening on LPF/eth1/00:04:4b:0a:48:5e 
Sending on   LPF/eth1/00:04:4b:0a:48:5e 
Listening on LPF/eth0/00:04:4b:0a:48:5f 
Sending on   LPF/eth0/00:04:4b:0a:48:5f 
Sending on   Socket/fallback 
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8 
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13 
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13 
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8 
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7 
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 


And this is the output(WHILE DIRECTLY CONNECTED TO MODEM) of CODE: ifconfig -a 

steven@ubuntu:~$ ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 00:04:4b:0a:48:5f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:25 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:04:4b:0a:48:5e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:26 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:6080 (6.0 KB)  TX bytes:6080 (6.0 KB) 

steven@ubuntu:~$ 



However, I noticed something interesting.  When I tried connecting directly the modem via my black Ethernet cable, the little light that saids "link" did not turn on, but when i plugged the yellow cable connecting the router to the modem it did turn on, SO I dont think I was ever linked the modem even though i plugged it in. 

I just dont understand how my brother can connect fine when he is connected to the router just like me and I cant connect =/

Stumped!

Yolo

---

### Post by Yolo on 2010-06-07
Bump.

Does anyone else have any insight into this problem?

---

### Post by Yolo on 2010-06-07
bump.

i really need help guys >.<

---

### Post by dineshs on 2010-06-08
> **Yolo said:**
>  When I tried connecting directly the modem via my black Ethernet cable, the little light that saids "link" did not turn on, but when i plugged the yellow cable connecting the router to the modem it did turn on, SO I dont think I was ever linked the modem even though i plugged it in. 

Did you try ifconfig -a in both the cases ?
Did you try both etehrnet ports?
Can you unplug the cable from your brothers PC and connect it your ethernet port 1 ,wait for a few seconds and try ifconfig -a 
If it doesnt show a valid IP try the other port.

---

### Post by Yolo on 2010-06-08
How do I tell if it's a valid Ip address or not?

---

### Post by dineshs on 2010-06-08
Any address of the form xxx.xxx.xxx.xxx where xxx is a number between 0 and 255

---

### Post by Yolo on 2010-06-08
DINESHS!

I FINALLY GOT IT!!!

I didnt realize i had like 3 ethernet ports in the back of my PC, so i tried one of the other onces and it worked!!!!

However, I encountered a slight problem.

Everytime i reboot the computer and go to Ubuntu, in order for the internet to start working , i need to enable the code 'sudo dhclient'

if I dont then it doesn't work. Should I be concerned for this? Other then that I can surf thr web perfectly.

Here is what im getting now for ifconfig -a

steven@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:04:4b:0a:48:5f  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::204:4bff:fe0a:485f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:159004 errors:0 dropped:0 overruns:0 frame:0
          TX packets:106332 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:218764101 (218.7 MB)  TX bytes:9892095 (9.8 MB)
          Interrupt:25 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:04:4b:0a:48:5e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:26 Base address:0x4000 

eth1:avahi Link encap:Ethernet  HWaddr 00:04:4b:0a:48:5e  
          inet addr:169.254.4.175  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:26 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)


and here is what i get for sudo dhclient:

steven@ubuntu:~$ sudo dhclient
[sudo] password for steven: 
There is already a pid file /var/run/dhclient.pid with pid 1832
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth1/00:04:4b:0a:48:5e
Sending on   LPF/eth1/00:04:4b:0a:48:5e
Listening on LPF/eth0/00:04:4b:0a:48:5f
Sending on   LPF/eth0/00:04:4b:0a:48:5f
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPREQUEST of 192.168.1.101 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.101 from 192.168.1.1
bound to 192.168.1.101 -- renewal in 40145 seconds.



If all looks well and it does on this end, other then the fact i have to input that code everytime, THANK YOU VERY MUCH!!

---

### Post by dineshs on 2010-06-08
can you post what is in /etc/network/interfaces?
```
cat /etc/network/interfaces 
```

---

### Post by monkreed on 2010-06-09
Hello,
 If you are a newbie (like me) give up now.  Ubuntu, when you have problems, is much too complicated for the average user but, if someone could explain, in simple terms, why the previous versions of Ubuntu were newbie user friendly and this 10.04 such a disaster, I, and I am sure, many others, would very much appreciate some helpful comments.
Good old Windows I say

---

