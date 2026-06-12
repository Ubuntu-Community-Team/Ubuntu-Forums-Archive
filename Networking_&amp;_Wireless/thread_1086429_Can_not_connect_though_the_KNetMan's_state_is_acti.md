---
title: "Can not connect though the KNetMan's state is activated"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by thinhhoang on 2009-03-04
Hello guys,
I've installed Ndiswrapper on Kubuntu 8.10 Intrepid Ibex successfully. After that, I used the KNetworkManager to setup my wireless network. Clicking Save & Connect, it changed its icon from a globe to the network bars and the state (of wlan0) was "Activated". But when I opened Konqueror and tried to type an Internet Address (such as [www.google.com](www.google.com)), I still can't get connected. Please help me out of this. Thanks a lot. ;)

---

### Post by N04h on 2009-03-04
Try ```
ping 72.14.205.104
``` from the command prompt and then paste your results back to the forum.

---

### Post by thinhhoang on 2009-03-04
> **N04h said:**
> Try ```
ping 72.14.205.104
``` from the command prompt and then paste your results back to the forum.

Thanks. I got my result similar to this.

```
thinhhoang@ubuntu:~$ ping 72.14.205.104
PING 72.14.205.104 (72.14.205.104) 56(84) bytes of data.
64 bytes from 72.14.205.104: icmp_seq=2 ttl=241 time=257 ms
64 bytes from 72.14.205.104: icmp_seq=2 ttl=241 time=257 ms (DUP!)
64 bytes from 72.14.205.104: icmp_seq=4 ttl=241 time=259 ms       
64 bytes from 72.14.205.104: icmp_seq=5 ttl=241 time=269 ms       
64 bytes from 72.14.205.104: icmp_seq=6 ttl=241 time=258 ms       
64 bytes from 72.14.205.104: icmp_seq=7 ttl=241 time=260 ms       
64 bytes from 72.14.205.104: icmp_seq=8 ttl=241 time=264 ms       
64 bytes from 72.14.205.104: icmp_seq=9 ttl=241 time=266 ms       
64 bytes from 72.14.205.104: icmp_seq=10 ttl=241 time=265 ms      
64 bytes from 72.14.205.104: icmp_seq=11 ttl=241 time=256 ms      
64 bytes from 72.14.205.104: icmp_seq=12 ttl=241 time=257 ms      
64 bytes from 72.14.205.104: icmp_seq=13 ttl=241 time=259 ms      
64 bytes from 72.14.205.104: icmp_seq=14 ttl=241 time=258 ms      
64 bytes from 72.14.205.104: icmp_seq=15 ttl=241 time=266 ms      
64 bytes from 72.14.205.104: icmp_seq=16 ttl=241 time=270 ms      
64 bytes from 72.14.205.104: icmp_seq=17 ttl=241 time=258 ms      
64 bytes from 72.14.205.104: icmp_seq=18 ttl=241 time=258 ms      
64 bytes from 72.14.205.104: icmp_seq=19 ttl=241 time=259 ms      
64 bytes from 72.14.205.104: icmp_seq=20 ttl=241 time=266 ms      
64 bytes from 72.14.205.104: icmp_seq=21 ttl=241 time=259 ms      
64 bytes from 72.14.205.104: icmp_seq=22 ttl=241 time=261 ms      
64 bytes from 72.14.205.104: icmp_seq=23 ttl=241 time=265 ms      
64 bytes from 72.14.205.104: icmp_seq=24 ttl=241 time=268 ms      
64 bytes from 72.14.205.104: icmp_seq=25 ttl=241 time=260 ms      
64 bytes from 72.14.205.104: icmp_seq=26 ttl=241 time=263 ms      
64 bytes from 72.14.205.104: icmp_seq=27 ttl=241 time=261 ms      
64 bytes from 72.14.205.104: icmp_seq=28 ttl=241 time=260 ms      
64 bytes from 72.14.205.104: icmp_seq=29 ttl=241 time=271 ms      
64 bytes from 72.14.205.104: icmp_seq=30 ttl=241 time=259 ms      
64 bytes from 72.14.205.104: icmp_seq=31 ttl=241 time=259 ms      
64 bytes from 72.14.205.104: icmp_seq=32 ttl=241 time=262 ms      
64 bytes from 72.14.205.104: icmp_seq=33 ttl=241 time=265 ms      
64 bytes from 72.14.205.104: icmp_seq=34 ttl=241 time=289 ms      
64 bytes from 72.14.205.104: icmp_seq=35 ttl=241 time=276 ms      
64 bytes from 72.14.205.104: icmp_seq=36 ttl=241 time=260 ms      
64 bytes from 72.14.205.104: icmp_seq=37 ttl=241 time=261 ms      
64 bytes from 72.14.205.104: icmp_seq=38 ttl=241 time=259 ms      
64 bytes from 72.14.205.104: icmp_seq=39 ttl=241 time=262 ms      
64 bytes from 72.14.205.104: icmp_seq=40 ttl=241 time=260 ms      
64 bytes from 72.14.205.104: icmp_seq=41 ttl=241 time=264 ms      
64 bytes from 72.14.205.104: icmp_seq=42 ttl=241 time=269 ms      
64 bytes from 72.14.205.104: icmp_seq=43 ttl=241 time=269 ms      
64 bytes from 72.14.205.104: icmp_seq=44 ttl=241 time=267 ms      
64 bytes from 72.14.205.104: icmp_seq=45 ttl=241 time=266 ms      
64 bytes from 72.14.205.104: icmp_seq=46 ttl=241 time=269 ms      
64 bytes from 72.14.205.104: icmp_seq=47 ttl=241 time=256 ms      
64 bytes from 72.14.205.104: icmp_seq=48 ttl=241 time=262 ms      
64 bytes from 72.14.205.104: icmp_seq=49 ttl=241 time=259 ms      
64 bytes from 72.14.205.104: icmp_seq=50 ttl=241 time=267 ms      
64 bytes from 72.14.205.104: icmp_seq=51 ttl=241 time=260 ms      
64 bytes from 72.14.205.104: icmp_seq=52 ttl=241 time=262 ms      
64 bytes from 72.14.205.104: icmp_seq=53 ttl=241 time=257 ms      
64 bytes from 72.14.205.104: icmp_seq=54 ttl=241 time=264 ms      
64 bytes from 72.14.205.104: icmp_seq=55 ttl=241 time=259 ms      
64 bytes from 72.14.205.104: icmp_seq=56 ttl=241 time=260 ms      
64 bytes from 72.14.205.104: icmp_seq=57 ttl=241 time=268 ms      
64 bytes from 72.14.205.104: icmp_seq=58 ttl=241 time=259 ms      
64 bytes from 72.14.205.104: icmp_seq=59 ttl=241 time=263 ms      
64 bytes from 72.14.205.104: icmp_seq=60 ttl=241 time=258 ms      
```

