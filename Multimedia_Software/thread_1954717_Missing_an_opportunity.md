---
title: "Missing an opportunity?"
date: 2012-04-08
forum: Multimedia Software
---

### Post by whell on 2012-04-08
I'll preface this thread by stating that I'm a non-techie end user of the Lubuntu Linux OS.  I am an avid music lover, and I'm currently riding the wave of the huge surge in popularity of PC-based high resolution digital audio playback.  To that end, I'd like to use this thread to "wonder out loud" if Linux may be missing an opportunity to bring it's product to the masses by taking the lead on offering a distro that make hi res audio playback a snap, while also.offering sonic advantages to Windows (and maybe even Mac).

So, let's define terms - what is meant by his res playback?  Playback of audio files at CD resolution or better.  CD's have a resolution of 16 bits / 44.1 kHz.  Along with ripping your own CD's for playback, there are a number of music download services that sell music files (even whole CD's) for download with resolution equal to or even greater than CD.  HD Tracks is an example of a service that sells many albums with resolution of 24 bit / 96 kHz or greater.  

Linux can do a great job of playing these files, and even outputting the audio signal to an external digital to analog converter in a high quality (audiophile) home stereo system.  I use Lubuntu, which doesn't come loaded down with Pulse Audio, and makes playback of high res tracks very easy to achieve with he default audio player Audacious.

The dirty secret may be that setting up Linux to achieve high resolution playback of music may be even easier than it is in Windows (XP or Win 7).  It may also - at least to my ears - sound better!

So, I&#8217;m suggesting that maybe someone with far more skills that I have take on tailoring a distro to the home music crowd.  Something that makes set up easy, and playback fun.  Seems to me that Lubuntu would make a great starting point since it lacks Pukse Audio, which down samples music to 16/44.1 by default.  It's also light and fast, and can accommodate older hardware.

Thoughts?

---

### Post by whell on 2012-04-08
Just a add a couple caveats -

Simplicity is a must.  Don't even get me started on MPD.  It may be wonderful, but set up,is anything but intuitive.  And is you have you music files on an external hard drive or NAS, forget it.  Now, if there were a GUI - based set up program for MPD...   I've seen MPDpup, but it still ain't easy.

Flexibility will also be needed.  Folks are typically storing music on a home network, not a hard drive or thumb drive.

---

### Post by ridetheteapot on 2012-04-08
Well,wellwellwelll
MPD is teh #one.

You may not say bad things about it - and it is super simple to set up (really it is not hard at all). However it does require editing a text file, but you really only need to do it one time ever.

I use mpd/alsa to play Hires flacs over fiber optic cable (and can control it from everywhere), and i use 2 mpd streams to stream around the house (1 low quality for poor wireless connects, one high quality). The down side to mpd's native streaming, and icecast, is that your reencoding... As an audiophile you can't really stream around the house losslessly without some other file sharing (or netcat) but that does get more complicated.

But whell, there is a frontend for mpd, called gmpc (my favorite gui client) that has an autompd feature. It makes mpd use a snap.

---

### Post by whell on 2012-04-08
> **ridetheteapot said:**
> Well,wellwellwelll
MPD is teh #one.

You may not say bad things about it - and it is super simple to set up (really it is not hard at all). However it does require editing a text file, but you really only need to do it one time ever.

I use mpd/alsa to play Hires flacs over fiber optic cable (and can control it from everywhere), and i use 2 mpd streams to stream around the house (1 low quality for poor wireless connects, one high quality). The down side to mpd's native streaming, and icecast, is that your reencoding... As an audiophile you can't really stream around the house losslessly without some other file sharing (or netcat) but that does get more complicated.

But whell, there is a frontend for mpd, called gmpc (my favorite gui client) that has an autompd feature. It makes mpd use a snap.

I'm glad it's easy for you.  However, if that is Linux' definition of easy, then this suggestion is going nowhere.  Heck, last time I checked, MPD would not read files from an external hard drive, which is where quite a number of folks store their music files.

No, it must be intuitive to use, and editing cryptic config files is no small feat for the average Joe computer user.

---

### Post by hughr2005 on 2012-04-08
I think Ubuntu has even greater potential for music makers. For the last number of years, Mac OS X has been the industry standard platform for music making - but now it seems that Apple are making OS X more iOSsy. They're really focusing on the consumer market rather than power users. A few good open source DAWs and the like could possibly gain a few users that are having to leave OS X. Even now, when OSX upgrades a version, it's years before all the plugin manufacturers fix their software to run on it.

