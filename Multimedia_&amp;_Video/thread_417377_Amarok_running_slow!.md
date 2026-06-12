---
title: "Amarok running slow!"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by Valinski on 2007-04-21
Ive been trying to use my favorite music player (amarok) since upgrading to fiesty and it seems to be running really slow. 

upon executing the program it tries to update the collection but gets stuck at 79%

It can take a while switching between tracks

Also after asking it to perform almost any task it brings up the busy symbol on the cursor (the watch) and stays like this for a good few minutes. 

I tried a complete removal but upon reinstalling i notice its saved all the info on things like the library and it also tries to pick up where it left off by updating the library. 

Any ideas would be appreciated! 

Thanks

---

### Post by clevin on 2007-04-22
i have to remove it coz it just stuck there upon open, and does not respond to anything for more than 5 minutes before I killed the process.

---

### Post by The Human Cow on 2007-04-23
I'm having the same problem.  After upgrading to Feisty, Amarok appears to hang for about 5 minutes if I try to do anything.  If I leave it alone, it will eventually work, but I can't switch to it in the middle of an operation or it will appear to have crashed.

---

### Post by jpkrautw on 2007-04-24
Just checking in to say I have the same problem.  This sucks.

---

### Post by andresv on 2007-04-29
same here - amarok was running at a normal speed under 6.10 but after I installed it on my new feisty, it is painfully slow ... :confused:

---

### Post by Boni2k on 2007-04-29
Switch your Database to MySQL. There is a working sollution for converting your exisiting database to MySQL.
It will speed up your amarok.

---

### Post by andresv on 2007-04-29
> **Boni2k said:**
> Switch your Database to MySQL. There is a working sollution for converting your exisiting database to MySQL.
It will speed up your amarok.

I will try that. What is the working solution to convert the existing database to MySQL?

---

### Post by Boni2k on 2007-04-29
[http://amarok.kde.org/wiki/MySQL_HowTo#SQLite_-.3E_MySQL](http://amarok.kde.org/wiki/MySQL_HowTo#SQLite_-.3E_MySQL)
It's not too complicated at all

---

### Post by ghostz00 on 2007-04-29
I'm using mysql and it is still slow.  After hitting the skip button the song will start but the amarok will lag behind.  after about 10 - 20 secs amarok will catch up and display the title of the song and continue to work.  But during the 10 - 20 secs.  amarok is unusable.  It doesn't seem to take hardly any cpu cycles during that time though.

I'm also grabbing my library from a shared folder from my network.  I might try copying my music to my computer and see if that helps.

---

### Post by Boni2k on 2007-04-29
Well I asked about that in their forums, they told me it's because amarok does a lot of database queries which makes it all slow due song change.
I had the same problems, with SQlite a song change lagged my PC for 4 seconds, with MySQL a half. I needed to make a new database yesterday because it bacame corrupted and everything runs _very_ fast now...

---

### Post by elchato on 2007-04-29
any howto?

I have the same problem

---

### Post by Tom B on 2007-04-29
I have also had problems with amarok since upgrading to Feisty. As soon as I start it, my CPU goes to 100% and stays there until I restart the computer. It plays music fine, but if I try to do anything with it (organize files, create a playlist, etc.) it becomes really laggy and I have to close it. And I don't know if it's related at all, but none of my keyboard shortcuts for amarok work anymore. I've been trying exaile (I'm using gnome), but I like amarok better and would love it if it worked like it did before the upgrade.

---

