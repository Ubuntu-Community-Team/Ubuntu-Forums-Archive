---
title: "Data CD ripping."
date: 2007-02-18
forum: Multimedia &amp; Video
---

### Post by KAL9000 on 2007-02-18
I am using the $ dd command to rip ISO files of all my game CD's so i can use deamon tools to mount in windows so they run faster and so I cant loose them or worry about scratching the CD's.

Now when i try this with windows 90% of all my games decide to fail the rip, now I've been told this is a rootkit/drm/data manipulation protection mechanism to stop you copying the CD's.

With the DD command in Linux I've been able to rip most of my games, but, Particularly those from "Maxis" and "Soldout"  still give me a I/O error and fail to rip at 1.5 or 1.6MB.

Ive tried with the noerror option and it does the same, is there anyway you guys know to rip ANY, absolutely ANY CD to .iso.

Let me just get this clear I'm trying to do this for backup purposes only, as I'm a pig with my CD's and I hate having to swap them all the time. They also lead quicker with them on the HD.

---

### Post by KAL9000 on 2007-02-19
BUMP. does anyone have any ideas on this. I want to make a total backup of my games and if i get round to it my DVD's (guess ill need a few HDD's :P) 

Does anyone know a way to just crack the whip just rip the damn thing.

---

### Post by Praill on 2007-02-28
Umm.. I'm not really sure why no one has answered you in an entire week.

There is a program called k3b that is pretty much Linux's Nero. It can rip images, write images, create CD/DVD copies, etc. It's pretty popular. It won the multimedia utility of the year award from linuxquestions.org
It's in the defualt apt-get repositories.
```
sudo apt-get install libk3b2 libk3b2-mp3 k3b
```

Maybe no one answered you because its part of the KDE suite? *shrugs*

---

### Post by KAL9000 on 2007-03-02
SO i found out how to JUST make an image, but the same happens.

It says 
"Problem while reading, retrying from sector 768"
"Error while reading sector 812"
"Error while reading session 1"

and bar the messages the observablke behaviour is the same as when using the dd command.

---

