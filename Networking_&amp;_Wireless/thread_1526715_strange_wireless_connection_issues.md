---
title: "strange wireless connection issues"
date: 2010-07-08
forum: Networking &amp; Wireless
---

### Post by JLahm on 2010-07-08
I have a Ubuntu machine that I use as a CUPS server. It connects to my home network using a wireless RT61-based PCI card. I have had issues with the connection ever since I upgraded to 9.10 desktop (it is running 10.04 now). It periodically will not allow inbound connections, although while in this state I can still use Firefox on the machine to browse the Internet.

To see how often this occurs, I wrote a simple PHP script that I ran on another Ubuntu machine I have that is connected by cable to my home network. It was **always** able to access the Ubuntu wireless machine. I was also always able to ping the wireless machine from the other Ubuntu server. So, I ran the same PHP script from my XP machine. It did show that it was unable to connect to the wireless Ubuntu machine at some times (although the other Ubuntu machine always could get in). When the XP machine could not get in, I was also unable to get in using my iPhone (as a further test).

I logged the output and a strange pattern appears: the wireless Ubuntu machine will be unavailable at a consistent time (say 14 minutes after the hour), be unavailable for from 45 minutes to 55 minutes, then be available for the next hour. So, it will basically go offline every 2 hours for about 50 minutes - like clockwork. I have checked my cron entries and nothing jumps out. There are no errors in the Apache logs or the syslog files.

Any ideas of where to look would be greatly appreciated! 

Jim

---

### Post by JLahm on 2010-07-09
Polite little bump... Any ideas?

---

