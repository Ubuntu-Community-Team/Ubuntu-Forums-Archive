---
title: "mpd hogs all the sound"
date: 2009-04-30
forum: Multimedia Software
---

### Post by monsterstack on 2009-04-30
Sorry if this has been done before, I couldn't seem to find much about this particular issue.

I have mpd running on the local host and I like it very much. I fire up nmcpc whenever I want to add songs etc. But I find it hogs all of the sound; that is, other applications are muted whenever mpd is running. I'm assuming I have to do something to the mpd.conf file to fix it. I'm also assuming it has something to do with the device section of that file.

The information [here]("http://mpd.wikia.com/wiki/Configuration#Audio_Outputs") [mpd.wikia.com] looks a little daunting really, as I don't really understand the alsa/pulseaudio stuff or how any of it works. My devices section looks like this:

```

audio_output {
        type                    "alsa"
        name                    "My ALSA Device"
        device                  "hw:0,0"     # optional
        format                  "44100:16:2" # optional
}

```

I didn't change it from the default, and it appears to work. It just hogs everything. Can anyone tell me what I must be doing wrong? I'm running 9.04 if that's useful to anyone.

---

### Post by mikezila on 2009-05-03
I have this exact problem.

I can specify ALSA settings, or let MPD take it's best guess, but the result is that either MPD hogs the soundcard.  I know that my ALSA setup is good (or at least functional), as it's totally stock, and other apps have no problem sharing the soundcard so long as MPD isn't running.  Rythmbox will play sound over YouTube in Firefox for example, but when MPD is started FireFox won't play sound (and usually crashes when I try) and other sound using apps either hang or won't start at all.

Any MPD users have a fix for this?

---

### Post by mikezila on 2009-05-03
I kind of fixed it, I think.  I think it has something to do with the user that MPD runs as, because if I start MPD myself (as opposed to it starting as part of init.d) it does not "hog" the sound, and ALSA mixes it as it should.

Try stopping the MPD daemon and just running it in a terminal, and see if that works.  Just open up a terminal and "mpd".  Make sure you've got a config file in your home directory, though.  It should fall back on the one in /etc/, but I'm not sure if it will be able to read it running as a normal user.  Make one in your home directory called .mpdconf , you can copy your one from /etc/ if you like.

Does that fix it for you?

---

### Post by monsterstack on 2009-05-04
> I kind of fixed it, I think. I think it has something to do with the user that MPD runs as, because if I start MPD myself (as opposed to it starting as part of init.d) it does not "hog" the sound, and ALSA mixes it as it should.

Try stopping the MPD daemon and just running it in a terminal, and see if that works. Just open up a terminal and "mpd". Make sure you've got a config file in your home directory, though. It should fall back on the one in /etc/, but I'm not sure if it will be able to read it running as a normal user. Make one in your home directory called .mpdconf , you can copy your one from /etc/ if you like.

Does that fix it for you? 

Thanks a lot; it did. I had to fiddle with the permissions a bit so that the stuff in the conf file was cool with non super-users.

For any other people struggling with this, do the following.

First, if you're struggling with this problem at all it's probably because you are running mpd as root! Make sure it is totally killed first of all:

```
sudo killall mpd
```

Copy the mpd.conf file in /etc to your home folder named .mpdconf:

```
sudo cp /etc/mpd.conf ~/.mpdconf
```

Now make sure you own it and that it doesn't have mad permissions (this might be a bit redundant but hey):

```
sudo chown user:user .mpdconf
chmod 700 .mpdconf
```

Now go ahead and open it up in your favourite editor...

```
nano .mpdconf
```

and change the directories in the "REQUIRED PATHS" to directories you as a user have access to. I changed all mine to an mpd folder in my home directory:

```

######################## REQUIRED PATHS ########################
# You can put symlinks in here, if you like. Make sure that
# the user that mpd runs as (see the 'user' config parameter)
# can read the files in this directory.
music_directory         "/media/stuff/Music"
playlist_directory      "/media/stuff/playlists"
db_file                 "/home/usr/mpd/tag_cache"
log_file                "/home/user/mpd/mpd.log"
error_file              "/home/user/mpd/errors.log"
################################################################

```

If you want to enable the pid option, make sure you change the paths in the "OPTIONAL PATHS" section too:

```
######################## OPTIONAL PATHS ########################
#
# If you wish to use mpd --kill to stop MPD, then you must
# specify a file here in which to store MPD's process ID.
#
pid_file                "/home/user/mpd/pid"
#
# If specified, MPD will save its current state (playlist,
# current song, playing/paused, etc.) at exit.  This will be
# used to restore the session the next time it is run.
#
state_file              "/home/user/mpd/state"
#
################################################################

```

Now have a look at the "DAEMON OPTIONS" and look at this bit:

```
#user                            "mpd"
```

This specifies what mpd does when it is started with superuser privileges. If you comment it out, it'll just go right ahead and run as the user that started it. That should be you, but if you have mpd starting up at boot, then it could be run as root! So if you don't want that, then leave it uncommented and change the username to your own. That way if you run mpd as root for whatever reason it'll drop root privileges and run like it belongs to you.

(Disclaimer: that last bit might be crazy and complete nonsense, but that's how I understand it. Feel free to correct me on it.)

Now that all should be fixed. Fire up mpd in a plain ol' user terminal and see what happens.

---

### Post by mikezila on 2009-05-04
Nice!  Productive threads like this give me a warm fuzzy feeling.

---

### Post by monsterstack on 2009-05-05
Yes indeed. Thanks for your help!

---

### Post by denarced on 2009-05-19
yes!!

my problem was fixed with this guide
many thanks .. no more sound-robbing!!

nice to get that one fixed,
mpd is after all an extremely well thought sound solution

:D

---

