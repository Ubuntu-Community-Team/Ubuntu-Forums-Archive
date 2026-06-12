---
title: "ATI Drivers: Disappearing file: fglrx.ko"
date: 2006-10-01
forum: Multimedia &amp; Video
---

### Post by Aikon- on 2006-10-01
I noticed that my Dapper install had been running rather slugishly for a while, so I did some unding, and fglrxinfo showed that I was using the Mesa3D drivers. Now, I KNOW I had installed the ATI drivers according to a guide on here, so I did some looking and it turned out my xorg.conf file was broken. So, I fixed it and rebooted.

Logged in, everything seemed to be working great, but fglrxinfo still showed me as using the Mesa drivers. After alot more searching, I realized that when my system tried to start X.org, it was unable to find the file /lib/modules/2.6.15-27-386/volatile/fglrx.ko so I did a search on my computer and found the file under 2.6.15-26-386. I figured somehow it got missed along the way, so I copied it over to the expected folder, started X.org, and everything was running beautifully. Responsiveness was crisp and sharp, and fglrxinfo did indeed show me using ATI drivers. Awesome.

Except that now its a week and a half later, and I just rebooted for the first time since then.. and the fglrx.ko file was gone again. I had to re-copy it.

What's causing this file to keep disappearing, some cleanup script? How can I make Ubuntu understand that the fglrx.ko file is SUPPOSED to be there? Suggestions?

Thanks in advance for any help,
-Aikon

---

### Post by Aikon- on 2006-10-02
Timed bump...... NOW!

---

### Post by Aikon- on 2006-10-03
Bump =(

---

### Post by Aikon- on 2006-10-03
Well, I have a solution.... but I'm loathe to call it that ](*,) 

I made a script that copies the file from /lib/modules/2.6.15-26-386/misc/fglrx.ko to /lib/modules/2.6.15-27-386/volatile/fglrx.ko and set it to run at boot-time using update-rc.d.

This is possibly the most disgusting hack I've ever come up with for getting something to work, so if anyone has any other ideas, I'm all ears!!!


-Aikon

---

### Post by andrikos on 2006-10-31
I think the best solution is to put the fglrx.ko module in the misc folder, delete it from the volatile one and then run sudo depmod -a.
This way, the kernel will look in the misc folder instead of the volatile one and you will be ok.

---

### Post by Aikon- on 2006-11-01
> **andrikos said:**
> I think the best solution is to put the fglrx.ko module in the misc folder, delete it from the volatile one and then run sudo depmod -a.
This way, the kernel will look in the misc folder instead of the volatile one and you will be ok.

Thanks a bunch! Worked like a charm ^_^

---

