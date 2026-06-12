---
title: "Media Centre auto start."
date: 2009-01-24
forum: Multimedia Software
---

### Post by coolercooler on 2009-01-24
Hello all, hope someone can help.

I have installed my dvb card to work with VDR on ubuntu, which is all fine and works good.  But I don't know how to start it without command line.  What I would like to do is get it to run when I switch on PC.  I've installed oxine and lot's other stuff.

If anyone can help how to do this.

Thanks

---

### Post by steefjeqv on 2009-01-24
Hi,

How do you start VDR at the moment ?

I suppose : sudo /etc/init.d/ vdr start

Do you use xine or xineliboutput for displaying ?

Greetings,
Steven

---

### Post by coolercooler on 2009-01-27
I use both xine and xineliboutput for displaying.

And you are quite right with start command, however I use the script to start vdr backend on startup, and for front end I use vdr-sxfe as command which I need it to run on startup up, for me it's not a problem but if you going to have media center then you'd expect to start on it's own especially if kids were to us it too.

I did however heard someone managed to use oxine to achieve this, but i have no idea how to do this.

---

### Post by steefjeqv on 2009-01-27
Hi,

So the backend runs on startup.

Then you startup the frontend by vdr-sxfe. If you don't need the sudo thing when running vdr-sxfe then you can autostart like so :

System > Preferences > Sessions

Then add the application (vdr-sxfe) you want to run at startup.

By the way, there is an updated VDR repo for Ubuntu (Hardy & Intrepid), kindly set up by hanno and e-tobi :

[http://www.hanno.de/blog/category/vdr/]("http://www.hanno.de/blog/category/vdr/")

If you master the German language :

[http://www.vdr-portal.de/board/portal.php]("http://www.vdr-portal.de/board/portal.php")

If there's a problem, let me know.

Greetings,
Steven

---

### Post by coolercooler on 2009-02-01
Thanks, that worked a treat.

---

