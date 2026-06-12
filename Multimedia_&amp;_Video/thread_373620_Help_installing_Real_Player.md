---
title: "Help installing Real Player"
date: 2007-03-01
forum: Multimedia &amp; Video
---

### Post by keithk50 on 2007-03-01
Hi,   Being new to Ubuntu I am really having problems installing Real Player.   All my own fault of course, as after years with windoze have never encountered the 'Terminal' before!
Using Terminal I followed the instructions and installed the player (so I thought).  This action resulted with a folder named Real Player sitting on my desktop.  The RealPlayer10GOLD.bin downloaded file is also on the desktop.   The last advice received was, Quote:

"Delete the folder using the command line and re-install the player to the /usr/bin directory.   There should be a prompt that appears during the command line installation which allows you to do this.   At the moment the file is just sitting on your desktop which explains why its not linked properly".

I am at a complete loss of how to acheive this.   I have looked through hundreds of threads trying to find the correct terminal codes but to be honest I am afraid of messing up my new Ubuntu system completely.  Any help would be great but would appreciate it explained for a complete beginner.   Thanks.:)

---

### Post by an.echte.trilingue on 2007-03-01
Linux usually uses a program manager and program repositories on line to install software.  There is is also a lot of documentation online in the wiki that will help you with things like this.  You should read [this page]("https://help.ubuntu.com/community/RestrictedFormats") to get things like real player and DVDs working.  (the link to the page on real player itself is about half way down the page).

Take care
-mat

---

### Post by keithk50 on 2007-03-01
Many thanks for your quick reply, the link looks really helpful.  I shall have a good look through it.   You learn something new everyday.   Thanks again.   Keith

PS   Will have to learn some French!

---

### Post by kevinlyfellow on 2007-03-01
ok, I'm assuming you installed the program using sudo?

This is what you need to do in the command line

```
sudo rm -r ~/Desktop/Realplayer
```

Keep in mind that the name of the folder may not correct in what I wrote.

To reinstall realplayer, follow the directions like before, but when it asks you
```
Enter the complete path to the directory where you want
RealPlayer to be installed.  You must specify the full
pathname of the directory and have write privileges to
the chosen directory.
Directory:  [/home/username/.desktop/RealPlayer]: 
```
then say instead
```
/opt/RealPlayer
```

and then you can link it into /usr/bin if it doesn't do it for you already (you will know this if you go into the terminal and type realplay and realplayer pops up).

Make sure to run the installer like this
```
cd Desktop
sudo ./RealPlayer10GOLD.bin 
```

---

### Post by keithk50 on 2007-03-01
Thankyou very much for your detailed reply.   I shall follow the instructions very carefully (and slowly).   Shall post results once completed.  May be a while!!   Take care.     

Keith

---

