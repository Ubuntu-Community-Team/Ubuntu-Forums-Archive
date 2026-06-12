---
title: "Can't write to Mac formatted (HFS+) iPod with GTKPod"
date: 2007-04-25
forum: Multimedia &amp; Video
---

### Post by nickj6282 on 2007-04-25
Hello all,

I'm having a problem. I've got a Mac formatted (HFS+) iPod. I installed HFS+ support and GTKPod and GTKPod reads my iPod just fine. When I try to add files though, GTKPod tells me that the iPod is a read-only filesystem. My /etc/mtab tells me otherwise:

```

/dev/hdb2 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-15-generic/volatile tmpfs rw 0 0
/dev/hda1 /media/hda1 ntfs rw,nls=utf8,umask=007,gid=46 0 0
/dev/hda2 /media/winshared vfat rw,utf8,umask=007,gid=46 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/sda3 /media/Nick's\040iPod hfsplus rw,noexec,nosuid,nodev 0 0

```

I'm using Feisty on an AMD64 machine and the iPod is a 5G 30GB black unit. Can anyone drop me a clue? Thanks!

---

### Post by simonn on 2007-04-25
Your ipod probably has journalling enabled - which is done by default when you re/initialize an ipod iusing OSX:

[http://gentoo-wiki.com/HOWTO_hfsplus#Disable_Journaling](http://gentoo-wiki.com/HOWTO_hfsplus#Disable_Journaling)

Also, HFS+ has proper unix permissions, unlike FAT file systems, so check the permissions on the ipod's file system 

```

ls -l /media

```

Are the user and group specified you? I have used chown -R to change the permissions with no apparent problem.

Also, it is probably worth building the hfs+ tools, the occasional fsck might be needed on the ipod:

[http://gentoo-wiki.com/HOWTO_hfsplus#Compiling_Apple.27s_Filesystem_Tools](http://gentoo-wiki.com/HOWTO_hfsplus#Compiling_Apple.27s_Filesystem_Tools)

(Note that you obviously do not need to emerge build the drivers on Ubuntu and you have to use the manual method because emerge does not work on Ubuntu :)). Also, I place the mkfs.hfsplus, mkfs.hfs, fsck.hfsplus, fsck.hfs in /usr/local/sbin, rather than /sbin as this is more in line with the Filesystem Hierarchy Standard - [http://www.pathname.com/fhs/](http://www.pathname.com/fhs/).

---

### Post by nickj6282 on 2007-05-01
Ok, when I check the iPod it is set to readonly, and I can't change it because I get a "read-only" filesystem error. The link you sent me for disabling journaling on the partition says that it is "non-destructive" if I do it using the Mac. If I do that, will the iPod still be usable under the Mac with iTunes? Or will it become linux-only at that point?

Thanks
-Nick

---

### Post by simonn on 2007-05-01
Yes and no.

Journalling should make no difference (although I do not know for certain). However, itunes does not like things being added to one of its ipod outside of it and will probably insist on reinitializing your ipod. After all, you are guilty unless proven innocent as far as content producers are concerned - you dirty little pirate :/. So, it will become linux, or at least gtkpod and/or gnupod, only once you use one of those tools - this is the fault of Apple and iTunes though and not because of disabling journaling.

---

### Post by nickj6282 on 2007-05-04
Ok. Well I don't really want to add or delete stuff from my iPod on my Linux PC. Mostly I just want to listen through the speakers while charging, and have the play counts increment just as if I was listening directly on the iPod. Also, to have the ability to rate songs while listening.

Is what I'm proposing even possible?

Thanks

---

### Post by ricardisimo on 2007-10-23
Here's what I'm getting from the Gentoo recommendation:
```
:~$ sudo mkfs.hfsplus -v "disk" /dev/sdc3
sudo: mkfs.hfsplus: command not found
```
"disk" is, by the way, what my iPod is appearing as. It is a 60GB 5th Generation VideoWhite (xA003). I'm getting this error when trying to have gtkpod create a file structure on it:
```
Error initialising iPod: Problem creating iPod directory or file: '/media/disk/iPod_Control/Music'.
```
Any help would be appreciated. Thanks.

P.S. - Yes, I have hfsutils installed, as well as hfsplus.

---

### Post by simonn on 2007-10-23
> **ricardisimo said:**
> Here's what I'm getting from the Gentoo recommendation:
```
:~$ sudo mkfs.hfsplus -v "disk" /dev/sdc3
sudo: mkfs.hfsplus: command not found
```
"disk" is, by the way, what my iPod is appearing as. It is a 60GB 5th Generation VideoWhite (xA003). I'm getting this error when trying to have gtkpod create a file structure on it:
```
Error initialising iPod: Problem creating iPod directory or file: '/media/disk/iPod_Control/Music'.
```


mkfs.hfsplus cannot be found so the partition is not formatted which is why the iPod cannot be initialized.

> P.S. - Yes, I have hfsutils installed, as well as hfsplus.

It's all in the doco, read people, read.

You do not want these installed.

[http://gentoo-wiki.com/HOWTO_hfsplus](http://gentoo-wiki.com/HOWTO_hfsplus)

"The above tools are not to be confused with the these system tools ie. hpmount, hpfsck contained in the gentoo package sys-fs/hfsplusutils. These utilities have not been updated since 2002, and are in the historical folder at penguinppc. They do not operate or mount newer hfsplus partitions, but are unforunatly the only hfsplus support included on a gentoo PPC livecd. Like the preceding example some distributions sadly omit hfsplus kernel support."

So, see [http://gentoo-wiki.com/HOWTO_hfsplus#Manual_Installs](http://gentoo-wiki.com/HOWTO_hfsplus#Manual_Installs)

On a side note, hfsplus formatted disks will not automatically mount (at least <= Feisty, I only installed Gutsy yesterday and have not tested).

---

### Post by ricardisimo on 2007-10-24
Those look like a bunch of commands that will not work in Ubuntu, which means transforming files and translating commands, etc.. If so, what you are telling me is that there is no way for a non-hacker like me to use this iPod without first re-formatting it on an MS Windows system. Uggh.

On the plus side, I've been looking for a reason to try [iPod Linux]("http://ipodlinux.org/Main_Page"). This might be it.

---

### Post by ricardisimo on 2007-10-24
Does the silence mean this is probably the case - that a quasi-newb like myself should probably not be trying to reformat an hfsplus iPod?

---

### Post by simonn on 2007-10-24
> **ricardisimo said:**
> 
Those look like a bunch of commands that will not work in Ubuntu, which means transforming files and translating commands, etc..


Oh yeah, you are quite right. They won't work which is why I quoted them in the first place. That is sarcasm by the way. Of course they work(!) - if compiling the tools needed to format and repair HFS+ partitions is what you actually want to do!

> **ricardisimo said:**
> 
If so, what you are telling me is that there is no way for a non-hacker like me to use this iPod without first re-formatting it on an MS Windows system. Uggh.


The definition of hacker that you imply sets a rather low bar of entry.

I have no idea why you want to reformat your iPod to begin with. Can I suggest you read the following and learn to ask what you actually want to do before annoying people who are giving their time up to try and help you:

[http://www.catb.org/~esr/faqs/smart-questions.html](http://www.catb.org/~esr/faqs/smart-questions.html)

If you have questions, ask them. Whining and moaning does not help anyone, particularly you.

> **ricardisimo said:**
> Does the silence mean this is probably the case - that a quasi-newb like myself should probably not be trying to reformat an hfsplus iPod?

No. It means that there are these things called timezones, look them up. Most of the world does not run on west coast USA time and, contrary to popular belief, a lot knowledgeable people have social lives which are far more enjoyable than helping people like you on a linux message board.

So, what are you actually trying to do? What have you tried so far? Is this a new, uninitialized iPod? 

Get the picture of what sort of information you should be providing?

---

### Post by nickj6282 on 2007-10-26
> **ricardisimo said:**
> Those look like a bunch of commands that will not work in Ubuntu, which means transforming files and translating commands, etc.. If so, what you are telling me is that there is no way for a non-hacker like me to use this iPod without first re-formatting it on an MS Windows system. Uggh.

On the plus side, I've been looking for a reason to try [iPod Linux]("http://ipodlinux.org/Main_Page"). This might be it.

ricardisimo,

I like the idea of iPod Linux, but I didn't like the way it ran on my iPod. The easiest thing to do is reformat your iPod as a FAT32 device. You can do this without Windows using Ubuntu's formatting tools.

I never got the HFS+ iPod working on Linux. I decided to just autosync it with my Mac and leave it at that. It works, no sense in trying to fix what isn't broken. Let me know if you need help getting your iPod formatted for FAT32.

---

### Post by tassoman on 2008-07-03
You cannot import mp3 from DAAC share (shared with rhythmbox) and import into ipod using itunes on osx.

So or you import entire music into itunes using a samba share and then to the ipod (i've not tried this at home), or you reformat ipod using fat32 on windows and use it with gnu.

:guitar:

---

