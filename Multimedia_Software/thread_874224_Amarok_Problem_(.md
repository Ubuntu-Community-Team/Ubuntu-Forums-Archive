---
title: "Amarok Problem :("
date: 2008-07-29
forum: Multimedia Software
---

### Post by alexandari on 2008-07-29
hello! i`m on ubuntu 8.04 and i decided to install amarok. Well,i did,everything is going well but...there`s one problem...when I swich songs in my playlist,the amarok just...freezes for like...3-4 seconds. the music is still playing,i mean,the music isnt freezing just the amarok is. it`s kinda annoying...and if you can tell me how to fix it :( i have about 300 songs in my playlist. disabeling OSD didnt help...
help me please :S :(

---

### Post by tuxxy on 2008-07-29
No KDE apps run well for me in GNOME, the only one that doesnt cause much of a problem is kshutdown lol

Have you tried Banshee or Rythembox for an alternative

---

### Post by niyonk on 2008-07-29
Hi, Alex :)

I don't know if I understood your question very well.
But, one of the problems I had recently was Amaro shuffling through all my songs one after another then ofcourse it freezes...

To solve it I went to 'configure amarok' then 'Engine' then choosinf the output plugin as either alsa or oss...
Try switching between the two and see if it works. 

Since then I have had no other problems with it. 
If this is not your problem, then give us more details on your EXACT problem 

Cheers! :biggrin:

---

### Post by perlluver on 2008-07-29
Exaile is also another great media player, closely resembling Amarok, and it is built for Gnome.  You could give that a try.

---

### Post by alexandari on 2008-07-29
well,niyonk I swiched between alsa and oss but...nothing...still freezing..for the ones that didnt understand,when i swich the songs in my playlist,when i press next track,the audio goes on,the track starts to play BUT not the audio is the one that freezez,the amarok is!

---

### Post by niyonk on 2008-07-29
Well, maybe you better try another media player.
But, it's a shame Amarok is freezing :(

---

### Post by alexandari on 2008-07-30
got it fixed! i deleted collection.db from the /home/username/.kde/share/apps/amarok directory :}

---

### Post by run1206 on 2008-07-30
that's odd. i'm using Amarok now on Hardy and having had a problem.  Try to build it through source, that's what i did when installing on edgy. Also check about the way it uses the collection database, i think it's either PostgreSQL or SQLite. i'm using SQLite.

edit: ^^ lol, glad to see you got it fixed!! :D

---

### Post by niyonk on 2008-07-30
::To the poster above me...(sorry, you username's kinda funny to write :tongue:)

How do you set up SQLite or PostgreSQL?? :(
I wanted to use it because Amarok says it's faster.

---

### Post by run1206 on 2008-07-30
when you open up Amarok, go to settings -> configure amarok. and in the collection tab there should be a box on the bottom that says "collection database".  you can choose PostgreSQL or SQLite or MySQL (for PostgreSQL and MySQL you have to setup the "hostname" "database" "username" and "password", so i just chose SQLite).

---

### Post by niyonk on 2008-07-31
run1206, 
Sorry, I think i confused SQLite with mySQL

I actually was asking for PostgreSQL or mySQL :lolflag:

---

### Post by run1206 on 2008-08-01
does it give you SQLite as a choice in the box?

---

### Post by niyonk on 2008-08-04
Yes, but Amarok recommends the other two since they are faster.
So i was wondering what are the requirements and steps to set them up

---

### Post by run1206 on 2008-08-06
> **niyonk said:**
> Yes, but Amarok recommends the other two since they are faster.
So i was wondering what are the requirements and steps to set them up

i'm not sure exactly, cuz i've never used to other two options, sorry :(

i'm sure there's some resources online to show the setup of an account for mySQL.

---

### Post by exisn on 2008-08-06
mySQL shouldn't be too complicated. Once the server is installed (mysql-server as far as I recall), the rest can be seen at the following link at amaroks wiki: [http://amarok.kde.org/wiki/MySQL_HowTo#MySQL_Setup](http://amarok.kde.org/wiki/MySQL_HowTo#MySQL_Setup)

Hope this helps.

---

### Post by run1206 on 2008-08-06
> **exisn said:**
> mySQL shouldn't be too complicated. Once the server is installed (mysql-server as far as I recall), the rest can be seen at the following link at amaroks wiki: [http://amarok.kde.org/wiki/MySQL_HowTo#MySQL_Setup](http://amarok.kde.org/wiki/MySQL_HowTo#MySQL_Setup)

Hope this helps.

kool, wasn't sure where the link was but you found it. i might try to setup my amarok with it, thanks much!! :D

---

### Post by homerwookey on 2008-10-22
Hi all just to say a big thanks to Alexandari for the info on solving the freezing of Amarok, its been bugging me for a while even to the point of changing to Banshee (which i'm still having trouble with trying to get my audio player to load tracks at a reasonable speed!) and your solution worked great for me... btw what is the collection.db file?
Nice one man

---

### Post by bacante on 2009-03-29
It worked for me. Thank you!

> **niyonk said:**
> Hi, Alex :)

I don't know if I understood your question very well.
But, one of the problems I had recently was Amaro shuffling through all my songs one after another then ofcourse it freezes...

To solve it I went to 'configure amarok' then 'Engine' then choosinf the output plugin as either alsa or oss...
Try switching between the two and see if it works. 

Since then I have had no other problems with it. 
If this is not your problem, then give us more details on your EXACT problem 

Cheers! :biggrin:

---

### Post by baraka607 on 2010-10-16
The following works for me:

Open your sources file for editing:

**sudo gedit /etc/apt/sources.list**

Add the following lines at the end:

[B]deb [http://ppa.launchpad.net/bogdanb/amarok14/ubuntu](http://ppa.launchpad.net/bogdanb/amarok14/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/bogdanb/amarok14/ubuntu](http://ppa.launchpad.net/bogdanb/amarok14/ubuntu) jaunty main[/B]

…and save the file.  Then add the authentication key and update your sources.  In terminal:

**sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AE74AE63 && sudo apt-get update**

Amarok 1.4 cannot coexist with Amarok 2.x, so you’ll need to remove that first:

**sudo apt-get remove amarok amarok-utils amarok-common**

You must specifically remove amarok-utils. This is important, people.  If you don’t, your Amarok 1.4 installation will fail with a dependency error because of a conflict with the collection scanner tool, and apt will subsequently refuse to do anything until you resolve it, which can be tricky.  So be sure you get rid of it in this step.

Typically this leaves some packages behind that you don’t really need any more, so let’s be neat and clean them up:

**sudo apt-get autoremove**

Before installing Amarok 1.4, there is a dependency that must be manually satisfied.  Sometime between the Lucid beta and the release candidate, the libmysqlclient15off package was dropped from the Ubuntu repositories, and your installation will need that.  Get the Karmic version from [http://packages.ubuntu.com/karmic/libmysqlclient15off](http://packages.ubuntu.com/karmic/libmysqlclient15off) and install it.  There’s a pair of download links at the bottom of that page; choose the one appropriate for your system (32-bit or 64-bit), click to download the .deb file, and then double-click the .deb file to install it.

Now you can install 1.4:

**sudo apt-get install amarok14**
:guitar:

---

