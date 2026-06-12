---
title: "Flash problems, YouTube controls"
date: 2009-12-16
forum: Multimedia Software
---

### Post by nightmicu on 2009-12-16
I recently installed Ubuntu 9.10 64 bit on a brand new desktop and have been having a lot of problems with Flash in Firefox 3.5.5 - which was installed after System Update.

My first issues occurred when I upgraded Firefox using Ubuntuzilla, as I have always done in Ubuntu 32 bit distros. After this, Flash stopped working completely, even after uninstalling and reinstalling the Adobe Flash Installer.

Out of frustration, I dumped the system and re-installed. This time, I upgraded everything using System Update. Flash still works but now I am noticing that the controls (Play/Pause, Full Screen, etc) in YouTube work sporadically. Everything works fine when I start a new session and watch one or two videos, then the clicks just do not seem to register.

I've read several other threads and so far nothing seems to really take care of this problem. Is this isolated to 64 bit? Should I consider installing Ubuntu 32 bit instead?

Please help! Trying to have this system running perfectly for a college student.

-Ben

---

### Post by iissmart on 2009-12-16
This happens to me as well. Clicking works in that the button reacts to the mouse (changes size, color), but nothing actually happens. I have to click play ~20 times before it actually starts playing. This happens for *every* flash object though, not just youtube.

---

### Post by HappyFeet on 2009-12-16
First, uninstall the flash you have. Then do:
```
sudo apt-get clean && sudo apt-get autoremove
```
Then get the [64bit flash]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz") file.

Right click it and **extract here**. You will be left with **libflashplayer.so** file. Put the libflashplayer.so file in your home folder.

Then do:```
sudo cp /home/your_user_name/libflashplayer.so /usr/lib64/mozilla/plugins
```

Make sure to put *your name* where I wrote your_user_name.

Restart firefox if open.

You see, you were using the 32bit flash file which does not always work well in 64bit ubuntu.

---

### Post by nightmicu on 2009-12-16
HappyFeet, thanks for the solution. Everything seems to be working fine now :)

---

### Post by iissmart on 2009-12-16
Where would I put the .so file for 64 bit Chrome?

---

### Post by plapczynski on 2009-12-16
Thanks I needed that fix!

---

### Post by nanotube on 2009-12-17
> **iissmart said:**
> Where would I put the .so file for 64 bit Chrome?

~/.mozilla/plugins/

(create plugins dir if it doesn't exist)

---

### Post by nechus on 2010-01-01
HappyFeet... you saved my life!!!  That plugin was driving me crazy!!  Thank you, thank you, thank you.

---

### Post by gosox on 2010-01-01
Fixed it, thanks.
Only thing is, i put the .so in the dir WITH the other flash, instead of deleting the old flash, and didn't need to restart FF, but either way, it works. \\:D/

---

### Post by HappyFeet on 2010-01-01
> **gosox said:**
> Fixed it, thanks.
Only thing is, i put the .so in the dir WITH the other flash, instead of deleting the old flash, and didn't need to restart FF, but either way, it works. \\:D/

Glad it works, but it is safe to delete the old one.

---

### Post by gosox on 2010-01-01
Yeah it is better, incase of plugin interaction problems, but it'll be alright for now.

---

### Post by De4dSpace on 2010-01-08
Thanx dood!  Big ups!  Sarma Soup...mmm [COLOR=Red]Paprika[/COLOR]

---

### Post by rand()m on 2010-01-08
This might be helpful if you still have any problems.

[http://www.youtube.com/watch?v=O2EPwlFLZMY](http://www.youtube.com/watch?v=O2EPwlFLZMY)

---

