---
title: "share photos online on ubuntu server"
date: 2008-07-13
forum: Multimedia Software
---

### Post by tvds on 2008-07-13
Hi,

Well, last week I finally jumped to Ubuntu with my server.
It first was a Windows XP machine, but after a lot of problems I installed Ubuntu with Remote Bit torrent server / FTP / LAMP / Printer server / Backup server.

For me, it was a lot of work but now I just love it.

But.... what I really really need is a photo gallery server. For online display.

I like gallery and coppermine, but what I would really like is a gallery that searches and indexes folders and files on my ubuntu server by itself.

So I just create a folder (with subfolders) with all my photo's and that the gallery just indexes it by itself. And if I add or remove photos that it also deletes and adds it to the gallery.

And off course... that it renders RAW and TIFF images to JPG.

Is something like this even possible ?

I know that there is some windows software that does this. (cannot remember the site)

So I really want to keep them on my server.

Thanxs !

---

### Post by brainspank on 2008-10-16
It's old and not flashy but apache gallery works for me.  If you want more features than it has, you can always dust off your perl skills.

[http://apachegallery.dk/](http://apachegallery.dk/)

I don't know how secure it is, but I only use it on my LAN.

---

### Post by freymann on 2008-10-16
I just ran across this the other day, it'll do what you're after:

[http://www.phpalbum.net/](http://www.phpalbum.net/)

Wasn't hard to install and configure either.

---

### Post by Deas on 2008-10-18
@brainspank

Are you using Apache2 and mod_perl2? What release of Ubuntu are you running?

Can you show me your httpd.conf/.htaccess on how you got Apachegallery to work? I just get alot of random errors when I try to use it.

I installed it using 'apt-get install libapache-gallery-perl' so I should have gotten all the dependencys.

// Deas

---

