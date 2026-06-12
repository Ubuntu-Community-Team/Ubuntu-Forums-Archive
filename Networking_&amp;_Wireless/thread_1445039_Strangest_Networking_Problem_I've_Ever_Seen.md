---
title: "Strangest Networking Problem I've Ever Seen"
date: 2010-04-02
forum: Networking &amp; Wireless
---

### Post by meekrab on 2010-04-02
So I'm posting this on Friday at about 7:46 GMT.  Around 1:00 GMT Wednesday night, Ubuntu 9.10 started giving me terrible ping times to everywhere on the internet.  And when I say terrible pings, I don't mean 150 ms, I mean 5000ms+.  I initially wrote it off as Comcast network trouble, opened up a book, and read until bedtime, because lets face it, Comcast is an "amazing" ISP.  However when I woke up and verified the problem still existed and rebooted into Windows XP to find that the internet works fine, and its not a Comcast problem at all.

I do recall there were two small (<50 kB) updates I applied Wednesday, but I have no recollection of what they were.  The really odd thing is that when I run programs through Wine, they seem to be able to connect to the internet just fine, with my normal <50 ms pings to most things in the USA.

I'm posting this from Windows, since even getting to this forum in Ubuntu is currently almost impossible (it literally takes 30 seconds to a minute to open google.com, opening the front page of the forums takes ages), so I probably won't be able to post any iwconfig or whatever results unless the suggested changes fix whatever my issue is.  Anyone have any ideas what the problem could be?  

Relevant hardware is:
D-Link WDA2320
Intel E4400 @ 2.0
Gigabyte GA-P35-DS3L

---

### Post by Iowan on 2010-04-02
[This]("http://ubuntuforums.org/showthread.php?t=1376506") thread goes through checking MTU settings. That may not be the problem, but shouldn't hurt to try...

---

### Post by Skaperen on 2010-04-02
I encountered a problem like that with Comcast several days ago (not the day you did).  With that problem was a very high (more than 40%, sometimes 98%) packet loss rate (based on pinging my colo server outside of their network).  I dabbled around with MTU settings and found a hard boundary at 424 bytes.  At 424, the losses and delays disappeared. Above that and they were there.  It was not a gradual increase (as I typically see on noisy connections).  The problem persisted for about 16 hours and then just disappeared (and then I went back to normal MTU 1500).

I don't know why it worked in Windows for you.  I didn't have Windows handy to give it a try and didn't even think of trying it.

---

### Post by meekrab on 2010-04-02
None of that MTU stuff changed anything, but I punted and reset the wireless router just for fun and am now posting this from a working Ubuntu with full speed internet.  Have no idea why it would work fine for a windows computer but not for one running Linux, but there you have it.

---

