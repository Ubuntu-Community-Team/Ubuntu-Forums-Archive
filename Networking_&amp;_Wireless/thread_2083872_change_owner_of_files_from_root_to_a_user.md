---
title: "change owner of files from root to a user"
date: 2012-11-13
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2012-11-13
I have some picture files.
I had to copy these onto a second partition ext4 which is apparrently owned by root. I used to boot off that drive partition.

I had to create a folder by using gksu nautilus and copied some files.
then I had to change permissions just so the user could see them

Now I would like to change the owner to both tricia and scott using the chown command on that entire folder.

never mind, I figured this out
long command but it was fairly easy
[http://en.wikipedia.org/wiki/Chown](http://en.wikipedia.org/wiki/Chown)
> tricia@scott-P5QC:/media/0db1fb5a-0727-4347-bfa7-a551d8db6632$ sudo chown tricia /media/0db1fb5a-0727-4347-bfa7-a551d8db6632/Jessica\ pictures\ from\ her\ computer/Jess\ Costa\ Rica
[sudo] password for tricia: 
tricia@scott-P5QC:/media/0db1fb5a-0727-4347-bfa7-a551d8db6632$ 


---

### Post by gerowen on 2012-11-13
Glad you got it figured out, but thought I'd throw my suggestion in here for your future reference, take it for what you think it's worth.

Since you are no longer booting from the drive and it's just a storage location, you could create a group, add the two users tricia and scott to that group, and change the owner to your user account, the owning group to the group you created, and then apply appropriate permissions.  By doing it this way you have the option of just adding users to the group to grant them permissions.

Make a new group with:
```
sudo groupadd GROUPNAME
```

Add users to the group with:
```
sudo usermod -a -G GROUPNAME tricia
sudo usermod -a -G GROUPNAME scott
```

Now change the owner of the drive to one of yourselves:
```
sudo chown -R scott /media/DRIVENAME
```

Change the owning group:
```
sudo chgrp -R GROUPNAME /media/DRIVENAME
```

Now set permissions so the owning user (scott), and the owning group we created have full permissions, and all others are denied access.  You can change this number as you deem appropriate.  You can read more about this method of chmod at:
[http://linuxguide.sourceforge.net/linux-chmod.html](http://linuxguide.sourceforge.net/linux-chmod.html)
```
sudo chmod -R 770 /media/DRIVENAME
```

Since you said you've figured it out, please use the "Thread Tools" button at top to mark the thread as solved.

---

### Post by sdowney717 on 2012-11-14
Hi, did that, set group to winhdd, a group I had already created with the users a mamner of the group.

I get the name of the drive from nautilus, Copy it off the header or from its properties page.

One thing is you have to know how to negotiate the landscape from terminal ( a unneccessary pain IMO)
cd .. to back out of dir folders 
ls to list dirs to see where you are
type a \ in front of spaces to escape them

I have tried making some changes using the gui permissions page but that seems to either not work, or has insufficient complexity to do the job.

Any thoughts on a gui to do permissions using point and click?

---

### Post by pkadeel on 2012-11-14
> **sdowney717 said:**
> Hi, did that, set group to winhdd, a group I had already created with the users a mamner of the group.

I get the name of the drive from nautilus, Copy it off the header or from its properties page.

One thing is you have to know how to negotiate the landscape from terminal ( a unneccessary pain IMO)
cd .. to back out of dir folders 
ls to list dirs to see where you are
type a \ in front of spaces to escape them

I have tried making some changes using the gui permissions page but that seems to either not work, or has insufficient complexity to do the job.

Any thoughts on a gui to do permissions using point and click?
Yes there is a way in Nautilus. I don't have Nautilus right now so can't tell the exact location but it is present in the Preferences where you can enable the detailed permission settings. However when you have to change the permission which require sudo access then it won't work right away. for that matter you will have to run Nautilus with sudo access. the method to do that is as follows
```
gksu nautilus
```
It will ask for password in a graphical UI. Be aware that modifying things in a GUI with root access can be dangerous so be cautious about what you do and close the Nautilus as soon the required job is done.

---

### Post by sdowney717 on 2012-11-14
yes try that then also reading on this, I am missing a whole lot of features?
screenshot shows this
from this [http://linux.about.com/library/gnome/blgnome6n6n.htm](http://linux.about.com/library/gnome/blgnome6n6n.htm)

seems to imply you can view things like 

> Text view

Displays the permissions that you select from the Read, Write, and Execute options, in text format.

Number view

Displays the permissions that you select from the Read, Write, and Execute options, in text format.

I do not see this in nautilus file permission gui

---

### Post by Morbius1 on 2012-11-14
I'd like to point out that you are going to be in an infinite loop changing ownership / permissions unless you take an extra step.

Let's say you changed ownership to have group = winhdd and changed permissions so that everyone in that group has r/w access. Now tricia adds a file to the folder. It will save with owner:group = tricia:tricia not tricia:winhdd so scott is out of luck in having write access.

One way out of this is to use something called setgid:

[1] Change group to winhdd ( which I think you have already done ):
```
sudo chown :winhdd /path/to/folder
```[2] Change permissions and enable the setgid bit:
```
sudo chmod 2775 /path/to/folder
```[COLOR=Blue]*Note: Do not use a "-R" - you should avoid using a "-R" with "number" permissions.*[/COLOR]

The "2" is the "setgid" bit. From that point on every file added to the folder will "inherit" the group of that folder - so in this case all files added will have winhdd as the group. Local non-root users on Ubuntu automatically save files as 664 so every file added will allow write access by group - in this case winhdd.

---

### Post by sdowney717 on 2012-11-14
Thanks.

This set gid is not available from the Nautilus permissions page and is pretty important in its function.

tested and your right

modified tricia permission with setgid bit in one folder not another. Then made a test file and here is the result, one locked other is not when viewed by scott.

How would you unset the gid?

---

### Post by Morbius1 on 2012-11-14
I did not understand your last post and I am not at all used to looking at files as icons. Please post the output of:
```
ls -al /path/to/testparmis
```
As long as both users are part of the winhdd group one user cannot be "locked" out from the other.

Anyway to answer your question:
```
sudo chmod g-s /path/to/folder
```

---

### Post by sdowney717 on 2012-11-14
All I am saying is your right and I did a test to demonstrate it to myself.
Created one new folder in directories, one had the setgid set other did not and the resultant permissions were shown in the gui display.
I have since set new files to inherit the desired permissions.

---

### Post by sdowney717 on 2012-11-18
> Note: Do not use a "-R" - you should avoid using a "-R" with "number" permissions.

Why not?

---

### Post by westie457 on 2012-11-18
A small extract from ```
man chown
```
 -R, --recursive
              operate on files and directories recursively


Basically this means that ownership will be changed from whatever to username for example. Including those files owned by root. The only way to recover from this scenario is to re-install or a clean install.

Hope this helps.

---

### Post by sdowney717 on 2012-11-18
should be ok on files I own not system files right?

---

### Post by Morbius1 on 2012-11-19
Octal chmod'ing ( using numbers ) isn't smart enough to differentiate between a directory and a file. A "chmod -R 755" sets the execute bit on all directories which you must do to "open" them to see what's inside. But it also sets all files as executable which is something you do not want to do.

A better way to do a "chmod -R 755" is the Jedi way:
```
chmod -R a+rwX,go-w
```All folders will be set as executable but all files will not unless they were set to executable to begin with. That's what the big "X" does.

---

### Post by sdowney717 on 2012-11-19
Ok, I had lots of music files which I moved into the music folder. Then for another user (tricia when logged on) to be able to use them I did some chmod chown commands. The other user can now reach into my user account and play the music.
However all the music mp3's are now executable.

To change them back to non executable, what to do?

some files in a folder
```
scott@scott-P5QC:~$ ls -l /home/scott/Music/Kutless/Sea\ of\ Faces
total 71648
-rwxrwsr-x 1 root winhdd 5681645 Jun 27  2007 01 Not What You See.mp3
-rwxrwsr-x 1 root winhdd 7304050 Jun 27  2007 02 All Alone.mp3
-rwxrwsr-x 1 root winhdd 6564240 Jun 27  2007 03 Better for You.mp3
-rwxrwsr-x 1 root winhdd 6879035 Jun 27  2007 04 Sea of Faces.mp3
-rwxrwsr-x 1 root winhdd 6223560 Jun 27  2007 05 Let You In.mp3
-rwxrwsr-x 1 root winhdd 5917950 Jun 27  2007 06 Passion.mp3
-rwxrwsr-x 1 root winhdd 6732910 Jun 27  2007 07 Perspectives.mp3
-rwxrwsr-x 1 root winhdd 6527500 Jun 27  2007 08 Treason.mp3
-rwxrwsr-x 1 root winhdd 7272320 Jun 27  2007 09 All the Words.mp3
-rwxrwsr-x 1 root winhdd 6694500 Jun 27  2007 10 Troubled Heart.mp3
-rwxrwsr-x 1 root winhdd 7516140 Jun 27  2007 11 It's Like Me.mp3
-rwxrwsr-x 1 root winhdd    9414 Jun 27  2007 AlbumArt_{9809CBDA-8972-432B-A7CF-44ED79D172B8}_Large.jpg
-rwxrwsr-x 1 root winhdd    2672 Jun 27  2007 AlbumArt_{9809CBDA-8972-432B-A7CF-44ED79D172B8}_Small.jpg
-rwxrwsr-x 1 root winhdd    2672 Jun 27  2007 AlbumArtSmall.jpg
-rwxrwsr-x 1 root winhdd    9414 Jun 27  2007 Folder.jpg
scott@scott-P5QC:~$ 

```

some dirs

```
scott@scott-P5QC:~$ ls -l /home/scott/Music
total 3616
-rwxrwsr-x 1 root  winhdd 3606528 Jul 12  2007 01-Tamaterai.mp3
drwx------ 3 scott scott     4096 Sep 24  2011 AC-DC
drwx------ 4 scott scott     4096 Sep 24  2011 Brooks & Dunn
drwxrwsr-x 3 root  winhdd    4096 Oct 29 10:57 country songs
drwx------ 4 scott scott     4096 Sep 24  2011 Creedence Clearwater Revisited
drwxrwsr-x 4 root  winhdd    4096 Oct 29 10:55 Day of Fire
drwxrwsr-x 2 root  winhdd    4096 Oct 29 10:57 Elvis songs
drwx------ 3 scott scott     4096 Sep 24  2011 Eric Church
drwxrwsr-x 3 root  winhdd    4096 Oct 29 10:55 Flyleaf
drwxrwsr-x 4 root  winhdd    4096 Oct 29 10:55 Hawk Nelson
drwxrwsr-x 4 root  winhdd    4096 Oct 29 10:55 iTunes
drwxrwsr-x 3 root  winhdd    4096 Oct 29 10:55 Josh Groban
drwxrwsr-x 3 root  winhdd    4096 Oct 29 10:55 Josh Turner
drwxrwsr-x 3 scott scott     4096 Nov 18 20:22 Kristin Itunes
drwxrwsr-x 4 root  winhdd    4096 Oct 29 10:55 Kutless
drwxrwsr-x 2 root  winhdd    4096 Oct 29 10:56 midisongs
drwxrwsr-x 5 root  winhdd    4096 Oct 29 10:55 Relient K
drwxrwsr-x 3 root  winhdd    4096 Oct 29 10:55 Sanctus Real
drwxrwsr-x 3 root  winhdd    4096 Oct 29 10:55 Sherwood
drwxrwsr-x 3 root  winhdd    4096 Oct 29 10:56 Soundtrack
drwxrwsr-x 4 root  winhdd    4096 Oct 29 10:56 Switchfoot
drwxrwsr-x 3 root  winhdd    4096 Oct 29 10:56 The Fray
drwxrwsr-x 3 root  winhdd    4096 Oct 29 10:56 Thousand Foot Krutch
drwxrwsr-x 3 root  winhdd    4096 Oct 29 10:55 Various

more dirs in a folder
scott@scott-P5QC:~$ ls -l /home/scott/Music/Kutless
total 8
drwxrwsr-x 2 root winhdd 4096 Oct 29 10:55 Hearts of the Innocent
drwxrwsr-x 2 root winhdd 4096 Oct 29 10:55 Sea of Faces
scott@scott-P5QC:~$ 

```

---

### Post by sdowney717 on 2012-11-19
how do you escape a '&' in a folder name?

> tricia@scott-P5QC:~$ sudo chmod -R 2775 /home/scott/Music/Brooks\ &\  Dunn[1] 15028
chmod: cannot access `/home/scott/Music/Brooks ': No such file or directory
 : command not found
[1]+  Exit 1                  sudo chmod -R 2775 /home/scott/Music/Brooks\ 
tricia@scott-P5QC:~$ 


---

### Post by Morbius1 on 2012-11-19
>  To change them back to non executable, what to do?```
sudo chmod -R a-x+X "/home/scott/Music/Kutless/Sea of Faces"
```I think if you then do an ls you will be left with some funky looking files with a big "S" on them because somewhere along the line you must have done a "chmod -R 2775". You usually don't do a recursive setgid on the whole tree you only use setgid on the parent directory. I don't think it will do them any harm to leave them that way.

---

