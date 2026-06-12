---
title: "Wireless Card Connected but cant' get online"
date: 2009-12-26
forum: Networking &amp; Wireless
---

### Post by dondiego2 on 2009-12-26
I finally got my wireless card to work and my network shows up when I scan. I have set the connection up with the SSID, the BSSID and have set up the wireless security.  It show that I am connected in Network Manager but when I open Firefox I cannot connect.  I have no problems when I am directly connected through the Ethernet as I am now.

Any suggestions?

Carl

---

### Post by dondiego2 on 2009-12-27
bump for help
Carl

---

### Post by chewearn on 2009-12-27
What error are you getting from Firefox?

---

### Post by dondiego2 on 2009-12-27
It just says it can't connect to the page.

When I plug in th Ethernet cable I can connect but when I pull it out and try to use the wireless card it says can't connect.

---

### Post by dondiego2 on 2009-12-27
The wireless connection in the Network Manage right now says that the signal is at 90% so I know I am connecting to the router.  When I edit the connection and click scan it picks up my router first and then a bunch of the neighbors routers.  It's like I'm not getting an IP address or something.

Carl

---

### Post by chewearn on 2009-12-27
Is the connection problem occurred just in Firefox, or generally?  For instance, could you ping a website?

```

ping www.google.com

```

---

### Post by dondiego2 on 2009-12-27
No I can't ping Google - only when the Ethernet cable is connected.k

I get unknown host [www.google.com](www.google.com)

---

### Post by chewearn on 2009-12-27
How about ping the IP of Google:
```

ping 216.239.61.104

```


If you got reply, then you are missing the DNS server settings.

If this still not working, post output of:

```

ifconfig

```

---

### Post by dondiego2 on 2009-12-27
When I ping 216.239.61.104 I get network unreachable.

here is the result of ifconfig

carl@carl:~$ ifconfig            
eth0      Link encap:Ethernet  HWaddr 00:17:31:b1:3a:3c  
          inet6 addr: fe80::217:31ff:feb1:3a3c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1        
          RX packets:178202 errors:0 dropped:0 overruns:0 frame:0
          TX packets:137685 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000                             
          RX bytes:191756375 (191.7 MB)  TX bytes:17973671 (17.9 MB)
          Interrupt:23 Base address:0xa000                          

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:295 errors:0 dropped:0 overruns:0 frame:0
          TX packets:295 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:20132 (20.1 KB)  TX bytes:20132 (20.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:11:f0:f1
          inet6 addr: fe80::211:50ff:fe11:f0f1/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)
          Interrupt:18 Memory:fddfc000-fddfe000

carl@carl:~$

---

### Post by dondiego2 on 2009-12-27
Now I see on the bar on the bottom it shows a wireless connection and when I click on it, it says that it is "Activating".  When I hover over it with the mouse it says "preparing to connect"

Carl

---

### Post by dondiego2 on 2009-12-27
When I hover over the wireless icon on the bottom it says configuring interface.

Now it says "Waiting for Authorization"


Carl

---

### Post by dondiego2 on 2009-12-27
OK - I went into my router and disabled encryption.  I then created anew wireless connection without the encryption and I'm in!

Except now I have to figure out how to get in with encryption.  The WPA password is in all caps which is what I use on the windows laptop I have and a mac pro laptop that my son has and it works.  But I could not get it to work with Kubuntu.  Do I need to enter it differently?

Carl

---

### Post by chewearn on 2009-12-27
I am not aware of any difference in the password entry.  It could be a bug.

Which Kubuntu version are you running?

---

### Post by dondiego2 on 2009-12-27
I am running version 9.10.

BTW - I am sending this over wireless that took me three days to figure out so I am extremely happy!  I am upstairs away from the router and it is still connected at  58% which is tons better than Windows XP would do for some reason.

Carl

---

### Post by chewearn on 2009-12-27
So, you have succeeded in connecting now?  Is this on open network?

I'm not able to be more helpful since I am not running both Kubuntu and 9.10.  Some Googling turned up this bug (which is supposed to be fix released):

[https://bugs.launchpad.net/ubuntu/+source/plasma-widget-network-manager/+bug/392593](https://bugs.launchpad.net/ubuntu/+source/plasma-widget-network-manager/+bug/392593)

Another bug which might be related:
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/446394](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/446394)

Perhaps, you could try different secure connections (WEP, WPA, WPA2), and see what work and what doesn't.  Also, apparently having hidden SSID is known to cause problem before.

Another person reported having to delete all manual configuration first, then the auto-detection finally work.

---

### Post by dondiego2 on 2009-12-27
Thanks a lot for your help.  I think I'll just leave it open for now.

Carl

---