---

### Post by ridetheteapot on 2012-04-08
soz whell, was just mostly joking around (it really isn't too bad though). I'm a fanatic for mpd. Gmpc does make it easy to use mpd though (no need to make a config it will do it on the fly). mpd doesn't have any problem reading files from external drives or nfs/samba shares for that matter. The main reason I use mpd is it handles huge collections like a champ. I have a ton of 24bit live recordings. On the other hand I have a some dts 5.1 and dolby albums that I have never tried with mpd, always have used a custom mplayer script for that (custom cause mplayer doesn't do gapless on its own).


But as for a distro, it would be pretty easy to include a preconfigured mpd server, and then just link the music collection to any predefined place, making it transparent to the user.
I wonder though if jackd wouldn't be the ultimate way to do an audiophile distro, its very nice for studio application like hughr mentioned.

Really though why make a separate distro? All the tools are available, and not that much customizing is needed to get a nice sound. On that point though there is a audiophile distro aimed at embedded devices.

---

### Post by whell on 2012-04-08
> **ridetheteapot said:**
> soz whell, was just mostly joking around (it really isn't too bad though). I'm a fanatic for mpd. Gmpc does make it easy to use mpd though (no need to make a config it will do it on the fly). mpd doesn't have any problem reading files from external drives or nfs/samba shares for that matter. The main reason I use mpd is it handles huge collections like a champ. I have a ton of 24bit live recordings. On the other hand I have a some dts 5.1 and dolby albums that I have never tried with mpd, always have used a custom mplayer script for that (custom cause mplayer doesn't do gapless on its own).


But as for a distro, it would be pretty easy to include a preconfigured mpd server, and then just link the music collection to any predefined place, making it transparent to the user.
I wonder though if jackd wouldn't be the ultimate way to do an audiophile distro, its very nice for studio application like hughr mentioned.

Really though why make a separate distro? All the tools are available, and not that much customizing is needed to get a nice sound. On that point though there is a audiophile distro aimed at embedded devices.

You're not understanding me, I guess.  You're talking from the perspective of someone familiar with Linux, and is comfortable tweaking it.  The distro / product I'm suggesting needs to be built for the type of car driver who,never looks under the hood, not for the mechanic.  

MPD is just not the right interface for that purpose.  A lightweight player like Audacious of gmusicplayer maybe would be better.  Heck, I tried for days to get MPD working for me, and while I fall in between an astute user and a techie, I could've get MPD to read music files from a USB hard drive.  

Also, the idea for a separate distro is exactly so folks don't need to mess with customizing much to get good sound.

---

### Post by ridetheteapot on 2012-04-08
no no, i get you. I agree with your perspective.
But I did add that if you(or anyone) where going to build a audio distro... including mpd preconfigured would be a cinch. What I mean by transparent is that the user would never have to even know it was there or running. Nevermind the details, but it would be easy as 3.14

___EDIT__
Actually if you wanted a pointer or two to get mpd working i'd help you out. If you never want to mess with it again, just ignore this.

---

### Post by whell on 2012-04-09
> **ridetheteapot said:**
> no no, i get you. I agree with your perspective.
But I did add that if you(or anyone) where going to build a audio distro... including mpd preconfigured would be a cinch. What I mean by transparent is that the user would never have to even know it was there or running. Nevermind the details, but it would be easy as 3.14

___EDIT__
Actually if you wanted a pointer or two to get mpd working i'd help you out. If you never want to mess with it again, just ignore this.

I actually don't think that mpd, in its current incarnation, can work for me.  I have my music connected on a USB hard drive.  mpd is not currently set up to recognize music libraries on external hard drives from what I've learned.  I'd love to be wrong, so if you or someone has a tip on this, please let me know!

---

