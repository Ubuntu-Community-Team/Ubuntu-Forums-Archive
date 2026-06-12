---
title: "partitioning troubles"
date: 2009-10-22
forum: Mythbuntu
---

### Post by Akriss on 2009-10-22
Sorry I realized now this should be posted in the "install" forum. please follow this post if you can help. [http://ubuntuforums.org/showthread.php?p=8149948#post8149948](http://ubuntuforums.org/showthread.php?p=8149948#post8149948)



I'm having a problem installing the latest RC when I choose manual partitioning. after the install and reboot grub loads with an error "unknown filesystem" and has a grub rescue prompt.

this is what I have and how I have tried so far. one 40gb IDE set as 756mb as swap and the remaining as /. One 500gb SATA set as home, And one 1tb SATA set as /var/lib/mythtv/. 

I tried ext3 and ext4 format for the 40gb os and home HD and XFS as the myth HD. but it always reboots to that error. However, if I have the installer just use the entire 40gb hd it installs fine and reboots fine. This happened on the beta build as well. 

Am I doing something wrong here?

I am going to read a bit on grub and see if there is something that i can do on that error prompt to maybe fix it. I am open to suggestions as well. :)

---

### Post by Akriss on 2009-10-22
Think I found my answer here. [http://ubuntuforums.org/showpost.php?p=3518911&postcount=9](http://ubuntuforums.org/showpost.php?p=3518911&postcount=9)

---

