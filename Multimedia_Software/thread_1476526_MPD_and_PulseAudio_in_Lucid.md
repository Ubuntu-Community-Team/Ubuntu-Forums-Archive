---
title: "MPD and PulseAudio in Lucid"
date: 2010-05-07
forum: Multimedia Software
---

### Post by paranoid_humanoid on 2010-05-07
Hi, I can't seem to get mpd to be able to talk to PulseAudio at all in Lucid. Using both versions from the standard Ubuntu repositories and now that I've upgraded MPD to 0.16 as well.

This is my /etc/mpd.conf:
```
# An example configuration file for MPD
# See the mpd.conf man page for a more detailed description of each parameter.


# Files and directories #######################################################
#
# This setting controls the top directory which MPD will search to discover the
# available audio files and add them to the daemon's online database. This 
# setting defaults to the XDG directory, otherwise the music directory will be
# be disabled and audio files will only be accepted over ipc socket (using
# file:// protocol) or streaming files over an accepted protocol.
#
music_directory		"/media/Saturn/Music"
#
# This setting sets the MPD internal playlist directory. The purpose of this
# directory is storage for playlists created by MPD. The server will use 
# playlist files not created by the server but only if they are in the MPD
# format. This setting defaults to playlist saving being disabled.
#
playlist_directory		"/var/lib/mpd/playlists"
#
# This setting sets the location of the MPD database. This file is used to
# load the database at server start up and store the database while the 
# server is not up. This setting defaults to disabled which will allow
# MPD to accept files over ipc socket (using file:// protocol) or streaming
# files over an accepted protocol.
#
db_file			"/var/lib/mpd/tag_cache"
# 
# These settings are the locations for the daemon log files for the daemon.
# These logs are great for troubleshooting, depending on your log_level
# settings.
#
# The special value "syslog" makes MPD use the local syslog daemon. This
# setting defaults to logging to syslog, otherwise logging is disabled.
#
log_file			"/var/log/mpd/mpd.log"
#
# This setting sets the location of the file which stores the process ID
# for use of mpd --kill and some init scripts. This setting is disabled by
# default and the pid file will not be stored.
#
pid_file			"/var/run/mpd/pid"
#
# This setting sets the location of the file which contains information about
# most variables to get MPD back into the same general shape it was in before
# it was brought down. This setting is disabled by default and the server 
# state will be reset on server start up.
#
state_file			"/var/lib/mpd/state"
#
# The location of the sticker database.  This is a database which
# manages dynamic information attached to songs.
#
sticker_file		"/var/lib/mpd/sticker.sqlite"
#
###############################################################################


# General music daemon options ################################################
#
# This setting specifies the user that MPD will run as. MPD should never run as
# root and you may use this setting to make MPD change its user ID after
# initialization. This setting is disabled by default and MPD is run as the
# current user.
#
user				"mpd"
#
# This setting specifies the group that MPD will run as. If not specified
# primary group of user specified with "user" setting will be used (if set).
# This is useful if MPD needs to be a member of group such as "audio" to
# have permission to use sound card.
#
group				"audio"
#
# This setting sets the address for the daemon to listen on. Careful attention
# should be paid if this is assigned to anything other then the default, any.
# This setting can deny access to control of the daemon.
#
# For network
#bind_to_address		"localhost"
#
# And for Unix Socket
#bind_to_address		"/var/run/mpd/socket"
#
# This setting is the TCP port that is desired for the daemon to get assigned
# to.
#
#port				"6600"
#
# This setting controls the type of information which is logged. Available 
# setting arguments are "default", "secure" or "verbose". The "verbose" setting
# argument is recommended for troubleshooting, though can quickly stretch
# available resources on limited hardware storage.
#
#log_level			"default"
#
# If you have a problem with your MP3s ending abruptly it is recommended that 
# you set this argument to "no" to attempt to fix the problem. If this solves
# the problem, it is highly recommended to fix the MP3 files with vbrfix
# (available from <http://www.willwap.co.uk/Programs/vbrfix.php>), at which
# point gapless MP3 playback can be enabled.
#
gapless_mp3_playback			"yes"
#
# This setting enables MPD to create playlists in a format usable by other
# music players.
#
#save_absolute_paths_in_playlists	"no"
#
# This setting defines a list of tag types that will be extracted during the 
# audio file discovery process. Optionally, 'comment' can be added to this
# list.
#
#metadata_to_use	"artist,album,title,track,name,genre,date,composer,performer,disc"
#
# This setting enables automatic update of MPD's database when files in 
# music_directory are changed.
#
#auto_update	"yes"
###############################################################################


# Symbolic link behavior ######################################################
#
# If this setting is set to "yes", MPD will discover audio files by following 
# symbolic links outside of the configured music_directory.
#
#follow_outside_symlinks	"yes"
#
# If this setting is set to "yes", MPD will discover audio files by following
# symbolic links inside of the configured music_directory.
#
#follow_inside_symlinks		"yes"
#
###############################################################################


# Zeroconf / Avahi Service Discovery ##########################################
#
# If this setting is set to "yes", service information will be published with
# Zeroconf / Avahi.
#
#zeroconf_enabled		"yes"
#
# The argument to this setting will be the Zeroconf / Avahi unique name for
# this MPD server on the network.
#
#zeroconf_name			"Music Player"
#
###############################################################################


# Permissions #################################################################
#
# If this setting is set, MPD will require password authorization. The password
# can setting can be specified multiple times for different password profiles.
#
#password                        "password@read,add,control,admin"
#
# This setting specifies the permissions a user has who has not yet logged in. 
#
#default_permissions             "read,add,control,admin"
#
###############################################################################


# Input #######################################################################
#

input {
        plugin "curl"
#       proxy "proxy.isp.com:8080"
#       proxy_user "user"
#       proxy_password "password"
}

#
###############################################################################

# Audio Output ################################################################
#
# MPD supports various audio output types, as well as playing through multiple 
# audio outputs at the same time, through multiple audio_output settings 
# blocks. Setting this block is optional, though the server will only attempt
# autodetection for one sound card.
#
# See <http://mpd.wikia.com/wiki/Configuration#Audio_Outputs> for examples of 
# other audio outputs.
#
# An example of an ALSA output:
#
audio_output {
	type		"alsa"
	name		"My ALSA Device"
	device		"hw:0,0"	# optional
	format		"44100:16:2"	# optional
	mixer_type      "software"	# optional
	mixer_device	"default"	# optional
	mixer_control	"PCM"		# optional
	mixer_index	"0"		# optional
}
#
# An example of an OSS output:
#
#audio_output {
#	type		"oss"
#	name		"My OSS Device"
##	device		"/dev/dsp"	# optional
##	format		"44100:16:2"	# optional
##	mixer_type      "hardware"	# optional
##	mixer_device	"/dev/mixer"	# optional
##	mixer_control	"PCM"		# optional
#}
#
# An example of a shout output (for streaming to Icecast):
#
#audio_output {
#	type		"shout"
#	encoding	"ogg"			# optional
#	name		"My Shout Stream"
#	host		"localhost"
#	port		"8000"
#	mount		"/mpd.ogg"
#	password	"hackme"
#	quality		"5.0"
#	bitrate		"128"
#	format		"44100:16:1"
##	protocol	"icecast2"		# optional
##	user		"source"		# optional
##	description	"My Stream Description"	# optional
##	genre		"jazz"			# optional
##	public		"no"			# optional
##	timeout		"2"			# optional
##	mixer_type      "software"		# optional
#}
#
# An example of a recorder output:
#
#audio_output {
#	type		"recorder"
#	name		"My recorder"
#	encoder		"vorbis"		# optional, vorbis or lame
#	path		"/var/lib/mpd/recorder/mpd.ogg"
##	quality		"5.0"			# do not define if bitrate is defined
#	bitrate		"128"			# do not define if quality is defined
#	format		"44100:16:1"
#}
#
# An example of a httpd output (built-in HTTP streaming server):
#
audio_output {
	type		"httpd"
	name		"Local Radio"
	encoder		"vorbis"		# optional, vorbis or lame
	port		"8000"
##	quality		"5.0"			# do not define if bitrate is defined
	bitrate		"192"			# do not define if quality is defined
	format		"44100:16:1"
	max_clients	"0"			# optional 0=no limit
}
#
# An example of a pulseaudio output (streaming to a remote pulseaudio server)
#
audio_output {
	type		"pulse"
	name		"My Pulse Output"
#	server		"remote_server"		# optional
#	sink		"remote_server_sink"	# optional
}
#
## Example "pipe" output:
#
#audio_output {
#	type		"pipe"
#	name		"my pipe"
#	command		"aplay -f cd 2>/dev/null"
## Or if you're want to use AudioCompress
#	command		"AudioCompress -m | aplay -f cd 2>/dev/null"
## Or to send raw PCM stream through PCM:
#	command		"nc example.org 8765"
#	format		"44100:16:2"
#}
#
## An example of a null output (for no audio output):
#
#audio_output {
#	type		"null"
#	name		"My Null Output"
#	mixer_type      "none"			# optional
#}
#
# This setting will change all decoded audio to be converted to the specified
# format before being passed to the audio outputs. By default, this setting is
# disabled.
#
#audio_output_format		"44100:16:2"
#
# If MPD has been compiled with libsamplerate support, this setting specifies 
# the sample rate converter to use.  Possible values can be found in the 
# mpd.conf man page or the libsamplerate documentation. By default, this is
# setting is disabled.
#
#samplerate_converter		"Fastest Sinc Interpolator"
#
###############################################################################


# Normalization automatic volume adjustments ##################################
#
# This setting specifies the type of ReplayGain to use. This setting can have
# the argument "off", "album" or "track". See <http://www.replaygain.org>
# for more details. This setting is off by default.
#
#replaygain			"album"
#
# This setting sets the pre-amp used for files that have ReplayGain tags. By
# default this setting is disabled.
#
#replaygain_preamp		"0"
#
# This setting enables on-the-fly normalization volume adjustment. This will
# result in the volume of all playing audio to be adjusted so the output has 
# equal "loudness". This setting is disabled by default.
#
#volume_normalization		"no"
#
###############################################################################


# MPD Internal Buffering ######################################################
#
# This setting adjusts the size of internal decoded audio buffering. Changing
# this may have undesired effects. Don't change this if you don't know what you
# are doing.
#
#audio_buffer_size		"2048"
#
# This setting controls the percentage of the buffer which is filled before 
# beginning to play. Increasing this reduces the chance of audio file skipping, 
# at the cost of increased time prior to audio playback.
#
#buffer_before_play		"10%"
#
###############################################################################


# Resource Limitations ########################################################
#
# These settings are various limitations to prevent MPD from using too many
# resources. Generally, these settings should be minimized to prevent security
# risks, depending on the operating resources.
#
#connection_timeout		"60"
#max_connections		"10"
#max_playlist_length		"16384"
#max_command_list_size		"2048"
#max_output_buffer_size		"8192"
#
###############################################################################


# Character Encoding ##########################################################
#
# If file or directory names do not display correctly for your locale then you 
# may need to modify this setting.
#
filesystem_charset		"UTF-8"
#
# This setting controls the encoding that ID3v1 tags should be converted from.
#
id3v1_encoding			"UTF-8"
#
###############################################################################
```