One more thing to consider: I've edited the interfaces and the resolv.conf to get my Wired Network to work.

---

### Post by N04h on 2009-03-05
Did you do the ping without the ethernet port working?  Do the ping with the cable unplugged and connected via wifi to the router.

---

### Post by thinhhoang on 2009-03-05
Nope. I did the ping in both cases. One within Ethernet cable plugged in and one without the Ethernet cable plugged in. Both  ping commands returned me the same result like above.

---

### Post by xycris on 2009-03-05
Hi,

I got almost the same problem but mine is with the Ethernet connection. I have installed the 8.10 Intrepid Ibex and by default KNetMan is able to see that I have a working network connection. I did try to browse but get an error but the ping works just fine same as mentioned in earlier posts by thinhhoang. I tried to access my router but it gave an error as well something like I am connected but I cannot open the URL I am trying to open and advised me to contact my network administrator.

> Nope. I did the ping in both cases. One within Ethernet cable plugged in and one without the Ethernet cable plugged in. Both ping commands returned me the same result like above.

Prior to this problem, I am aware that before the 8.10 was introduced, 8.04 version was unable to use my hardware and found in ubuntuforums.org that the existing linux kernel that time period does not support it. Below are forum threads with regards to the kind of hardware I have. The first one had the issue resolved.

