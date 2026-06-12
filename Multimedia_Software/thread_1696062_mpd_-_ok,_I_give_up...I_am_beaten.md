---
title: "mpd - ok, I give up...I am beaten"
date: 2011-02-26
forum: Multimedia Software
---

### Post by dunbrokin on 2011-02-26
I had mpd installed and running throughout my home system...it ran great. Then I got WD Elements 500G drive as I was running out of space. I had a problem with the permissioning as it was NTFS...so, ok I reformatted the disk with no partition and ext4. I reinstalled Sonata and mpd. I set up a link in /var/lib/mpd/music/ to my music...and bingo ...it should work....but it does not...and I have no idea why. I have tried everything I can think of....I am now beaten. 

Any suggestions appreciated.

ls -l shows
total 4

drwxrwxrwx 4 music music 4096 2011-02-27 13:42 JukeBox1

I have no idea what the 4 applies to?!!?

Where do I go from here.

---

### Post by dunbrokin on 2011-02-27
Bump....anybody?

---

### Post by samfuzz on 2011-02-27
can you post what gives :

/usr/bin/mpd --version

kill mpd and start it whith this line and gives the result:

/usr/bin/mpd /etc/mpd.conf --verbose --no-daemon --stdout

and post your mpd.conf

---

### Post by dunbrokin on 2011-02-27
music@MusicBox:~$ /usr/bin/mpd --version
mpd (MPD: Music Player Daemon) 0.15.10 

Copyright (C) 2003-2007 Warren Dukes <warren.dukes@gmail.com>
Copyright (C) 2008 Max Kellermann <max@duempel.org>
This is free software; see the source for copying conditions.  There is NO
warranty; not even MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

Supported decoders:

[mad] mp3 mp2
[vorbis] ogg oga
[oggflac] ogg oga
[flac] flac
[audiofile] wav au aiff aif
[faad] aac
[mpcdec] mpc
[wavpack] wv
[sidplay] sid
[ffmpeg] 16sv 3g2 3gp 4xm 8svx aa3 aac ac3 afc aif aifc aiff al alaw amr anim apc ape asf atrac au aud avi avm2 avs bap bfi c93 cak cin cmv cpk daud dct divx dts dv dvd dxa eac3 film flac flc fli fll flx flv g726 gsm gxf iss m1v m2v m2t m2ts m4a m4v mad mj2 mjpeg mjpg mka mkv mlp mm mmf mov mp+ mp1 mp2 mp3 mp4 mpc mpeg mpg mpga mpp mpu mve mvi mxf nc nsv nut nuv oga ogm ogv ogx oma ogg omg psp pva qcp qt r3d ra ram rl2 rm rmvb roq rpl rvc shn smk snd sol son spx str swf tgi tgq tgv thp ts tsp tta xa xvid uv uv2 vb vid vob voc vp6 vmd wav wma wmv wsaud wsvga wv wve

Supported outputs:

shout null fifo alsa ao oss pulse jack httpd 

Supported protocols:

file:// http:// lastfm:// mms:// mmsh:// mmst:// mmsu://

---

### Post by dunbrokin on 2011-02-27
music@MusicBox:~$ /usr/bin/mpd /etc/mpd.conf --verbose --no-daemon --stdout
config: loading file /etc/mpd.conf
listen: binding to address for localhost
listen: binding to socket address [::1]:6600
listen: binding to socket address 127.0.0.1:6600
daemon: cannot setgid for user "mpd": Operation not permitted
Aborted

---

### Post by dunbrokin on 2011-02-27
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
music_directory		"/media/JukeBox1"
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
log_file			"~/.mpd/mpd.log"
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
state_file			"~/.mpd/state"
#
###############################################################################


