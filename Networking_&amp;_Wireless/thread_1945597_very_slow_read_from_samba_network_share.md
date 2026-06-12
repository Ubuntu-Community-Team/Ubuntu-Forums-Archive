---
title: "very slow read from samba network share"
date: 2012-03-23
forum: Networking &amp; Wireless
---

### Post by ashpuk on 2012-03-23
Hi Guys,

on a network with about 30 computers running a mixture of XP & OSX.

My computer runs Ubuntu 11.10 and I am having problems reading from our shared (smb) XP folder on another computer.

I can access the folders ok and can write fast enough (1MB+ a sec)

However when it comes to downloading from this computer its really slow 10-15KB/s.

Seems odd that I can upload fine but really slow download?

Let me know what config I need to post.

Thanks

---

### Post by ChrisLancs on 2012-03-23
Not sure if this will be helpful to you but its possible that the network is very busy, if its normally of good speed then i would be thinking this to be the case.

---

### Post by 2F4U on 2012-03-23
Do you know if you are the only one with an upload problem? If not, it may be, as ChrisLancs suggested, a general network problem.

---

### Post by ashpuk on 2012-03-23
Hi guys, thanks for reply. 

Unfortunately it seems to be only me with the problem. Other computers (os x & xp) work fine which leads me to believe its Ubuntu or hardware problem. I think it's unlikely to be hardware however as everything else on the computer works very well (such as Internet browsing and copying of files etc)

Is there any config or diagnostics I can use to see what's causing the problem? 

Cheers

---

### Post by ashpuk on 2012-03-26
any ideas guys?

---

### Post by ashpuk on 2012-03-26
ok guys, i figured it out!

it was because i am using the r8168 chipset and needed to use the older driver.

Followed these instructions to fix:

[http://ubuntuforums.org/showthread.php?t=1661489](http://ubuntuforums.org/showthread.php?t=1661489)

---

