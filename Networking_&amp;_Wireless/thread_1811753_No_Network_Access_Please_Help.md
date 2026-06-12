---
title: "No Network Access Please Help"
date: 2011-07-25
forum: Networking &amp; Wireless
---

### Post by TheStealthDj on 2011-07-25
I have a problem with my network right after I install apps on XP dual boot.

About two weeks ago I installed XP (dual boot) for my music apps but did not install anything into XP and had no problems until today when I installed drivers, updates and apps on XP, everything works on XP but when I booted into Ubuntu 10.10 which has been sweet for 6+ months I get no network access.

My connection is wired and I have no wireless adapter to try, my motherboard is a xfx nforce 680i lt sli and my router is a HomeHub 2.

I booted from live cd and still nothing even on a linux mint live cd?

What has XP done to my network to do this and what can I do to fix this?

---

### Post by chellrose on 2011-07-25
Have you tried resetting the connection?  (Not sure if that's the correct technical term...)

Fire up a terminal and type

```

sudo ifdown eth0
sudo ifup eth0

```

replacing "eth0" with whatever Ubuntu calls your wired connection.
You have network access on XP, correct?

I haven't seen this particular issue, but the above usually solves all of my connection problems.

---

### Post by TheStealthDj on 2011-07-25
Yes my XP has network connection and when I try what you say in terminal I get...

"Interface eth0 not configured"

---

### Post by chellrose on 2011-07-25
Could you try typing ```
ifconfig
``` in a terminal and post the output?

---

### Post by TheStealthDj on 2011-07-25
thestealthdj@STEALTH-MACHINE:~$ ifconfig


eth0      
Link encap:Ethernet  HWaddr 00:04:4b:03:59:a8  
          
inet6 addr: fe80::204:4bff:fe03:59a8/64 Scope:Link
          
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          
RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:1000 
          
RX bytes:2832 (2.8 KB)  TX bytes:5121 (5.1 KB)
          
Interrupt:41 Base address:0xa000 



lo        
Link encap:Local Loopback  
          
inet addr:127.0.0.1  Mask:255.0.0.0
          
inet6 addr: ::1/128 Scope:Host
          
UP LOOPBACK RUNNING  MTU:16436  Metric:1
          
RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:0 
          
RX bytes:1696 (1.6 KB)  TX bytes:1696 (1.6 KB)



thestealthdj@STEALTH-MACHINE:~$

---

### Post by chellrose on 2011-07-25
Hmm...

I don't *see* anything out of the ordinary there, but then I don't have a lot of experience with this...

The message "Interface eth0 not configured" should have appeared when you did ```
sudo ifdown eth0
```.  That's good - in a way - it basically tells us what we already knew, namely, that you had no network connection.

Did the terminal give any output when you typed ```
sudo ifup eth0
```?

---

### Post by TheStealthDj on 2011-07-25
The command "sudo ifup eth0" returns....

"ignoring unknown interface eth0=eth0"

I feel like weeping.

---

### Post by chellrose on 2011-07-25
Hmm... I'm almost out of ideas here.

When you installed XP, I'm guessing that you partitioned your hard drive and put XP on a separate partition?

What's in your /etc/network/interfaces file?

---

### Post by TheStealthDj on 2011-07-25
Thanks for your help Sissy, I didnt need to create a partition during the installation of XP, Ubuntu's connection was working after installation of XP and for 2 weeks untill today when I updated or sumthing?

I'm pretty sure nothing had changed with Ubuntu, its definetly XP's fault!

---

### Post by chellrose on 2011-07-25
No doubt it is XP's fault.  I have no experience with both OS's being installed on the same partition, but if that is indeed the case, then XP may have accessed something that it wasn't supposed to...

Have you noticed anything else broken in Ubuntu since your installation of XP?

I have a couple of last suggestions.  Open your /etc/network/interfaces file, via ```
gksudo gedit /etc/network/interfaces
``` (or replace gedit with your favorite text editor).  Comment out (with a # at the beginning of the line) everything _except_ the following lines:
```

auto lo
iface lo inet loopback

```
Then run
```

sudo /etc/init.d/networking restart

```
and let me know if it gives you any error messages or other weird output.

---

### Post by TheStealthDj on 2011-07-25
Im sorry I should of been a bit more clear, I had a spare partition what i cleaned up for XP so both OS's on sperate partitions. 

The /etc/network/interfaces file only has the txt you say to leave and the output of
 [FONT=monospace]"[/FONT]sudo /etc/init.d/networking restart"

"* reconfiguring network interfaces...            [ok]"

Nothing strange looking realy.

---

### Post by chellrose on 2011-07-25
> **TheStealthDj said:**
> I had a spare partition what i cleaned up for XP so both OS's on sperate partitions. 


OK, that's a good thing.

Nothing looks strange at all in the output.  I just did ifup and ifdown on this computer, and I also got the "Ignoring unknown interface eth0=eth0" message, but I still have network access.  (I'm on a work computer, so I don't usually play with the network here.)  I know that on my laptop at home, I get no such error messages.

When I get home this afternoon, I'll dig up the configuration files there and see if there's something more enlightening if necessary (but hopefully someone with more knowledge than me will jump in here and solve this before then ;)).

Do you have multiple kernels in your GRUB boot list?  What I mean is several listings like "Ubuntu, kernel 2.6.32-32-generic", which differ only in the number directly preceding the "generic".  If so, try booting into the one with the _second_ highest number.  E.g., if you have
```

Ubuntu, kernel 2.6.32-33-generic
Ubuntu, kernel 2.6.32-32-generic
Ubuntu, kernel 2.6.32-31-generic

```then boot into the 2.6.32-**32**-generic.  (Your numbers may differ slightly.)  It's possible that there was a Linux kernel update right around the time you installed XP, and that actually broke something.  See if you can get network access from within one of those older kernels.

If that fails, then run your update manager (from within the *newest* kernel/the one you typically use), and make sure everything is up-to-date.

Otherwise, the only other thing I can think of is to check the drivers.  I can't think of any reason why installing XP should have messed with them, but...

Do you remember, when you first installed Ubuntu, if your network connection worked "out of the box" or if you had to install proprietary drivers/do something else special?  If the latter, then you might try reinstalling those drivers, or check the documentation for them to see if there is some way to reset/regenerate the connection (Google "Ubuntu network drivers for (your network card)" or something similar).

That's all I can think of off-hand.  Sorry I couldn't be of more help.

---

### Post by TheStealthDj on 2011-07-26
Yes I have been through all the kernels and still the same, and my ethernet worked out of the box untill yesterday so I dont think its software thats changed its more like a setting on the hardware has been changed but what that is I'm clueless?

Thanks again for your support Sissy but if I cannot get it to connect today I'm going to revert back to Windows wich will be a shame, I have my Ubuntu setup just right for me.

So anyone out there in the magical ether that can manifest a solution to my problem?

---

### Post by TheStealthDj on 2011-07-26
Is there any expert that can help me?

---

### Post by TheStealthDj on 2011-07-26
Bump!

---

### Post by chellrose on 2011-07-27
Try adding "auto eth0" (without the quotes) to the end of your /etc/network/interfaces file, then do a sudo /etc/init.d/networking restart again.

After a bit of thought, I suspect that "Interrupt" message at the end of your ifconfig output might provide a clue.  I'm not sure what it is, though.  Anyone else reading this might want to see post #5.

I hope you are able to get it working.  It would be a shame to have to give up Ubuntu entirely because of this.

Another thought... It would be a pain, but you might try backing up your files and reinstalling Ubuntu?

---

### Post by TheStealthDj on 2011-07-27
Ahh another day and no internet on Ubuntu, it will be a shame if I have to give it up but thats the way its looking. Im pretty sure Ive tryed what you suggested yesterday amongst alot of other things. It looks like the Windows bully has taken my ethernet from Ubuntu and nobody can/wont help me get it back.   If I cannot fix this problem by the end of today Im going to cut my losses because I dont like being stressed and fustrated.

---

### Post by varunendra on 2011-07-27
> **Sissy13 said:**
> No doubt it is XP's fault.  I have no experience with both OS's being installed on the same partition, but if that is indeed the case, then XP may have accessed something that it wasn't supposed to...Quite possibly, but not necessarily. It may be anything involved in the networking - hardware or software, including an Ubuntu update itself.

Sissy, AFAIK, it is not possible to install windows and ubuntu on the same partition, because windows can not 'see' linux partitions (ext 2/3/4). WUBI installations are also no exceptions, because they use a file as a complete filesystem, which is completely isolated from rest of the contents on windows drive, and windows can't 'see' inside it.

> **TheStealthDj said:**
> Im pretty sure Ive tryed what you suggested yesterday amongst alot of other things. It looks like the Windows bully has taken my ethernet from Ubuntu and nobody can/wont help me get it back.   If I cannot fix this problem by the end of today Im going to cut my losses because I dont like being stressed and fustrated.
TheStealthDj, let's see if I may be able to reduce your frustration :)

Just to be sure, can you please post the output of **ifconfig -a** again?
From your previous output of ifconfig, it seems you've got no IP configuration for your LAN interface in Ubuntu. Do you have dhcp enabled on your router? If yes, try this-
```
sudo dhclient
```

You can also try to manually assign IP address if you know what it is in XP (ipconfig command for XP).

---

### Post by TheStealthDj on 2011-07-27
Hi varunendra and thanks for your reply.

The output of [B]ifconfig -a

[/B]thestealthdj@STEALTH-MACHINE:~$ ifconfig -a


eth0      Link encap:Ethernet  HWaddr 00:04:4b:03:59:a8  
          
    inet6 addr: fe80::204:4bff:fe03:59a8/64 Scope:Link
          
    UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          
    RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          
    TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          
    collisions:0 txqueuelen:1000 
          
    RX bytes:3206 (3.2 KB)  TX bytes:6052 (6.0 KB)
          
    Interrupt:41 Base address:0x4000 



lo     Link encap:Local Loopback  
          
    inet addr:127.0.0.1  Mask:255.0.0.0
          
    inet6 addr: ::1/128 Scope:Host
          
    UP LOOPBACK RUNNING  MTU:16436  Metric:1
          
    RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          
    TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          
    collisions:0 txqueuelen:0 
          
    RX bytes:1696 (1.6 KB)  TX bytes:1696 (1.6 KB)



thestealthdj@STEALTH-MACHINE:~$ 



And the output of **sudo dhclient **

thestealthdj@STEALTH-MACHINE:~$ sudo dhclient
[sudo] password for thestealthdj: 
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:04:4b:03:59:a8
Sending on   LPF/eth0/00:04:4b:03:59:a8
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.1.64 from 192.168.1.254
DHCPREQUEST of 192.168.1.64 on eth0 to 255.255.255.255 port 67
DHCPNAK from 192.168.1.254
DHCPREQUEST of 192.168.1.64 on eth0 to 255.255.255.255 port 67
DHCPNAK from 192.168.1.254
DHCPREQUEST of 192.168.1.64 on eth0 to 255.255.255.255 port 67
DHCPNAK from 192.168.1.254

Then it keeps looping from DHCPDISCOVER over and over again.[]("http://ubuntuforums.org/member.php?u=1043629")

---

### Post by varunendra on 2011-07-27
I'm not yet familiar with DHCPNAK reply. I need to look deeper into this before I can explain it. Apparently, your router's IP is 192.168.1.254 and it HAS DHCP enabled. But a quick glance over 'NAK' reply suggests that the offered IP (192.168.1.64) does not exist on your subnet.

So quite basically, you should try to manually assign IP address to your eth0 interface. If you know what your computer's IP address in windows is, you can use Network Manager (easier), or use following command to assign it in Ubuntu:
```
sudo ifconfig eth0 xxx.xxx.xxx.xxx
```where xxx.xxx..... is the IP address. Then redo ifconfig to see if that address sticks to it. Then we'll need to define Gateway and DNS.

If not sure, boot into **windows**, make sure it is connected to Internet, then open command prompt and enter this command:
```
ipconfig /all > c:\ipconfig.txt
```This will create an 'ipconfig.txt' file in your C: drive. Post its contents here.





**_PS_:**
wrap your outputs in [ code] and [ /code] tags, or simply select (only) the output text, then click on **#** symbol at the top of the edit box. It makes your post more readable.

---

### Post by TheStealthDj on 2011-07-27
The output from XP ipconfig is...

Windows IP Configuration



        Host Name . . . . . . . . . . . . : music-machine

        Primary Dns Suffix  . . . . . . . : 

        Node Type . . . . . . . . . . . . : Unknown

        IP Routing Enabled. . . . . . . . : No

        WINS Proxy Enabled. . . . . . . . : No

        DNS Suffix Search List. . . . . . : home



Ethernet adapter Local Area Connection 3:



        Connection-specific DNS Suffix  . : home

        Description . . . . . . . . . . . : NVIDIA nForce Networking Controller

        Physical Address. . . . . . . . . : 00-04-4B-03-59-A8

        Dhcp Enabled. . . . . . . . . . . : Yes

        Autoconfiguration Enabled . . . . : Yes

        IP Address. . . . . . . . . . . . : 192.168.1.64

        Subnet Mask . . . . . . . . . . . : 255.255.255.0

        Default Gateway . . . . . . . . . : 192.168.1.254

        DHCP Server . . . . . . . . . . . : 192.168.1.254

        DNS Servers . . . . . . . . . . . : 192.168.1.254

        Lease Obtained. . . . . . . . . . : 27 July 2011 14:24:22

        Lease Expires . . . . . . . . . . : 28 July 2011 14:24:22

---

### Post by varunendra on 2011-07-27
> **TheStealthDj said:**
> The output from XP ipconfig is...
        IP Address. . . . . . . . . . . . : 192.168.1.64

        Subnet Mask . . . . . . . . . . . : 255.255.255.0

        Default Gateway . . . . . . . . . : 192.168.1.254

        DHCP Server . . . . . . . . . . . : 192.168.1.254

        DNS Servers . . . . . . . . . . . : 192.168.1.254

        Lease Obtained. . . . . . . . . . : 27 July 2011 14:24:22

        Lease Expires . . . . . . . . . . : 28 July 2011 14:24:22
Alright, some further search tells that for some reason, your DHCP server is sending Negative AcKnowledgement (that's what NAK is). That is, it is offering IP 192.168.1.64, but when it is requested by dhclient, it refuses saying that "it is already assigned to a **different client**." Funny, but that's what is happening. An excerpts from the source of this info- > *According to the protocol, the primary identifier of a client is the *>* "client identifier" option. The server uses the MAC address only if there *>* is no "client identifier". Normally, if a client makes two requests, one *>* with and one without a "client identifier", they are seen by the server as *>* separate clients and are given two different IP addresses. This is what *>* happens in the PXE boot process. Judging from traffic on this list, it has *>* long been an annoyance to some people. *>>*      I suspect somebody has tried to "fix" this behaviour but has not quite *>* completed the job. The code to process the discover considers the two cases *>* to be equivalent but the code doing the request does not. Whether that *>* somebody was at ISC (in which case you should probably file a bug report) *>* or modified you copy, I do not know. I would expect the release notes to *>* say something if there has been an official change.*(source: [https://lists.isc.org/pipermail/dhcp-users/2011-March/012878.html](https://lists.isc.org/pipermail/dhcp-users/2011-March/012878.html))


Anyway, that was just explanation part. Solution should be quite easy for you. Just assign it manually. So, open Network Manager (NM applet on right upper panel > right-click > edit connections), goto "Wired" tab, select your eth0 interface and click "Edit" button.

Then goto IPv4 tab, change 'Method' to 'Manual', click 'Add' and set 192.168.1.64 as IP, 255.255.255.0 as Netmask, 192.168.1.254 as Gateway and same (192.168.1.254) as DNS.

Make sure to press 'Enter' on your keyboard after typing each set of addresses to make NM accept it.

---

### Post by TheStealthDj on 2011-07-27
THANK YOU VERY MUCH.

Its working now, I done this yesterday but didnt put didnt know what to put in the gateway colum.

Again thank you, you have made me a happy person.

---

### Post by varunendra on 2011-07-27
I think I just got lucky with this one. :D
Glad my luck helped someone.

Now, as a side note, you may wish to disable IPv6 on that interface. It sometimes causes slow browsing issues. You may use this guide to do so: [http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)

or this one:
[http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)

---

### Post by TheStealthDj on 2011-07-27
Thanks mate I will do that.

:D

---

