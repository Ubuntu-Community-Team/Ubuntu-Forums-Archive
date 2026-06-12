---
title: "xserver issues"
date: 2006-08-22
forum: Multimedia &amp; Video
---

### Post by The Pinny Parlour on 2006-08-22
Hi all,

Recent crappy xserver updates have ruined my X.  It won't start no matter what I throw at in editing the xorg.conf

If anyone has some bright ideas that will help me the get thing going, I'm all ears.

Thank You,

---

### Post by thumper on 2006-08-22
Read [previous post](http://ubuntuforums.org/showthread.php?t=241174)

---

### Post by tseliot on 2006-08-22
There's no need to start more than a thread for this.

---

### Post by Dale61 on 2006-08-22
Pinny, after 8 hours of frustration and disappointment, I followed the instructions as posted by tseliot in the thread above, and it worked for me first time.

---

### Post by The Pinny Parlour on 2006-08-22
Thank you for your replies.  I have applied what is recommended and it did successfully downgrade, but it's still screwed.  I'm ready to give up on ubuntu, it's just to much darn hard work to get anything going.  I'm really dissapointed with these latest turn of events.

---

### Post by coffeecat on 2006-08-22
> **The Pinny Parlour said:**
> I have applied what is recommended and it did successfully downgrade, but it's still screwed.  I'm ready to give up on ubuntu,

Before you give up, I notice that you tried editing your xorg.conf before posting. Perhaps you've done something there that's causing another problem - it's easily done. Have you tried running:

sudo dpkg-reconfigure xserver-xorg

to get xorg.conf back to where it should be?

Might be worth a try.

---

### Post by The Pinny Parlour on 2006-08-22
thanks mate yeah,  tried that about 15 times.

---

