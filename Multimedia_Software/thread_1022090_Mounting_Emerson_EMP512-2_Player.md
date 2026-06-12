---
title: "Mounting Emerson EMP512-2 Player?"
date: 2008-12-26
forum: Multimedia Software
---

### Post by DM was on fire! on 2008-12-26
SUP.
Long time no talk to.
This means I haven't done anything wrong to my computer in a while. XD

Got a question.
I got an Emerson EMP-512-2 .mp3 player for Christmas, and I was wanting to put some of the music I have on my Ubuntu machine on there (mainly all Japanese, and some songs by independent artists). 
I plugged it in, and it actually mounted on it's own. BUT. It crashed/unmounted while I was transferring files and now I can't get it to mount again.
So, how do I?

I know I should start with:

```
sudo mkdir /media/Emerson MP3
```

But I don't know where to go next.
Any help would be appreciated. <3

P.S.: Still running Dapper.
I'll upgrade one year. XD

EDIT - I tried mounting it as UMS, and got THIS:

```
ashleigh1992@ubuntu:~$ sudo mount /dev/sda /media/usb -t vfat -o umask=0
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Should I maybe check in fstab and see what it says there?

EDIT II - I checked fstab anyway. XD

```
ashleigh1992@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

Now, HDC isn't actually mounted right now, and I guess HDA5 is the .mp3 player?

EDIT - I did a restart and was able to get my floppy to mount again AND THEN I GOT THE MP3 PLAYER TO MOUNT. 8D
BUT.
I'm copying files right now and all of a sudden it crashes/unmounts. I get the following error:

```
Error "I/O error" while copying "/home/as...166.mp3".
```

And then I have to restart to get it to mount again. D;

EDIT - WTF IT JUST MOUNTED ON ME AGAIN. XD

EDIT II - AND NOW IT'S WRITING.

---

