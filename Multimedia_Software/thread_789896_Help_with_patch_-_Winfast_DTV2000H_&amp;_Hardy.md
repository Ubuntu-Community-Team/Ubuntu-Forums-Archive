---
title: "Help with patch - Winfast DTV2000H &amp; Hardy"
date: 2008-05-10
forum: Multimedia Software
---

### Post by jordanius on 2008-05-10
Hi Guys,

I notice there seems to have been a mountain of issues with 8.04 and connexant tuner cards. Despite searching the forums endlessly I hadn't seen anything in the way of a pemanent fix until I found this.. 

[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/211652](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/211652)

Can someone please let me know how I go about applying this?. I've googled around for a how to but there seems to be no hard and fast rule on how to proceed. 

Any suggestions muchly appreciated!

---

### Post by Crusty Juggler on 2008-05-11
I'm following this thread.  I bought this card solely because I thought it was supported out of the box.  Oops.  Mythbuntu has been a major PITA to get going, but I am determined.

---

### Post by Crusty Juggler on 2008-05-11
I was able to get my system to recognise the card by adding
```
 options cx88xx card=51 
```

to /etc/modprobe.d/options and then rebooting.

---

