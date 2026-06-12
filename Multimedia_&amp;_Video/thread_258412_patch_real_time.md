---
title: "patch real time"
date: 2006-09-15
forum: Multimedia &amp; Video
---

### Post by damu on 2006-09-15
I've tried to follow this method to apply the real time patch :

> 
Open a terminal, and type :

sudo apt-get install module-assistant

then launch the module-assistant :

sudo module-assistant

Slect the update menu 

Then select the "PREPARE" menu . It will download everything needed for the next steps

Sélect the "SELECT" menu , and choose "RealTime-lsm module" in the list, and press OK.

In the text menu select "GET", "BUILD" et "INSTALL" following this order.

Your realtime patch is installed. You will need to restart for the change to be effective.

SO that it works every time you boot, edit the file /etc/default/realtime file.
Make sure that you have the  ligne ENABLE=yes :

   1. enable loading of module at startup

ENABLE=yes

and that you have

   1. parameter settings for module

PARAMETERS="gid=29"
Open Jack and in the settings, configuration, realtime... 

Unfortunately, at the Build step, I've been warned that some packages were missing, and had to cancel the installation...Any clue? I sit due to the fact that I just upgraded Ubuntu (with a kernel update)?

---

### Post by dolson on 2006-09-15
I don't know where you got that info from, but the proper method for the realtime-lsm module is here:
[http://ubuntustudio.com/wiki/index.php/Breezy:Realtime_LSM](http://ubuntustudio.com/wiki/index.php/Breezy:Realtime_LSM)

HOWEVER: You do not need this on Dapper or Edgy. Please don't follow Breezy tutorials on more recent distros. If you use Breezy, um, I'm sorry.

---

### Post by damu on 2006-09-16
Thanks Dolson.

I got the info from [a very exciting website]("http://mdesigner.free.fr/index.php?2006/09/14/72-installation-du-patch-realtime-pour-ubuntu") (in french...time to improve your french... :lol: ) which deals about open source and music.

I sent an email to the author of the article, so that he can take in account my experience and your suggestions, and  eventually update his article. 
I obviously pointed Ubuntu Studio, and this thread, so that we can eventually interact.
One solution might be a french translation of your wiki!

---

