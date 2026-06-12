---
title: "I hate computers"
date: 2008-02-02
forum: Multimedia Production
---

### Post by wildrain on 2008-02-02
Yesterday I installed a new cd/dvd reader/writer

Now I get "You are not privileged to mount volume X" but I just spent last night downloading and even burned the iso image using KD3

Let me guess, chmod something...but something what? /dev/scd0? Then to what!

What gives? Okay I'm learning, that's hope I'll someday join your ranks but right now I'm, well, frustrated. Everything has a learning curve, even me ;-)

Thanks for your help, WR

---

### Post by Mze on 2008-02-02
Is there another user using this machine? Possibly didn't unmount DVD when users were switched. 

A restart should solve your problem.

---

### Post by wildrain on 2008-02-02
Sorry, I'm frustrated...I'm using Ubuntu at home and I'm a greenpea. But Mze that's a very good point, I've posted on the incorrect forum, we assume here I actually might know something....I need Linux for Dummies, forgive me I'm not quite ready for show time yet. Perhaps, not incorrect just premature???? Thanks for your help, all I know is I managed to buy hardware, Ubuntu install drivers, well, greenpeas. We were all there once I guess :-(

---

### Post by eye208 on 2008-02-02
> **wildrain said:**
> Sorry, I'm frustrated...I'm using Ubuntu at home and I'm a greenpea. But Mze that's a very good point, I've posted on the incorrect forum, we assume here I actually might know something....I need Linux for Dummies, forgive me I'm not quite ready for show time yet. Perhaps, not incorrect just premature???? Thanks for your help, all I know is I managed to buy hardware, Ubuntu install drivers, well, greenpeas. We were all there once I guess :-(
Would you please describe your problem in more detail? Right now we can only guess: Did you burn the ISO, then install a new burner? Did you install a new burner, then burn an ISO, then suddenly everything stopped working? Did you burn the ISO, then install a new burner, then install from the ISO? It's not clear. You need to be more careful when describing a problem, otherwise no one can really help you.

---

### Post by wildrain on 2008-02-02
Ah...thanks for being understanding. 

Well, I installed the burner and was able to copy an audio CD using KD3. 

I inserted a DVD to play and I got the message "You are not privileged to mount volume X" but I was able to burn a DVD. 

I downloaded an iso image and when I tried to install the program I get "You are not privileged to mount volume X".  But I was able to burn the CD.

Here are the privs when I exec ls -all scd0  in /dev directory    brw-rw----

I apologise in advance for not knowing more, but I hope this helps you diagnose. Thanks

---

### Post by eye208 on 2008-02-02
Please enter the following commands in a terminal and paste the output here.

```
cat /etc/fstab
ls -l /media
```

The privileges of the device node are OK, otherwise you would not have been able to burn CDs/DVDs at all. But something goes wrong when you try to mount them, so we need to check your fstab file and mount points.

---

### Post by wildrain on 2008-02-02
Okay privs...that makes sense. Here's what I got

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=e3e145c8-192d-4c65-909a-2a93ea2d564d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=10d17bca-98f3-4411-9b04-5ba0042f917f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660,user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

output from ls -l /media

lrwxrwxrwx 1 root root    6 2007-12-01 00:29 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2007-12-01 00:29 cdrom0
drwxrwxrwx 1 root root 8192 2008-01-31 17:35 disk
lrwxrwxrwx 1 root root    7 2007-12-01 00:29 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2007-12-01 00:29 floppy0

Thanks for helping me

---

### Post by eye208 on 2008-02-03
> **wildrain said:**
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=e3e145c8-192d-4c65-909a-2a93ea2d564d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=10d17bca-98f3-4411-9b04-5ba0042f917f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660[COLOR="Red"]**,**[/COLOR]user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
Replace the comma with a space or tab character.

---

### Post by wildrain on 2008-02-03
Duh...thanks. Why don't computers understand what I mean?

---

