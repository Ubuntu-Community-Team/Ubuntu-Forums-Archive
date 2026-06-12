---
title: "Timeout while copying files trough network"
date: 2011-05-09
forum: Networking &amp; Wireless
---

### Post by MartinMAP on 2011-05-09
Hello,

im copying my files from desctop-pc to my notebook to backup them. Im using the samba windows-network. Its a lot of files and sometimes the copy-dialog pops up cause a timeout occurred. So the actual file gets damaged. I can continue the copying after about 1 minute till the next timeout-massage pops up. And so on... whats the reason for that timeout? How can i set the time or deactivate the timeouts?

Thanks!
Martin

---

### Post by SecretCode on 2011-05-09
Is one of the systems a Windows OS? If they are both Linux, using rsync is a very good way to avoid this - with the --partial option, interrupted copies can later on be resumed from wherever they got to. Even with Windows, it's possible and worthwhile to install a version of rsync.

I don't think removing the timeout will help ... it could just result in the copying hanging. The reason for the timeout: copying can be interrupted or corrupted for various reasons. Is this within one building? Are you using wireless? Sometimes I have a seen a problem with the wrong MTU size set for wireless connections, and it does sometimes affect Windows copying.

---

### Post by MartinMAP on 2011-05-09
Hello!

I already tryed rsync with grsync. But i didn find a option to sync files over network. I tried several paths to test it - but im too noob i guess :)

Here is what I did:

/home/map/bilder (as source)

and as destination I tried:

//smb://192.168.1.5/home/map/bilder 
192.168.1.5/home/map/bilder
map@map-note/home/map/bilder
map@192.168.1.5/home/map/bilder

...etc...

...nothing happend

I got a lot of problems with my network - i have no idea if I AM too noob, or if my system  just went stupid: [http://ubuntuforums.org/showthread.php?t=1752989](http://ubuntuforums.org/showthread.php?t=1752989)

MAP

---

