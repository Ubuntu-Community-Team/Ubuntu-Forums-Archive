---
title: "MPD behaves weird with Pulse audio"
date: 2012-05-17
forum: Multimedia Software
---

### Post by NoiSeNOR on 2012-05-17
I have been battling for servial hours now getting MPD to work with Pulse audio, now i'm at the end of what i can take. I have done alot weird stuff, can't remember everything but this is how it behaves now which is the best i could get so far:

When having a fresh session, or/and no other programs are shown in the "playback" tab in pavucontrol, it would run(playback and sound) although mpd itself does not show up in pavucontrol nor does show the sound created in the volume meter on the output device.

When staring f.ex. a youtube playback, skype and stuff like that, while mpd is playing, it shows up in the "playback" tab, but i can not hear it nor does it show up on the volume meter. When i then stop mpd, after a few seconds the sound of the yt video or skype would finally be there but then mpd won't even start playing anymore. 

**So in short:** mpd is completely invisible for pulseaudio, and it either overides all pulseaudio or gets overriden by it, 

but i wan't it to work with pulseaudio, not against it :sad:


i have enabled "network access to local sound devices" and "don't require authentication" in pulseaudio Preference

and **my mpd.conf is**:

```

music_directory		"/home/heiko/Music/Musikk"
playlist_directory		"/home/heiko/Music/Musikk/playlists"

db_file			"/var/lib/mpd/tag_cache"
log_file			"/var/log/mpd/mpd.log"
pid_file			"/var/run/mpd/pid"
state_file			"/var/lib/mpd/state"
sticker_file                   "/var/lib/mpd/sticker.sql"

user				"mpd"
#group                          "nogroup"

bind_to_address		"localhost"
#port				"6600"

#log_level			"default"
#gapless_mp3_playback			"yes"
#save_absolute_paths_in_playlists	"no"
#metadata_to_use	"artist,album,title,track,name,genre,date,composer,performer,disc"
#auto_update    "yes"
#auto_update_depth "3"

#follow_outside_symlinks	"yes"
#follow_inside_symlinks		"yes"

#zeroconf_enabled		"yes"
#zeroconf_name			"Music Player"

#password                        "password@read,add,control,admin"
#default_permissions             "read,add,control,admin"

input {
        plugin "curl"
#       proxy "proxy.isp.com:8080"
#       proxy_user "user"
#       proxy_password "password"
}

#audio_output {
#	type		"alsa"
#	name		"My ALSA Device"
#	device		"hw:0,0"	# optional
#	format		"44100:16:2"	# optional
#	mixer_device	"default"	# optional
#	mixer_control	"PCM"		# optional
#	mixer_index	"0"		# optional
#}

audio_output {
	type		"pulse"
	name		"MPD"
#	device "hw:0,0" # optional
#	format "44100:16:2" # optional
#	server		"remote_server"		# optional
#	sink		"remote_server_sink"	# optional
}

#samplerate_converter		"Fastest Sinc Interpolator"

#mixer_type			"hardware"
#mixer_type			"software"
#mixer_type			"disabled"
#replaygain			"album"
#replaygain_preamp		"0"
#volume_normalization		"no"
#audio_buffer_size		"2048"
#buffer_before_play		"10%"

#connection_timeout		"60"
#max_connections		"10"
#max_playlist_length		"16384"
#max_command_list_size		"2048"
#max_output_buffer_size		"8192"

filesystem_charset		"UTF-8"
id3v1_encoding			"UTF-8"

#decoder {
#       plugin                  "sidplay"
#       songlength_database     "/media/C64Music/DOCUMENTS/Songlengths.txt"
#       default_songlength      "120"
#       filter "true"
#}

```

Note:
```

audio_output {
	type		"pulse"
	name		"MPD"
}

```

after all i know that should be everything you need to make it work with pulseaudio, but somehow it's still not working

[SIZE="3"]**SOLUTION:**[/SIZE]
 I added the line:
```
	server		"localhost"
```

to the pulse audio:output part in mpd.conf so it should look something like this:

```
audio_output {
	type		"pulse"
	name		"MPD"
	server		"localhost"
}
```

It now displays as it should in pavucontrol as Music Player Daemon and plays nice together with other audio sources.

---

### Post by number5 on 2012-05-17
First thing I'd like to check is if the mpd user is in pulse-access group.
Also look at the mpd.log to see if there are any pulse related error there.

PS: I would suggest to use mpd-userspace from [https://launchpad.net/~gmpc-trunk/+archive/mpd-trunk](https://launchpad.net/~gmpc-trunk/+archive/mpd-trunk)
that'll save you from a lots of permission problems.

---

### Post by NoiSeNOR on 2012-05-18
> **number5 said:**
> First thing I'd like to check is if the mpd user is in pulse-access group.

it already is there:
```
heiko@PUNKIN:~$ id mpd
uid=109(mpd) gid=29(audio) groups=29(audio),117(pulse),118(pulse-access)

```

> **number5 said:**
> 
Also look at the mpd.log to see if there are any pulse related error there.

This is the output of mpd.log after starting it in a fresh session, then stoping the playback, then starting a yt playing, then trying to play again:
```
No protocol specified
xcb_connection_has_error() returned true
No protocol specified
May 18 11:06 : avahi: Service 'Music Player' successfully established.
May 18 11:07 : output: "MPD" [pulse] failed to play: suspended
May 18 11:07 : output: "MPD" [pulse] failed to play: suspended
May 18 11:07 : output: "MPD" [pulse] failed to play: suspended
May 18 11:07 : output: "MPD" [pulse] failed to play: suspended
May 18 11:07 : output: "MPD" [pulse] failed to play: suspended
```

> **number5 said:**
> 
PS: I would suggest to use mpd-userspace from [https://launchpad.net/~gmpc-trunk/+archive/mpd-trunk](https://launchpad.net/~gmpc-trunk/+archive/mpd-trunk)
that'll save you from a lots of permission problems.

i installed it. But to be honest, i don't know what to do with it know, only thing it did is giving me the option to download an alternative mpd.conf, which didn't work.


**Edit: i got it to work**, googling the error messange from mpd.conf i found a thread, solution was to add 
```
	server		"localhost"
```

to the pulse audio_output in mpd.conf. It seems to work nicly naow, tho does stop playin when i logout, which is not a problem for me tho.

---

