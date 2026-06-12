---
title: "MPD not reading directories"
date: 2011-05-26
forum: Multimedia Software
---

### Post by Wickk on 2011-05-26
I'm trying to setup ncmpcpp correctly and I'm running into an issue with mpd not reading my directories correctly. 

I dual boot ubuntu/w7 on this computer, and for the sake of laziness I just keep all of my music within the default windows folder ( since half my music was there first ). 

Now I have a symlink within my home directory's music folder that points to this, however according to mpd it isn't a director.

The complete error message ( obviously my directory issue isn't the only problem )
```
 
wick@lappy:~$ sudo /etc/init.d/mpd start
 * Starting Music Player Daemon mpd
music directory is not a directory: "/home/wick/Music/Music"
playlist directory is not a directory: "/home/wick/.mpd/playlists/"
Failed to load database: Failed to open database file "/home/wick/.mpd/mpd.db": Permission denied
database: Couldn't stat parent directory of db file "/home/wick/.mpd/mpd.db": Permission denied
                                                                                                       [fail]

```

---

### Post by Red Long Johns on 2011-07-01
Has anyone solved this? I installed xubuntu 11.04 on a new computer last night, now mpd will not read the directories properly...

All the files are where they should be, Amarok will play them...
```

/var/lib/mpd$ ls -l music/
total 0
lrwxrwxrwx 1 root root 19 2011-06-30 23:28 music_sorted -> /misc/music_sorted/
lrwxrwxrwx 1 root root 21 2011-06-30 23:28 music_unsorted -> /misc/music_unsorted/

```

I have set both follow_outside_symlinks and follow_inside_symlinks to "yes" in /etc/mpd.conf - which I had another, very odd problem with: I could not read it as my regular user, despite being a member of its group, which had read access:
```

$ ls -l mpd.conf 
-rw-r----- 1 mpd audio 12409 2011-02-02 12:48 mpd.conf
$ cat group|grep audio
audio:x:29:pulse,mikaels
$ less mpd.conf 
mpd.conf: Permission denied
$ sudo chmod a+r mpd.conf 
$ less mpd.conf 
(worked)
```

mpd can find one subdir of music_unsorted and, about one recreated db in ten, music_sorted (but none of its subdirs).

I tried compiling mpd from source to see if that made any difference, but failed because of a lack of glib; I have no idea which of the cryptically named dev packages might contain it.

---

### Post by Erik1984 on 2011-07-15
Maybe this is not the nicest way but what I did is to create the proper configuration files in my homedir and then run the command "mpd" on startup. Note: this is not the same as running "/etc/init.d/mpd start" ! when you type just "mpd" it starts a daemon and first checks your /home/user folder for config files. So I disabled the daemon in /etc/init.d with the following command:

```
update-rc.d -f mpd remove
```Then placed the command 'mpd' in the startup list (how to do this depends on your ubuntu version and DE)

My ~/.mpdconf looks like this:
```

port                    "6600"
music_directory         "/home/name/Music"
playlist_directory      "/home/name/.mpd/playlists"
db_file                 "/home/name/.mpd/mpd.db"
log_file                "/home/name/.mpd/mpd.log"
state_file              "/home/name/.mpdstate"
pid_file                "~/.mpd/mpd.pid"
bind_to_address         "localhost"

audio_output {
        type    "pulse"
        name    "My MPD PulseAudio Output"
}

```

Now it seems to work fine.

---

