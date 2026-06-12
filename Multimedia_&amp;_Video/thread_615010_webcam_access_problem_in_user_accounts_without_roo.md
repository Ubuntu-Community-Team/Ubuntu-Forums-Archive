---
title: "webcam access problem in user accounts without root privilege"
date: 2007-11-16
forum: Multimedia &amp; Video
---

### Post by phasenew on 2007-11-16
system is ubuntu gutsy. the problem is found while using skype. but I think it is a more general one.  the webcam is a USB logitech STX.
In the account with root privilege (can sudo), the camera shows up and can be used normaly with skype, but in accounts without the sudo ability, skype cannot see the device. in /dev, the device shows as:

lrwxrwxrwx 1 root root       11 2007-11-16 23:01 video -> /dev/video0
crw-rw---- 1 root video 81,   0 2007-11-16 22:59 video0

when I change the permission of /dev/video0 in the root account to 
crw-rw-rw- 1 root video 81,   0 2007-11-16 22:59 video0
the camera works in every account.

but when the camera is unplugged, /dev/video0 is removed by the system, it is just created / removed by the system whenever the device is un/plugged.
also is the group of "video" created and removed with the device plugged or not.

the question is:
how to let the system automatically set the camera permission to be accessible to all users? 
or in other way, because the system automatically set /dev/video accessible to video group memebers, how can i let system automatically add the general users to the video group (note the video group is also created /removed by system with the camera un/pluged) when the camera is pulgged in?

thanks a lot for input.

---

### Post by beaudry on 2007-12-01
I'm having the same problems. Is there any fix.

---

### Post by jimwood10 on 2007-12-08
Found the fix here :

[http://ubuntuforums.org/showthread.php?t=408448&highlight=webcam+users](http://ubuntuforums.org/showthread.php?t=408448&highlight=webcam+users)

---

### Post by teksaver on 2007-12-16
> After I installed a webcam driver I wasn't able to use it.

**Turns out that while the FIRST user created when installing feisty is set to belong to the 'video' group, it isn't so for OTHER users.**

A newly added user isn't part of the 'video' group, and the gui to add/remove user doesn't provide any way to change this. In fact, the "Manage groups" screen doesn't even list 'video' even though it is in /etc/group.

I worked around the problem by manually editing /etc/group.

this was back in feisty. The problem remains in gusty  - I can't expect "normal" users to manually add groups to users using the command line. 

I guess "video" should be added automatically, to all users or at least appear in the group selection GUI. Is there any bug open about this ?

---

### Post by banger69 on 2008-03-18
guys , i am having the same problem , i cant figure it out

---

