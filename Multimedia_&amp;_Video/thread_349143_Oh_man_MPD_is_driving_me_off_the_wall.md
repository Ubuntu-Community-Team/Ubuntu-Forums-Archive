---
title: "Oh man MPD is driving me off the wall"
date: 2007-01-29
forum: Multimedia &amp; Video
---

### Post by Junk_head on 2007-01-29
Ok I have spent four hours here on this reading several different guides on getting mpd.conf, to make a database.
I get different errors like:
cannot setgid for user "mpd" at line 11: Operation not permitted
or DB file no created in directory no permission. 

Here's my entire conf:
# required
playlist_directory "/var/lib/mpd/playlists"	
music_directory    "~/My Music"
port               "6600"
log_file           "/var/log/mpd/mpd.log"
error_file         "/var/log/mpd/errors.log"


# optional, but HIGHLY RECOMMENDED
db_file            "/var/lib/mpd/mpddb"
user               "mpd"

# optional, but recommended
state_file         "/var/lib/mpd/state"

Im also using gmpc
This is a whole lot of grivance for some gapless playback

---

### Post by deadlydeathcone on 2007-01-29
The same thing happened to me, but I cleared it up by having it run under my own user priveleges.

I attached my config file; just change the user name under "security settings" and you're good to go.

---

### Post by Junk_head on 2007-01-29
Still wont make database, .
cannot init supplementary groups of user "alx" at line 187: Operation not permitted

db file "/home/alx/.mpd/mpddb" is not a regular file

---

### Post by deadlydeathcone on 2007-01-29
> **Junk_head said:**
> Still wont make database, .
cannot init supplementary groups of user "alx" at line 187: Operation not permitted

db file "/home/alx/.mpd/mpddb" is not a regular file

That's odd. Does the file and folder exist? If it doesn't enter these two lines in a terminal:

```
mkdir /home/alx/.mpd
touch /home/alx/.mpd/mpddb
```

edit: you might also try adding yourself to the "mpd" group.

---

### Post by Junk_head on 2007-01-29
Thanks for the help so far, but im still not getting the mpd to create a database

"cannot init supplementary groups of user "alex" at line 187: Operation not permitted

db file "/home/alex/.mpd/mpddb" is not a regular file


the mpd group would be the first section, i assume, so i fixed that but got the error above still, one thing that puzzles me is how it says the user prob since i gave it my password and all.

---

### Post by deadlydeathcone on 2007-01-30
One last thing: try generating a database with:

```
sudo mpd --create-db
```

---

### Post by Junk_head on 2007-01-30
IT;s taken care of

---

### Post by Junk_head on 2007-01-30
Ok after so more shell command learning i sorta figured that changing permissions was the problem, so i switched em with the ol' $chown 666 /var/lib/mpd command, 
and got the whole thing to scan my music, but now a another problem showed up, I cant log into 
6600 server to get mpd up with gmpc connection with localhost is refused...any ideas here?:confused:

---

### Post by Junk_head on 2007-01-30
Ok my problem is solved a quick restart of GNOME and the localhost opened up and GMPC picked up, you know after all this anger and hours spent,  realized how ubuntu takes care of itself, with permissions and all, it might be infuriating to comprehend at first, but once you do you realize how stable and killer ubuntu is.:guitar: 
MPD is the shiznit too, I love this thing, limited resources, and gapless :drool: .
Well worth the trouble spent, and just when I was gonna quit.
Thanks for the support deadlydeathcone.

---

