---
title: "General Networking Voodoo."
date: 2010-06-15
forum: Networking &amp; Wireless
---

### Post by M!K3_$ on 2010-06-15
Not an Ubuntu question, But definitely a networking question.

(I will describe the situation assuming you have looked at the attached network diagram)

PC1(win 7) is sharing its internet connection to the 192.168.137.0/24 network.

When pinging from PC1 to PC2(an ubuntu server actually) I get either destination net unreachable or request time-out.

It appears as though my computer is trying to find PC2 out the wrong interface. But I find this unusual because they are on the same subnet.

This wasn't a problem until yesterday.

Yesterday I fixed it by forcing the switch to renew its ARP table. This didn't work today.

Suggestions? 


thank you,
Mike

---

### Post by Iowan on 2010-06-15
I was gonna ask about results of **route -n**, but decided it's probably different on a Windows machine. My XP box uses **route print** to deliver the information.

---

### Post by M!K3_$ on 2010-06-15
When I get home I'll give you the output going both ways.

thank you.

---

### Post by M!K3_$ on 2010-06-16
weird... it works now.

*shrug*

---