I set PulseAudio to enable network access and not to require authentication from paprefs. MPD works fine with ALSA and HTTPD. This is what it says in the log when I enable my pulse output:
```
May 08 05:16 : output: Failed to enable "My Pulse Output" [pulse]: pa_context_new() has failed
```

Any ideas? Btw, MPD and PA were running smoothely on karmic using the exact same setup.

---

### Post by Method X on 2010-05-08
Same problem. I think solution will be with some updates e.t.c... ;)

---

### Post by paranoid_humanoid on 2010-05-08
This workaround worked for me [http://mpd.wikia.com/wiki/PulseAudio#For_Distros_where_PulseAudio_output_is_broken](http://mpd.wikia.com/wiki/PulseAudio#For_Distros_where_PulseAudio_output_is_broken)

Use this as an output device:
```
audio_output {
type "ao"
driver "esd"
options "host=127.0.0.1:16001"
name "esd"
mixer_type "software"
}

```

---

### Post by sp200606 on 2010-05-31
Make sure the mpd user has access rights to pulse:

Supposing the mpd user (as defined in /etc/mpd.conf) is "mpd",
```
sudo vi /etc/group
```
then add mpd to the pulse-access line like:

```
pulse-access:x:116:mpd
```

save and

```
sudo killall pulseaudio
sudo killall mpd
```

```
sudo /etc/init.d/pulseaudio start
sudo /etc/init.d/mpd start
mpc play
```

... and hopefully, it's done!

---

### Post by paranoid_humanoid on 2010-06-01
> **sp200606 said:**
> Make sure the mpd user has access rights to pulse:

Supposing the mpd user (as defined in /etc/mpd.conf) is "mpd",
```
sudo vi /etc/group
```
then add mpd to the pulse-access line like:

```
pulse-access:x:116:mpd
```

save and

```
sudo killall pulseaudio
sudo killall mpd
```

```
sudo /etc/init.d/pulseaudio start
sudo /etc/init.d/mpd start
mpc play
```

... and hopefully, it's done!

Sadly not. I still get:
> bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)


