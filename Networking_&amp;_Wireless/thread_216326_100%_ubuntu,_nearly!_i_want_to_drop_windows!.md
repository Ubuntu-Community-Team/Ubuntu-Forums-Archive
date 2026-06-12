---
title: "100% ubuntu, nearly! i want to drop windows!"
date: 2006-07-15
forum: Networking &amp; Wireless
---

### Post by thefamousnomo on 2006-07-15
hello people

win2000pro collapsed on me, completely! used a small live cd to backup important stuff onto dvd, and want to go 100% ubuntu, im sick of windows general poorness!

so, im booting the cd, everything seems great, but i cant get my wireless to work! this is the balance-point that will sway what i install on my machine.

so, the details are

6.06 detects my wireless dongle (a d-link dwl-g122)
i am able to enable the interface
i am able to insert my essid, wep key and ip requirements
whenever i try to activate the connection everything freezes

i have also tried using the noapic nolapic boot parameters with no joy!

any ideas please? im desperate to go 100% ubuntu!

thanx

---

### Post by wieman01 on 2006-07-15
Hi, 

I had the same problem before. I remember that this was a problem with the current version of "ndiswrapper" that comes with Dapper Drake. In my case I had to get the latest version from another source and compile it manually.

This resolved my problem and the system hasn't had any issues ever since.

---

### Post by thefamousnomo on 2006-07-16
hello wieman01

i have tried this before with breezy but could not get the ndis source to compile. can you please break down the steps please as im desperate to drop windows!

thanks in advance

---

### Post by jISh on 2006-07-16
Hmm, you may have missed some steps. Check your process over in my guide, maybe it can help you.

[http://www.ubuntuforums.org/showthread.php?t=209315](http://www.ubuntuforums.org/showthread.php?t=209315)

---

### Post by thefamousnomo on 2006-07-17
> **jISh said:**
> Hmm, you may have missed some steps. Check your process over in my guide, maybe it can help you.

[http://www.ubuntuforums.org/showthread.php?t=209315](http://www.ubuntuforums.org/showthread.php?t=209315)

hello people

i apologise, i misunderstood the initial reply, i though that i was going to have to install the latest version of ndiswrapper from source. if it is just that i need to use the version of ndiswrapper that comes with 6.06 to update drivers i should be able to muddle through. thanx for the guide link, ill get on it asap.

thanx

---

### Post by wieman01 on 2006-07-17
Perhaps my comment was part of the confusion... If your system continues to freeze then you will have to update. But if it works using the guide mentioned in here, just follow it and you will be fine.

However, if you continue to have problems with ndiswrapper, an update should resolve them. Good luck!

---

