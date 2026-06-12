---
title: "Can't connect to belkin n1 router"
date: 2010-06-23
forum: Networking &amp; Wireless
---

### Post by Mariane on 2010-06-23
I have a new belkin N1 router which I tested in somebody else's flat. It worked fine. 

When I got home I reset it by pushing a paperclip in the hole for 10+ seconds to erase this flat's internet connection settings (username and password and stuff). 

After this I plugged it the computer and tried to connect to it (wired connection) using 192.168.2.1 (this is correct for that router, it is not 192.168.0.1). But the browser says it is offline and cannot connect. The lights of the router cycle, the "modem router" light blinks continuously and the others briefly come on and go off again, every few seconds. 

I tried resetting it again, several times, leaving it off for a few hours, leaving it on for a few hours, etc. 

All suggestions welcome. 

Mariane

---

### Post by ghamilton on 2010-06-23
Have a look on the following page:  (at [LinuxHomeNetworking]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch04_:_Simple_Network_Troubleshooting")) and follow the steps there to cover the basic interface and connection issues.

There's a lot of stuff on that page.

In particular, the arp command (e.g. arp -a) should tell you what's sitting at the other end of your ethernet cable.

When I run that command at home, I get 
```
? (192.168.1.1) at 00:1F:E6:25:9A:A4 [ether] on eth0
```
. . . which, happily, is my gateway router.

When I run that command at work, I get 
```
qatest-lt.workbox.local (10.10.50.106) at 00:21:85:1b:c5:62 [ether] on eth2
? (10.10.40.1) at 00:25:0f:9a:8b:45 [ether] on eth2
```
. . . one of which is the QA server, and the other is the gateway.

When you run it where you are, you should at least get the router.

Anyway, that page is a good place to start.

****

---

### Post by Mariane on 2010-06-23
Nothing. 

When I do "arp - a" with the old router I get:
? (192.168.0.1) at 00:0f:b5:7f:94:00 [ether] on eth1

So the command is functioning. But with the Belkin N1 
it just returns without outputing anything. The plug 
for wired connection has a little light, which comes 
on when I plug the cable in, so normally the computer 
should know it is connected to something, shouldn't it? 
The light on the router plug also comes on when I plug 
in the cable. Nothing is wrong with the cable itself 
because it is the same one I use to connect to the old 
router and to the new one. 

Thank you for the link, I'll read this page tomorrow. 

Mariane

---

