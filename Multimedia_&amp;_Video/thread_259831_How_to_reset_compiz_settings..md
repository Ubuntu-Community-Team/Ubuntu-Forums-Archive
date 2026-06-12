---
title: "How to reset compiz settings."
date: 2006-09-17
forum: Multimedia &amp; Video
---

### Post by fizgig on 2006-09-17
[FONT=Verdana][SIZE=3]I followed the direction [here]("http://www.compiz.net/viewtopic.php?id=389") to install compiz (worked great).  I then proceeded to mess with the compiz settings such that it wouldn't load anymore.

The symptoms were:
1. No compiz effects
2. No menu bars.

In the instructions, there is a line to install a few packages:

> sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome cgwd cgwd-themes
 
So I simply purged them:
> sudo dpkg --purge compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome cgwd cgwd-themes 
I then deleted this file: /home/yourname/.compiz/csm_settings

I then reinstalled the above packages and I was back to normal.  I'm sure there was probably an easier way to do it but it worked for me.[/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT]

---

### Post by louis_nichols on 2006-09-18
I think the easiest way would be to simply delete all folders which save settings:

~/.gconf/apps/compiz
~/.compiz

and others related

---

### Post by diaz028 on 2007-12-05
Didnt work for me, same symptoms though.... 

Do i need to re-install my OS?

-D

---

### Post by wynjones1 on 2008-03-02
I you just go to Preferences->Reset To Defaults, That should solve your problem.

---

