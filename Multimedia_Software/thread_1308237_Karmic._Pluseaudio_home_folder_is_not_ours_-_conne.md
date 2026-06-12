---
title: "Karmic. Pluseaudio home folder is not ours - connection refused"
date: 2009-10-31
forum: Multimedia Software
---

### Post by shof2k on 2009-10-31
Hi,
Running a 2 day old Karmic install when all my sound went.

Installing paman showed the 'Connection refused' message and the message * /home/xxxxxx is not ours *

Reading around, I found that pulseaudio is run on a user session basis and needs access to the /home directory.  I check nautilus and it seems my userid permissions were changed. 

Basically changed my home folder permissions back to my userid and group id and all worked after a reboot.

---

### Post by Rodrigues on 2009-12-08
I had the exactly same problem. Lost hours going around on the forums, trying every guide to solve pulseaudio problems, but nothing worked until I read your post.
For some reason the owner and the group settings of my home folder were wrong. Just changed it back to the correct setting, rebooted and voilà, sound is working again!
Thanks a lot man!

---

### Post by whalogreg on 2009-12-08
I've been having sound problems after going into suspend/hibernate. I have a feeling I might be having the same issue here. What exactly do I need to do to change the settings correctly?

---

### Post by loveunit on 2011-02-07
genius - that fixed a range of sound problems.. look out for notices about not having permission.. this is a tell tale sign

something had changed the owner and group of my home folder.

good one - sound restored!

---

