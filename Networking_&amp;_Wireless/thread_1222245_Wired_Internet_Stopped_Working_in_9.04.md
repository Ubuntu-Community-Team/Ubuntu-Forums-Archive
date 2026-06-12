---
title: "Wired Internet Stopped Working in 9.04"
date: 2009-07-24
forum: Networking &amp; Wireless
---

### Post by Newfoundlander on 2009-07-24
Last night I connected to the Internet using the ethernet cable as usual and shut down before going to bed.  When I started up my laptop, I could not browse the web.  Using a Ubuntu Live CD, I am able to browse the web just fine.  I haven't installed any new applications or tinkered with my settings, but there were some automatic updates yesterday.

The results of ifconfig in both the Live CD and my normal login show the same details.  I'm using Ubuntu 9.04.

Any ideas what may be happening or anything else I can check?

Thanks,

Steve

---

### Post by s3MA00RRNY on 2009-07-24
Check /etc/NetworkManager/nm-system-settings.conf and make sure that [ifupdown]/managed is set to true.

---

### Post by cgb on 2009-07-24
Possibly a browser or driver problem.  There were some firfox updates that occured yesterday that might be the culprit.  You may wish to try and reinstall firefox and see if this fixes the issue.  For further troubleshooting you may want to try and ping a site through terminal and see if you are getting a response.  This will further determine if it is a browser issue or complete connection issue.

---

### Post by Newfoundlander on 2009-07-24
> **cgb said:**
> Possibly a browser or driver problem.  There were some firfox updates that occured yesterday that might be the culprit.

I use Opera as my main browser but Firefox also gave me "no connection" errors.

> **pcdude2143 said:**
> Check /etc/NetworkManager/nm-system-settings.conf and make sure that [ifupdown]/managed is set to true.

It was false so I set it to true and restarted but still no connection. :(

---

### Post by cgb on 2009-07-24
Interesting.  Did you try running a ping command through terminal to see how it would respond or possibly test other network connections such as file sharing?
```
ping www.google.com
```

---

### Post by Newfoundlander on 2009-07-25
Pinging returns "ping: unknown host www.google.com"

Up in the panel the network icon says "Wired network connection 'Auto eth0' active" and everything appears good but no connectivity, no pings, no traceroutes.

---

### Post by LookTJ on 2009-07-25
Try:
```
sudo ifconfig
```If eth0 is there, we know the driver is working.

But if the IP isn't right in your eyes, then try:
```
sudo dhclient eth0
```If that fails, try checking/swapping out your rj45 cable, or your router.

:)

---

### Post by Iowan on 2009-07-25
Try pinging 74.125.95.103. if that works, you may have DNS problem.

---

### Post by Newfoundlander on 2009-07-25
Results of ifconfig:
```

stephen@seaPOC:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:e7:2a:54  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fee7:2a54/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:94 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31069 (31.0 KB)  TX bytes:1152 (1.1 KB)
          Interrupt:16 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

```

The ethernet cable and modem worked fine with my other computer and also with my non-connecting laptop when running a Live CD so I feel that the hardware is okay and this is a software issue.
 
Pinging Google's IP address worked so this may be a DNS problem but I have no idea where to go from here.

---

### Post by cgb on 2009-07-25
It must be the DNS then.  You could try inputing the DNS setting manually which according to LookTJ you can edit with the below code.  See if that helps.  

```
sudo gedit /etc/resolv.conf
```

then add this line

```

nameserver 192.168.1.1
```

your gateway should be fine with providing DNS

---

### Post by Newfoundlander on 2009-07-25
> **cgb said:**
> It must be the DNS then.  You could try inputing the DNS setting manually which according to LookTJ you can edit with the below code.  See if that helps.  

```
sudo gedit /etc/resolv.conf
```

then add this line

```

nameserver 192.168.1.1
```

your gateway should be fine with providing DNS


When I checked, that file already contains "nameserver 192.168.1.1".  This is really baffling me.

---

### Post by Newfoundlander on 2009-07-26
I have everything backed up on my portable drive so I just did a fresh install of Ubuntu 9.04 to get rid of some lingering problems (and mostly to get my Internet connection back).

Everything was going good, I had some of my common applications installed and had rebooted.  Flash was working in my web browsers and surfing sites was working.  Then I went to Add/Remove and selected several more apps.  Partway through the installation, an error appeared so I checked and the DNS problem is back!

What is causing this?  How can I fix it?

---

### Post by Iowan on 2009-07-26
Another option for you: 
Edit */etc/dhcp3/dhclient.conf*. Uncomment the "prepend domain-name-servers" line and insert OpenDNS server addresses (208.67.222.222, 208.67.220.220).
ie. change ```
#prepend domain-name-servers 127.0.0.1;
``` to ```
prepend domain-name-servers 208.67.222.222,208.67.220.220;
```

---

### Post by Newfoundlander on 2009-07-26
> **Iowan said:**
> Another option for you: 
Edit */etc/dhcp3/dhclient.conf*. Uncomment the "prepend domain-name-servers" line and insert OpenDNS server addresses (208.67.222.222, 208.67.220.220).

Sadly, that did not work.  I noticed another thread with the same problem and was really hoping that would fix the problem.

---

### Post by DragonDon on 2009-07-26
Getting the same problem with with a Live CD.  I've tried this CD on many systems and it results with the same problem.  The systems work fine in Windows otherwise.

I have a static IP setup using an Linksys WRT45GS router with DD-WRT 

Given the number of people who have this same problem, this should seriously be addressed.

FWIW, using network tools, I could tracert google.ca and resolve to an IP (huh??).....but can't ping/browse it in any form.  Using the default FF version that comes with the LiveCD.

Also, just booted with Ubuntu 8.04 LTS Live CD (on the same Dell Dimension 1100 as I tried 9.04 with)and everything works fine.  9.04 has some serious issues when something as basic as network functionality gets screwed up.

---