---

### Post by jamesrl on 2010-07-05
> **sp200606 said:**
> ```
sudo killall pulseaudio
sudo killall mpd
sudo /etc/init.d/pulseaudio start
sudo /etc/init.d/mpd start
mpc play
```

... and hopefully, it's done!

This procedure works for me, except I have to do it every time I reboot.  E.g., after mpd thinks it started ok (no error messages), but all songs have no sound whatsoever.  There's an error message in /var/log/mpd/mpd.log:
```

No protocol specified
XOpenDisplay() failed

```
If I do the restart of both (by first killing pulseaudio with killall; just doing /etc/init.d/pulseaudio restart will not fix the problem), then mpd will work fine.

Investigating, I first thought it had to do with the order of the startup scripts, as it seems that mpd starts before pulseaudio.  E.g., /etc/rc3.d contains: ```

S30mpd 
S50pulseaudio

```
So I just moved S30mpd to S55mpd in each /etc/rc[2-5].d directory:
```

sudo mv /etc/rc2.d/S30mpd /etc/rc2.d/S55mpd
sudo mv /etc/rc3.d/S30mpd /etc/rc3.d/S55mpd
sudo mv /etc/rc4.d/S30mpd /etc/rc4.d/S55mpd
sudo mv /etc/rc5.d/S30mpd /etc/rc5.d/S55mpd
# actually I just did the following line which is equivalent to above
for f in /etc/rc[2-5].d/S30mpd; do sudo mv $f ${f/30/55} ; done

```
but on reboot this didn't solve the problem.  

