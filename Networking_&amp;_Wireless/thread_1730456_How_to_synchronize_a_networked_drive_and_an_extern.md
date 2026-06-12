---
title: "How to synchronize a networked drive and an external drive (Ubuntu &amp; OS X)?"
date: 2011-04-16
forum: Networking &amp; Wireless
---

### Post by pedrogent on 2011-04-16
Firstly, I've posted something similar [here]("http://unix.stackexchange.com/questions/11386/how-to-synchronize-a-networked-drive-and-an-external-drive-ubuntu-os-x"). I'm not sure the answer there goes into enough detail for me to understand. Furthermore, I'm not sure it deals with my concerns about resource forks being handled properly.

OK:

In light of a recent [hardware failure]("http://askubuntu.com/questions/34862/weak-filesystem-seems-to-have-died-what-can-i-do"), I've decided that it's time to be a little less lax regarding back-ups.

What I have:

[LIST]
[*]An Ubuntu 10.10 'server/NAS'
[*]A MacBook 5,2
[*]A WD external HDD
[/LIST]

The server and the MacBook are permanently connected by Ethernet.

I have a directory on the server that I'd like to keep synchronized with the external drive that I plug in from time to time. The Ubuntu filesystem is ext4 and the external drive is HFS+ (Mac OS Extended [Journaled]). It should be noted that this is not case-sensitive. I'm unsure if this is a problem. If it is I can reformat the external HDD so that it is.

It should also be noted that OS X 10.6 ships with a fairly old rsync, ver. 2.6.9. I believe there are some problems with this concerning the handling of resource forks and other things.

So then, what is the best way to proceed?

[LIST]
[*]Should I be doing rsyncs across the network? If so some guidance re: how to achieve this using the CLI would be appreciated (I've read the rsync man page numerous times and can't quite get my head around it).
[*]Or should I be installing a kernel module so that I can just plug the HFS+ formatted drive into the server and it be read & writeable in Linux? Again, some rsync CLI guidance would be great.
[*]Or should I be doing something else entirely?
[/LIST]

Thanks in advance and sorry about this duplication, but I really want to get my head around rsync. I feel if I do, my computing life will be made a lot easier.

---

### Post by MrEgg on 2011-04-16
If Ubuntu is your server, then can we assume that it's Ubuntu you want to rsync to your external drive - and that you manually take care of synchronizing your local files on the Mac with your server?

Additionally, are you going to remove the external drive from the server, or can you afford to leave it plugged in and turned on all the time?

If so, here's what I would do.

1. Format the external HD to ext4.
2. On the Ubuntu server, write a script that :
   2.1. manually detects if your external is plugged into the server
   2.2. rsyncs your server directory to the external drive
   2.3. unmount the external drive (optional)
3. Set the script to run periodically

Let us know if this would do the trick for you so we can work on the script.

---

### Post by pedrogent on 2011-04-16
Thanks for the quick reply MrEgg.

For clarification purposes first:

[LIST]
[*]The external HDD is currently attached to the MacBook. So it looks something like this: Ubuntu --> MacBook --> external HDD.
[*]You're correct that I wish to rsync the server to the external HDD, and that I can manually handle the MacBook side of things.
[/LIST]

With that in mind, it seems as though the best course of action is for me to format the external HDD to ext4 and thus avoid rsync'ing across Ethernet. Do you happen to know the state-of-play vis-à-vis FUSE-type utilities for OS X. I want to have this external HDD read & writeable in OS X.

After this I'll need a bit of a lesson in writing rsync scripts.

Cheers again for the rapid reply.

---

### Post by MrEgg on 2011-04-16
I'm not able to help from the Mac end, unfortunately.

In your configuration, would it be possible to plug the external HD directly to the server? If you format it in ext4, I do not know whether you'll be able to read it directly from the Mac or not -- ie you'll have to check for yourself. However, if you're okay with that configuration, we'll work on the script together, of course.

---

### Post by pedrogent on 2011-04-16
Thanks again MrEgg. I'll do some research re: having ext4 read/writeable in OS X. Once I've worked this out let's get down to that script. :)

I have a few things to do right now, but I'll report back ASAP.

:KS

---

