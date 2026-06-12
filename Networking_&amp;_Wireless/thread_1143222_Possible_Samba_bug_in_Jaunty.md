---
title: "Possible Samba bug in Jaunty"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by sahendrickson on 2009-04-29
I am trying to share a folder (which is a symlink) in my home directory. It looks like if the symlink itself is shared, then everything is always read-only. However, if I share the folder that contains the symlink and then navigate in to the symlink, I can write just fine. 

UPDATE: It seems that only my home directory can be shared as anything other than read-only. Yes, the other folders I've shared are read/write for the user account (and I can read/write to them from within the home directory share).

Details:
- /home/scott/shared is a symlink
- if I share /home/scott/shared as follows:

```
[shared]
	path = /home/scott/shared
	writeable = yes
	browseable = yes
	valid users = scott
```

I can only read files in the "shared" share.
However, if I share it's parent folder, as follows:

```
[scott]
	path = /home/scott
	writeable = yes
	browseable = yes
	valid users = scott
```

When I go to //computer/scott/shared (which is logically the same as the first share) I can update files without any problem.

I only started getting this problem when I upgraded to Jaunty. Can anyone verify that this is a bug?

Thanks, 
-- Scott

---

### Post by dmizer on 2009-05-01
I don't have Jaunty yet, but perhaps we can narrow things down.

Where is the sym link pointing to? What are the permissions on the linked directory? Is the linked directory a mounted filesystem?

---

### Post by sahendrickson on 2009-05-17
Hi dmizer,

My apologies for not responding earlier -- I hadn't subscribed to the thread and thus didn't realize that you had responded. I have subscribed now and my responses are below...

> **dmizer said:**
> I don't have Jaunty yet, but perhaps we can narrow things down.

Where is the sym link pointing to? What are the permissions on the linked directory? Is the linked directory a mounted filesystem?

1) Where is the sym link pointing to? 

```
scott@data 21:10:29 ~
$ pwd
/home/scott
scott@data 21:10:29 ~
$ ls -alF
total 3.5G
drwxr-xr-x 79 scott scott 4.0K 2009-05-16 21:08 ./
drwxr-xr-x  3 root  root  4.0K 2008-12-06 16:05 ../
lrwxrwxrwx  1 scott scott   37 2009-05-16 20:48 shared -> /data/backup-manual/home/scott/shared/

```

2) What are the permissions on the linked directory?

```
scott@data 21:12:12 /data/backup-manual/home/scott
$ pwd
/data/backup-manual/home/scott
scott@data 21:12:17 /data/backup-manual/home/scott
$ ls -alF
total 12K
drwxr-xr-x 3 scott scott 4.0K 2009-04-29 15:51 ./
drwxr-xr-x 3 root  root  4.0K 2008-01-23 17:59 ../
drwxrwxr-x 7 scott scott 4.0K 2009-05-16 21:07 shared/

```

3) Is the linked directory a mounted filesystem?

The home and linked directory are on two different partitions of the same, internal hard drive.

I just confirmed that I still have this problem after the latest apt-get updates for Jaunty.

Thanks dmizer,
-- Scott

---

### Post by Killing Vector on 2009-10-10
I can confirm this problem.  Symlinks will be in blue font. On my Kubuntu Jaunty box:

/data/multimedia
/data/multimedia/mp3
[COLOR="RoyalBlue"]/data/mp3[/COLOR]      <-------- symlink to /data/multimedia/mp3


On Windows, when I access the files under [COLOR="RoyalBlue"]/data/mp3[/COLOR], they are all read-only.  No write permissions at all.

But when I access those same files using /data/multimedia/mp3, they are read/write.

For example, when I use the Network Neighborhood:
* /data/multimedia/mp3/readme.txt  is read/write.
* [COLOR="RoyalBlue"]/data/mp3/[/COLOR]readme.txt is read-only.

There's something about following a symlink that makes the files read-only.

_More Information_

All files under /data/multimedia/mp3 have permissions rw-rw-r and all directories have permissions rwxrwxr-x.  Everything has ownership p:users (p is my username and is a member of users).

Here is the relevant sections of smb.conf:

[COLOR="SeaGreen"][FONT="Courier New"][data]
   comment   = Public read/write data directory.
   path      = /data
   read only = no
   public    = yes

[mp3]
   comment         = Public read/write mp3 directory.
   path            = /data/mp3
   read only       = no
   writable        = yes
   follow symlinks = yes
   wide links      = yes
   public          = yes[/FONT][/COLOR]

One interesting thing I've noticed in my log files about trying to write to share mp3:

[COLOR="SeaGreen"][FONT="Courier New"][2009/10/09 20:48:43,  0] param/loadparm.c: process_usershare_file(8327)
  process_usershare_file: stat of **/var/lib/samba/usershares/mp** failed. No such file or directory[/FONT][/COLOR]


The "3" in "mp3" seems to have been cut off.  I wonder if that's relevant?

---

### Post by dmizer on 2009-10-10
> **Killing Vector said:**
> Everything has ownership p:users (p is my username and is a member of users).

But when you access the shares, you're not accessing them as p, you're accessing them as your Windows user, who won't have permission unless you've added the Windows username as a user on your Ubuntu server.

---

