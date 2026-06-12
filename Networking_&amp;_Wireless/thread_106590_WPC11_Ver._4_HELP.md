---
title: "WPC11 Ver. 4 HELP"
date: 2005-12-21
forum: Networking &amp; Wireless
---

### Post by naruto11111 on 2005-12-21
Hi, I know there are tons of threads dealing with this type of issue, even with this card, but I haven't been able to find the answer.

I am a new linux user (I am done with windows for all the problems it has given me) and I installed ubuntu on my laptop.  I have a built in ethernet card but it is not wireless so I have a Linksys wpc11 ver 4 wireless PCMCIA card.

I downloaded the drivers for it and installed it with ndiswrapper

ndiswrapper -i NET8180.INF

it says it's installed.

Now what do I do?

When I goto the networking utilities, it lists loop and eth0.  when I set it to eth0, it does not allow me to connect to my network.

I have a Linksys wireless router for which I have turned off all security to try to get this to work, so it's on all the default settings (ssid:  linksys, etc)

Can anyone please help?  Thanks.

---

### Post by Lambert on 2005-12-21
Not knowing what instructions you followed or if you completed all the steps, here are some thoughts.
 
1. what driver did you use? did you copy it to your hard drive and install from that location? did you copy all files such as .inf .sys .bin into the file on your drive?
2. after installing the driver did you run the command depmod -a
3. did you load the ndiswrapper module with modprobe? check to make sure it's running with this command   lsmod | grep ndis   if you get no output and it just goes to another prompt then it's not loaded. 
4. to make sure it loads on boot run the command   ndiswrapper -m
 
There's a link in my signature about ndiswrapper. There's a link in that page to ndiswrapper wiki with a troubleshooting section. You can look there for more help.
 
Currently if wlan0 is not showing up in the list then the driver is either not loaded or not working properly.

---

### Post by naruto11111 on 2005-12-24
Thanks a lot, got it working.   your directions really helped.  I only copied the INF file and the rest of the steps worked out perfectly.

Thanks again.

---