### Post by ridetheteapot on 2012-04-10
sure. i do not know who told you such a thing, but mpd absolutly has no trouble with an external drive.
First off just for reference [http://linux.die.net/man/5/mpd.conf](http://linux.die.net/man/5/mpd.conf) . I only add that becase the mpd.conf man page is different from the mpd man page.

The one prerequisite is that your external drive mounts to the same spot each time you use it. Well that and you need read access to the files. (I would imagine that any player would need both)

Pretty much the only option you NEED different would be
"auto_update no"

That is just so mpd doesn't recreate an empty library if your external drive is not attached when you start mpd up.
Even if you don't use that option there should be no problem reading the files though.

options that you need in general (each with the location of your choosing): 
```
music_directory
playlist_directory
db_file
log_file
pid_file
state_file
```
_______________________________
IGNORABLE (you do not have to do this, its just an nice way to consolidate your music if you have multiple drive/folders):
the music directory option can be totally arbitrary. like you can use /usr/share/mpd/music/ as your directory, and then just link to your music folders.
for instance,
```
ln -s /media/external_drive/music /usr/share/mpd/music/
```
would create a (symbolic) link from your xternal music folder to a folder inside /usr/share/mpd/music/ .
If you used this method you'd want to also use
```
follow_outside_symlinks yes
``` so that mpd will respect your awesome decision.
_______________________________________


Things to know:
mpd will create a library upon first run, otherwise you can (always) update the library with a client. GMPC will let you update by folder, i.e you do not have to update the whole library if you just added a new album to your rick&roll (:P) folder.

You will also 'need' an audio_output section in your configuration file - this is very easy to deal with, esp with pulseaudio. But if you don't add this specifically mpd will try to guess, so you could try without this option if you wanted.

There are many options that you can use to expand and enhance your mpd usability. I use mpd to handle my sansa fuze mp3 player simply by using
```
save_absolute_paths_in_playlists no
``` and a little cp script to copy the files in a playlist and the playlist itself to my player. But there are many optionally optional options to play with...

Hey sorry for getting your thread of topic, I kind of feel like a prick.



____EDIT___
I just looked at your join date, and your post count. I thought I had a low ratio! High Five dude, much respect. (not sarcasm if it reads that way)

---

### Post by whell on 2012-04-10
I'm not sure, but my head may have just exploded reading all this.:?:  Just kidding.  It will take me some time to digest this.  I think part of the issue may be that Ubuntu recognizes my usb drive as something like /media/GoFlex Free Agent/ or something similar.  Would MPD have issue with the spaces in the drive name?

---

### Post by ridetheteapot on 2012-04-10
yea, in the mpdconf you would use "" around the whole path anyway - it will deal with the spaces fine. ie "/media/GoFlex Free Agent/"
And its nice the drive mounts to a logical spot each time (i'm gonna guess that its because the partition is labeled "GoFlex Free Agent") - already setup for you to have an easier time dealing with it.

___EDIT
Here would be an example config for you:
```

port                    "6600"
music_directory         "/media/GoFlex Free Agent"
playlist_directory      "/home/user/.mpd/playlists"
db_file                 "/home/user/.mpd/mpd.db"
log_file                "/home/user/.mpd/mpd.log"
pid_file                "/home/user/.mpd/pid"
state_file              "/home/user/.mpd/current"
#bind_to_address        "localhost"
password                "mypassword@read,add,control,admin"
default_permissions     "read"
save_absolute_paths_in_playlists "no"

audio_output {
        type    "pulse"
        name    "MPD@desktop"
}

```
You would want to create the folders .mpd/ and .mpd/playlists before running mpd --
mkdir -p ~/.mpd/playlists . as well as for simplicity mount your usb drive before you run mpd for the first time.

This config is more directed at a per user set up (mpd would be set to start when you login, rather then when the computer starts). pulseaudio is much more suited to this usage. But if you use alsa (or are streaming music) and want mpd to start for all users on the machine - logged in or not, we would change that config to be slightly more appropriate.
Also there is a password "mypassword" so that other lan'ers don't go around changing the song or muting you uninvited. Similarly the bind_to_address is commented out, but you could use that to restrict control to just one machine (or an ssl tunnel if your controlling over the internet but w/e on that.)
And just to link back to the thought on the other post - if you have multiple folders with music there would indeed be some things i would change about the music_directory option.

---

### Post by ridetheteapot on 2012-04-11
I'm gonna just double post on myself....

ignorable - but has to to with the nature of mpd/audiophile desires.
I've been thinking about lossless mpd, over lan in general.
Personally i have been using like 3 methods to stream music - 2 lossy methods, and i'm also using a fifo to stream pcm losslessly over the net.
I am on a gigabyte lan and I can stream pcm without any side effects- but really it still is not optimal.
What i am trying to get at is if we're using flacs (or shn) it's just extra bandwidth --- still works fine over decent bandwidth, but is the difference of flac vs wav.
if your goal is to use flac to save disk space, but do not care about the bandwidth aspect this is not a problem.

totally relevant to the audiophile linux topic, but not really to the side topic of setting up mpd for audiophiles.

---

### Post by whell on 2012-04-14
Here are the key entries in my MPD.CONF file.  Neither Ario or GMPC can seem to find my music files:

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
music_directory		"/media/FreeAgent GoFlex Drive/Music/"
#
# This setting sets the MPD internal playlist directory. The purpose of this
# directory is storage for playlists created by MPD. The server will use 
# playlist files not created by the server but only if they are in the MPD
# format. This setting defaults to playlist saving being disabled.
#
playlist_directory		"/home/whell/.mpd/playlist"
#
# This setting sets the location of the MPD database. This file is used to
# load the database at server start up and store the database while the 
# server is not up. This setting defaults to disabled which will allow
# MPD to accept files over ipc socket (using file:// protocol) or streaming
# files over an accepted protocol.
#
db_file			"/home/whell/.mpd/tag_cache"
# 
# These settings are the locations for the daemon log files for the daemon.
# These logs are great for troubleshooting, depending on your log_level
# settings.
#
# The special value "syslog" makes MPD use the local syslog daemon. This
# setting defaults to logging to syslog, otherwise logging is disabled.
#
log_file			"/home/whell/.mpd/mpd.log"
#
# This setting sets the location of the file which stores the process ID
# for use of mpd --kill and some init scripts. This setting is disabled by
# default and the pid file will not be stored.
#
pid_file			"/home/whell/.mpd/pid"
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
sticker_file                   "/var/lib/mpd/sticker.sql"
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
#group                          "nogroup"
#
# This setting sets the address for the daemon to listen on. Careful attention
# should be paid if this is assigned to anything other then the default, any.
# This setting can deny access to control of the daemon. Choose any if you want
# to have mpd listen on every address
#
# For network
bind_to_address		"192.168.1.126"
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
# (available as vbrfix in the debian archive), at which
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
# This setting enables automatic update of MPD's database when files in 
# music_directory are changed.
#
#auto_update    "yes"
#
# Limit the depth of the directories being watched, 0 means only watch
# the music directory itself.  There is no limit by default.
#
#auto_update_depth "3"
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
An example of an ALSA output:

audio_output {
	type		"alsa"
	name		"My ALSA Device"
	device		"hw:1,0"	# optional
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
# An example of a recorder output:
#
#audio_output {
#       type            "recorder"
#       name            "My recorder"
#       encoder         "vorbis"                # optional, vorbis or lame
#       path            "/var/lib/mpd/recorder/mpd.ogg"
##      quality         "5.0"                   # do not define if bitrate is defined
#       bitrate         "128"                   # do not define if quality is defined
#       format          "44100:16:1"
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
# SIDPlay decoder #############################################################
#
# songlength_database:
#  Location of your songlengths file, as distributed with the HVSC.
#  The sidplay plugin checks this for matching MD5 fingerprints.
#  See [http://www.c64.org/HVSC/DOCUMENTS/Songlengths.faq](http://www.c64.org/HVSC/DOCUMENTS/Songlengths.faq)
#
# default_songlength:
#  This is the default playing time in seconds for songs not in the
#  songlength database, or in case you're not using a database.
#  A value of 0 means play indefinitely.
#
# filter:
#  Turns the SID filter emulation on or off.
#
#decoder {
#       plugin                  "sidplay"
#       songlength_database     "/media/C64Music/DOCUMENTS/Songlengths.txt"
#       default_songlength      "120"
#       filter "true"
#}
#
###############################################################################

```

---

### Post by Yellow Pasque on 2012-04-14
> **whell said:**
> <Huge block of text>
In the future, please use [ code ][ /code ] tags around large blocks of text. My scroll wheel will thank you.

---

### Post by whell on 2012-04-14
> **Temüjin said:**
> In the future, please use [ code ][ /code ] tags around large blocks of text. My scroll wheel will thank you.

Tried editing them back in.  No luck.

---

### Post by Yellow Pasque on 2012-04-14
Don't put spaces inside the brackets :)
(I only did that for illustrative purposes.)

---

### Post by ridetheteapot on 2012-04-17
hey whell just saw your post,

first off I'd make sure that user 'mpd' can read your files (or just comment the user var out and retry, running as someone who definitely can).

Second have you tried to refresh the library using an mpd client? (you can use 'mpc update')

also use the option
```
auto_update no
```
i see i left it out of my last post - but it's important so that if you start mpd without the drive connected you won't wipe out your library database.

might as well ask, but where are you storing your mpd.conf(/home/user/.mpdconf or /etc/mpd.conf) and how are you starting mpd(at boot, after login, manual from commandline, etc)?

---