# General music daemon options ################################################
#
# This setting specifies the user that MPD will run as. MPD should never run as
# root and you may use this setting to make MPD change its user ID after
# initialization. This setting is disabled by default and MPD is run as the
# current user.
#
#user				"mpd"
#
# This setting sets the address for the daemon to listen on. Careful attention
# should be paid if this is assigned to anything other then the default, any.
# This setting can deny access to control of the daemon.
#
# For network
bind_to_address		"localhost"
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
#gapless_mp3_playback			"yes"
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
#	device		"/dev/dsp"	# optional
#	format		"44100:16:2"	# optional
#	mixer_device	"/dev/mixer"	# optional
#	mixer_control	"PCM"		# optional
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
#	protocol	"icecast2"		# optional
#	user		"source"		# optional
#	description	"My Stream Description"	# optional
#	genre		"jazz"			# optional
#	public		"no"			# optional
#	timeout		"2"			# optional
#}
#
# An example of a httpd output (built-in HTTP streaming server):
#
#audio_output {
#	type		"httpd"
#	name		"My HTTP Stream"
#	encoder		"vorbis"		# optional, vorbis or lame
#	port		"8000"
#	quality		"5.0"			# do not define if bitrate is defined
#	bitrate		"128"			# do not define if quality is defined
#	format		"44100:16:1"
#}
#
# An example of a pulseaudio output (streaming to a remote pulseaudio server)
#
#audio_output {
#	type		"pulse"
#	name		"My Pulse Output"
#	server		"remote_server"		# optional
#	sink		"remote_server_sink"	# optional
#}
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


# Volume control mixer ########################################################
#
# These are the global volume control settings. By default, this setting will
# be detected to the available audio output device, with preference going to 
# hardware mixing. Hardware and software mixers for individual audio_output
# sections cannot yet be mixed.
#
# An example for controlling an ALSA, OSS or Pulseaudio mixer; If this
# setting is used other sound applications will be affected by the volume
# being controlled by MPD.
#
#mixer_type			"hardware"
#
# An example for controlling all mixers through software. This will control
# all controls, even if the mixer is not supported by the device and will not
# affect any other sound producing applications.
#
#mixer_type			"software"
#
# This example will not allow MPD to touch the mixer at all and will disable
# all volume controls.
#
#mixer_type			"disabled"
#
###############################################################################


# Normalization automatic volume adjustments ##################################
#
# This setting specifies the type of ReplayGain to use. This setting can have
# the argument "album" or "track". See <http://www.replaygain.org> for more
# details. This setting is disabled by default.
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
# may need to modify this setting. After modification of this setting mpd 
# --create-db must be run to change the database.
#
filesystem_charset		"UTF-8"
#
# This setting controls the encoding that ID3v1 tags should be converted from.
#
id3v1_encoding			"UTF-8"
#
###############################################################################

---

### Post by dunbrokin on 2011-02-28
We seem to be getting somewhere.....but I am not sure where to go next I still cannot see any files on any of the mpd clients.

---

### Post by dunbrokin on 2011-02-28
Feb 28 21:26 : update: added Classical Various/03 - Piano Converto No.2 - 4th mvt, Allegretto grazioso.ogg
Feb 28 21:26 : update: added Classical Various/04 - Symphony No.27 - 1st mvt, Allegro molto.ogg
Feb 28 21:26 : update: added Classical Various/10 - String Quartet No.3 - 2nd mvt, Allegretto vivo e scherzando.ogg
Feb 28 21:26 : database: unable to write to db file "/var/lib/mpd/tag_cache": Permission denied
Feb 28 21:27 : can't find alsa mixer control "PCM"
Feb 28 21:27 : update: Failed to open directory /media/JukeBox1/lost+found: Permission denied
Feb 28 21:27 : database: unable to write to db file "/var/lib/mpd/tag_cache": Permission denied
Feb 28 21:28 : update: Failed to open directory /media/JukeBox1/lost+found: Permission denied
Feb 28 21:28 : database: unable to write to db file "/var/lib/mpd/tag_cache": Permission denied

---

### Post by dunbrokin on 2011-02-28
OK, I have nearly cracked it......

