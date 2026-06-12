---
title: "No Wired Connection, wireless works just fine"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by goldsteinadj on 2008-12-21
Ok, so I got sold on ubuntu when I found how easy it was to use, stable and full of free stuff (I love openoffice!). However, I am definately still a newb at linux in general. So I had 8.04 on my Inspiron 8600 and everything seemed dandy. I recently upgraded to 8.10 since I was having trouble with one of my video game installs and figured the upgrade might help. Surprisingly it did. However, I seemed to have lost my wired connection in the process. I am making due with the wireless, but since I do download media and play video games time to time, I would really like to get the ethernet back up and running. I tried googling the problem to see if I could find someone with the same problem, but it seems like everyone else has the opposite problem (no wireless). Any help would be appreciated.

---

### Post by SeriyVolk on 2008-12-21
Actually a lot of people are having this problem. This thread seems to solve it for many of them: [http://ubuntuforums.org/showthread.php?t=963335](http://ubuntuforums.org/showthread.php?t=963335)

Basically you have to uninstall NetworkManager and edit your /etc/network/interfaces file and possibly your resolv.conf file. Hasn't fixed it for me yet, but hopefully it will help you.

---

### Post by goldsteinadj on 2008-12-21
awesome! thanks for the help

---

