---
title: "using aircrack-ng [fixed channel mon1: -1]"
date: 2011-02-02
forum: Networking &amp; Wireless
---

### Post by dd1linux on 2011-02-02
I am trying to audit my wireless router due to someone in the neighbourhood hacking it, and have run into a few problems.  When I run airodump-ng, everything works fine.  However, when I try to get the .csv file and run 
"airodump-ng -w test --channel 6 --bssid ---------- mon1"
(obviously with my the mac address of my AP instead of x's) I get this:

CH  6 ][ Elapsed: 4 s ][ 2011-02-02 17:48 ][ fixed channel mon1: -1 ]

The problem is the [ fixed channel mon1: -1 ], because when I go to the next step to try to force a handshake, it says:

18:00:34 Waiting for beacon frame (BSSID:-----------) on channel -1
18:00:34 mon1 is on channel -1, but the AP uses channel 6

I have scoured the Internet for answers, and have seen several people with the same problem, but no solutions that work for me. I think it may have something to do with the driver. I really do apologise if this has been answered properly several times, but none of the solutions seem to be working in my case. Please let me know if you need any additional system information.

---

### Post by dd1linux on 2011-02-02
I dont know how to delete this one, sorry.

---

### Post by dd1linux on 2011-02-04
fixed using directions here:

[http://ubuntuforums.org/showthread.php?t=1598930](http://ubuntuforums.org/showthread.php?t=1598930)

---

