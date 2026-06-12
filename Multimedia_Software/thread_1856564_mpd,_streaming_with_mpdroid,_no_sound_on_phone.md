---
title: "mpd, streaming with mpdroid, no sound on phone"
date: 2011-10-08
forum: Multimedia Software
---

### Post by vajorie on 2011-10-08
For some reason I cannot get streaming to work on my phone using mpdroid... 

I'm using ubuntu 11.04, mpd 0.16.1. 

Here's my mpd.conf residing in ~/.mpd/mpd.conf

```

bind_to_address "127.0.0.1"
bind_to_address "192.168.1.45"
bind_to_address "10.30.0.14" #can't bind to 6600 without these bits, says "6600 already in use" though it isn't

audio_output {
        type                    "pulse" 
        name                    "Sound Card"
}

audio_output {
	type  "httpd"
	name  "HTTP Stream"
	encoder  "lame"  # optional, vorbis or lame
	bind_to_address "0.0.0.0" #can't bind to 8000 without this bit... says "8000 is in use" though it isn't
	port  "8000"
	quality  "2.0"   # do not define if bitrate is defined
	# bitrate  "128"   # do not define if quality is defined
	format  "11025:8:1"
	max_clients "0"   # optional 0=no limit
}

music_directory	"~/Music"
playlist_directory	"~/.mpd/playlists"
db_file	"~/.mpd/mpd.db"
log_file	"~/.mpd/mpd.log"
pid_file	"~/.mpd/mpd.pid"
state_file	"~/.mpd/mpdstate"

```

On mpdroid, I create a playlist, hit play and streaming, but there's no sound on my phone... If I enable "Sound Card" as the output on mpdroid, I hear the PC play the songs. "HTTP Streaming" is already enabled on mpdroid. 

I only have these lines on my mpd.log

```

httpd_output: unexpected input from client

```

Any advice?

---

### Post by vajorie on 2011-10-09
Nevermind, I "solved" it (not really the way I like, but oh well... 

This is the conf file I now use. 

```

#bind_to_address "127.0.0.1"
#bind_to_address "any"
#bind_to_address "0.0.0.0"
#bind_to_address "192.168.1.45"
#bind_to_address "10.30.0.14"
#port "6600"

audio_output {
        type                    "pulse" 
        name                    "Sound Card"
}

audio_output {
	type  "httpd"
	name  "HTTP Stream"
	encoder  "lame"  # optional, vorbis or lame
	quality  "5.0"   # do not define if bitrate is defined
	#bitrate  "128"  # do not define if quality is defined (was 128)
	format  "22050:16:1"
	max_clients "3"   # optional 0=no limit
}

music_directory	"~/Music"
playlist_directory	"~/.mpd/playlists"
db_file	"~/.mpd/mpd.db"
log_file	"~/.mpd/mpd.log"
pid_file	"~/.mpd/mpd.pid"
state_file	"~/.mpd/mpdstate"

```

It binds to ipv6 and not to ipv4 and listens to everything under the sink (so here's hoping my firewalls work well). But at least it works!

It takes a while for the phone to get the sound, so one needs to be patient.

---