### Post by MrEgg on 2011-04-16
Just in case OSX and ext4 don't play together well, check OSX and xfs as another possibility.

---

### Post by pedrogent on 2011-04-16
Ah cool will do. Am I hallucinating or is exFAT now supported on both ends? I'll looks into it.

---

### Post by MrEgg on 2011-04-16
> **pedrogent said:**
> Ah cool will do. Am I hallucinating or is exFAT now supported on both ends? I'll looks into it.

WHAT?? You want to use a msft filesystem?? You're kidding, right??? :D

It won't support file ownership nor file permissions. It will fragment. You said you wanted to use your external HD for backup purposes - so use a reliable filesystem, please!

For ext4 on OSX, check this out (it's in French, you may want to google translate it) : [URL="http://www.digitalspirit.org/blog/index.php/post/2009/10/12/Monter-une-partition-ext2,-ext3-ou-ext4-sur-MacOs"]http://www.digitalspirit.org/blog/index.php/post/2009/10/12/Monter-une-partition-ext2,-ext3-ou-ext4-sur-MacOs
[/URL]

Now, in your situation is it absolutely mandatory that OSX can mount the external HD directly? Even in ext4, it can be accessed by the mac through the ubuntu server via a proper network share.

---

### Post by pedrogent on 2011-04-16
Haha, yes... Moving on... But before we do, why can't we all get along and all use ZFS? OK, moving on now...

What you describe is fine: i.e. external HDD plugged into Ubuntu and I'll access that over the network. It'd be better if the drive was OS X read/writeable but it may not be possible under these circumstances.

I've been having [odd AFP (netatalk/avahi-daemon) issues]("http://askubuntu.com/questions/34368/finder-freezes-when-deleting-files-across-a-os-x-linux-network") from time to time. Perhaps I should be using SMB?

Thanks for the link. I'll take a look.

---

### Post by MrEgg on 2011-04-16
You have at least 2 options :

SMB is easy and works just fine. How do you currently send your documents from the mac to the server? It could be just the same with the external drive. Remember that it's the server that'll be sending stuff to it, not the mac. Access through the mac is only for checking purposes, really. And besides, you'll always be able to ssh to the server and check the contents of the drive from there. Quick, fast, easy.

You can also mount the server drive on your mac through SSH, using macfusion. It works. Even remotely through the internet. Check this : [http://www.simplehelp.net/2008/07/25/how-to-mount-a-remote-file-system-as-a-local-drive-in-os-x/]("http://www.simplehelp.net/2008/07/25/how-to-mount-a-remote-file-system-as-a-local-drive-in-os-x/")

Just settle for a filesystem already, and then we can move on :D

---

### Post by pedrogent on 2011-04-16
OK, it seems Ubuntu reads HFS+ partitions no problem. The external HDD has two HFS+ partitions. In order to write to the partition I need to disable journaling, which I have done for the partition in question. I've also installed hfsplus which allegedly allows me to write to that partition.

I believe I need to fix up my /etc/fstab now so that one partition auto-mounts and one doesn't.

I don't want to lose a bunch of valuable data here so sorry if I'm going a little slow.

---

### Post by MrEgg on 2011-04-16
Okay, if you want to use that filesystem, I suggest you first do some thorough testing read and writing files from the server. You want to rsyncs to be reliable.

I suggest you take the time to do that and come back once you validate.

Also, let me know if the drive auto mounts in Ubuntu or not. It should appear in /media on the server. Post the result of
```
ls -l /media
```
on the server.

We'll take it from there.

---

### Post by pedrogent on 2011-04-16
The partitions auto mount on the server. I've confounded things a little here in that I'd already done:

```
$ sudo mkdir /media/extras /media/syncatron
```

But in any case, here's the print out of ls -l /media

```
boehj@sutti:~$ ls -l /media
total 16
drwxr-xr-x 2 root  root  4096 2010-12-14 23:36 cdrom
drwxrwxrwx 5 boehj boehj 4096 2011-02-28 10:49 data
drwxr-xr-x 2 root  root  4096 2011-04-16 20:21 extras
drwxrwxr-x 1    99    99    9 2011-04-16 19:54 extras_
drwxr-xr-x 2 root  root  4096 2011-04-16 20:21 syncatron
drwxrwxr-t 1 root     80   33 2011-04-15 20:19 syncatron_
```

I'm guessing the 'extras_' and 'syncatron_' directories are the auto mount points.

I also updated my /etc/fstab (haven't saved it yet) but I wonder about the options. Here are the relevant bits:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=dd096328-2e0d-46d1-a630-760f895ece15 /                     ext4 errors=remount-ro,user_xattr 0       1
UUID=4d901313-a4f7-45b3-b15a-a70b2a4182e2 /media/data           ext4    defaults                  0       2
UUID=69a1dd0a-9da2-4ca4-bd21-00cd5d23ee0d none                  swap    sw                        0       0

#WD external
UUID=1d811ccf-2b05-3c1a-aeec-1974caae0627 /media/syncatron      hfsplus	noauto                    0       2
UUID=512f1f64-83c0-3c7a-8899-8229bc21c63d /media/extras         hfsplus noauto                    0       2
```

I've done noauto because I don't want these (particularly 'syncatron') mounting unless I specifically tell them to. Are there any other options I should be putting here. Options that perhaps pertain to permissions.

Bah, to be honest, this HFS+ stuff is making me woozy. I'd feel much more comfortable just formatting one partition ('extras') as ext4 and being done with it.

I'm sorry this has become so unwieldy. I think I've wasted a lot of your time. Once I've reformatted 'extras' as ext4 I'll report back and perhaps, if you still have the patience, you can teach me how to write a rsync script.

Thanks again for your help.

---

### Post by MrEgg on 2011-04-16
Okay, big confusion here.

You have to decide one of two situation, which are mutually exclusive.

EITHER you opt for automounting, which means the drive automatically appears in /media when you plug it in. Here, there must be no entry in fstab, and you remove the directories you manually created in /media

OR you don't need automounting, and you indeed put the entries in fstab and create the directories, but not necessarily in /media. It could better to mount it in /mnt or in /backup. [Just so you know, what you put in /media automatically appears on the Desktop]. In this scenario, you want to plug the drive before you boot the server, and you won't be unmounting the external drive.

You have to choose. The script will test if the drive is present or not before trying to send any data.

I think automounting could be good enough.

---

### Post by pedrogent on 2011-04-16
I'm aware /media mounted drives appear on the desktop. I like this. I don't want 'syncatron' mounting unless I specifically say so because this is a bootable clone of my OS X system.

Are you saying I can never unplug the external drive (except when the system is off) if I choose the non-auto mounting route?

I've nuked the 'extras' partition which was HFS+ and it's now ext4. The relevant bit of my /etc/fstab looks like this:

```
#WD external
UUID=1d811ccf-2b05-3c1a-aeec-1974caae0627 /media/syncatron      hfsplus	noauto                    0       2
UUID=5c98197f-c4fd-4375-9d9f-6becd1cbc76c /media/extras         ext4    defaults                  0       2
```

I'm happy with this arrangement.

Now when I made the /media/extras and /media/syncatron directories I also did the following:

```
$ sudo chown -R boehj:boehj /media/extras/
$ sudo chmod -R 755 /media/extras/
```

ls -l /media prints this:

```
boehj@sutti:~$ ls -l /media/
total 12
drwxr-xr-x 2 root  root  4096 2010-12-14 23:36 cdrom
drwxrwxrwx 5 boehj boehj 4096 2011-02-28 10:49 data
drwxr-xr-x 3 boehj boehj 4096 2011-04-16 21:55 extras
drwxrwxr-t 1 root     80   33 2011-04-15 20:19 syncatron
```

Slightly worried I've borked the permissions on 'syncatron'. I'm going to check that now. How we looking so far? I'm starting to feel that manual back-ups are more my style.

---

### Post by MrEgg on 2011-04-16
Okay, doing good so far. Great you opted for leaving the drive automounting, its more OSX style : you see it when it mounts, and you already know how to unmount it before you remove it.

Now, I need to know where are your files on your server and where you want to send them on the HD.

Example:
From server: /home/joe/Documents/*
To HD: /media/extras/Backup

Also, now is a good time to determine whether you want to sync everything from the server, or if there are directories or types of files you want to exclude.

What we'll do next : create the script. Almost there.

---

