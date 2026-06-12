---
title: "DVB WebScheduler Installation!"
date: 2007-04-05
forum: Multimedia &amp; Video
---

### Post by gundo on 2007-04-05
Hello everyone,
Ive been XP free for about a week now! 

Ive managed to get most of my little quirks sorted, but I havnt managed to get DVB Webscehduler installed yet. 
Its a java server that runs through a web browser to record TV shows thru a DVB-T card.
I downloaded the tar package from sourceforge, but now I am not sure what to do with it or how to get it working.
I extracted all the files and I can browse through them all, just dont know how to install/launch it!

Anybody know what I have to do? 
Thanks very much,

Mark

---

### Post by gundo on 2007-04-07
Is there no one out there in linux land who can shed some light on this one?
Thanks,
Mark

---

### Post by [S2] on 2007-04-16
> **gundo said:**
> Hello everyone,
I extracted all the files and I can browse through them all, just dont know how to install/launch it!


Just search for the executable and run it!

---

### Post by jroosh on 2007-07-06
The original thread is in the Australian dvbowners.com forum

[http://forums.dvbowners.com/index.php?showtopic=7740&hl=Linux&st=0]("http://forums.dvbowners.com/index.php?showtopic=7740&hl=Linux&st=0")

to start the app, open a terminal window and go to your webscheduler directory

then type

[INDENT]**java -jar WebScheduler.jar**[/INDENT]

ATM the app uses zapdvb to do the recording

[http://www.j-pfennig.de/zapdvb/install_zapdvb.html]("http://www.j-pfennig.de/zapdvb/install_zapdvb.html")

After you install both these programs (zapdvb records/ webscheduler serves pages) you need to edit the webscheduler server.prop config to point to your zapdvb folder

ZapDVB.Path=******

To find your ZapDVB Path in a terminal type

[INDENT]**which ZapDVB**[/INDENT]

When it is sorted...it rocks. Keep an eye on the dvbowners forum for more info on the OS linux port.

---

