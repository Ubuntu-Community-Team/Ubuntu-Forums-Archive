---
title: "WMP300N (BroadCom BCM43XG) Not sensed"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by lordbob75 on 2009-02-15
Hello all, I am new to linux and was hoping to gain some knowledge and usage out of Ubuntu or Fedora.  Unfortunately Fedora and Ubuntu are unable to sense my wireless card, and that is the biggest problem stopping me from using Linux over Windows.

The people on the Fedora forum could not get it working, can anyone here help me out?

~Lordbob

---

### Post by superprash2003 on 2009-02-15
go to the terminal and type **lshw -C network** and post output here

---

### Post by lordbob75 on 2009-02-15
Hello Superprash, thanks for the reply.

Here is the out put and a screenshot (hope that is ok)
[IMG]http://i43.tinypic.com/2a7vhck.jpg[/IMG]

It does seem to sense the card, but I cant get it to work.  When you click on network up in the right corner, it has a greyed out Wired Connection, then VPN setup.

~Lordbob

EDIT:  Hopefully fixed picture

---

### Post by lordbob75 on 2009-02-15
bump?

It would be nice to get some help with this, as I have tinker time tomorrow instead of school.  This is a problem that has been frustrating me for about a year now... And it would be nice to get it fixed.

~Lordbob

---

### Post by superprash2003 on 2009-02-16
cant find your output!!

---

### Post by lordbob75 on 2009-02-16
What the heck does that mean?  I posted the screen shot of what appeared after I typed in the command you gave me...

~Lordbob

---

### Post by Ayuthia on 2009-02-16
If you look at your previous posts in this thread, there is no screenshot.  Can you try and see if you can post it again?

---

### Post by sailthesea on 2009-02-16
Are you using a Live CD by any chance?

---

### Post by lordbob75 on 2009-02-16
No screenshot?  I can see it.... Do I need to put it as an attachtment?

And yes, I have had this problem with both the LiveCD, Live USB, and installing it on my HDD.

~Lordbob

---

### Post by superprash2003 on 2009-02-17
well.. it hasnt uploaded properly.. use tinypic to upload and post the link here..

---

### Post by lordbob75 on 2009-02-17
Ok I think I fixed it above, but here it is again.
[IMG]http://i43.tinypic.com/2a7vhck.jpg[/IMG]

Let me know if you can see it.  If not, here is the link to the picture.
[lshw -C network output]("http://www.vistax64.com/members/lordbob75-albums-stuff-picture424-ubuntu.jpg")

~Lordbob

---

### Post by superprash2003 on 2009-02-18
here.. hope this helps [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) .. even though its for feisty it should work!!also post output of **iwconfig**

---

