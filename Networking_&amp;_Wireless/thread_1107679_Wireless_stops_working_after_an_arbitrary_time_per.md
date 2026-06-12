---
title: "Wireless stops working after an arbitrary time period"
date: 2009-03-27
forum: Networking &amp; Wireless
---

### Post by jobix on 2009-03-27
I have Ubuntu 8.04 (Hardy) on an AMD 64 machine. I'm using a 150N AirLink USB adapter - AWLL6070. I have ndiswrapper installed and also the /etc/wpa_supplicant files since I'm using WPA-PSK.

Problem is I get a wireless connection but after some random amount of time (5 minutes to an hour or more) it stops working. Usually, I'm on the internet when I try to load a page and see that it fails. However, the little network icon at the top right of my desktop shows that I still have two bars of connectivity. It tells me that I'm connected to my SSID. If I execute "ifconfig" that too tells me I have a valid IP address that hasn't changed. But, when I try to ping some external IP address, it fails. 

I've tried clicking on the network icon and it would "spin" for a little before giving up. I tried pulling out the USB adapter and putting it back in. I tried restarting networking (sudo /etc/init.d/networking restart) but nothing works. The only way to get wireless again is to restart the computer. Even that doesn't work sometimes and I have to reboot 2-3 times.

Any ideas on what could be going wrong? What else can I do to troubleshoot this?

Thanks.

---

### Post by Agent.Logic_ on 2009-04-14
I have the same problem! Except that it takes me almost over an hour for this problem to kick in. Using in-built wireless adapter. Only a system restart fixes the problem. I've even tested this sitting beside the wireless router, it still happens. Could this be related to heat build up?

---

### Post by Black_Wolf_92 on 2009-04-14
IDENTICAL problem. I've posted this myself in a few threads now, it seems a lot of people are sharing the same problem. My PCI card works flawlessly (WG311) But the USB adapter a bought new a while ago (while still on windows) has this exact problem.

I made a thread about it a while ago, you can search for it if you want. But I'm thinking its not so much an anomoly, but a bug with certain cards.

By the way, this is all using ndiswrapper with both my cards (one at a time of course) the PCI(working) and the USB(not working)

If you are not using ndiswrapper, I recommend trying it to see if you can get it working, but taking into account its a USB card your talking about, you're probebly already using it ;)


Check these threads to see if the problems are similar, we may have a bug on our hands that needs reporting!
[http://ubuntuforums.org/showthread.php?t=1124934](http://ubuntuforums.org/showthread.php?t=1124934)
[http://ubuntuforums.org/showthread.php?t=1120371](http://ubuntuforums.org/showthread.php?t=1120371)

---

### Post by jobix on 2009-04-22
Thanks for the links. Looks like it's all the same problem. And yes, to answer your question, I am using ndiswrapper like I mentioned in my original post.

Another data point, I never get more than 2 out of 4 bars of wireless strength even if I'm sitting right next to the router. So, it's usually around 20-45% strength.

I've just been reading and typing faster to circumvent this problem of limited connectivity :)

---

