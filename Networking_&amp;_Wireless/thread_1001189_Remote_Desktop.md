---
title: "Remote Desktop"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by Patricrawley on 2008-12-03
I am trying to connect to my grandmother's new iMac from my home computer so I can do a couple things for her. I have her IP address and her username, she doesn't have a password. What do I do? I could easily find the computer name out. I just need a few hints and nudges in the right direction because I am next to clueless when it comes to networking.

---

### Post by AmericanSkin on 2008-12-04
You will need to route incoming traffic on her router to her PC. You'll need to determine what remote desktop program you are using and what port the program is using.

I've never done this on a Linksys or home router, but on a PIX you would allow traffic from your external IP address on port 3389 and forward traffic that is using port 3389 to her internal IP.

---

### Post by Patricrawley on 2008-12-05
I know absolutely nothing when it comes to this kind of thing so I kind of need a step-by-step tutorial on how to remote desktop from 8.10 ubuntu to the newest iMac's I don't know the OS, 10.6 maybe?

---

### Post by Patricrawley on 2008-12-06
bump

---

