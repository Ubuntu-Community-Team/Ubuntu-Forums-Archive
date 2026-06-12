---
title: "What are /var/lib/mythtv permissions?"
date: 2008-05-21
forum: Mythbuntu
---

### Post by scsever on 2008-05-21
What are the default permissions and owner:group for the directories under /var/lib/mythtv?  I was having problems with other systems connecting via NFS and made some changes a few weeks back, now I can't watch live TV.  Of course by the time I discovered the problem I had forgotten the original settings.

Thanks,
Steve

---

### Post by mrand on 2008-05-21
> **scsever said:**
> What are the default permissions and owner:group for the directories under /var/lib/mythtv?  I was having problems with other systems connecting via NFS and made some changes a few weeks back, now I can't watch live TV.  Of course by the time I discovered the problem I had forgotten the original settings.

Thanks,
SteveHowdy Steve,

Here's mine:```
/var/lib$ ls -l | egrep myth
drwxrwsr-x   3 mythtv        mythtv          17 2008-01-13 12:21 mythdvd
drwxr-xr-x   6 root          root            63 2008-01-13 12:21 mythtv

/var/lib$ ls -l mythtv mythdvd
mythdvd:
total 0
drwxrwsr-x 2 mythtv mythtv 20 2008-01-13 13:30 temp

mythtv:
total 24
drwxrwsr-x 8 mythtv mythtv   156 2008-02-01 20:15 music
drwxrwxr-x 6 mythtv mythtv    60 2008-04-25 22:05 pictures
drwxrwsr-x 2 mythtv mythtv 20480 2008-05-21 21:30 recordings
drwxrwxr-x 4 mythtv mythtv    28 2008-04-26 09:07 videos
/var/lib$ 
```[INDENT]Marc[/INDENT]

---

### Post by scsever on 2008-05-22
Excellent,
 Thanks Marc

---

### Post by temujin77 on 2008-05-22
A somewhat related topic...

Usually I load stuff to my Mythbuntu box via the Samba shares, which assumes the user "mythtv", so all is well.

Last week, I popped in my external HD to the Mythbuntu box, which had a bunch of MP3s that I ripped from my 1990s CD collections a long time ago.  I figured local transfer is faster over the web, so I just SSH'd into the box, made a folder .../music/90sCds and then issued Linux "cp" command to copy it in.  This works well, but I noticed that the folder "90sCds" is made by a different user, so I cannot move the files when coming in from Samba, because MythTV does not have permission to change stuff created by another user.

Then, I thought I'd just "chown" that folder, but I don't know what the root password is.

Long story short:  What is best course of action for me?
1. SSH back in, delete, and re-copy over Samba.
2. Figure out what the default root password is (need your help here) and change owner.
3. Others?

---

### Post by mrand on 2008-05-22
> **temujin77 said:**
> A somewhat related topic...

Usually I load stuff to my Mythbuntu box via the Samba shares, which assumes the user "mythtv", so all is well.

Last week, I popped in my external HD to the Mythbuntu box, which had a bunch of MP3s that I ripped from my 1990s CD collections a long time ago.  I figured local transfer is faster over the web, so I just SSH'd into the box, made a folder .../music/90sCds and then issued Linux "cp" command to copy it in.  This works well, but I noticed that the folder "90sCds" is made by a different user, so I cannot move the files when coming in from Samba, because MythTV does not have permission to change stuff created by another user.

Then, I thought I'd just "chown" that folder, but I don't know what the root password is.

Long story short:  What is best course of action for me?
1. SSH back in, delete, and re-copy over Samba.
2. Figure out what the default root password is (need your help here) and change owner.
3. Others?

Does the user that you copied the files with have admin privileges?  If so, you should be able to put "sudo" in front of your chown.

   [INDENT]Marc[/INDENT]

---

### Post by temujin77 on 2008-05-22
> **mrand said:**
> Does the user that you copied the files with have admin privileges?  If so, you should be able to put "sudo" in front of your chown.

   [INDENT]Marc[/INDENT]

I tried sudo, but I don't seem to know the root password.  Is there a default root password to Mythbuntu?  I don't recall ever entering one during the install.

---

### Post by mrand on 2008-05-23
> **temujin77 said:**
> I tried sudo, but I don't seem to know the root password.  Is there a default root password to Mythbuntu?  I don't recall ever entering one during the install.
Assuming your user has admin/root privileges, the password you enter for sudo is *your* password. By default, ubuntu doesn't have a root password: [http://www.google.com/search?q=root+password+ubuntu](http://www.google.com/search?q=root+password+ubuntu)

[INDENT]Marc[/INDENT]

---

### Post by temujin77 on 2008-05-23
> **mrand said:**
> Assuming your user has admin/root privileges, the password you enter for sudo is *your* password. By default, ubuntu doesn't have a root password: [http://www.google.com/search?q=root+password+ubuntu](http://www.google.com/search?q=root+password+ubuntu)

[INDENT]Marc[/INDENT]

Hm, I thought I tried my own password, but didn't work, but I will give it a shot again.  Thanks Marc!

---

