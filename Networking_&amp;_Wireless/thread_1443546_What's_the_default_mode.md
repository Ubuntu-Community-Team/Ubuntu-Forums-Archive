---
title: "What's the default mode"
date: 2010-03-31
forum: Networking &amp; Wireless
---

### Post by Luke771 on 2010-03-31
Just dropping the question while I try to google it up (the first couple of tries didnt give any result), I will mark it [solved] and link to the solution if I happen to find it, but in the meantime, here's the question:

Setup:
Ubuntu Server 9.10 running on an old junkware box (multipurpose server)

Client also has linux but runs mostly  Windows XP 64bit (need it for gaming) 

The problem is that I screwed up while trying to make the whole system visible to the Samba user: I  did ls -s / /home/user/sys
but when trying to access the symlink from Samba I got permission denied, so (the smart guy that I am) I did chmod a+r / -R ... and it even worked for a while.

But after some time it started giving me problems. It would take a couple of pages to describe what happens but long story short, I guess I should set the mode back to the default.

An error message told me to set /etc/sudoers to  440 so I did that (recovery mode) and now I can sudo again.

Next step would be to set the whole / back to whatever it's supposed to be. Problem is that I dunno for sure. Is that 440? Or something else? Is there a command that does "set all modes to default"?

---

### Post by Iowan on 2010-03-31
Most of the / directories on this hardy machines are 755 - /proc is 555, most links are 777 - I didn't check the subdirectories and individual files. You still have the install CD? 8-[

---