I've also followed advice modifying PulseAudio Prefs after installing and using paprefs, enabling network access to local sound devices and not requiring authentication.  

I'd rather not have to manually killall for pulseaudio manually every time I reboot, and also don't want to have a login script either.  (As I frequently ssh in, and switch between other users and don't want that messing up the sound server).  Any suggestions?

---

### Post by shaggy999 on 2010-08-03
I am also having these same problems. I can also confirm that the fix above has to be done after every reboot.

---

### Post by genjix on 2010-08-12
broken here. not found any fixes yet.

---

### Post by lidex on 2010-08-14
[http://www.google.com/search?client=ubuntu&channel=fs&q=mpd+autostart&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=mpd+autostart&ie=utf-8&oe=utf-8)

---

### Post by DodgeV83 on 2010-11-21
My solution to using Pulseaudio with MPD, giving me full volume support in my iPhone MPD client app:

```

audio_output {
	type		"pulse"
	name		"My Pulse Output"
	#server		"localhost"		# optional
	#sink		"alsa_output"	# optional
}
```

I also set the "user" preference to my username:

```

# This setting specifies the user that MPD will run as. MPD should never run as
# root and you may use this setting to make MPD change its user ID after
# initialization. This setting is disabled by default and MPD is run as the
# current user.
#
user				"rob"
```

This worked in both 10.04 and 10.10.

Note, I made these changes to the mpd.conf file, located either in /etc/mpd.conf or your home_diretory/.mpd.conf

---

### Post by reireirei on 2011-01-27
i have exactly the same problem. its started happening when i enabled the state file on mpd.conf.
so the problem seems to be fixed if you comment out the state file line on mpd.conf.

but i really wanted mpd to restore state on startup. does anyone know a workaround for this?

edit: ok, i found a solution: i used sysv-rc-conf to set mpd runlevel to 1, and then start manually mpd with "/etc/init.d/mpd start" after login, whitch can be put at startup applications.
im not sure what this means, but works lol. thanks anyways

---

### Post by blackgr on 2011-02-16
Install paprefs
Go to Network Server tab
Tick first and third box

---

### Post by snapback77 on 2011-02-20
Try this link.  Worked for me.

[http://ubuntuforums.org/showthread.php?t=1298789](http://ubuntuforums.org/showthread.php?t=1298789)

---

