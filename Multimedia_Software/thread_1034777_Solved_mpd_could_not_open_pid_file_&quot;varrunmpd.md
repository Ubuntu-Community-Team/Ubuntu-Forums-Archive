---
title: "Solved: mpd could not open pid_file &quot;/var/run/mpd/pid&quot; (at line 13)"
date: 2009-01-09
forum: Multimedia Software
---

### Post by skralljt on 2009-01-09
If anybody is having the problem of 
starting the mpd daemon and get the error: 

could not open pid_file "/var/run/mpd/pid" (at line 13) for writing: Permission denied

then here is your answer:  
first make the directory /var/run/mpd
sudo mkdir /var/run/mpd

next, make the file pid
sudo mousepad /var/run/mpd/pid 
or in ubuntu:
sudo gedit /var/run/mpd/pid
and just save as an empty file.

Next, modify the read/write permissions.  This is dangerous and allows anybody with access to your computer to read /var/run/mpd/pid, if that is important to you.
sudo chmod 777 /var/run/mpd/pid

Now type sudo /etc/init.d/mpd start and you should be rolling!  If you get errors about a log file not being able to be written to, you can change the /etc/mpd.conf settings.

Type sudo gedit /etc/mpd.conf and change all of the places mpd stores things to ~/mpd.log or ~/mpd.db.  Good luck!

---

### Post by h!v on 2009-04-24
There is simpler and safer way to do this.


1st
We move all mpd' files to ~/.mpd. Create this directory if, it's not there.
2nd
Now edit properly 
```

/etc/mpd.conf

```
Find and edit this part.
```

# An example configuration file for MPD
# See the mpd.conf man page for a more detailed description of each parameter.

######################## REQUIRED PATHS ########################
# You can put symlinks in here, if you like. Make sure that
# the user that mpd runs as (see the 'user' config parameter)
# can read the files in this directory.
music_directory		"/[your_mp3_dir]"
playlist_directory	"/home/[user]/.mpd/playlists"
db_file			"/home/[user]/.mpd/tag_cache"
log_file		"/home/[user]/.mpd/mpd.log"
error_file		"/home/[user]/.mpd/errors.log"
################################################################

```
3rd
Find and modify this
```

######################## DAEMON OPTIONS ########################
#
# If started as root, MPD will drop root privileges and run as
# this user instead.  Otherwise, MPD will run as the user it was
# started by.  If left unspecified, MPD will not drop root
# privileges at all (not recommended).
#
user                            "[user]"

```

Since we run mpd as "ourself", go find and edit this.

```

######################## OPTIONAL PATHS ########################
#
# If you wish to use mpd --kill to stop MPD, then you must
# specify a file here in which to store MPD's process ID.
#
pid_file		"/home/[user]/.mpd/pid"
#
# If specified, MPD will save its current state (playlist,
# current song, playing/paused, etc.) at exit.  This will be
# used to restore the session the next time it is run.
#
state_file		"/var/lib/mpd/state"
#
################################################################

```

Run 
```

touch ~/.mpd/pid

```

For finish touches just restart mpd and create collection.
Ofcourse you can do same with state file. Since I'm not using it, I didn't.

Cheers.

---

### Post by Exic on 2010-11-28
Well, why does ubuntu change the directory permission in the first place?

I always do sudo chown mpd:audio /var/run/mpd for my directory, but I'd like to know how to tell ubuntu to keep these settings.

Best regards

---

