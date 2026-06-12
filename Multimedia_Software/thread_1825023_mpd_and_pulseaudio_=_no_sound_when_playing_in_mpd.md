---
title: "mpd and pulseaudio = no sound when playing in mpd"
date: 2011-08-14
forum: Multimedia Software
---

### Post by graysky on 2011-08-14
Just like the title says,  when I use mpd with pulseaudio, I get no sound but clients appear to be playing (ncmpcpp and gmpc).  Other players such as vlc or mplayer work just fine.

If I go under the mixer, I get "no application is currently playing or recording audio" under the "Applications" tab when playing through mpd.  In contrast, when I'm using mplayer or vlc, both show up in that tab.  It behaves as though pulse is simply not configured to work with mpd.

Here is my config (edited out any commented line for brevity):
```
$ cat /etc/mpd.conf | sed '/#/d'
music_directory		"/media/data/DM/Genre"
playlist_directory	"/var/lib/mpd/playlists"
db_file			"/var/lib/mpd/mpd.db"
log_file		"/var/log/mpd/mpd.log"
pid_file		"/var/run/mpd/mpd.pid"
state_file		"/var/lib/mpd/mpdstate"
user "mpd"

log_level     "verbose"

gapless_mp3_playback			"yes"

zeroconf_enabled		"yes"
zeroconf_name			"Music Player"

input {
        plugin "curl"
}

audio_output {
	type		"pulse"
name		"My Pulse Output"
}

mixer_type			"software"
audio_buffer_size "35000"
buffer_before_play "5%"
```

Pulseaudio is running for mpd:
```
$ ps aux | grep mpd
mpd       6503  0.4  0.0 222952  4840 ?        S<sl 15:26   0:00 /usr/bin/pulseaudio --start --log-target=syslog
mpd       6507  0.0  0.0 102992  3228 ?        S    15:26   0:00 /usr/lib/pulse/gconf-helper
```

I switched the loglevel to verbose, deleted the existing log, started mpd so a fresh log would get written and tried to play a tune.  No audio output but it appeared to be playing in the client.  Here is the log.

