---
title: "'mount' audio cd"
date: 2008-06-15
forum: Multimedia Software
---

### Post by jipke on 2008-06-15
I'm running openbox & installed ivman (automount).

After some reading I understand audio CDs can't be mounted (as there is no filesystem on it) in /media/cdrom. Therefore I need to access the content/tracks directly. 

According to my /etc/fstab/ this should be done in /dev/scd0

```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

There isn't such a directory. The most confusing however is that Rhythmbox plays my audio CDs (???). Where does the program scan for the media? Looking at the properties of a track I get:

```
file name: scd0
location: cdda://1#/dev
```

---

### Post by prshah on 2008-06-15
> **jipke said:**
> 
After some reading I understand audio CDs can't be mounted (as there is no filesystem on it) in /media/cdrom. 

There isn't such a directory. 


/dev/scd0 refers to a device, though it looks like a directory. You cannot "access" it by directory commands, you have to use different type of commands (commands for block devices)

And, it _can_ be mounted, but not as a filesystem.

Why do you want to access it directly? Ripping etc? To play the audio CD, use the url```
cdda://1
``` in the player of your choice. (Though most will have an option to "Open disc")

---

