---
title: "Ubuntu Cannot see Windows shares"
date: 2009-06-15
forum: Networking &amp; Wireless
---

### Post by bagwanram on 2009-06-15
Hello,

My Ubuntu laptop was seeing my windows computer's shared folders just fine and now, using Nautilus, when I go to network servers, it see's the computer(Named Vista64) but nothing shows up when I open it.

Hmmm, I looked over smb.conf and I dont really understand it all yet.....

So any help would be appreciated!

---

### Post by Iowan on 2009-06-15
First stop (or next one) might be [here]("http://ubuntuforums.org/showthread.php?t=1169149").

---

### Post by philcamlin on 2009-06-15
ubuntu cant read ntfs until you install the patch :popcorn:

---

### Post by dmizer on 2009-06-15
> **philcamlin said:**
> ubuntu cant read ntfs until you install the patch :popcorn:

This is unnecessary. It makes no difference what the remote computer's drive is formatted as. This only matters if the hard drive or partition is physically attached to the Ubuntu computer.

---

