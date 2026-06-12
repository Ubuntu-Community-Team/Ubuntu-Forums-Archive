---
title: "LIRC questions"
date: 2007-05-17
forum: Multimedia &amp; Video
---

### Post by poke4christ on 2007-05-17
I've got a PVR-150 and I'm working on getting the remote working.  I've gotten through testing and no I'm on the creation of the .lircrc file.  I'm having a little trouble here though.  I created the file using nano, but when I ls the home directory nothing shows up.  However, when I try to nano back into the file, I'm still able to see it.  Also, I tried the command "ln -s ~/.lircrc ~/.mythtv/lircrc" to link to the file, but I just get this error:

ln: creating symbolic link `/home/zach/.mythtv/lircrc' to `/home/zach/.lircrc':
No such file or directory

Am I doing something wrong?

---

### Post by david_2001 on 2007-05-17
> **poke4christ said:**
> 

Also, I tried the command "ln -s ~/.lircrc ~/.mythtv/lircrc" to link to the file, but I just get this error:

ln: creating symbolic link `/home/zach/.mythtv/lircrc' to `/home/zach/.lircrc':
No such file or directory

Am I doing something wrong?

Files with names that begin with a dot, e.g. ".lircrc" are hidden in normal directory listings.  Try "ls -a" or "ls -al" to see .lircrc.

The ln error most likely means that a directory called ".mythtv" does not exist.  Make it with the mkdir command, i.e. "mkdir .mythtv", then try again.

---

### Post by poke4christ on 2007-05-17
> **david_2001 said:**
> Files with names that begin with a dot, e.g. ".lircrc" are hidden in normal directory listings.  Try "ls -a" or "ls -al" to see .lircrc.

The ln error most likely means that a directory called ".mythtv" does not exist.  Make it with the mkdir command, i.e. "mkdir .mythtv", then try again.

Wonderful!  I figured it was something simple like that.  Thanks.  I'm still learning Linux and I appreciate you putting up with simple questions :D.

---

### Post by poke4christ on 2007-05-17
Hey, I've got another question.  Is th home/*user* directory that the "~" refers to refering to the mythtv user or my directory.  I had been using my login directory, but I can understand how this is supposed to be the mythtv directory.  Anyway, it's not working yet so I know I did something wrong.

---

### Post by newlinux on 2007-05-17
If you run mythfrontend as the mythtv user you need to put the file in /home/mythtv/.lircrc and  link it to /home/mythtv/.mythtv/lircrc.

~ refers to the home directory of the user you are logged in as.

---

