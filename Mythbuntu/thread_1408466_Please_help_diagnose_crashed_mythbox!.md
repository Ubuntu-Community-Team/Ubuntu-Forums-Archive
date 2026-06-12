---
title: "Please help diagnose crashed mythbox!"
date: 2010-02-16
forum: Mythbuntu
---

### Post by itlarson on 2010-02-16
My mythbox crashed last night.  I had been having a few warning signs.  There were recordings with blank previews, which give a "recording not found" message when I tried to play them.  Also there were a few recordings which would play to a certain point then stop. Then there was the time I lost all schedule information.  Last night I tried to play one of the blank preview recordings.  It didn't play, and I was immediately kicked back to the menu.  Only now there were no recordings showing up at all.  I rebooted, and about half my recordings were missing- the older ones.  I rebooted again, and my system didn't autologin, instead giving me the graphical login screen.  Manually logging in from here didn't work either.  Here I should mention that both my home directory, and the older recordings are on sdb, and root is on sda.  I suspected sdb is going bad, but the smarctl long test passed both drives.  Should I believe smartctl?  Could it be the motherboard drive control hardware?  or even a bad sata cable?  If anyone has hints or thoughts, I would appreciate them!

---

### Post by ian dobson on 2010-02-16
Hi,

It could be a screwed up filesystem or maybe corruption in the mysql database.

What do you see in the syslog (/var/log/syslog)
 
Bootup in recovery mode and run a fsck on all your file systems.

smartctl just reads out what a hd says about itself and that is based on what the manufacturer thinks is OK. I don't really trust it but it's better than nothing.

Regards
Ian Dobson

---

### Post by itlarson on 2010-02-16
Thanks for the reply.  I will try that this evening.  I forgot to mention that I saw some xfs errors on logout, and in one of the logs.

---

### Post by itlarson on 2010-02-16
Now I'm really lost.  Turns out my home IS on the newer (sda, boot) drive, I forgot I moved it when I upgraded to .22.  So now I have no idea why I can't log in as my user.  fsck reported nothing for my home or root drives.  I can mount them from a rescue CD.  A few quick questions: 
-where is the database kept?
-Why is my root directory (10g) totally full?  /var is over 6g.
 
I will check the logs after Lost.  Watching live tv sucks!

---

### Post by itlarson on 2010-02-16
Well, it's working again.  All I had to do was delete /var/log/messages.1 -which was over 1g.  One of my two xfs storage partitions was throwing an error, which would generate a traceback.  This would add dozens of lines to the logs every second when myth was active.  I had previously run xfs_repair, so freeing up the space in root was all it took.  I didn't know a full root partition could cause problems like this, but I should of suspected it would.  The xfs error message doesn't seem to be showing up anymore.

---

### Post by ian dobson on 2010-02-17
Hi,

Good to hear it's working again. Everytime I hear about fs problems it's almost always xfs.

Regards
Ian Dobson

---

