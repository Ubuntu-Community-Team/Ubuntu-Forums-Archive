---
title: "MPD: Failed to open ALSA device &quot;default&quot;: Permission denied"
date: 2013-03-10
forum: Multimedia Software
---

### Post by moody_mark on 2013-03-10
I have an issue with mpd running on an old toshiba sattelite laptop. Its running Ubuntu Server 11.10. I installed mpd a while ago and everything was working along quite merrily. I had some troubles where mpd was not allowing connections and I think it was due to two mpd daemons getting started accidentally (my fault), anyway since then I can connect to the server using a client via a mobile device or via sonata on a PC, but I cannot seem to play any music, everytime I attempt to do so I get

output: Failed to open "default" [alsa]: Failed to open ALSA device "default": Permission denied

Here's my mpd.conf file (with comments and blank lines removed):

```

music_directory		"/home/user/Music"
playlist_directory		"/home/user/Music"
db_file			"/home/user/mpd/tag_cache"
log_file			"/home/user/mpd/mpd.log"
pid_file			"/home/user/mpd/pid"
state_file			"/home/user/mpd/state"
sticker_file                   "/home/user/mpd/sticker.sql"
user				"user"
group                          "user"
bind_to_address		"192.168.0.11"
port				"6600"
log_level			"default"
metadata_to_use	"artist,album,title,track,name,genre,date,composer,performer,disc"
auto_update    "yes"
auto_update_depth "3"
follow_outside_symlinks	"no"
zeroconf_enabled		"yes"
zeroconf_name			"Marge"
input {
        plugin "curl"
}
audio_output { 
         type                    "alsa"
         name                    "default"
         #device                  "hw:0,0"     # optional
         format                  "44100:16:2" # optional
}
filesystem_charset		"UTF-8"
id3v1_encoding			"UTF-8"

```

the "user" user also is a member of the audio group.

I have a feeling some other process has grabbed the "default" alsa output, **I even tried running this as "root" user and I get the same error**.

Any ideas anyone? Thanks!

---

### Post by moody_mark on 2013-03-11
Ok so I actually fixed this and it was a simple permissions thing. The very strange thing is, how could these permissions have changed? Anyway thanks to the following post:

[http://www.linuxforums.org/forum/miscellaneous/51410-alsa_get_mixer-attaching-mixer-hw-0-failed-permission-denied.html](http://www.linuxforums.org/forum/miscellaneous/51410-alsa_get_mixer-attaching-mixer-hw-0-failed-permission-denied.html)

... I was able to fix the issue, the command below was a quick and easy way of changing the permissions for me, in my case it was the /dev/snd directory and all 

```
sudo chmod -R a+rw /dev/{audio,dsp,midi,mixer,snd}
```

I'd love to know how the permissions were changed in the first place though :-)

---