[http://ubuntuforums.org/showthread.php?t=847873](http://ubuntuforums.org/showthread.php?t=847873)
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=429845](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=429845)
[http://ubuntuforums.org/showthread.php?t=1086429](http://ubuntuforums.org/showthread.php?t=1086429)

So my dillema right now is do I need to use the driver provided by Asus or I just need to tweak my KNetMan? If ever I need to tweak, please provide me a step by step process for I am totally a newbie.

Thank you.

---

### Post by thinhhoang on 2009-03-05
Are you using static IP address?

---

### Post by thinhhoang on 2009-03-05
I've already been to this case too. Configuring KNetMan giving me no result, so I had to edit the resolv.conf and the interfaces by hand. I think there must be something wrong with the KNetman.

---

### Post by N04h on 2009-03-05
> **thinhhoang said:**
> Nope. I did the ping in both cases. One within Ethernet cable plugged in and one without the Ethernet cable plugged in. Both  ping commands returned me the same result like above.

If that is the case it sounds like a DNS issue.  Try [http://72.14.205.104/](http://72.14.205.104/) in your web browser and it should load google.com.  Please confirm your DNS settings are set up at the router if using DHCP.  If that is the case make sure that you are getting the DHCP info from the router.

---

### Post by N04h on 2009-03-05
> **xycris said:**
> Hi,

I got almost the same problem but mine is with the Ethernet connection. I have installed the 8.10 Intrepid Ibex and by default KNetMan is able to see that I have a working network connection. I did try to browse but get an error but the ping works just fine same as mentioned in earlier posts by thinhhoang. I tried to access my router but it gave an error as well something like I am connected but I cannot open the URL I am trying to open and advised me to contact my network administrator.



Prior to this problem, I am aware that before the 8.10 was introduced, 8.04 version was unable to use my hardware and found in ubuntuforums.org that the existing linux kernel that time period does not support it. Below are forum threads with regards to the kind of hardware I have. The first one had the issue resolved.

[http://ubuntuforums.org/showthread.php?t=847873](http://ubuntuforums.org/showthread.php?t=847873)
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=429845](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=429845)
[http://ubuntuforums.org/showthread.php?t=1086429](http://ubuntuforums.org/showthread.php?t=1086429)

So my dillema right now is do I need to use the driver provided by Asus or I just need to tweak my KNetMan? If ever I need to tweak, please provide me a step by step process for I am totally a newbie.

Thank you.

Turn off all encryption on your Wifi and try connecting preferably through the command line.  This is a quick and dirty way to confirm if your wifi is working.

---

### Post by thinhhoang on 2009-03-06
I confirmed that the DHCP settings have been set up at the router, but I still can't get connected.

---

### Post by thinhhoang on 2009-03-06
> **N04h said:**
> If that is the case it sounds like a DNS issue.  Try [http://72.14.205.104/](http://72.14.205.104/) in your web browser and it should load google.com.  Please confirm your DNS settings are set up at the router if using DHCP.  If that is the case make sure that you are getting the DHCP info from the router.

I think we're almost close to the solution. When I opened Konqueror and typed: [http://72.14.205.104](http://72.14.205.104), it directed me to Google, but typing [http://google.com](http://google.com) directed me to nowhere. :( Please help me out of this.

---

### Post by N04h on 2009-03-06
You can manually set your DNS server in your interfaces file. 

Here is an example: [http://ubuntuforums.org/showthread.php?t=108712]("http://ubuntuforums.org/showthread.php?t=108712")

---

### Post by thinhhoang on 2009-03-07
Can you tell me more details please? I haven't to configure anything on Windows, so I think it should be the same on Linux.

---

### Post by xycris on 2009-03-09
Hi N04h,

> Turn off all encryption on your Wifi and try connecting preferably through the command line. This is a quick and dirty way to confirm if your wifi is working.
__________________
||TheMostlyHonestTruth|| 

How do you do that? Is there a thread or an existing thread that has instructions for that encryption?

I have made a direct connection instead using PPPOE, but, somehow, I am monopolising the Internet connection and others at my place also wants to be connected.

The router worked fine when my computer was still running Windows and so did other computers who are in the network. I found Ubuntu/Kubuntu to be appealing as to the speed, the lighter load to the processor, and the free bundle compared to Vista and even the beta Windows 7.

Thanks for the help in advance. :)

---

### Post by thinhhoang on 2009-03-10
Thank you, I find out that I have to modify the interfaces manually cause of the impossibility to configure DNS by DHCP.

---

### Post by xycris on 2009-03-11
By the way, my hardware devices for networking are an Attansic Ethernet with a Surecome model # EP-4904SX.

---

