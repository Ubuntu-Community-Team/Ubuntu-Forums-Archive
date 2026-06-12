---
title: "kppp not finding pppd (8.10 desktop)"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by zymurgist on 2008-12-13
I've got a Sprint/Novatel U727 which worked great under 8.04.

Following the directions from Sprint (and d/l kppp and pppd) everything is fine until I notice in the 'misc' tab the 'pppd' field says 'unknown'. Sure enough .. when I try to connect, kppp talks to the modem (CONNECT) and locks up when "Starting pppd". I kill the kppp jobs, try again, and receive:

The pppd daemon died unexpectedly!
Exit status: 0

I've uninstalled/reinstalled pppd and kppp. 

Any ideas?

---

### Post by GuyK on 2008-12-31
I'd like to commiserate with you. I'm having the same type of problem. I'll hang around snd see if any help comes our way. It's frustrating. The only way I can get to the Internet is to go to a site with wireless access.

Guy K

---

### Post by rmknightstar on 2009-08-06
I had the same problem.

Turns out the when I did a which pppd nothing came up.

pppd is in the 'dip' group and is group executable but not world executable

Make sure that you are in the dip group.

---

