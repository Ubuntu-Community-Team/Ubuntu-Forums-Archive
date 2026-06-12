---
title: "[SOLVED] Unable to delete a file in OS X"
date: 2007-07-26
forum: Mac OSX
---

### Post by aysiu on 2007-07-26
For some strange reason, a root-owned folder was in my wife's trash on her Powerbook (it's running Tiger--not sure if that matters). She would try to empty the trash, and it would make the "empty trash" sound, but the trash would stay full.

She hoped I'd be able to solve the problem through the terminal. I tried, and I couldn't get rid of the file. I did ```
sudo rm -rf nameoffolder
``` but I was told the folder wasn't empty. So I went in one level deep to try to remove the folder insider ```
cd nameoffolder
sudo rm -rf secondfolder
``` I got the same message about the folder not being empty. So I went into that folder and tried to remove the file inside (some .html file with weird encoding--a lot of question marks in the file name) and was told the file didn't exist. Here's the weird part. If I did a ```
ls
``` I'd see the .html file there. If, however, I did a ```
ls -al
``` all I'd see were the . and .. listings.

As a temporary workaround, I enabled a graphical root login, moved the folder from the user's trash to root's trash, but even emptying the trash as root wouldn't work (same problem... "empty trash" sound but the trash didn't empty).

Is there any way to get rid of this fake-existing file?

---

### Post by smoker on 2007-07-26
just a suggestion, can you boot into a linux live-cd, find the file and delete it then?

have you opened the file, tried deleting the contents, or renaming then deleting, or changing the file attributes then deleting?

best of luck

---

### Post by aysiu on 2007-07-26
Yeah, I've tried all that. Thanks for the suggestions, though.

Apparently, Linux can't write to HFS+ unless journaling is turned off. And I can't open the file, because it doesn't exist, apparently... even though it does exist.

I tried changing ownership of the folder recursively, and it changed ownership of the first two folders, but it wouldn't change ownership of the .html file... because it apparently doesn't exist.

---

### Post by apunc1 on 2007-07-26
have you tried 

```
cd .Trash
sudo rm -r *
```

beware, it deletes everything in the trash.

---

### Post by aysiu on 2007-07-26
> **apunc1 said:**
> have you tried 

```
cd .Trash
sudo rm -r *
```

beware, it deletes everything in the trash.
Yeah, I've tried that, too. Here's actual terminal output (names have been changed to protect my wife): ```
Usernames-Computer:~ root# **cd .Trash/**
Usernames-Computer:~/.Trash root# **ls**
.DS_Store               Adobe Photoshop CS2
``` So I've entered the Trash directory and listed the contents. ```
Usernames-Computer:~/.Trash root# **sudo rm -r *** 
rm: Adobe Photoshop CS2/Legal.localized/Tie&#770;&#769;ng Vie&#770;&#803;t.html: No such file or directory
rm: Adobe Photoshop CS2/Legal.localized: Directory not empty
rm: Adobe Photoshop CS2: Directory not empty
``` I try to remove everything there, and I'm told the directories aren't empty and that that file doesn't exist. ```
Usernames-Computer:~/.Trash root# **sudo rm -rf ***
rm: Adobe Photoshop CS2/Legal.localized: Directory not empty
rm: Adobe Photoshop CS2: Directory not empty
``` If I try with the force flag, I still get the same error message. ```
Usernames-Computer:~/.Trash root# **cd Adobe\ Photoshop\ CS2/**
Usernames-Computer:~/.Trash/Adobe Photoshop CS2 root# **rm -r Legal.localized** 
rm: Legal.localized/Tie&#770;&#769;ng Vie&#770;&#803;t.html: No such file or directory
rm: Legal.localized: Directory not empty
Usernames-Computer:~/.Trash/Adobe Photoshop CS2 root# **cd Legal.localized **
Usernames-Computer:~/.Trash/Adobe Photoshop CS2/Legal.localized root# **rm Tie\314\202\314\201ng\ Vie\314\202\314\243t.html **
rm: Tie&#770;&#769;ng Vie&#770;&#803;t.html: No such file or directory
``` And if I *cd* into each directory, I get these error messages. Trying to remove the .html file directly tells me the file doesn't exist. ```
Usernames-Computer:~/.Trash/Adobe Photoshop CS2/Legal.localized root# **ls**
Tie????ng Vie????t.html
``` And listing what's in the directory tells me the file does exist. ```
Usernames-Computer:~/.Trash/Adobe Photoshop CS2/Legal.localized root# **ls -al**
ls: Tie&#770;&#769;ng Vie&#770;&#803;t.html: No such file or directory
total 0
drwxrwxrwx   3 username  username  102 Jul 22 21:49 .
drwxrwxrwx   3 username  username  102 Jul 24 22:30 ..
Usernames-Computer:~/.Trash/Adobe Photoshop CS2/Legal.localized root# 
``` But listing with more information tells me the file *doesn't* exist.

---

### Post by aysiu on 2007-07-26
Well, still no progress.

But through Google searches, I found out my wife isn't the only one experiencing this problem. It appears to be some kind of character encoding issue.
[New twist on Trash problems](http://forums.macrumors.com/showthread.php?t=227841)
[how to delete files which special characters on Mac OS 10.3](http://mail.python.org/pipermail/pythonmac-sig/2004-January/009948.html)

---

### Post by apunc1 on 2007-07-26
yes, it appears you've tried all of the normal solutions
have you tried moving the file from trash back into the /home directory and booting into OS9 and deleting it that way?

---

### Post by aysiu on 2007-07-26
> **apunc1 said:**
> yes, it appears you've tried all of the normal solutions
have you tried moving the file from trash back into the /home directory and booting into OS9 and deleting it that way?
No, I haven't tried that yet.

I Googled around some more and have apparently found a solution:
[Tieng Viet.html - How To Delete the Undeletable](http://www.spiderjay.com/blog/?p=37)

I'm in the process of booting into "safe mode." It takes a really long time... We'll see if it all works out.

---

### Post by aysiu on 2007-07-26
It worked!

Shut down.

Boot up. Hold the  **Shift** key while booting up.

This will take forever. It took about five minutes for the person who posted the solution in that link. I took about ten minutes on my wife's Powerbook.

Log in. Empty the trash.

Reboot into normal mode.

---

### Post by apunc1 on 2007-07-26
yikes. Adobe should fix that in CS3

---

### Post by aysiu on 2007-07-26
> **apunc1 said:**
> yikes. Adobe should fix that in CS3
Well, at least there's a workaround in the meantime.

---

