---
title: "Why mythbuntu and not ubuntu + myth packages?"
date: 2008-01-02
forum: Mythbuntu
---

### Post by elj4176 on 2008-01-02
What is the advantage of using mythbuntu instead of installing ubuntu-desktop and then installing the myth packages?

Does mythbuntu have ssh and mythweb included? Does it have easier config of lirc and channel change scripts? 

It's been awhile since I setup my pvr-350 myth box by installing ubuntu and then myth packages. I remember having trouble with lirc and the dtv channel change scripts. If mythbuntu makes this setup easier then I may give ti a try.
My primary drive died last night and took my mysql DB with it. Recordings and videos are on another drive but w/o the db they are somewhat useless.

Thanks!

---

### Post by dannyboy79 on 2008-01-02
i use mythbuntu gutsy. it supposedly has better support for setting up lirc but I don't have a remote for that machine. it's a slave backend with  a pvr-500 in it. anything you can do with ubuntu (ssh etc etc) you can do with mythbuntu. Mario (the author of mythbuntu) told me that himself.

---

### Post by aaltieri on 2008-01-02
> **elj4176 said:**
> What is the advantage of using mythbuntu instead of installing ubuntu-desktop and then installing the myth packages?

Does mythbuntu have ssh and mythweb included? Does it have easier config of lirc and channel change scripts? 

It's been awhile since I setup my pvr-350 myth box by installing ubuntu and then myth packages. I remember having trouble with lirc and the dtv channel change scripts. If mythbuntu makes this setup easier then I may give ti a try.
My primary drive died last night and took my mysql DB with it. Recordings and videos are on another drive but w/o the db they are somewhat useless.

Thanks!


For me, my PVR 500/150 cards worked out of the box without any problem.  The Aver a180 is just finicky (could be something involving the fire in my previous server) but was recognized straight away.

Lirc using the mceusb2 remote worked brilliantly, although I would VERY highly recommend changing some of the keymappings.

SSH and VNCserver installed automagically, and it sets up the sql and myth passwords and various other things as part of the install.  It also installs all the codecs you need and all the players you could ever want.

Mythbuntu also does not install a lot of the gloat from the regular desktop install.  And because you are not downloading things, the install (even including the updates, oddly enough) seems to take less time and is very straight forward. My compliments to the team.

The single hang up I found with installing mythbuntu (and this could be my goober) was that I had to set up just about all of the video file types before they were recognized.  When I installed the packages separately, I don't recall having to do that.  But as long as you tell myth where they are, it will find the videos you currently have and catalog them appropriately.  The recordings...well...yeah.

Between the two methods, if you are running the box as a primary media server/front end.  Use mythbuntu.  If you are going to use it as a desktop, install the desktop version and add the myth packages.

---

### Post by BrianElliott0218 on 2008-01-02
[QUOTE=
My primary drive died last night and took my mysql DB with it. Recordings and videos are on another drive but w/o the db they are somewhat useless.
[/QUOTE]

You should go get the Ultimate Boot CD and see if you can recover your MySQL DB from the old HDD.  The UBCD has a huge number of recovery utilities and can often fix a problem that other higher end utilities can't.  It's a Free Live CD too, just go download the ISO and burn it.

[http://www.ultimatebootcd.com/download.html](http://www.ultimatebootcd.com/download.html)

Good luck!:guitar:
~BE

---

### Post by elj4176 on 2008-01-02
Thanks for the info.
I've got mythbuntu just about installed but it cannot conenct to the mysql db - and yes i did change the /etc/mythtv/mysql.txt to reflect the same password as i nteh BE setup.

I also set it up before having a net connection to the box and before I had the channel change script. How od I get back in tehre to fix those problems? I think I used the wrong schedules direct pw too....doh!

So far it was na easy setup and lirc worked out of hte box.

I tried several rescue CD's but the drive doesnt even spin now so it gone!

---

### Post by elj4176 on 2008-01-02
I figured most of it out but I can't get the d11 channel change script to work and I have to install and run an ivtv-tune coammand to detect a signal.

ivtv-tune -c3 -d /dev/video0 

I have a directtv d11 receiver and the channel changer worked great before.

Any ideas?

---

### Post by dannyboy79 on 2008-01-02
don't forget that mythbuntu comes with mythweb enabled by default and unless you have a fireall everyone in the world can see your mythtv recordings and schedule stuff and delete stuff as they see fit!

---

### Post by elj4176 on 2008-01-03
Not a problem.  I've already secured it in several different ways ;)
It also helps if I correctly type the path to the channel change script LOL
I'm surprised that phpmyadmin isn't included. I'll be using it to backup my db regualrly from now on.

---

### Post by dannyboy79 on 2008-01-03
automysqlbackup bash script is awesome! I use in my cron.daily. It backups mythconverg daily and weekly, compresses them, rotates them, erases older ones etc etc. check it out: [http://sourceforge.net/projects/automysqlbackup/](http://sourceforge.net/projects/automysqlbackup/)

this is the command I run in my cron.daily folder

---

### Post by elj4176 on 2008-01-03
Sound like what I am looking for. I'll check it out. Thanks!

---

### Post by elj4176 on 2008-01-04
A quick update for those interested.
The myth.rebuilddatebase.pl scipt will import the old recordings into my db again. Glad I found that.

Now to get the above backup script ready.

---

