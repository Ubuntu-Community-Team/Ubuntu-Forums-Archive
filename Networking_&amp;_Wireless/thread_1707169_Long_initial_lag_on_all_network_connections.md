---
title: "Long initial lag on all network connections"
date: 2011-03-14
forum: Networking &amp; Wireless
---

### Post by pmjboyle on 2011-03-14
Hi everyone,

I am having a curious problem in ubuntu 10.10, although the problem also existed in 10.04. My machine is connected through a d-link router, the network card is built-in on my Gigabyte GA-880GM-UD2H and the driver in use is "r8169 Gigabit Ethernet driver 2.3LK-NAPI". Hopefully this is sufficient hardware information. 

Here is the problem: whenever I initiate a network connection of any kind, there is a 5-10 second lag (i.e. long, by today's standards) before the connection takes. For instance, when I point my browser to a new URL, there is a delay before the page starts loading. Once the connection is established, things seem to zip along at the expected rate (similar to my Windows 7 machines).

I'm not sure where to start in debugging this. I have plenty of experience working in the shell, but I have never dealt with a problem like this before. If there is a log file I can watch while starting a new connection, I guess that would be a good place to start :)

Thanks,
Patrick

---

### Post by CherryInHove on 2011-03-17
I'm absolutely not an expert at Ubuntu and was having this exact same problem where I found this thread.

I have just managed to solve this problem by following the instructions listed in here [http://ubuntuforums.org/showthread.php?t=1615318&page=2](http://ubuntuforums.org/showthread.php?t=1615318&page=2)

They said do 

sudo iwconfig eth1 power off

but my wireless is wlan0 so I just did

sudo iwconfig wlan0 power off

and it seems to be much much better. It could just be that I'm imagining it or I'm just very lucky and things happen to be connecting quickly, but it's worth a gry.

---

### Post by pmjboyle on 2011-03-18
Thanks for the tip Cheryl, but I don't think that's the problem. I ran the command and the feedback was "operation not supported" for eth0. 

This isn't a laptop, so I doubt power management is the issue.

Cheers,
Patrick

---

