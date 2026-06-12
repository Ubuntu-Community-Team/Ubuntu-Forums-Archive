---
title: "killed all my video files when fixing file permissions"
date: 2013-03-28
forum: Mythbuntu
---

### Post by chipppy on 2013-03-28
Good Morning

My 2 issues put short and simple are
1. What did I do wrong when changing the file owner and permissions recursively. and how do I fix this so I get it all correct?
2. How do I get my folders back to type:folder (recursively if possible as there is a lot of folder but I will do singly if its the only option).

Now the long version
System details
Xubutnu 12.10 with mythtv install ontop, RAID5 8TB, highend mobo, I7 chipset, 16GB memory, highend graphics (hardware not been an issue)

I have had a problem with mythtv videos library after moving most of my library around to clean things up. 
After some time I realised it was a file permission problem (due to storing files on Windows machines, then coping them all back to mythtv machine.  Also used 2TB portable HDD to copy files back and forth)

For those that ask I cannot back up as I have 7.5TB of videos.  That is why files were spread across different machines during clean up
Before I started I had all the files for the kids store nicly under /var/lib/mythtv/videos/kids.  The files we single file (single movie) or in folders (tv series) or folder groups single moives (eg disney, xmen, etc).

OK here is all the terminal stuff I did to fix the owner, group owner and file permissions problem
I am trying to recursive change all to owner:mythtv:RW, group:mythtv:RW, other:R only

```
chipppy@MythTV-Main:/var/lib/mythtv/videos/kids$ sudo chown mythtv:mythtv -R
[sudo] password for chipppy: 
chown: missing operand after `mythtv:mythtv'
Try `chown --help' for more information.
chipppy@MythTV-Main:/var/lib/mythtv/videos/kids$ sudo chown mythtv:mythtv -R /var/lib/mthtv/videos/kids
chown: cannot access `/var/lib/mthtv/videos/kids': No such file or directory
chipppy@MythTV-Main:/var/lib/mythtv/videos/kids$ sudo chown mythtv:mythtv -R /kids
chown: cannot access `/kids': No such file or directory
chipppy@MythTV-Main:/var/lib/mythtv/videos/kids$ cd ..
chipppy@MythTV-Main:/var/lib/mythtv/videos$ sudo chown mythtv:mythtv -R /kids
chown: cannot access `/kids': No such file or directory
chipppy@MythTV-Main:/var/lib/mythtv/videos$ sudo chown mythtv:mythtv /kids
chown: cannot access `/kids': No such file or directory
chipppy@MythTV-Main:/var/lib/mythtv/videos$ ls -l
total 16
drwxrwsr-x 84 mythtv mythtv 12288 Feb 17 21:01 kids
chipppy@MythTV-Main:/var/lib/mythtv/videos$ ls
kids
chipppy@MythTV-Main:/var/lib/mythtv/videos$ sudo chown mythtv:mythtv -R
chown: missing operand after `mythtv:mythtv'
Try `chown --help' for more information.
chipppy@MythTV-Main:/var/lib/mythtv/videos$ chown --help
Usage: chown [OPTION]... [OWNER][:[GROUP]] FILE...
  or: chown [OPTION]... --reference=RFILE FILE...
Change the owner and/or group of each FILE to OWNER and/or GROUP.
With --reference, change the owner and group of each FILE to those of RFILE.

  -c, --changes          like verbose but report only when a change is made
      --dereference      affect the referent of each symbolic link (this is
                         the default), rather than the symbolic link itself
  -h, --no-dereference affect each symbolic link instead of any referenced
                         file (useful only on systems that can change the
                         ownership of a symlink)
      --from=CURRENT_OWNER:CURRENT_GROUP
                         change the owner and/or group of each file only if
                         its current owner and/or group match those specified
                         here.  Either may be omitted, in which case a match
                         is not required for the omitted attribute
      --no-preserve-root  do not treat `/' specially (the default)
      --preserve-root    fail to operate recursively on `/'
  -f, --silent, --quiet  suppress most error messages
      --reference=RFILE  use RFILE's owner and group rather than
                         specifying OWNER:GROUP values
  -R, --recursive        operate on files and directories recursively
  -v, --verbose          output a diagnostic for every file processed

The following options modify how a hierarchy is traversed when the -R
option is also specified. If more than one is specified, only the final
one takes effect.

  -H if a command line argument is a symbolic link
                         to a directory, traverse it
  -L traverse every symbolic link to a directory
                         encountered
  -P do not traverse any symbolic links (default)

      --help display this help and exit
      --version output version information and exit

Owner is unchanged if missing. Group is unchanged if missing, but changed
to login group if implied by a `:' following a symbolic OWNER.
OWNER and GROUP may be numeric as well as symbolic.

Examples:
  chown root /u Change the owner of /u to "root".
  chown root:staff /u Likewise, but also change its group to "staff".
  chown -hR root /u Change the owner of /u and subfiles to "root".

Report chown bugs to bug-coreutils@gnu.org
GNU coreutils home page: <http://www.gnu.org/software/coreutils/>
General help using GNU software: <http://www.gnu.org/gethelp/>
For complete documentation, run: info coreutils 'chown invocation'
chipppy@MythTV-Main:/var/lib/mythtv/videos$ sudo chown -hR mythtv:mythtv /kids
chown: cannot access `/kids': No such file or directory
chipppy@MythTV-Main:/var/lib/mythtv/videos$ sudo chown -hR mythtv:mythtv /var/lib/mythtv/videos/kids
chipppy@MythTV-Main:/var/lib/mythtv/videos$ sudo chmod 664 -R /var/lib/mythtv/videos/kids
chipppy@MythTV-Main:/var/lib/mythtv/videos$ 

```

What I have ended up with is 

