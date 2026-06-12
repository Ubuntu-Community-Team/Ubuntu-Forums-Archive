---
title: "Banshee won't play files every time I restart my computer"
date: 2010-12-30
forum: Multimedia Software
---

### Post by Zlayaaa on 2010-12-30
Hi guys,
here's what happens:

I found out that every time I play a file from my Banchee playlist after restarting my computer it won't play.

The cure for this is just opening places/ntfs partition.
After that it plays the same playlist normaly. 
But it's anoying having to do this every time...

Can you tell me how can I solve this??

---

### Post by Ekeluo on 2010-12-30
You just have to get the partition to mount automatically on boot up. Search around the forums, should be easy to follow instructions to add the partition to fstab. Don't know if ntfs-config is still available, will help ease this.

Edit: just checked, ntfs-config doesn't work for me, seems to require hal.

BTW, welcome to ubuntuforums. :P

This link should give you all you need  - [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Zlayaaa on 2010-12-31
Thank you!!!

---

### Post by Ekeluo on 2011-01-08
You're welcome. For any other users, pysdm seems to work still.

---

