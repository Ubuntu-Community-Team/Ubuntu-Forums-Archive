---
title: "Running two vlc windows on seperate x"
date: 2008-05-23
forum: Multimedia Software
---

### Post by b166er on 2008-05-23
Hi all!
I'm curretently setting up a computer running Ubuntu attached to two hdtvs. The reason I'm doing this is because I'm going to have the two hdtvs playing two playlists nonstop.
I have installed everything and all is upp and running exept one litle anoying thing.
After about two days vlc becomes "laggy". I don't know why, but I do know that restarting vlc solves the problem. But that creates another problem. I don't want to manually restart both vlc windows all the time. I want it to be automatic/scheduled. 
But since I use sepperate-x the windows will only start in the primary display if im using a cron command. Does anyone know a workaround or a solution? If I on the other hand use the mouse to launch vlc (via the panel-menues on the second display) all works good. So is there a way of launching an application in the second display using a commandline?

---

### Post by NT4usB on 2008-05-23
> **b166er said:**
> ...So is there a way of launching an application in the second display using a commandline?

There is... but it's been years since I used it. Way back when I set up MythTV, I had a LCD and TV connected. Did my work on the LCD and viewed the results on the TV.
iirc, the command was something like ```
mplayer /somefolder/somemovie.avi >screen0:1
``` or something??? 
crs is a bitch.

---

### Post by b166er on 2008-05-24
Ah thanks thats great, I will try that.
But that will probably only work with mplayer right?
The reason I'm asking is because I have had some problems with mplayer and playlists. But I think I can overcome that problem.

---

### Post by NT4usB on 2008-05-24
Actually, I was using it to run mythfrontend on the TV so if we figure out what exactly the line should read, it will work for any app.
I'm gonna have a look through my bookmarks and see if I can come up with it.

---

### Post by NT4usB on 2008-05-24
OK, I found it:```
DISPLAY=":0.1" programname
```will run on the second display.

[http://gentoo-wiki.com/HOWTO_Dual_Monitors#Using_multiple_screens](http://gentoo-wiki.com/HOWTO_Dual_Monitors#Using_multiple_screens)

---

### Post by b166er on 2008-05-25
> **NT4usB said:**
> OK, I found it:```
DISPLAY=":0.1" programname
```will run on the second display.

[http://gentoo-wiki.com/HOWTO_Dual_Monitors#Using_multiple_screens](http://gentoo-wiki.com/HOWTO_Dual_Monitors#Using_multiple_screens)

Ah! thanks you're great! :)
I will try that first thing tomorrow.

---

### Post by b166er on 2008-05-28
It worked really good! Thank you.

---

### Post by Joacom on 2009-01-11
You can use this command:

```
DISPLAY=:0.1 vlc -I http
```

Then you can use you`re web browser to pick files to play. 

[http://localhost:8080](http://localhost:8080)

Worked great for me!

Joacom

---

### Post by binbash on 2009-01-11
> **Joacom said:**
> You can use this command:

```
DISPLAY=:0.1 vlc -I http
```

Then you can use you`re web browser to pick files to play. 

[http://localhost:8080](http://localhost:8080)

Worked great for me!

Joacom


Wow great!! i am gonna try this when i go at home

---

