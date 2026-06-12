---
title: "Ubuntu 9.10 Slow Internet"
date: 2009-10-29
forum: Networking &amp; Wireless
---

### Post by voodoo_child on 2009-10-29
I just upgraded my 9.04 installation with a clean install of 9.10

Browsing the internet is very slow. I can download at my full speed (for updates etc) but doing a search or opening a URL takes like 30 seconds before each page loads. 

Everything was perfect under 9.04

-Acer3002WTMI (laptop)
-Intel Pro Wireless (I think IPW220BG?)
-Netopia 3347W Wireless router (using OpenDNS servers)

Any suggestions?
Thanks

---

### Post by voodoo_child on 2009-10-29
Went into the ivp4 settings and changed it to Automatic (DHCP) Adresses only. Then  I put in my OpenDSN servers in the box down on the bottom. 

Seems to have worked. Evertyhing running smoothly now. Lock thread please ;)

---

### Post by grizato on 2009-10-29
Are you sure it's not Firefox 3.5?
I have heard reports that it is slower in some places.
Try chromium or Opera instead if that's the case

---

### Post by voodoo_child on 2009-10-29
No, im sure was definitely a DNS issue. Found a lot of people with same problem, thats how I found the solution. What I done definitely fixed it immediately (after a reboot) so no worries.  

Thanks.

---

### Post by sergeyss on 2009-10-30
I have this problem also.
I have set ipv4 settings like you said, but this didn't help me. Beside, my Internet was switched off after several minutes (btw Fi/Wi works not very good too). So,.. this bug, it seems, related not with web, firefox or something (but when working with firefox it is the best sample). It comes out within general gnome windows - there is some delay (uu to 5-10 seconds on my machine) takes place there and a window doesn't respond and going to be grey for awhile.

So, it seems, this problem with NVIDIA driver. 
When I switched to recommended one (not free - v185) - this problem gone at all, but I now have another problem - when watching some video it shows to me inverse vision of everything like in reversed image (in old photo).

So, If someone know how to fix this, I would be glad to hear.
But now,... I just switching from one driver to another one - when working with comp - like browsing web, and when having fun - like watching video.

---

### Post by voodoo_child on 2009-10-30
Better to start your own thread mate. 

This one is marked 'solved' so probably nobody is going to read it, so you won't get help easily.

---

### Post by antharr on 2009-10-30
Just wanted to say that changing to OpenDns servers worked like a charm.

---

### Post by rigg-a-mortice on 2009-10-30
HI,
I have same problem but do not know where to alter ivp4 settings, can someone tell me please?

Thanks

---

### Post by antharr on 2009-10-30
Create a free account here:

[https://store.opendns.com/get/basic]("https://store.opendns.com/get/basic")

After you create the account there is a tutorial for setting this up in Ubuntu.

---

### Post by tanke86 on 2009-10-30
I had the same problem, OpenDNS worked for me

---

### Post by sagasha on 2009-11-02
Open Firefox and put about:config in address bar and hit enter.

In filter type network.dns.disableIPv6 and hit enter:

double click on line and it will change to:
network.dns.disableIPv6;true

---

### Post by VagabundoXXI on 2009-11-19
> **voodoo_child said:**
> Went into the ivp4 settings and changed it to Automatic (DHCP) Adresses only. Then  I put in my OpenDSN servers in the box down on the bottom. 

Seems to have worked. Evertyhing running smoothly now. Lock thread please ;)

Yes, It works... But samba crashes... Any solution?

---

### Post by Digikid on 2009-11-21
Worked for me.  Thanks OpenDNS

---

### Post by Freckweb on 2009-11-26
Another solution

I performed a clean install of 9.10 and ended up with a very slow internet connection. Everything was slow, not just Firefox.

Following extensive reading of the various reports on the forums, I came to the conclusion that my Dynamode router was the problem.

The router normally returns its own address as the DNS server. I could not find any method of changing this to use OpenDNS however there is a check box [Assign ISPDNS] on the Lan Group Configuration page which results in the router passing my ISP DNS addresses to the clients. Checking this box fixed the problem and my Internet is now working at full speed.

---

