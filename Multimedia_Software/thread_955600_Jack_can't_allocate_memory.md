---
title: "Jack can't allocate memory"
date: 2008-10-22
forum: Multimedia Software
---

### Post by Mzwo on 2008-10-22
hi,

jack gives me the following message:

JACK: unable to mlock() port buffers: Cannot allocate memory
JACK: unable to mlock() port buffers: Cannot allocate memory

and


cannot lock down memory for RT thread (Cannot allocate memory)

Realtime is enabled in the server settings, memlock is enabled in studio controls and set to 50%. running 8.04 studio.

doesn't seem right. any suggestions?

Mzwo

---

### Post by markbuntu on 2008-10-22
Try this, it will unlock the memory for jack and set it to high priority for the rrt kernel:
Edit /etc/security/limits.conf and add or modify these lines

```

audio - memlock unlimited
audio - nice -10
audio - rtprio 99

```


    * The 'memlock' line determines the amount of memory available to users in the group "audio
    * The 'nice' line, has to do with how long the processor will wait for processes queued from group "audio".
    * The 'rtprio' line assigns an extremely high priority to the group "audio".

The nice and rtprio settings will basically give your audio top priority at the cpu which is necessary for live work.

---

### Post by Mzwo on 2008-10-23
Thanks, will try and report back.

what is the user group "audio"? id din'T know there was such a thing as user groups ... ?

Mzwo

---

### Post by markbuntu on 2008-10-23
System/Adminstration/Users and Groups. This is where you set permissions for users and the groups they belong to. Linux was designed from the ground up for multiple users and high security and things like controlling system services for users and groups is a big part of what makes it so secure. You should look in there, it will help you to understand why linux is so hard to invade.

---