/kids owner:mythtv:RW group:mthtv:RW, other R only.  Plus warning symbol below other box followed by 'the file permissions are inconsistent, you may not be able to work with files in this folder'.

When I drill into /kids the files and folder seem to be all there but (oh a but, that not good)

The single files are all the correct types (mpeg-4, iso, avi, etc) but have the permissions of owner:root (root):RW, group:root:RW, other RW.
When I try to open a file (play movie with both VLC and mplayer) they get a permission denied error

The folders are type:unknown and have permissions of owner:root (root):RW, group:root:RW, other RW.
As the folders are type unknown I cannot drill into then to check what has happen with the files.

This leaves me with 2 issues
1. What did I do wrong when changing the file owner and permissions recursively. and how do I fix this so I get it all correct?
2. How do I get my folders back to type:folder (recursively if possible as there is a lot of folder but I will do singly if its the only option).

Cheers
Chipppy

---

### Post by klc5555 on 2013-03-29
Short answer: You  cd'ed to /var/lib/mythtv/videos  Then you looked for a directory /kids

The leading "/" in /kids means that it should be a root directory. So naturally it's not found. Once you're in /var/lib/mythtv/videos the next level down would be simply "kids"  (no "/")

But the first time you specified the full path /var/lib/mythtv/videos/kids, you also typoed "mythtv" ("mthtv") So naturally it's not found either.

On the final attempt (from within /var/lib/mythtv/videos) you neglected to indicate any directory at all for the command to operate on (kids). So the command couldn't complete.

Eliminate these three errors and you should experience better success.

---

### Post by chipppy on 2013-03-29
Good Evening

Thanks for the advice about the (no /) and tried the following

```
chipppy@MythTV-Main:/var/lib/mythtv/videos$ sudo chown -hR mythtv:mythtv kids
[sudo] password for chipppy: 
chipppy@MythTV-Main:/var/lib/mythtv/videos$ sudo chmod 664 -R kids
chipppy@MythTV-Main:/var/lib/mythtv/videos$ 

```

end result is no change both on the permission side and the type unknown.
What silly simple mistake have I made?

Cheers 
Chipppy

---

### Post by steeldriver on 2013-03-29
> **chipppy said:**
> What silly simple mistake have I made?

```
chmod 664 -R kids
```

first gives the *directory* 'kids' mode 664 - but directories need execute permissions in order to be opened. So it then can't open 'kids' to change the mode of the files within it.

What you probably wanted assuming 'kids' contains no subdirectories - only plain files - was

```
chmod 664 kids**/***
```

If 'kids' contains subdirs, you could have done

```
sudo chmod -R ug=rwX,o=rX kids
```

which will recursively set plain files rw-rw-r-- and dirs rwxrwxr-x  


Now. How to fix it. 

If 'kids' contains no subdirectories you can just do

```
sudo chmod 775 kids
sudo chmod 664 kids/*
```

If there are subdirs, then it's a bit more complicated but you can try

```
sudo chmod 775 kids
sudo find kids/ -type d -exec chmod 775 {} \;
sudo find kids/ -type f -exec chmod 664 {} \;
```

These all assume you are already in the /var/lib/mythtv/videos directory

Hope this helps

---

### Post by chipppy on 2013-03-29
Good Mornig

Ok.  I have kids folder with sub folder and files.  inside the sub folders are more sub folders and files.  This can go on for 6 or 7 levels.

so from your reply
> If there are subdirs, then it's a bit more complicated but you can try

```
sudo chmod 775 kids
sudo find kids/ -type d -exec chmod 775 {} \;
sudo find kids/ -type f -exec chmod 664 {} \;
```

These all assume you are already in the /var/lib/mythtv/videos directory
The assumpotion is correct

OK so I entered
```
sudo chmod 775 kids
```
This fixed the kids folder.  All the folders reappeared with type folder and the files got the correct type as well.  all the sizes (byte) returned tpo the correct size, but the permissions owner:root (root):RW, group:root:RW, other:RW was still a problem

I did the entered
```
sudo find kids/ -type d -exec chmod 775 {} \;
sudo find kids/ -type f -exec chmod 664 {} \;
```

All good AND the permissions went to owner:mythtv:RW, group:mythtv:RW, other Read only.

My kids are  going to be soooo stoked that you guys were able to get theremythbox work properly again.  

[SIZE=6]HUGE THANKS PPL[/SIZE]

What I dont undderstand is why did the owner and group go from root to mythtv when we did a chmod?  Shouldnt of I needed a chown to do that?

Cheers
chipppy

---

### Post by The Cog on 2013-03-29
> What I dont undderstand is why did the owner and group go from root to mythtv when we did a chmod? Shouldnt of I needed a chown to do that?Yes, it needs a chown to change the owner. I wonder of you did a recursive chown before changing the directories with chmod, thereby changing the owner and then making the files inaccessible?

---

### Post by chipppy on 2013-04-02
Good Afternoon

Yep originally I did the chown and then the chmod.  That may have been my undoing.  The bit I dont understand is why at the end when I only did the chmod the owner changed to as per the original chown (2 days before) and fixed the root ownership issue that I created?

Anyway a mythtv question to try and eliminate the issue in the first place

How do I copy a file (moive) from one computer into my mythtv computer directory so that the copied file has the required permissions.
eg
chipppyComptuer : moivefile.avi, permissions are owner:chipppy:RWX, group:chipppy-main:RX, other Read only.

Step 1 Copy file from chipppyComputer to USB stick
Step 2 Copy file from USB stick to mythtvcomputer in /var/lib/mytthtv/videos/kids (required permissions will be owner:mythtv:RW, group:mythtv:RW, other Read only)

How do I get the file accross and the permissions correct?

Cheers
chipppy

---

