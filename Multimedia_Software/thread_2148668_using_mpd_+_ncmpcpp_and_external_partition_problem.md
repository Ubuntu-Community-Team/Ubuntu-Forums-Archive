---
title: "using mpd + ncmpcpp and external partition problem"
date: 2013-05-26
forum: Multimedia Software
---

### Post by kerasi on 2013-05-26
Hi 

i installed the new version of [COLOR=#000000][FONT=sans-serif]Lubuntu 13.04 and when i set up all it comes this error[/FONT][/COLOR]
```

foo@nyx:~$ sudo /etc/init.d/mpd restart
[sudo] password for foo: 
* Stopping Music Player Daemon mpd                                                                                 [ OK ] 
* Starting Music Player Daemon mpd
music directory is not a directory: "/media/foo/music"                                                            [ OK ]

                                                                      


```
[COLOR=#000000][FONT=sans-serif]
i use mpd.conf  which is in /etc  i will a global configuration[/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]i have the directory from .ncmcpp set up under /home/foo/.ncmpcpp with the config for ncmcpp inside 
[/FONT]
when i click on the music partition i have always to type my password in older version i have not, now because i mount the partition per fstab i dont have cause this the problem?
[/COLOR]
[COLOR=#000000][FONT=sans-serif]i dont know what i make wrong[/FONT]
[/COLOR]


[COLOR=#000000][FONT=sans-serif]my music is now mount in /media/foo/music in older version it was mounted under /media/music is that the reason that it wont work?
[/FONT][/COLOR]
```

foo@nyx:~$ ls -al /media/foo
insgesamt 60
drwxr-x---+  4 root root     4096 Mai 26 10:17 .
drwxr-xr-x   4 root root     4096 Mai 25 19:37 ..
drwx------  91 foo  foo     24576 Jan  1  1970 BMW
drwxrwx---   1 root plugdev 28672 Mai 11 02:18 music

```
[COLOR=#000000][FONT=sans-serif]

my fstab
[/FONT][/COLOR]
```

foo@nyx:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda8 during installation
UUID=33cd6e14-1263-4b28-8019-7320568c0bb3 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda10 during installation
UUID=0c2a19a3-1f1f-4833-87b2-6e91ffeebf57 /home           ext4    defaults        0       2
# swap was on /dev/sda9 during installation
UUID=086e3afb-282c-473d-8067-0aaeaa6ed8cd none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# music was on /sda5
UUID=464C96747AFB6EB9 /media/foo/music ntfs rw,auto,users,nls=utf8,umask=007,gid

```

```

foo@nyx:~$ id mpd
uid=109(mpd) gid=29(audio) Gruppen=29(audio),46(plugdev)

```
[COLOR=#000000][FONT=sans-serif]


[/FONT][/COLOR]

---

### Post by ohnonot on 2013-05-27
i don't know much about mpd, but obviously
```
music directory is not a directory: "/media/foo/music"                                                            [ OK ]
```this is a very clear error mesaage.
(edit: is it an error message? it says ok in the end)
why is it not a directory? is it a permissions problem? or wrong file system?
```

drwxrwx---   1 root plugdev 28672 Mai 11 02:18 music

``````

UUID=464C96747AFB6EB9 /media/foo/music ntfs rw,auto,users,nls=utf8,umask=007,gid

```
the UUID looks too short???

i once tried to manage my music collection, which was on an ntfs (say windoze) drive, with gmusicbrowser and it just never quite worked...

try something different, like creating a link in your home folder to your mounted music drive, and letting mpd use that.

edit: actually the problem might be in your fstab - try to mount the ntfs drive/partition with normal user rights.
don't know if this will work, but i use```
/dev/sda9 /home/data ext4 defaults 1 2
```
i think "defaults 1 2" is the key.  but will that work with ntfs... :-(
also the folder you are mounting to must have the right permissions.

---

