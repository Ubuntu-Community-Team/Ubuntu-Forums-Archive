---
title: "/dev/video0 has no group"
date: 2008-12-10
forum: Multimedia Software
---

### Post by barney_1 on 2008-12-10
Hi folks,

I was able to get my webcam (sony eyetoy) working but I managed to mess up while doing so.  Now when I plug in the webcam, there is no group assigned to it.  As you can see, root is the own but no group is listed:

```
ls /dev/video0 -l
crw-rw---- 1 root 44 81, 0 2008-12-10 11:48 /dev/video0

```

Any idea how I can fix this so that is once again assigns the group "video" to it?

Here's a post explaining what I did to get into this mess:
[http://ubuntuforums.org/showpost.php?p=6343457&postcount=9](http://ubuntuforums.org/showpost.php?p=6343457&postcount=9)

It should be known that I did go to user/group management and manually add the group "video".

Thanks for the help!

---

