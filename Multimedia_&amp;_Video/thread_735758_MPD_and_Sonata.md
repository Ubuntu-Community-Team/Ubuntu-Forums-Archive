---
title: "MPD and Sonata"
date: 2008-03-26
forum: Multimedia &amp; Video
---

### Post by NobleRooster on 2008-03-26
Ok, well, I am going ape-**** over this.  I have looked every where and tried practically everything to try and get Sonata and MPD to work.  The main thing is, I don't know how to set both of them up to work together.

Can someone PLEASE just point me to a guide that works?
btw, I'm using UBuntu Gutsy.

Thanks,
-Justin

---

### Post by girishv on 2008-03-26
Hi,

its as simple as running mpd first and then starting sonata. It connects to the mpd directly without any problem. You can also setup sonata to start mpd if its not started already. Sorry,
I can not check this as I removed sonata which was causing some strange problem with FVWM

Girish

---

### Post by kaiju on 2008-03-26
first of all, make sure that you have valid settings in mpd's config file.
```
sudo gedit /etc/mpd.conf
```
'music_directory' should point to your music collection, either by changing the default value or by adding symlinks to /var/lib/mpd/music. another important thing is for the mpd user to have access to all the files specified in the 'REQUIRED PATHS' section. it is also safe to change 'user "mpd"' to your user name. other than that, the commented lines in the file explain the whole thing pretty well.

to see if anything is wrong, you can start mpd from a terminal, as this will give you messages about eventual file permission errors, and you'll know what to change.
to play music, you will first have to create a database with mpd --create-db.
to start/stop/restart the daemon anytime, use
```
sudo /etc/init.d/mpd
```

if your mpd settings are right, sonata will work out of the box, just make sure that it uses the same music directory as mpd.

---

### Post by TenPlus1 on 2008-03-26
This is how I got MPD and Sonata working:

Create the following directories in your home folder:

mkdir .mpd
cd .mpd
mkdir playlists

Here is the contents of /etc/mpd.conf (sudo gedit /etc/mpd.conf):

# This is an example configuration for MPD music daemon
music_directory                 "~/music"
playlist_directory              "~/.mpd/playlists"
db_file                         "~/.mpd/mpd.db"
log_file                        "~/.mpd/mpd.log"
error_file                      "~/.mpd/mpd.error"
port                            "6666"


Make sure Sonata preferences use the same directories & port form the config file.

Here is a quick script that you can add as a menu item to run MPD, then run Sonata straight after (gedit StartMPD.sh):

mpd &


That's it, make the script executable (right-click, properties, permissions) and add it to your gnome menu for easy access, all should be fine...

Type mpd --create-db  to update your music list (or you can leave it to Sonata)...

---

### Post by kaiju on 2008-03-26
> **TenPlus1 said:**
> Here is a quick script that you can add as a menu item to run MPD, then run Sonata straight after (gedit StartMPD.sh):

mpd &


That's it, make the script executable (right-click, properties, permissions) and add it to your gnome menu for easy access, all should be fine...

excuse me if i'm not understanding you here, but mpd is a daemon (music player daemon), meaning that, once set up correctly, it will always run in the background (even when it's not playing anything).
considering this, i don't see why you'd want to run mpd every time you run sonata. this can only be useful if you set up sonata to kill mpd every time it exits (which sort of defeats the purpose of using a daemon in the first place).

---

### Post by spaceship.rodeo on 2008-04-23
lol bump.  

So I'm trying to set up MPD here using **[this](http://ohioloco.ubuntuforums.org/showthread.php?t=320469)** guide, and when I type in 
```
sudo mpd --create-db
``` 
it's giving me this error:
```
problems opening file &#8211;create-db for reading: No such file or directory

```

Surely it's not supposed to be doing that.  So what am I doing wrong here?

---

### Post by kaiju on 2008-04-24
> **spaceship.rodeo said:**
> ...```
problems opening file –create-db for reading: No such file or directory

```...

try ```
sudo /etc/init.d/mpd create-db
``` or, to see all the available options, just ```
sudo /etc/init.d/mpd
```

---

### Post by spaceship.rodeo on 2008-04-24
> **kaiju said:**
> try ```
sudo /etc/init.d/mpd create-db
``` or, to see all the available options, just ```
sudo /etc/init.d/mpd
```

Thanks, but I made a thread [here](http://www.uluga.ubuntuforums.org/showthread.php?p=4776541#post4776541) and figured it out already.

Edit - Okay, so I got mpd working how it should so far.  But now when I try to play the music in Sonata, it won't play.  Everything will show up nice and fine, but as soon as I hit 'play,' nothing happens.  Well, it'll try to play the file, but then it will just stop again.

---

