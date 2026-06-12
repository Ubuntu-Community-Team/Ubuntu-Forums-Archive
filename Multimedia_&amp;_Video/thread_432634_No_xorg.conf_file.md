---
title: "No xorg.conf file?"
date: 2007-05-04
forum: Multimedia &amp; Video
---

### Post by mcmilner on 2007-05-04
While searching for how to change the resolution on my screen, I came across several posts referring to the xorg.conf file and helpful hints on what to do with it.  Is it possible that I don't have an xorg.conf file?  Here are a few commands I typed and the results.

m@Acer:~$ sudo cat /etc/x11/xorg.conf
cat: /etc/x11/xorg.conf: No such file or directory
m@Acer:~$ cd xorg.conf
bash: cd: xorg.conf: No such file or directory
m@Acer:~$ cd etc/x11/xorg.conf
bash: cd: etc/x11/xorg.conf: No such file or directory
m@Acer:~$ sudo gededit /etc/x11/xorg.conf
sudo: gededit: command not found
m@Acer:~$ sudo gedit /etc/x11/xorg.conf
   GEDIT BRINGS UP NEW, BLANK FILE

---

### Post by bashologist on 2007-05-04
It's case sensitive. gksudo gedit /etc/X11/xorg.conf

---

### Post by mcmilner on 2007-05-04
> **bashologist said:**
> It's case sensitive. gksudo gedit /etc/X11/xorg.conf

Thanks.  i'll try, again.

---

### Post by mcmilner on 2007-05-04
Thank you.  This time I got the file.  The graphics driver is an "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"  All the settings in the last sections are for 1280 x 800, but that isn't what I'm getting.  From the Preferences menu, I assume I'm getting 1024 x 768.
So, I thought I'd reconfigure and see what happened and typed
sudo dpkg-reconfigure xserver-xorg
The screen that came up does not have Intel graphics cards.
Now what?

---

### Post by HeavyAl on 2007-05-04
Post your xorg.conf .. that will help in diagnosing the problem.

---

### Post by NilsE on 2007-05-04
> **mcmilner said:**
> The screen that came up does not have Intel graphics cards.
Now what?

i810 is the old intel driver.  You can install the new intel driver by searching on "video-intel" without the quotes in Synaptic but try the i810 first unless you need dual heads.

Also, try this command instead:

sudo dpkg-reconfigure -phigh xserver-xorg

This way you only have to answer the video questions.

---

### Post by ronocdh on 2007-05-04
> **NilsE said:**
> 
Also, try this command instead:

sudo dpkg-reconfigure -phigh xserver-xorg

This way you only have to answer the video questions.
That is freaking awesome, thank you!

Also, OP, have you grabbed the 915resolution package from the repos?

---

### Post by mcmilner on 2007-05-05
O.K., tried the i810 driver, but nothing changed.  Then I got the new driver from Synaptic.  Success!

This leads to another question: I didn't change anything else int he xorg.conf file, but it seems to have changed my keyboard to "us" all by itself.  So I changed it back to "fr."  That was a system message to the effect that changed xorg.conf files are not automatically updated.  If I want mine automatically updated in the future, I should run:  sudo dpkg-reconfigure -phigh xserver-xorg.

But that's the command I ran to get the video driver screen up.

Am I missing something here?  I've bought two Ubuntu Linux manuals.  Maybe I need to buy a vanilla Linux manual, so I'll have the commands and the explanations?

And thanks for the help, so far.  You guys are great!

---

### Post by NilsE on 2007-05-05
If you want to configure ALL server devices then leave out the -phigh and it will step you through all the choices like keyboard etc.

You can take the default for everything unless you want to change it like the keyboard.

---

### Post by mcmilner on 2007-05-05
Thank you!

---

### Post by NilsE on 2007-05-05
> **mcmilner said:**
> Thank you!
Your welcome.  Have fun

---

