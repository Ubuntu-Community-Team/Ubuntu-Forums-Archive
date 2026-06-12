---
title: "Ubuntu 9.04 networking drops after large file transfer"
date: 2009-08-09
forum: Networking &amp; Wireless
---

### Post by joker535 on 2009-08-09
I have a Dell 1510 laptop and I loaded 8.10 on it when I got it earlier this year. I had no issues with it. I regularly download large media files (650-800M) and transfer them to my NAS (freenas). I have been doing this with no issue until I chose to do the "upgrade" to 9.04 last month. Now I can transfer 1 file with no issue but when I go to transfer the next file, all networking wired or wireless stops working. I usually do the transfers via gigabit wired. I am dual boot with windows and I tried it on XP and it works fine there which tells me my laptop hardware, NAS, and network hardware is Ok..

Any idea how to fix this without having to re-load the machine with 8.10?

Thanks

Bob

---

### Post by ryall on 2009-09-28
I'm experiencing the exact same problem, during a large transfer networking drops and won't come back up until a reboot. The system doesn't seem to notice that it's down (Network Manager Applet still green), but even pings get nowhere. 

I've tried ```
sudo /etc/init.d/networking restart
``` but still no luck.  


Hopefully someone can shed some light on this.

---

### Post by ryall on 2009-09-28
Actually, I wouldn't hold my breath. Looks like this problem has been around for [two years]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/60764") and still isn't fixed. 

Anyway, I tried [this suggested fix]("https://bugs.launchpad.net/ubuntu/+bug/296162/comments/10"):

```
sudo ethtool -K eth0 rx off tx off
```

...and now my whole system freezes when I do a large file transfer.


TBH i'm pretty much over this. I really like linux, it has some great features and in a consolified server environment it works brilliantly. But I've just realised that as a desktop OS, I spend about 80% of my time just trying to get **** to work. And I'm not talking about state-of-the-art super-alpha concepts here. Just day-to-day stuff like copying files between computers, or checking my email without the mouse freezing or the system randomly locking up. A desktop OS just shouldn't have these kinds of continual problems.

---

