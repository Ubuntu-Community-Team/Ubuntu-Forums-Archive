---
title: "problem of updating MPD database"
date: 2009-11-02
forum: Multimedia Software
---

### Post by chaopoch on 2009-11-02
I want to add some new songs to MPD (version 0.15.4) database in Ubuntu 9.10, so I run command 'sudo mpd --create-db', but it fails to update database and returns message as follows:

**listen: unable to listen to address 127.0.0.1 : Address already in use**

then I can no more listen to MPD even though I reboot the computer, need help to solve this depressing problem. thanks.

---

### Post by chaopoch on 2009-11-02
anyone?

---

### Post by jacksonpollack on 2009-11-02
I have a similar problem, also in Karmic and using the same version of mpd. I use "sudo mpd --create-db", but then just get this message:

listen: Failed to listen on localhost (line 69): Address already in use
Aborted

Any help would be appreciated.

---

### Post by chaopoch on 2009-11-03
Administrator of MPD forum told me to update database with command 'mpc update', but it is useless, does any geek know how to update the MPD database effectively in Ubuntu 9.10? thanks.

---

### Post by cumanzor on 2009-11-03
I'm on the same boat, but I cannot even start mpd. I get the same message.

---

### Post by bao-anh on 2009-11-04
Hi,

I have the same problem as yours with Karmic Koala. > listen: Failed to listen on localhostI fixed it by the following :
- Check all active port on your servers : > sudo netstat -lnptu- Kill all which listen to your localhost 127.0.0.1 (if you run mpd before, you can see mpd in the list, don't kill it)
- Then update your database with the --create-db thing and run mpc or another client.
It works for me.

Cheers.

---

### Post by jacksonpollack on 2009-11-04
Hm, I'm not sure if my problem is the same as everyone else, since the above didn't work. I did find a fix for my problem though.

If I killed everything listening to the port (or changed the port in /etc/mpd.conf) then ran mpd --create-db, nothing seemed to happen at all. No database was created. 

I found this suggestion (see the comments of the post):
[http://www.webupd8.org/2009/10/mpd-sonata-powerful-audio-player-for.html](http://www.webupd8.org/2009/10/mpd-sonata-powerful-audio-player-for.html)

I checked the /var/log/mpd/mpd.log file and found that despite the weird error, it was actually attempting to create a database - but couldn't since mpd didn't have permission to access my music directory. I changed its permissions to be read/writeable for all users and also edited mpd.conf to make it create the database in my music directory. Only then did it create a database properly.

---

### Post by chaopoch on 2009-11-09
The problem is still unsolved.

It is really weird, I could run command 'sudo mpd --create-db' to update the database in Ubuntu 9.04 when I added new songs, but now the command seems to be useless, what happens?

Thanks for help.

---

### Post by nike984 on 2009-11-12
Try 

sudo /etc/init.d/mpd start-create-db
sudo /etc/init.d/mpd stop

instead of 

sudo mpd --create-db

at least, it worked for me

---

### Post by henriquemaia on 2010-01-27
Thanks **nike984** for your suggestion. I had the same issue and your post did the trick!

---

### Post by Merijn on 2010-11-19
I changed "localhost" to "127.0.0.1" in my /etc/mpd.conf
that worked

---

### Post by store88 on 2010-12-26
try --no-daemon parameter.

It likes the mpd daemon mod has some bug in it, i guess

---

### Post by genjix on 2011-01-01
I did:

sudo /etc/init.d/mpd stop
sudo mpd --create-db
ncmpcpp

works fine.

---

### Post by michalzuber on 2011-05-22
For me the following worked:

sudo /etc/init.d/mpd stop
sudo rm /var/lib/mpd/tag_cache
sudo /etc/init.d/mpd start-create-db

If you experience some errors or missing stuff than check
less /var/log/mpd/mpd.log

I had some reading Permission denies

---

