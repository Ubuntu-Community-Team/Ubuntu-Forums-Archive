---
title: "web server question- port forwardin"
date: 2009-03-16
forum: Networking &amp; Wireless
---

### Post by Lakeside5 on 2009-03-16
Starting over..again..(lost my hard drive, Hardy Heron re-installed..again lol) I seem to forget stuff,  and now I'm trying to enter the http info  into my Wireless Linksys 160N router.  I acquired a static ip from  DynDNS, and entered this info into my router, so that part is done.  Now, when I want to forward to port 80,  I chose 'sigle port forwardin'  picked 'http' form a drop down choice,  put '80' in start, and '80' in end,  and  192.168.1.100 as the ip address to forward it to (this was listed as the 'intet' address, under 'wlan' when I did an 'ifconfig' in terminal.  I am assuming, that as, I got a free dns service from DynDNS, then it directs traffic to my router(192.168.1.1) keeping things static, as I chose DNS (entering info from my  DNS acount)? That part seems to go fine (says static ip updated successfully)
I can't seem to forward ports though. I chose 'single port forwarding' , and picked 'http' from a drop down box, it wouldn't let me  put in 80, 80
in two boxes (I assumed they are put in by default when I picked http) but I tried to type in '100' after the 192.168.1._ (port forwarded to), and I got this error: You can't use the Router's IP, network or broadcast address...doing 'ifconfig'  in terminal shows me my  wlan ip is 192.168.1.100,  (192.168.1.1 is my router).  How am I supposed to set up http, because right now I can't seem to connect to my Hardy Heron server to actually serve my website.

---

### Post by Iowan on 2009-03-17
192.168.1.100 is the servers address? 
... or did it somehow get assigned to the router (which now thinks you're trying to port forward to it (the router)?

---

### Post by Lakeside5 on 2009-03-18
192.168.1.1 is my router,  If I type that in the address bar, it brings up my Linksys wireless router settings page, where I'm trying to   setup port  forwarding.  I misunderstood something I guess.  I want static IP, to be accessed by the same name, not a changing ip  (ie  Webster.mylinux.com) so I got a free nameserver, from DynDNS.  I thought DynDNS is directing traffic to my router's ip, which never changes so..I enter my router's ip?  No..well I   tried the ip I got from  'ifconfig', the  'wlan' ip: (inet address) 192.168.1.100 and I entered that in the port range, or tried to.

---

### Post by Iowan on 2009-03-20
The DynDNS (WAN) address for your router will probably (depending on your ISP) be a "standard" IP address - not a private address (192.168.X.X, 10.X.X.X, or 172.16.0.0 - 172.31.255.255) - and will most likely change. The router should forward information coming IN on this address (port 80) to your server (192.168.1.100). Your router's INTERNAL address is 192.168.1.1. One of us is probably confused about WAN vs LAN address. ;)

---

### Post by Lakeside5 on 2009-03-20
So, I am going to enter this info in my router, and show u a screenshot, if u don't mind.  thanks for clarifying, that my server would be 192.168.1.100  (and my router is 192.168.1.1)
Here is my problem, if I understand u correctly and try to do it:  [IMG][[IMG]http://img8.imageshack.us/img8/8380/portforward.th.png[/IMG]](http://img8.imageshack.us/my.php?image=portforward.png)[/IMG]

[[IMG]http://img19.imageshack.us/img19/3734/screenshot1q.th.png[/IMG]](http://img19.imageshack.us/my.php?image=screenshot1q.png)  When I try to save the settings, in the first picture,  it  doesn't save them, everything goes back to blank, except the 192.169 part, but it goes back to 1 at the end, not 100.  And in the second pic,  I chose 'static' dns, instead of dynamic, I hope that  was right.

---