### Post by pbhill on 2007-04-30
I installed Amarok this weekend. Now my whole system has slowed down. (I'm running Feisty).
I also cannot seem to get Amarok to connect with my Zen Microphoto. Any thoughts?
:confused:

---

### Post by Boni2k on 2007-04-30
Which process is going high?
Only the one from amarok?
Again, I advise you to use MySQL instead

---

### Post by Tom B on 2007-05-02
It's weird. The amarokapp is using about 60MB, which doesn't seem like a lot to me. I think part of the problem was an amarok script that was running, because now that I've stopped the script it's less laggy. I tried the instructions to setup MySQL, but when I tried to set the password I got "ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)" I don't really know what that means.

Also, is any of this related to keyboard shortcuts not working in amarok or is that another problem entirely?

---

### Post by alecthunder on 2007-05-05
Hi!

Just for the statistics, Amarok is also very slow on my system (HP Pavilion ze4900 / Ubuntu 7.04) I have about 40GB of mp3s and:

- building the database after installing is really slow, but this might be normal taking into account that it reads all files.
- starting Amarok takes more than one minute, during this time not even the user interface responds. Does it load all mp3s again?
- the search filter takes more than five seconds to react. Think of the "jump" button in winamp, which filters almost instantly.
- clicking on play, stop, next takes more than five seconds to respond

I really want to understand why developers build so many features in a program when not even the basics work right. Other than that, it would be a nice program to work with.

---

### Post by Boni2k on 2007-05-09
Do you use mySQL, alecthunder?

---

### Post by alecthunder on 2007-05-09
No, I use the standard configuration, I don't want a database running on my private notebook because it would slow my system down (I think). But nevermind, I installed XMMS and it's exactly what I wanted. Plus it has the almighty 'J' key :)

Greets.

---

### Post by wataboutbob on 2007-05-13
I've been having problems with Amarok 1.44 as well as 1.45 with Edgy as well as Feisty. It was only when I had reinstalled my laptop the day before and when I was more careful adding songs to the library that I'd noticed something interesting...

My music is about 35 GB, divided broadly into 5 different folders for languages, under which are my songs. Of this, the biggest is the English folder ~ 18 GB. For 2 days, I didn't add this one folder to the library and everything was peachy. No lag, no slowdown when starting or creating playlists or when skipping songs. Perfect.

But after I added the large English folder to the library, all the problems started again. Slow startup, constant freezes when creating playlists or when skipping songs, or when trying to create smart playlists - CPU usage 100% and RAM usage at over 100 MB.

Seeing what the problem may be, I deleted Amarok's database. Split my music folder into about 11 genre folders so that the largest folder isn't bigger than "Rock" ~ 9.5 GB and asked Amarok to rebuild again.

No problems whatsoever. Didn't stall when building the collection. Doesn't stall / freeze for anything anymore. Restarted application and laptop multiple times but still perfect. Maybe MySQL solves it for others, but it never did for me. My tip though is to maybe have multiple folders which aren't too big.

cheers!

---

### Post by 0micron on 2008-01-09
Just to let you know, I had the same problem with Athlon X2 1.8zGhz and 2GB Ram; 2500 mp3s - sluggish reaction time when changing songs, main window turning grey for 5-6 seconds, 50% processor usage (just for amaroK), etc. I followed the instructions to switch to MySQL here:

[http://mikesubuntu.blogspot.com/2007/09/how-to-set-up-mysql-database-in-amarok.html](http://mikesubuntu.blogspot.com/2007/09/how-to-set-up-mysql-database-in-amarok.html)

and everything works fine now, no lag, no nothing. Give it a try, it's quite easy.

---

### Post by skralljt on 2008-05-28
As I am typing this looking at atop my mysql usage by amarok is topping out the list in the cpu column: 46% of my amd64 3800 is being used, while 31% is used by amarokapp.  I have a few plugins enabled, one I know slows things down a lot: the replaygain plugin.  I have a fair amount of experience with what bogs down amarok, after slogging through the internets to find out why it is so slow:

1.  Covers.  If you have album covers set up to display, and your collection is large, it will be slow.  
2.  plugins.  disable plugins that are unnecessary.
3.  running amarok outside of kde.  I use xfce, and there are always python-binding and dbus errors that don't pop up when in kde.  Run it in kde for slight speed improvements.
4.  turn off the automatic database updating in the amarok preferences, and watching folders.  Just scan your collection once and turn that thing off.
5.  Turn off the visualizations.  I don't know if that makes a difference but in the past in other players in my experience it has.  
6.  Turn off the osd, crossfading,and any other stuff like last.fm that you don't need.

  That is all I have at the moment.  Amarok is a big slow beast but it is the only way I have set up to easily send podcasts to my mp3 player and it has a good database interaction.  Honestly I use audacious a lot more though, and just use amarok now for organizing media.  I really wish that somebody would port foobar2000 to linux!

---

