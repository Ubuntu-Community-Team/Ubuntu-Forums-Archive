---
title: "For God sake please Help."
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by satan2204 on 2009-01-15
so here i go. Please help. I was so inspired with  linux that i quicly thought of switching to ubuntu finally. Then it came up with so many problems i never realised. Its been 3 days im looking to solve these problems. So first i crashed my hard disk drive loosing all data then black back ground problem but finally solved these issues. Now i have came up with a real issue with no help . After installing ubuntu I clicked those 2 pc's it showed that wireless is available and it connected it with 30 % quality, used to connect at 50% on my pc.after conecting it doest work. I mean no downloading, uploading browsing, nothing. i pinged my ips and showed me healthy connection. What the hell is wrong with ubuntu.

By the way im using usb wireless card with my PC. we have a router in our home, all cousins share that router. internet is working on there pcs but not mine. It was working fine on my pc too when i had xp. please help   i donbt want to switch to xp again.... Please........... and sorry for poor english.

---

### Post by satan2204 on 2009-01-15
anybody?? Please. Im damn help less please help.

---

### Post by wmdiem on 2009-01-15
what does it give you when you run
dig [www.google.com](www.google.com)

---

### Post by satan2204 on 2009-01-15
> **wmdiem said:**
> what does it give you when you run
dig [www.google.com](www.google.com)

I cant dig ? I can see my wireless network in drop down and when i try to connect it it doesnt. after seachin for some time it just disconects. Last night it was connecting but noi browsing now it doesnt even connectionting, still still sjowing 30%

---

### Post by AlexDudko on 2009-01-15
If you can ping by ip's but can't get web pages in your browser it must be the DNS problem. Check /etc/resolv.conf if there is your dns server ip. If there's nothing, just add one in this way:
> nameserver xxx.xxx.xxxx.xxx
where xxx.xxx.xxxx.xxx is your dns server's ip.

---

### Post by wmdiem on 2009-01-15
Please give the output from

ifconfig
iwconfig

---

### Post by hyper_ch on 2009-01-15
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

Also bumping a post sooner than 24h after you first posted it not kind towards all others that seek help!

---

### Post by satan2204 on 2009-01-15
icludint screenshot of my pc, hope it can help you.

---

### Post by satan2204 on 2009-01-15
posting my Ifconfig here

```

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:09:6b:19:2e:91  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9248 (9.2 KB)  TX bytes:9248 (9.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:e0:4c:00:d0:aa  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:720 (720.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-E0-4C-00-D0-AA-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by satan2204 on 2009-01-15
Anybody here to help me? Im planing to switch back to XP. :(

---

### Post by satan2204 on 2009-01-15
Guys please help me I will be very appreciate you guys, Iam sick of this ubuntu, Its giving me headaches:( :(

---

### Post by perlluver on 2009-01-15
You have to give us time to help you, we are not paid to do this, we all work for free.  You can't make threats about going back to Windows, and expect people here to help you.  If you are really that determined to go back to Windows, then go, we won't hold you back.

Now if you want to have some patience, to let us help you, then we will be more then happy too.

---

### Post by satan2204 on 2009-01-15
Sorry man, I have patience. But you know life without internet is hell. I cant downlopad updates. I cant do anything. Im so frustrated. Its been 2 ddays. Im sorry again for the behaviour. Thank you,

Please help me If you can

---

### Post by hyper_ch on 2009-01-15
Another one on my ignore list because of unnecessary bumping of threads to the disadvantage of others that seek help - despite being told so.

---

### Post by wmdiem on 2009-01-15
did you post the output from iwconfig?

---

### Post by pdtpatrick on 2009-01-15
stop trying to tell him to post iwconfig and ifconfig output. He already said he cannot connect to the network so why would it matter to keep posting such outputs.

can you please run this:

sudo dkpg -l | grep -i network-manager (what version is installed?)
sudo lshw | grep -i wireless
sudo lsusb | grep -i wireless

Also how far away are you from the router? can you try going right next to the router and see if the signal strengthens please.

---

### Post by wmdiem on 2009-01-15
> **pdtpatrick said:**
> stop trying to tell him to post iwconfig and ifconfig output. He already said he cannot connect to the network so why would it matter to keep posting such outputs.


1) because at least when the problem started he obviously did have a network connection because he said he could ping, and the subsequent posts indicate that the connection comes and goes. 
2) iwconfig might tell whether it was a weak signal or high noise(and lots of other niffty stuff that might have given a clue about why his connection is flaky).

---

### Post by satan2204 on 2009-01-17
UPDATE: I installled xp to see if my wireless is working. Wireless was working fine on xp but not on ubuntu. Yea I had to renew th ips on xp to use the iinternet. When i logged in xp again to see the problem. It connected to the net. It even showed that wireless network is connected. But when I browse."no internet" Can u guys figure out what is the problem??? wireless connects now but no browsing? do i have to renew IPs ? I use to do this on my xp!! dont know how to do this in ubuntu.

---

