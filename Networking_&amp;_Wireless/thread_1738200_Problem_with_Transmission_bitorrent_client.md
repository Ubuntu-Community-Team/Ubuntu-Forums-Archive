---
title: "Problem with Transmission bitorrent client?"
date: 2011-04-24
forum: Networking &amp; Wireless
---

### Post by Spe3dball on 2011-04-24
I have a 20 Mbps download speed and 3 Mbps upload speed. Is Transmission bitorrent client giving me wrong information because my **maximum upload speed could be 366,21 KiB/s** but the client shows me **425 to even 500 KiB/s** when I upload? What can be the solution for this problem? (I converted the speeds in the following site: [http://web.forret.com/tools/bandwidth.asp](http://web.forret.com/tools/bandwidth.asp) )

---

### Post by DanneStrat on 2011-04-25
> **Spe3dball said:**
> I have a 20 Mbps download speed and 3 Mbps upload speed. Is Transmission bitorrent client giving me wrong information because my **maximum upload speed could be 366,21 KiB/s** but the client shows me **425 to even 500 KiB/s** when I upload? What can be the solution for this problem? (I converted the speeds in the following site: [http://web.forret.com/tools/bandwidth.asp](http://web.forret.com/tools/bandwidth.asp) )

Have you tried running a sppedtest here: 

[http://www.speedtest.net/](http://www.speedtest.net/)

If you get the same results there, you may actually get a little 

more speed than what you're paying for and you will also find

out if transmission is accurate.


Transmission shows speed in "kilobytes" or "kB" and

you internet provider give you the speed in "Megabits".

3 MB(megabits) is 384 kB(kilobytes) and even if you get

500 kB/s upload speed, that's 3,9 MB/s which is 0,9 MB over

your rated speed. If that is the case I wouln't say it's 

a bad thing!:)

Good luck.

---

### Post by Spe3dball on 2011-04-25
The solution: a bug was fixed in Transmission 2.22

**Fix 2.20 bug that sometimes showed inaccurate upload/download speeds**

ref: [https://trac.transmissionbt.com/wiki/Changes](https://trac.transmissionbt.com/wiki/Changes)

So the real solution is to upgrade. :D

---

### Post by DanneStrat on 2011-04-25
> **Spe3dball said:**
> The solution: a bug was fixed in Transmission 2.22

**Fix 2.20 bug that sometimes showed inaccurate upload/download speeds**

ref: [https://trac.transmissionbt.com/wiki/Changes](https://trac.transmissionbt.com/wiki/Changes)

So the real solution is to upgrade. :D

OK!

I'm glad you got it fixed!

---

