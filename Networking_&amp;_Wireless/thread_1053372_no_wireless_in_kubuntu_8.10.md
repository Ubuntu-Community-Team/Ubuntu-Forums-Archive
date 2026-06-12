---
title: "no wireless in kubuntu 8.10"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by hkb on 2009-01-28
I have just switched from ubuntu to kubuntu and everything is working pretty fine except for the wireless network. I can't see any wireless networks (and i know that there are at least 10 available though password protected) and if i manually set up for my own wireless router i can se it but wont connect to it. 

What can the problem bee? There were no problems in ubuntu (i mean in GNOME).

---

### Post by Josh_Lapointe on 2009-01-28
Probably cause of the fact that your drivers hasn't been recognized. Do you know what your Wireless card is, and do you know if you have proper drivers installed?

go into terminal and type in 
lspci -n

and post.

---

### Post by hkb on 2009-01-28
the output from lspci -n is:

[FONT="Courier New"]00:00.0 0600: 8086:2590 (rev 04)
00:02.0 0300: 8086:2592 (rev 04)
00:02.1 0380: 8086:2792 (rev 04)
00:1b.0 0403: 8086:2668 (rev 04)
00:1c.0 0604: 8086:2660 (rev 04)
00:1c.2 0604: 8086:2664 (rev 04)
00:1d.0 0c03: 8086:2658 (rev 04)
00:1d.1 0c03: 8086:2659 (rev 04)
00:1d.2 0c03: 8086:265a (rev 04)
00:1d.3 0c03: 8086:265b (rev 04)
00:1d.7 0c03: 8086:265c (rev 04)
00:1e.0 0604: 8086:2448 (rev d4)
00:1f.0 0601: 8086:2641 (rev 04)
00:1f.1 0101: 8086:266f (rev 04)
00:1f.2 0101: 8086:2653 (rev 04)
00:1f.3 0c05: 8086:266a (rev 04)
02:00.0 0200: 11ab:4362 (rev 19)
06:00.0 0607: 104c:8031
06:00.2 0c00: 104c:8032
06:00.3 0180: 104c:8033
06:00.4 0805: 104c:8034
06:02.0 0280: 8086:4220 (rev 05)[/FONT]

---

### Post by Josh_Lapointe on 2009-01-28
Pardon. I'm still kinda newbish myself, its actually lspci I do believe that I was looking more into sorry, it'll list all the PCI devices on your system, and the drivers corespondng with them. (Please mind my typos) Also, did you try upgrading to the latest updates?

---

### Post by hkb on 2009-01-28
No problem.

Yes i always keep my systems updated. There has never been a problem under GNOME. Its only under KDE (4.1 and 4.2) that it dont find any wireless networks.

If it helps then i have a computer like this [http://asia.cnet.com/reviews/notebooks/0,39050488,39095227p,00.htm](http://asia.cnet.com/reviews/notebooks/0,39050488,39095227p,00.htm) but with 1GB RAM.

---

### Post by hkb on 2009-01-28
the wierd thing is that if i run 'iwlist eth1 scanning' i can see al the networks. But they dont show up in the manager.

---

### Post by hkb on 2009-01-28
installed gnome network manager and everything works perfect now

---

### Post by thor187 on 2010-02-16
I am having the same problem, where/how did you install the gnome network manager?

---

