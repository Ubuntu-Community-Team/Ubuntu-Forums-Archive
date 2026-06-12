---
title: "Adding music to mpd"
date: 2009-09-26
forum: Multimedia Software
---

### Post by scheibo on 2009-09-26
Try as I might, I can't get mpd and ncmpcpp to work. These are the steps I'm following:

```

sudo apt-get install mpd
cd /var/lib/mpd/music
sudo ln -s /home/scheibo/music
sudo mpd --create-db
sudo /etc/init.d/mpd restart

```

which doesn't work. I then try changing /etc/mpd.conf to read

```

music_directory		"/home/scheibo/music"

```

and once again try to create a db and restart mpd. no avail, revert to default. A snippet from the long /etc/mpd.conf (the default from installing through apt:

```

######################## REQUIRED PATHS ########################
# You can put symlinks in here, if you like. Make sure that
# the user that mpd runs as (see the 'user' config parameter)
# can read the files in this directory.
music_directory		"/var/lib/mpd/music"
playlist_directory	"/var/lib/mpd/playlists"
db_file			"/var/lib/mpd/tag_cache"
log_file		"/var/log/mpd/mpd.log"
error_file		"/var/log/mpd/errors.log"
################################################################


######################## OPTIONAL PATHS ########################
#
# If you wish to use mpd --kill to stop MPD, then you must
# specify a file here in which to store MPD's process ID.
#
pid_file		"/var/run/mpd/pid"
#
# If specified, MPD will save its current state (playlist,
# current song, playing/paused, etc.) at exit.  This will be
# used to restore the session the next time it is run.
#
state_file		"/var/lib/mpd/state"
#
################################################################

```

and even after running sudo mpd --create-db my tag_caches still looks like this:

```

info_begin
mpd_version: 0.14.2
fs_charset: UTF-8
info_end
songList begin
songList end

```

Note there are no songs in the song list. 

I'd love some help with this, I've followed every mpd tutorial i could find on google and this site, but nothing seems to work. I feel like i'm doing the right steps, I'm just confused as to why I can't get mpd and ncmpcpp to work?

tia,
kjs

---

### Post by Endolith on 2009-10-10
I can't figure this out, either.  When I said "sudo mpd --create-db" it actually displayed the name of the only file in ~/Music and said ffmpeg couldn't read it.  But when I deleted it, it just displays nothing.  

> You do that by changing the ~/.mpdconf file (for individual users) or /etc/mpd.conf for system-wide MPD. It seems mpd is started at startup, even with no one logged in, but it's running as user mpd?  So which file is it using?

Remote client won't connect.  Local client connects but shows nothing.

Ok, I put some more test files in the Music directory and did create db and then update in gmpc and now it sees them. ffmpeg can't read two of them. I guess ffmpeg sucks.

The rest of the files probably aren't being read because the drives don't automount.  

Remote client still can't see it, though.

I have no idea which audio card it's trying to use, or even how to figure this out.

Oh, ok.  I did "sudo mpd --kill" and then "sudo mpd --stdout" and it logs to the screen now, so I can see it say 'Error opening ALSA device "hw:1,0": Device or resource busy'  or 'Successfully detected a alsa audio device'

---

### Post by scheibo on 2009-10-11
I added "read" permission to my music folder in my home directory (which i stupidly did not think to add at first), and now when i try "sudo mpd --create-db" i get lines and lines of:

ffmpeg: failed to open /var/lib/mpd/music/music/eazy e - louisville slugger.mp3
ffmpeg: failed to open /var/lib/mpd/music/music/Gary Jules - Mad World.mp3
ffmpeg: failed to open /var/lib/mpd/music/music/The Beatles - 02 - I'm A Loser.mp3
ffmpeg: failed to open /var/lib/mpd/music/music/The Beatles - 01 - No Reply.mp3
ffmpeg: failed to open /var/lib/mpd/music/music/The Beatles - 05 - Think For Yourself.mp3
ffmpeg: failed to open /var/lib/mpd/music/music/2Pac - 205 - U Don't Have 2 Worry.mp3
...

one for each song in my library. i assume this is the same issue you were having, Endolith? my /var/lib/mpd/tag_cache still isn't being written too, but this ffmpeg thing is a huge advance in getting mpd to work imo, b/c now it at least acknowledges the fact that i HAVE music files.

does anyone know a way around this ffmpeg mess? now that ive been burned once with permissions ive been anal at checking all the permissions on the mpd directories and noticed the default /var/lib/mpd/music directory is owned by root:root and i tried chown-ing to mpd:audio like all the other files in the directory in hopes that it would help with the ffmpeg error message but still no go.

- kjs

---

### Post by Endolith on 2009-10-11
> **scheibo said:**
> 
one for each song in my library. i assume this is the same issue you were having, Endolith?

That's the error I got, though only for a few files.  Most loaded and I was able to get them to play, but with lots of difficulty, and not remotely.  I think I've given up on MPD, especially because it doesn't let me edit tracks or delete files or anything like that.

---

### Post by HyperHacker on 2009-10-11
mpd just quit on me a while ago. I just reinstalled from scratch and still it wouldn't actually create the database.

What got it working was:> sudo mpd --create-db
sudo mpd --kill
sudo mpd --stdoutthat told me this, which seemed odd:> $ sudo mpd --stdout
unable to bind port 6600: Address already in use
maybe MPD is still running?
Abortedso I stopped it and then started it this way:> $ sudo /etc/init.d/mpd stop
 * Stopping Music Player Daemon mpd                                      [ OK ] 
$ sudo mpd --stdout
No "audio_output" defined in config file
Attempt to detect audio output device
Attempting to detect a alsa audio device
Successfully detected a alsa audio deviceThat got it working and Sonata connecting again, finally! I can hit Ctrl+C to disconnect it from the console and it keeps going in the background.

So, I suppose "/etc/init.d/mpd start" is not the proper way to start MPD.

After that I was able to change the bind address and password in MPD and Sonata, which I don't think ever worked before.

---

