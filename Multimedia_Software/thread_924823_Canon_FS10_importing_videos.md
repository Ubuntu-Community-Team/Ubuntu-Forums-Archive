---
title: "Canon FS10 importing videos"
date: 2008-09-19
forum: Multimedia Software
---

### Post by ravindra.rajaram on 2008-09-19
I've been through most of the posts in this forum with the same problem, but none offered a reliable solution, checking again if some has a different solution.
I have a Canon FS10 camcorder and when set in camera view mode, F-SPOT recognizes it and offers to import the pictures, which is OK with me (I'd have preferred a mount point, but this is allright).
Now, the problem is what can I do to import videos?
I've tried Kino, but see the typical cannot load raw1394, need read/write permissions etc.
I've added my user to the group "disk", but still the same problem.

I've added the below lines to /etc/modules:
raw1394
video1394
dv1394

and all three modules load up when the system boots up and dmesg shows "NOTE: The dv1394 driver is unsupported and may be removed in a future Linux release. Use raw1394 instead" (hmm.may be i shud remove dv1394 from loading) 
When I connect my camera in the video view mode, I see a mount point and listing of files, but when I try to copy using nautilus or a shell using "cp", both of them hang ( I guess one or more of the drivers crashed). Right now, I'm a bit worried about loosing data if I connect again to my Ubuntu system, as this process freezes the camcorder too( I actually have to remove the battery to "re-boot" the camcorder) ;  I'll have to have the camera mounted on a friends' windozze system (which I hate to), have the files backedup.
Once, I back up the data,I can provide more details from dmesg,syslog etc.
Now, is there a reliable solution to this problem?
Oh, and this camcorder has an 8GB Internal memory and I'm not using any SD Card, so a card reader is out of question here.

Thanks++ in advance for any help!

I'm using Hardy with all the latest updates :)

-RR

---

### Post by ravindra.rajaram on 2008-09-20
Additional info:
I'm connecting the camcorder using the USB cable provided 
-RR

---

### Post by martinlutherwill on 2008-09-20
I'm connecting the camcorder using the USB cable provided. I think it will work in much more better way. Do you know about the video conferencing technique?The best way to make communication with a person or group of person officially or unofficially is through Web Conferencing. It is one of the best way to communicate with the person located far from us. Due to its audio and video impact it has really more approachable. One of the services [http://www.rhubcom.com/](http://www.rhubcom.com/) provides the facility of web conferencing. I think just browse the link you will come to know about it.

---

### Post by remeeraz on 2008-10-14
> **ravindra.rajaram said:**
> I've been through most of the posts in this forum with the same problem, but none offered a reliable solution, checking again if some has a different solution.
I have a Canon FS10 camcorder and when set in camera view mode, F-SPOT recognizes it and offers to import the pictures, which is OK with me (I'd have preferred a mount point, but this is allright).
Now, the problem is what can I do to import videos?
I've tried Kino, but see the typical cannot load raw1394, need read/write permissions etc.
I've added my user to the group "disk", but still the same problem.

I've added the below lines to /etc/modules:
raw1394
video1394
dv1394

and all three modules load up when the system boots up and dmesg shows "NOTE: The dv1394 driver is unsupported and may be removed in a future Linux release. Use raw1394 instead" (hmm.may be i shud remove dv1394 from loading) 
When I connect my camera in the video view mode, I see a mount point and listing of files, but when I try to copy using nautilus or a shell using "cp", both of them hang ( I guess one or more of the drivers crashed). Right now, I'm a bit worried about loosing data if I connect again to my Ubuntu system, as this process freezes the camcorder too( I actually have to remove the battery to "re-boot" the camcorder) ;  I'll have to have the camera mounted on a friends' windozze system (which I hate to), have the files backedup.
Once, I back up the data,I can provide more details from dmesg,syslog etc.
Now, is there a reliable solution to this problem?
Oh, and this camcorder has an 8GB Internal memory and I'm not using any SD Card, so a card reader is out of question here.

Thanks++ in advance for any help!

I'm using Hardy with all the latest updates :)

-RR

Totally agree with you about windowze. If you want to get Firewire to work, follow my instructions in this post.

[http://ubuntuforums.org/showthread.php?t=946708](http://ubuntuforums.org/showthread.php?t=946708)

---

