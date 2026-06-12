---
title: "Very strange problems .. please help!"
date: 2014-09-16
forum: Mythbuntu
---

### Post by misc-daminator on 2014-09-16
Hello all,

I've been using Mythbuntu for years and currently have version 12.04.5 LTS of Xbuntu/Mythbuntu installed on my home server.

The system has been very stable for a long time, but I have encountered some trouble tonight!
It seems like all of the disks are write protected or something.

I have run
```
sudo mount -o rw,remount / 
```
(found online)
on all of the drives, but that doesn't seem to help.

Here's the output of df -h (again, that command online)
```
df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        15G  8.6G  5.4G  62% /
udev            3.8G  4.0K  3.8G   1% /dev
tmpfs           787M  1.3M  785M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G     0  3.9G   0% /run/shm
/dev/sda4       189G  108G   72G  60% /tv
/dev/sdb1       1.8T  1.5T  269G  85% /files
```

A few other observations that might help track down the problem ...

A) If I try to add anything in Synaptic, I get the error:
```
E: Can't write /root/.synaptic/selections.proceed
```
and one of the lines I see in the terminal is:
```
socket.error: [Errno 28] No space left on device
```

B) If I try to create a file in my home directory, using nautilus  get the error:
```
There was an error creating the directory in /home/gingerserver.
```
and
```
Error opening file '/home/homeserver/Untitled Document': No space left on device
```
in 'show more details'

C) If I try to run Dropbox, I see ...
```
IOError: [Errno 2] No usable temporary directory found in ['/tmp', '/var/tmp', '/usr/tmp', '/home/homeserver']
```
in the terminal.
I then see a 'Downloading Dropbox' graphic pop up and scroll all the way to 100%. As soon as it gets to 100%, the GUI says:
```
Trouble connecting to Dropbox servers. Maybe your internet connection is down, or you need to set your http_proxy environment variable.
```

D) If I try to open Firefox, the terminal says:
```
** (firefox:5407): ERROR **: Resource problem creating '/tmp/orbit-homeserver'
Trace/breakpoint trap (core dumped)
```

Although I have been using Mythbuntu for years, I know almost nothing about the command line. Everything I've entered above has been from trying to find a solution online and simply copying and pasting the command.

I have been close to backing up this system before upgrading it to the latest version of Mythbuntu. I assume I should try to get this fixed before I start upgrading now!

Let me know if you have any ideas what to do next.

Thanks,
Damian

---

### Post by tgm4883 on 2014-09-17
Sounds like you are having disk issues and that the system remounted as ro. I'd take a look through (or post) /var/log/syslog

---

### Post by tgm4883 on 2014-09-17
> **tgm4883 said:**
> Sounds like you are having disk issues and that the system remounted as ro. I'd take a look through (or post) /var/log/syslog


I'm guessing that you are the same person that posted on the mailing list (judging by the timeframe and that you used the same title), so I'm going to put the resolution here as well in case someone comes searching and finds this.

You responded to the mailing list with

```
The output of df -ih is:
df -ih
Filesystem     Inodes IUsed IFree IUse% Mounted on
/dev/sda1        955K  955K     0  100% /
udev             973K   500  972K    1% /dev
tmpfs            983K   421  983K    1% /run
none             983K     2  983K    1% /run/lock
none             983K     1  983K    1% /run/shm
/dev/sda4         12M   990   12M    1% /tv
/dev/sdb1        117M  202K  117M    1% /files
```


Responses include 

> Oh dear, as you say, it's not good.
What it means is that you cannot create a new inode on the root filesystem which will break all sorts of stuff. And inode is roughly equivalent to a file - each file is stored in an inode, and any directory entries for that file are simply pointers to that inode.

In practical terms, it means a file can be edited, but any operation that needs to create a new file (even temporarily) will fail with much the same symptoms as a full or read-only filesystem.

> I would guess that something wrote a whole bunch of tiny (0 byte?) files to /... using up all your inodes.  I would start looking in /tmp and /var.

You could run a command like the following from each directory and it should give you a count of all the files smaller than 1 byte by subdirectory... just iterate through the directories with the largest numbers until you find all the files:

 sudo find -maxdepth 1 -type d | while read -r dir; do printf "%s:\t" "$dir"; sudo find "$dir" -type f -size -1c| wc -l; done

> You probably have a *lot* of small files somewhere on your / filesystem.  If you did not create the filesystem by yourself - specifying a small number of inodes, or "-t hugefile or largefile", then all modern distros use sane values.  Find the files with "find / -type d -exec ls -la {} \;" and look for the number next to the directory name - that is your inode count for that directory.  4096 is default, but if the directory goes over, that number will increase.  Look for the directory with higher than 4096 and investigate.  A lot of times, /tmp (where coredumps, etc will be) and if /var is not on a separate partition, a log that is not rotated properly in /var/log, etc..


If that is not you on the mailing list, then please also post the output of

```
df -ih
```

---

