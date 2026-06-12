---
title: "Mythbuntu 9.10 Error: directory is not writable..."
date: 2010-02-18
forum: Mythbuntu
---

### Post by killabee44 on 2010-02-18
Guys, I am getting the following error on a fresh Mythbuntu 9.10 install when exiting the MythTV Setup:

[I]Unable to create file "//.test" - directory is not writable?

[/I]
My livetv folder is set up under: /media/mythtv/video/livetv

I am able to scan channels just fine and everything looks good. My tuner is the Hdhomerun.

From searching, it looks like a permissions problem but I don't know how to go about it.

Here is the output of ls -la:
```

drwxr-xr-x 30 htpc1  htpc1  4096 2010-01-31 11:24 .
drwxr-xr-x  4 root   root     16 2009-12-05 17:34 ..
-rw-------  1 htpc1  htpc1  5396 2010-02-18 18:24 .bash_history
-rw-r--r--  1 htpc1  htpc1   220 2009-12-05 17:34 .bash_logout
-rw-r--r--  1 htpc1  htpc1  3180 2009-12-05 17:34 .bashrc
drwxr-xr-x  4 htpc1  htpc1    24 2009-12-06 12:41 .cache
drwxr-xr-x  7 htpc1  htpc1  4096 2009-12-08 23:09 .config
drwx------  3 htpc1  htpc1     8 2009-12-06 00:43 .dbus
drwxr-xr-x  2 htpc1  htpc1     1 2009-12-06 00:43 Desktop
drwxr-xr-x  2 htpc1  htpc1     1 2009-12-06 00:43 documents
drwxr-xr-x  3 htpc1  htpc1  4096 2010-01-31 11:11 downloads
-rw-------  1 htpc1  htpc1    16 2009-12-06 10:50 .esd_auth
drwxr-xr-x  2 htpc1  htpc1  4096 2009-12-06 00:44 .fontconfig
-rw-r--r--  1 htpc1  htpc1  1943 2009-12-07 14:52 fstab and mythbuntu partitionoing
drwx------  3 htpc1  htpc1  4096 2010-02-18 06:25 .gconf
drwx------  2 htpc1  htpc1  4096 2010-01-31 11:19 .gconfd
-rw-r-----  1 htpc1  htpc1     0 2010-01-31 11:18 .gksu.lock
drwxr-xr-x  6 htpc1  htpc1    72 2010-01-31 10:42 .gnome2
drwx------  2 htpc1  htpc1     1 2009-12-06 10:50 .gnome2_private
drwxr-xr-x  2 htpc1  htpc1    40 2010-01-31 10:34 .gstreamer-0.10
-rw-------  1 htpc1  htpc1   178 2010-01-31 10:40 .gtk-bookmarks
drwx------  2 htpc1  htpc1     1 2009-12-06 00:44 .gvfs
-rw-r--r--  1 htpc1  htpc1  3655 2009-12-08 22:57 How to set up a Myth media drive
-rw-------  1 htpc1  admin   692 2010-01-31 10:34 .ICEauthority
drwxr-xr-x  2 htpc1  htpc1    64 2009-12-05 17:35 .lirc
-rw-r--r--  1 htpc1  htpc1   296 2009-12-05 17:35 .lircrc
drwxr-xr-x  3 htpc1  htpc1     8 2009-12-06 00:44 .local
drwx------  4 htpc1  htpc1    16 2009-12-06 10:50 .mozilla
drwxrwsr-x  2 mythtv mythtv    8 2009-12-08 22:53 music
drwxr-xr-x  4 htpc1  htpc1    48 2009-12-06 09:23 .mythtv
drwxr-xr-x  2 htpc1  htpc1     1 2009-12-06 09:31 .nautilus
drwxrwxr-x  2 mythtv mythtv    1 2009-12-06 00:43 pictures
-rw-r--r--  1 htpc1  htpc1   675 2009-12-05 17:34 .profile
drwxr-xr-x  2 htpc1  htpc1     1 2009-12-06 00:43 Public
-rw-------  1 htpc1  admin  1533 2010-01-31 11:05 .recently-used.xbel
-rw-r--r--  1 htpc1  htpc1     0 2009-12-06 00:49 .sudo_as_admin_successful
drwx------  2 htpc1  htpc1    16 2009-12-07 16:35 .synaptic
drwxr-xr-x  2 htpc1  htpc1     1 2009-12-06 00:43 Templates
drwxr-xr-x  3 htpc1  htpc1     8 2009-12-06 12:41 .thumbnails
drwxr-xr-x  2 htpc1  htpc1     8 2009-12-06 21:24 .update-manager-core
drwx------  2 htpc1  htpc1     1 2009-12-06 00:44 .update-notifier
drwxr-xr-x  2 htpc1  htpc1     8 2009-12-05 17:35 .vnc
drwxr-xr-x  3 htpc1  admin     8 2010-01-31 11:24 .xmltv
-rw-------  1 htpc1  admin  6612 2010-01-31 11:19 .xsession-errors
-rw-------  1 htpc1  admin  6237 2010-01-31 10:33 .xsession-errors.old

```

It looks to me like htpc1 (the name of my htpc) is the current owner of the .mythtv folder.That folder is located on a separate hard drive that only holds media. Could that be it? Thanks.

---

### Post by nickrout on 2010-02-19
you need to look at the permissions and ownerships of /media/mythtv/video/livetv

---

### Post by killabee44 on 2010-02-19
nickrout,

Thanks. I researched how and changed the ownership of that group. Now if I ever need to manually delete a file out of that folder will I be able to? My user (htpc1) is a member of the Mythtv group. Im not sure if that would be enough. Thanks.

---

### Post by nickrout on 2010-02-19
> **killabee44 said:**
> nickrout,

Thanks. I researched how and changed the ownership of that group. Now if I ever need to manually delete a file out of that folder will I be able to? My user (htpc1) is a member of the Mythtv group. Im not sure if that would be enough. Thanks.

I don't know as you haven't told us what you changed and what you changed it to.

---

### Post by killabee44 on 2010-02-20
I just did a: *chown username filepath*

It worked. I guess I will worry about my other concerns as they happen.. Thanks.

---

### Post by stefan.hattrell on 2010-11-30
I know this post is pretty old but it may be helpful for other users who are looking for a solution to this problem to actually post how the problem was resolved.

Firstly, you can use any directory to store recordings etc, so long as you have write permissions. When you install Mythtv on Ubuntu it will add you to the mythtv group automatically so as long as this group has write permissions on the folder, it will work.

Simply use these commands:

sudo chown -R mythtv:mythtv /path/to/folder

sudo chmod -R 775 /path/to/folder

You should see this if you do 'ls -la' on that folder

drwxrwxr-x  7 mythtv   mythtv   4096 2010-11-30 16:37 mythtv

---

### Post by nickrout on 2010-11-30
Not forgetting that permissions/ownership of parent directories are relevant too.

---

