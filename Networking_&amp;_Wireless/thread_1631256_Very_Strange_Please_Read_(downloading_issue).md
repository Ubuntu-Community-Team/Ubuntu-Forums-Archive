---
title: "Very Strange Please Read (downloading issue)"
date: 2010-11-26
forum: Networking &amp; Wireless
---

### Post by slixz85 on 2010-11-26
Hi, I am having a problem when I download anything from firefox or google chrome, I have also installed some extensions for ff and gc for download accelerator and/or management. tried alot of em uninstalled all now, made no difference.

i use wifi my downloads start excellent and peak at over a couple mb/sec but soon in about 1-2 minutes from progress starting the speed goes clear down to like a 33.6k modem haha and even been lower like 7k but 30 on avg, soon after they just sit there like idle. probably equal in the timing for both firefox and google

? any help greatly appreciated. IPv6 settings are ignored and off

---

### Post by igoddard on 2010-11-28
Is your ISP choking you?

---

### Post by uncaspi on 2010-11-28
or even been hacked or got a worm? Stay connected and shut down all applications running and issue sudo tcpdump -i wlan0
Replace wlan0 with your interface card.
If you now monitor heavy traffic through your card you've been hacked or got a worm.

---

### Post by slixz85 on 2010-11-28
> **uncaspi said:**
> or even been hacked or got a worm? Stay connected and shut down all applications running and issue sudo tcpdump -i wlan0
Replace wlan0 with your interface card.
If you now monitor heavy traffic through your card you've been hacked or got a worm.

sace@ace-Inspiron-1011:~$ sudo tcpdump -i eth0
[sudo] password for ace: 
tcpdump: WARNING: eth0: no IPv4 address assigned
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes



i think eth0 is what my wifi connection is. and also should i use -v or -vv  and how would that command look? i know how to type in terminal of course just not how everything strings together

---

### Post by uncaspi on 2010-11-28
no just type sudo tcpdump -i eth0
and wait a few seconds to see lines containing in arpa and several ip addresses and domains displayed.
If there is nothing there is nothing to worry about.

---

### Post by slixz85 on 2010-11-28
> **uncaspi said:**
> no just type sudo tcpdump -i eth0
and wait a few seconds to see lines containing in arpa and several ip addresses and domains displayed.
If there is nothing there is nothing to worry about.


did this but same message as above when i typed it

---

### Post by uncaspi on 2010-11-28
There is no traffic through eth0. Sure this is your wifi card. Check with sudo ifconfig

---

### Post by slixz85 on 2010-11-29
lmao had to post that. it was eth1 actually and when no apps or ibrowser windows open it shows nothing but when i open one google chrome page it will show stuff and ips keep transmitting something.
unless this is something an internet browser does but i am sitting idle on this page and not consistently but every few minutes a few ips fly by but so new to this dont know which would be mine so aint postin it for no hackers haha.
and also if i switch websites it will show a ton of them flying by but i figured that is expected obviously.

---

### Post by uncaspi on 2010-11-29
You will see traffic through your card when you browse internet. Thats normal.

---