The remaining problem is the /var/run/mpd/ fodler.....if I change the owner to "music" then it works.....however, when I reboot the machine, the permission has changed back from music to "mpd". I have deleted the owner "mpd"...but it gets reinstalled each time I reboot.....so close and yet so far. mpd is a great system.....but, geez. why is it so hard to get it to work!! It has taken me the best part of 2 days and I am still not there!!

---

### Post by dunbrokin on 2011-02-28
OK, now got mpd up and running...reinstalled and made sure all permissions were correct.....so, now we have mpd on PC A....but nothing on the network will recognize the music server (least what I am calling the music server). When I had mpd set up to access music on the hard drive, PC A was recognized by mpd remotes......now that I have all my music on a USB disk, the remotes will not recognise PC A as a music server.....where do I go (bed perhaps would be the best idea.) from here?!??!!?

---

### Post by aeiah on 2011-02-28
maybe you need to specify the port. its commented out in your mpd.conf but i assume that means it defaults to 6600. try uncommenting it and from another machine, try pinging your mpd server's ip, and try using telnet to connect to the mpd port. 
```

telnet ip.address 6600

```
it should connect if available.


or perhaps you were broadcasting the name via zeroconf before? that area of your mpd.conf is commented out.

---

### Post by samfuzz on 2011-02-28
check the permission of the configuration files of mpd.conf

if you set user as music in mpd.conf
check the permission for : tag_cache, mpd.log, pid, state
(all this files are in my home folder)
and permission to playlist and music_directory


cd /media/JukeBox1
sudo find . -type d -exec chmod 755 {} \;
sudo find . -type f -exec chmod 644 {} \;

---

### Post by dunbrokin on 2011-02-28
> **aeiah said:**
> maybe you need to specify the port. its commented out in your mpd.conf but i assume that means it defaults to 6600. try uncommenting it and from another machine, try pinging your mpd server's ip, and try using telnet to connect to the mpd port. 
```

telnet ip.address 6600

```
it should connect if available.


or perhaps you were broadcasting the name via zeroconf before? that area of your mpd.conf is commented out.


Thanks, I have uncommented it and restarted but the connection is being refused.

---

### Post by dunbrokin on 2011-02-28
> **samfuzz said:**
> check the permission of the configuration files of mpd.conf

if you set user as music in mpd.conf
check the permission for : tag_cache, mpd.log, pid, state
(all this files are in my home folder)
and permission to playlist and music_directory


cd /media/JukeBox1
sudo find . -type d -exec chmod 755 {} \;
sudo find . -type f -exec chmod 644 {} \;


You are also right....my permissions keep changing...I keep on getting owner as "mpd" and group as "audio". I don't even have these users set up on this PC. The only user is "music"...but when I change the permissions, they default back ot "mpd" and "audio" on reboot.

---

### Post by dunbrokin on 2011-02-28
> **samfuzz said:**
> check the permission of the configuration files of mpd.conf

if you set user as music in mpd.conf
check the permission for : tag_cache, mpd.log, pid, state
(all this files are in my home folder)
and permission to playlist and music_directory


cd /media/JukeBox1
sudo find . -type d -exec chmod 755 {} \;
sudo find . -type f -exec chmod 644 {} \;

10.1.1.10	MusicBox	# Added by NetworkManager
127.0.0.1	localhost.localdomain	localhost
::1	MusicBox	localhost6.localdomain6	localhost6
127.0.1.1	MusicBox

---

### Post by samfuzz on 2011-02-28
set in mpd.conf

user	 "music"
and leave group option commented

---

### Post by dunbrokin on 2011-02-28
> **samfuzz said:**
> set in mpd.conf

user	 "music"
and leave group option commented

That may indeed be one of the problems....however the other is that I cannot ping 10.1.1.10.....I can get to it via remote desktop viewer...which is how I am writing this...but it will not take a ping!

Even when I go on the machine and get it to ping itself, it does not do it....weird!

It looks like (from port scan) that 6600 is not open!

---

### Post by dunbrokin on 2011-02-28
Resolved: from another thread and the mpd forum - comment out the bind_to_address "localhost" line in mpd.conf


Thanks to all for their pointers and help....you rock.

---