```
# cat /var/log/mpd/mpd.log 
Aug 14 15:22 : avahi: Initializing interface
Aug 14 15:22 : avahi: Client changed to state 101
Aug 14 15:22 : avahi: Client is CONNECTING
Aug 14 15:22 : state_file: Loading state file /var/lib/mpd/mpdstate
Aug 14 15:22 : database: get song: Not_So_Hard_Stuff/Disturbed-The Sickness-2000-flac/01_Voices.flac
Aug 14 15:22 : client: [0] opened from [::1]:57866
Aug 14 15:22 : client: [0] process command "status"
Aug 14 15:22 : client: [0] command returned 0
Aug 14 15:22 : client: [0] process command "idle"
Aug 14 15:22 : client: [0] command returned 1
Aug 14 15:22 : client: [0] process command "plchanges "0""
Aug 14 15:22 : client: [0] command returned 0
Aug 14 15:22 : client: [0] process command "idle"
Aug 14 15:22 : client: [0] command returned 1
Aug 14 15:22 : client: [0] process command "idle"
Aug 14 15:22 : client: [0] command returned 1
Aug 14 15:22 : client: [0] process command "status"
Aug 14 15:22 : client: [0] command returned 0
Aug 14 15:22 : client: [0] process command "idle"
Aug 14 15:22 : client: [0] command returned 1
Aug 14 15:22 : client: [0] process command "play"
Aug 14 15:22 : playlist: play 0:"Not_So_Hard_Stuff/Disturbed-The Sickness-2000-flac/01_Voices.flac"
Aug 14 15:22 : decoder_thread: clearing mixramp tags
Aug 14 15:22 : decoder_control: mixramp_start = NULL
Aug 14 15:22 : decoder_control: mixramp_prev_end = NULL
Aug 14 15:22 : client: [0] command returned 0
Aug 14 15:22 : client: [0] process command "status"
Aug 14 15:22 : client: [0] command returned 0
Aug 14 15:22 : client: [0] process command "currentsong"
Aug 14 15:22 : client: [0] command returned 0
Aug 14 15:22 : client: [0] process command "idle"
Aug 14 15:22 : client: [0] command returned 1
Aug 14 15:22 : decoder: audio_format=44100:16:2, seekable=true
Aug 14 15:22 : output: opened plugin=pulse name="My Pulse Output" audio_format=44100:16:2
Aug 14 15:22 : client: [0] process command "status"
Aug 14 15:22 : client: [0] command returned 0
Aug 14 15:22 : client: [0] process command "idle"
Aug 14 15:22 : client: [0] command returned 1
Aug 14 15:22 : client: [0] process command "status"
Aug 14 15:22 : client: [0] command returned 0
Aug 14 15:22 : client: [0] process command "idle"
Aug 14 15:22 : client: [0] command returned 1
Aug 14 15:22 : client: [0] process command "status"
Aug 14 15:22 : client: [0] command returned 0
Aug 14 15:22 : client: [0] process command "idle"
Aug 14 15:22 : client: [0] command returned 1
Aug 14 15:22 : client: [0] process command "status"
Aug 14 15:22 : client: [0] command returned 0
Aug 14 15:22 : client: [0] process command "idle"
Aug 14 15:22 : client: [0] command returned 1
Aug 14 15:22 : client: [0] process command "status"
Aug 14 15:22 : client: [0] command returned 0
Aug 14 15:22 : client: [0] process command "idle"
Aug 14 15:22 : client: [0] command returned 1
Aug 14 15:22 : client: [0] process command "status"
Aug 14 15:22 : client: [0] command returned 0
Aug 14 15:22 : client: [0] process command "idle"
Aug 14 15:22 : client: [0] command returned 1
Aug 14 15:23 : client: [0] process command "status"
Aug 14 15:23 : client: [0] command returned 0
Aug 14 15:23 : client: [0] process command "idle"
Aug 14 15:23 : client: [0] command returned 1
Aug 14 15:23 : client: [0] process command "status"
Aug 14 15:23 : client: [0] command returned 0
Aug 14 15:23 : client: [0] process command "idle"
Aug 14 15:23 : client: [0] command returned 1
Aug 14 15:23 : client: [0] process command "status"
Aug 14 15:23 : client: [0] command returned 0
Aug 14 15:23 : client: [0] process command "idle"
Aug 14 15:23 : client: [0] command returned 1
Aug 14 15:23 : client: [0] process command "status"
Aug 14 15:23 : client: [0] command returned 0
Aug 14 15:23 : client: [0] process command "idle"
Aug 14 15:23 : client: [0] command returned 1
Aug 14 15:23 : client: [0] process command "status"
Aug 14 15:23 : client: [0] command returned 0
Aug 14 15:23 : client: [0] process command "idle"
Aug 14 15:23 : client: [0] command returned 1
Aug 14 15:23 : client: [0] process command "status"
Aug 14 15:23 : client: [0] command returned 0
Aug 14 15:23 : client: [0] process command "idle"
Aug 14 15:23 : client: [0] command returned 1
Aug 14 15:23 : client: [0] process command "status"
Aug 14 15:23 : client: [0] command returned 0
Aug 14 15:23 : client: [0] process command "idle"
Aug 14 15:23 : client: [0] command returned 1
Aug 14 15:23 : client: [0] process command "status"
Aug 14 15:23 : client: [0] command returned 0
Aug 14 15:23 : client: [0] process command "idle"
Aug 14 15:23 : client: [0] command returned 1
Aug 14 15:23 : client: [0] process command "status"
Aug 14 15:23 : client: [0] command returned 0
Aug 14 15:23 : client: [0] process command "idle"
Aug 14 15:23 : client: [0] command returned 1
Aug 14 15:23 : client: [0] process command "clear"
Aug 14 15:23 : playlist: stop
Aug 14 15:23 : output: closed plugin=pulse name="My Pulse Output"
Aug 14 15:23 : client: [0] command returned 0
Aug 14 15:23 : client: [0] process command "status"
Aug 14 15:23 : client: [0] command returned 0
Aug 14 15:23 : client: [0] process command "idle"
Aug 14 15:23 : client: [0] command returned 1
Aug 14 15:23 : client: [0] process command "plchanges "2""
Aug 14 15:23 : client: [0] command returned 0
Aug 14 15:23 : client: [0] process command "idle"
Aug 14 15:23 : client: [0] command returned 1
Aug 14 15:23 : client: [0] process command "idle"
Aug 14 15:23 : client: [0] command returned 1
Aug 14 15:23 : client: [0] process command "status"
Aug 14 15:23 : client: [0] command returned 0
Aug 14 15:23 : client: [0] process command "idle"
Aug 14 15:23 : client: [0] command returned 1
Aug 14 15:23 : client: [0] closed
Aug 14 15:23 : state_file: Saving state file /var/lib/mpd/mpdstate
Aug 14 15:23 : avahi: Shutting down interface
Aug 14 15:23 : listen: listen_global_finish called
Aug 14 15:23 : db_finish took 0.010000 seconds
```

---

### Post by afrodeity on 2011-08-15
All you need for pulseaudio is:

```


audio_output {
	type		"alsa"
	name		"My ALSA Device"
	device		"hw:0,0"	# optional
	format		"44100:16:2"	# optional
	mixer_device	"default"	# optional
#	mixer_control	"PCM"		# optional
	mixer_control   "Master"
	mixer_index	"0"		# optional
	mixer_type 	"software"
}


audio_output {
	type 		"pulse"
	name 		"My MPD PulseAudio Output"
}

```

Check [here]("http://ubuntuforums.org/showthread.php?t=1298789")

---

