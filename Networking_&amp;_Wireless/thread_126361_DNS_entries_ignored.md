---
title: "DNS entries ignored"
date: 2006-02-06
forum: Networking &amp; Wireless
---

### Post by SteveGreenhouse on 2006-02-06
Hi there

My name is Steve, and I'm a recovering Windows user.  I've been clean now for about 5 days.

I've installed Ubuntu and am so totally new to this that the install CD hasn't stopped spinning yet.

I have 2 machines, one running XP which my wife uses (she believes Linux is too steep a learning curve), and mine.  The situation is this:

Hers is directly connected to our ISP via a USB modem.  Don't laugh, it works.  My machine is connected to hers via a cross-over cable.  Our internet connection seems to be shared right out of the box, except for adding DNS entries.  I'm trying to add our ISP, but it keeps being ignored in favor of 192.168.0.1.  I know I'm probably supposed to do this as either Root, or through sudo, but have no clue how to do it from the terminal.  I'm too GUI oriented and I blame Micro$oft.

Help??

Steve

---

### Post by SteveGreenhouse on 2006-02-06
Found the answer, thanks to the nice folks in this forum.

sudo nano /etc/resolv.conf  and add the appropriate entries.

Simple when you know how.

---

