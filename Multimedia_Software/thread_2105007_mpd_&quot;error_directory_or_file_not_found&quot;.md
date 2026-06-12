---
title: "mpd &quot;error: directory or file not found&quot;"
date: 2013-01-14
forum: Multimedia Software
---

### Post by bvargo on 2013-01-14
I keep getting this error when I try to add my music directory [ mpc add /library/music ].

when i try mpc add, it just hangs.  

any thoughts?

---

### Post by efflandt on 2013-01-15
What user and group is mpd running as and what are owner, group and permissions of path and files of /library/music?  Maybe mpd does not have permission to access that.

---

### Post by SlugSlug on 2013-01-15
in code tags please post output of

```
cat /etc/mpd.conf
```

And where is your Music stored?

---

### Post by bvargo on 2013-01-15
Thanks for the help...  Here is all of the information I can think to supply.

Permissions for m/etc/mpd.conf
```

/etc# ll mpd*
-rw-r-----   1 mpd      audio    14515 Jan 13 22:30 mpd.conf

```Groups user mpd is in
```

/etc# groups mpd
mpd : audio library

```mpd config file:
```

/etc# cat mpd.conf
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
music_directory        "/library/music/"
#
# This setting sets the MPD internal playlist directory. The purpose of this
# directory is storage for playlists created by MPD. The server will use 
# playlist files not created by the server but only if they are in the MPD
# format. This setting defaults to playlist saving being disabled.
#
playlist_directory        "/var/lib/mpd/playlists"
#
# This setting sets the location of the MPD database. This file is used to
# load the database at server start up and store the database while the 
# server is not up. This setting defaults to disabled which will allow
# MPD to accept files over ipc socket (using file:// protocol) or streaming
# files over an accepted protocol.
#
db_file            "/var/lib/mpd/tag_cache"
# 
# These settings are the locations for the daemon log files for the daemon.
# These logs are great for troubleshooting, depending on your log_level
# settings.
#
# The special value "syslog" makes MPD use the local syslog daemon. This
# setting defaults to logging to syslog, otherwise logging is disabled.
#
log_file            "/var/log/mpd/mpd.log"
#
# This setting sets the location of the file which stores the process ID
# for use of mpd --kill and some init scripts. This setting is disabled by
# default and the pid file will not be stored.
#
pid_file            "/var/run/mpd/pid"
#
# This setting sets the location of the file which contains information about
# most variables to get MPD back into the same general shape it was in before
# it was brought down. This setting is disabled by default and the server 
# state will be reset on server start up.
#
state_file            "/var/lib/mpd/state"
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
user                "mpd"
#
# This setting specifies the group that MPD will run as. If not specified
# primary group of user specified with "user" setting will be used (if set).
# This is useful if MPD needs to be a member of group such as "audio" to
# have permission to use sound card.
#
group                          "library"
#
# This setting sets the address for the daemon to listen on. Careful attention
# should be paid if this is assigned to anything other then the default, any.
# This setting can deny access to control of the daemon. Choose any if you want
# to have mpd listen on every address
#
# For network
bind_to_address        "localhost"
#
# And for Unix Socket
#bind_to_address        "/var/run/mpd/socket"
#
# This setting is the TCP port that is desired for the daemon to get assigned
# to.
#
#port                "6600"
#
# This setting controls the type of information which is logged. Available 
# setting arguments are "default", "secure" or "verbose". The "verbose" setting
# argument is recommended for troubleshooting, though can quickly stretch
# available resources on limited hardware storage.
#
#log_level            "default"
#
# If you have a problem with your MP3s ending abruptly it is recommended that 
# you set this argument to "no" to attempt to fix the problem. If this solves
# the problem, it is highly recommended to fix the MP3 files with vbrfix
# (available as vbrfix in the debian archive), at which
# point gapless MP3 playback can be enabled.
#
#gapless_mp3_playback            "yes"
#
# This setting enables MPD to create playlists in a format usable by other
# music players.
#
#save_absolute_paths_in_playlists    "no"
#
# This setting defines a list of tag types that will be extracted during the 
# audio file discovery process. Optionally, 'comment' can be added to this
# list.
#
#metadata_to_use    "artist,album,title,track,name,genre,date,composer,performer,disc"
#
# This setting enables automatic update of MPD's database when files in 
# music_directory are changed.
#
auto_update    "yes"
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
#follow_outside_symlinks    "yes"
#
# If this setting is set to "yes", MPD will discover audio files by following
# symbolic links inside of the configured music_directory.
#
#follow_inside_symlinks        "yes"
#
###############################################################################


# Zeroconf / Avahi Service Discovery ##########################################
#
# If this setting is set to "yes", service information will be published with
# Zeroconf / Avahi.
#
#zeroconf_enabled        "yes"
#
# The argument to this setting will be the Zeroconf / Avahi unique name for
# this MPD server on the network.
#
#zeroconf_name            "Music Player"
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
    type        "alsa"
    name        "My ALSA Device"
    device        "hw:0,0"    # optional
    format        "44100:16:2"    # optional
    mixer_device    "default"    # optional
    mixer_control    "PCM"        # optional
    mixer_index    "0"        # optional
}
#
# An example of an OSS output:
#
#audio_output {
#    type        "oss"
#    name        "My OSS Device"
#    device        "/dev/dsp"    # optional
#    format        "44100:16:2"    # optional
#    mixer_device    "/dev/mixer"    # optional
#    mixer_control    "PCM"        # optional
#}
#
# An example of a shout output (for streaming to Icecast):
#
#audio_output {
#    type        "shout"
#    encoding    "ogg"            # optional
#    name        "My Shout Stream"
#    host        "localhost"
#    port        "8000"
#    mount        "/mpd.ogg"
#    password    "hackme"
#    quality        "5.0"
#    bitrate        "128"
#    format        "44100:16:1"
#    protocol    "icecast2"        # optional
#    user        "source"        # optional
#    description    "My Stream Description"    # optional
#    genre        "jazz"            # optional
#    public        "no"            # optional
#    timeout        "2"            # optional
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
#    type        "httpd"
#    name        "My HTTP Stream"
#    encoder        "vorbis"        # optional, vorbis or lame
#    port        "8000"
#    quality        "5.0"            # do not define if bitrate is defined
#    bitrate        "128"            # do not define if quality is defined
#    format        "44100:16:1"
#}
#
# An example of a pulseaudio output (streaming to a remote pulseaudio server)
#
#audio_output {
#    type        "pulse"
#    name        "My Pulse Output"
#    server        "remote_server"        # optional
#    sink        "remote_server_sink"    # optional
#}
#
## Example "pipe" output:
#
#audio_output {
#    type        "pipe"
#    name        "my pipe"
#    command        "aplay -f cd 2>/dev/null"
## Or if you're want to use AudioCompress
#    command        "AudioCompress -m | aplay -f cd 2>/dev/null"
## Or to send raw PCM stream through PCM:
#    command        "nc example.org 8765"
#    format        "44100:16:2"
#}
#
## An example of a null output (for no audio output):
#
#audio_output {
#    type        "null"
#    name        "My Null Output"
#}
#
# This setting will change all decoded audio to be converted to the specified
# format before being passed to the audio outputs. By default, this setting is
# disabled.
#
#audio_output_format        "44100:16:2"
#
# If MPD has been compiled with libsamplerate support, this setting specifies 
# the sample rate converter to use.  Possible values can be found in the 
# mpd.conf man page or the libsamplerate documentation. By default, this is
# setting is disabled.
#
#samplerate_converter        "Fastest Sinc Interpolator"
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
#mixer_type            "hardware"
#
# An example for controlling all mixers through software. This will control
# all controls, even if the mixer is not supported by the device and will not
# affect any other sound producing applications.
#
#mixer_type            "software"
#
# This example will not allow MPD to touch the mixer at all and will disable
# all volume controls.
#
#mixer_type            "disabled"
#
###############################################################################


# Normalization automatic volume adjustments ##################################
#
# This setting specifies the type of ReplayGain to use. This setting can have
# the argument "album" or "track". See <http://www.replaygain.org> for more
# details. This setting is disabled by default.
#
#replaygain            "album"
#
# This setting sets the pre-amp used for files that have ReplayGain tags. By
# default this setting is disabled.
#
#replaygain_preamp        "0"
#
# This setting enables on-the-fly normalization volume adjustment. This will
# result in the volume of all playing audio to be adjusted so the output has 
# equal "loudness". This setting is disabled by default.
#
#volume_normalization        "no"
#
###############################################################################


# MPD Internal Buffering ######################################################
#
# This setting adjusts the size of internal decoded audio buffering. Changing
# this may have undesired effects. Don't change this if you don't know what you
# are doing.
#
#audio_buffer_size        "2048"
#
# This setting controls the percentage of the buffer which is filled before 
# beginning to play. Increasing this reduces the chance of audio file skipping, 
# at the cost of increased time prior to audio playback.
#
#buffer_before_play        "10%"
#
###############################################################################


# Resource Limitations ########################################################
#
# These settings are various limitations to prevent MPD from using too many
# resources. Generally, these settings should be minimized to prevent security
# risks, depending on the operating resources.
#
#connection_timeout        "60"
#max_connections        "10"
#max_playlist_length        "16384"
#max_command_list_size        "2048"
#max_output_buffer_size        "8192"
#
###############################################################################


# Character Encoding ##########################################################
#
# If file or directory names do not display correctly for your locale then you 
# may need to modify this setting. After modification of this setting mpd 
# --create-db must be run to change the database.
#
filesystem_charset        "UTF-8"
#
# This setting controls the encoding that ID3v1 tags should be converted from.
#
id3v1_encoding            "UTF-8"
#
###############################################################################
# SIDPlay decoder #############################################################
#
# songlength_database:
#  Location of your songlengths file, as distributed with the HVSC.
#  The sidplay plugin checks this for matching MD5 fingerprints.
#  See http://www.c64.org/HVSC/DOCUMENTS/Songlengths.faq
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


```mpd is running as mpd:
```
/etc# ps aux |grep mpd
mpd       1233  0.0  0.0 372608  6268 ?        Ssl  Jan14   0:00 /usr/bin/mpd /etc/mpd.conf

```/library/

```

/library# ll
total 52
drwxrwxr-x 10 bvargo library  4096 Jan 13 19:42 ./
drwxr-xr-x 24 root   root     4096 Jan 14 06:52 ../
drwxr-xr-x  6 bvargo library  4096 Jan  6 11:05 books/
drwx------  2 bvargo library 16384 Jan 13 15:26 lost+found/
drwxrwxr-x 21 mpd    library  4096 Jan  6 11:02 music/
drwxr-xr-x  3 bvargo library  4096 Jan  5 18:14 pictures/
drwxr-xr-x  8 bvargo library  4096 Jan  8 08:44 video/

```/library/music/
(no laughing, I'm rebuilding my music archive virtually from scratch)
```

root@gigabyte:/library/music# ll
total 22868
drwxrwxr-x 21 mpd    library    4096 Jan  6 11:02 ./
drwxrwxr-x 10 bvargo library    4096 Jan 13 19:42 ../
drwxrwxr-x  2 mpd    library    4096 Jan  5 18:14 Adele - 21/
drwxrwxr-x 45 mpd    library    4096 Jan  5 18:18 Bob Dylan/
drwxrwxr-x  2 mpd    library    4096 Jan  6 11:01 Bob Dylan -- Live At Budokan/
drwxrwxr-x  2 mpd    library    4096 Jan  6 10:55 Bob Dylan -- Tempest/
drwxrwxr-x 35 mpd    library    4096 Jan  5 18:19 Bob Marley/
drwxrwxr-x  2 mpd    library    4096 Jan  6 11:02 Bruce Springsteen -- Live In New York City/
-rwxrwxr-x  1 mpd    library 5031120 Jan  6 11:00 Cornershop - Brimful of Asha.mp3*
drwxrwxr-x  2 mpd    library    4096 Jan  6 10:55 Eric Bibb -- Painting Signs/
drwxrwxr-x  3 mpd    library    4096 Jan  5 18:19 Grateful Dead/
drwxrwxr-x  2 mpd    library    4096 Jan  6 11:02 Grateful Dead -- Postcards of the Hanging/
drwxrwxr-x  2 mpd    library    4096 Jan  6 11:02 Jimmy Thackery and Tab Benoit -- Whiskey Store Live/
drwxrwxr-x  8 mpd    library    4096 Jan  5 18:20 Johnny Cash/
drwxrwxr-x  2 mpd    library    4096 Jan  6 10:56 Kings of Leon -- Only by the Night/
drwxrwxr-x  4 mpd    library    4096 Jan  5 18:14 mpd/
drwxrwxr-x  2 mpd    library    4096 Jan  6 11:01 Neil Young & Crazy Horse -- Americana/
drwxrwxr-x  3 mpd    library    4096 Jan  5 18:20 Ryan Bingham/
drwxrwxr-x  3 mpd    library    4096 Jan  5 18:14 Steve Earle/
drwxrwxr-x  2 mpd    library    4096 Jan  6 10:56 Untitled Folder/
drwxrwxr-x  3 mpd    library    4096 Jan  5 18:14 Various Artists/

```I did a chown -R /library/music mpd library so everything inside the above directory tree looks like:

```

root@gigabyte:/library/music/Bob Dylan -- Tempest# ll
total 161320
drwxrwxr-x  2 mpd library     4096 Jan  6 10:55 ./
drwxrwxr-x 21 mpd library     4096 Jan  6 11:02 ../
-rwxrwxrwx  1 mpd library 13826085 Jan  6 10:55 01 Duquesne Whistle.mp3*
-rwxrwxrwx  1 mpd library  8395368 Jan  6 10:55 02 Soon After Midnight.mp3*
-rwxrwxrwx  1 mpd library 18001119 Jan  6 10:55 03 Narrow Way.mp3*
-rwxrwxrwx  1 mpd library  9119210 Jan  6 10:55 04 Long and Wasted Years.mp3*
-rwxrwxrwx  1 mpd library 12461921 Jan  6 10:55 05 Pay In Blood.mp3*
-rwxrwxrwx  1 mpd library 17484641 Jan  6 10:55 06 Scarlet Town.mp3*
-rwxrwxrwx  1 mpd library 12641446 Jan  6 10:55 07 Early Roman Kings.mp3*
-rwxrwxrwx  1 mpd library 21880478 Jan  6 10:55 08 Tin Angel.mp3*
-rwxrwxrwx  1 mpd library 33449436 Jan  6 10:55 09 Tempest.mp3*
-rwxrwxrwx  1 mpd library 17904162 Jan  6 10:55 10 Roll On John.mp3*

```Here are the errors:

```

:/library/music/Bob Dylan -- Tempest# mpc add *
error: directory or file not found
:/library/music/Bob Dylan -- Tempest# mpc add /library/music
error: directory or file not found
:/library/music/Bob Dylan -- Tempest# mpc status
volume: n/a   repeat: off   random: off   single: off   consume: off

```For the record this is 12.04.1 LTS server on a relatively clean install (started Sunday).   mpd was installed out of the repositories and here is the version info:

```
:/library/music/Bob Dylan -- Tempest# mpd -V
mpd (MPD: Music Player Daemon) 0.16.5 

Copyright (C) 2003-2007 Warren Dukes <warren.dukes@gmail.com>
Copyright (C) 2008-2010 Max Kellermann <max@duempel.org>
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
[mikmod] amf dsm far gdm imf it med mod mtm s3m stm stx ult uni xm
[ffmpeg] 16sv 3g2 3gp 4xm 8svx aa3 aac ac3 afc aif aifc aiff al alaw amr anim apc ape asf atrac au aud avi avm2 avs bap bfi c93 cak cin cmv cpk daud dct divx dts dv dvd dxa eac3 film flac flc fli fll flx flv g726 gsm gxf iss m1v m2v m2t m2ts m4a m4b m4v mad mj2 mjpeg mjpg mka mkv mlp mm mmf mov mp+ mp1 mp2 mp3 mp4 mpc mpeg mpg mpga mpp mpu mve mvi mxf nc nsv nut nuv oga ogm ogv ogx oma ogg omg psp pva qcp qt r3d ra ram rl2 rm rmvb roq rpl rvc shn smk snd sol son spx str swf tgi tgq tgv thp ts tsp tta xa xvid uv uv2 vb vid vob voc vp6 vmd wav wma wmv wsaud wsvga wv wve

Supported outputs:

shout null fifo pipe alsa ao oss pulse jack httpd recorder 

Supported encoders:

null vorbis lame wave flac 

Supported protocols:

file:// http:// mms:// mmsh:// mmst:// mmsu:// gopher:// rtp:// rtsp:// rtmp:// rtmpt:// rtmps:// 

``````

:/var/lib/mpd# ll
total 28
drwxr-xr-x  4 mpd  audio 4096 Jan 13 21:33 ./
drwxr-xr-x 46 root root  4096 Jan 14 08:37 ../
-rw-r--r--  1 root root     0 Jan 13 21:34 db_file
-rw-r--r--  1 root root     0 Jan 13 21:34 log_file
drwxr-xr-x  2 mpd  audio 4096 Mar 16  2012 music/
-rw-r--r--  1 root root     0 Jan 13 21:34 pid_file
drwxr-xr-x  2 mpd  audio 4096 Mar 16  2012 playlists/
-rw-r--r--  1 mpd  audio  183 Jan 14 21:37 state
-rw-r--r--  1 root root     0 Jan 13 21:34 state_file
-rw-r--r--  1 mpd  audio 3072 Jan 13 21:34 sticker.sql
-rw-r--r--  1 mpd  audio  344 Jan 13 21:34 tag_cache

```fixed ownership of these files:
```
:/var/lib# chown -R mpd:audio mpd

```Still getting error:

```

:/var/lib/mpd# ll
total 28
drwxr-xr-x  4 mpd  audio 4096 Jan 13 21:33 ./
drwxr-xr-x 46 root root  4096 Jan 14 08:37 ../
-rw-r--r--  1 mpd  audio    0 Jan 13 21:34 db_file
-rw-r--r--  1 mpd  audio    0 Jan 13 21:34 log_file
drwxr-xr-x  2 mpd  audio 4096 Mar 16  2012 music/
-rw-r--r--  1 mpd  audio    0 Jan 13 21:34 pid_file
drwxr-xr-x  2 mpd  audio 4096 Mar 16  2012 playlists/
-rw-r--r--  1 mpd  audio  183 Jan 14 21:37 state
-rw-r--r--  1 mpd  audio    0 Jan 13 21:34 state_file
-rw-r--r--  1 mpd  audio 3072 Jan 13 21:34 sticker.sql
-rw-r--r--  1 mpd  audio  344 Jan 13 21:34 tag_cache
:/var/lib/mpd# mpc add /library/music
error: directory or file not found

```As I said, 12.04.1 LTS Server on the following:  GIGABYTE  GA-Z77X-UD3H, Intel  Core i5-3570K, Patriot  G2 Series 8GB (2 x  4GB) PC3-12800, DDR3 1600MHz.
                                
I really have no idea where to go from here...

---

### Post by SlugSlug on 2013-01-15
```
ll -l /
```please

(Want to check library folder in on /   and mpd has perms)

I don't use the mpc command I just edit the config.

anything in 
/var/log/mpd/mpd.log/var/log/mpd/mpd.log

---

### Post by bvargo on 2013-01-15
```

/etc/default# ll -l /
total 101
drwxr-xr-x  25 root   root     4096 Jan 15 09:17 ./
drwxr-xr-x  25 root   root     4096 Jan 15 09:17 ../
drwxr-xr-x   2 root   root     4096 Jan 13 10:18 bin/
drwxr-xr-x   5 root   root     1024 Jan 14 06:52 boot/
drwxr-xr-x  16 root   root     4380 Jan 14 21:40 dev/
drwxr-xr-x 108 root   root     4096 Jan 15 09:19 etc/
drwxrwxrwx   4 root   root     4096 Jan 15 09:19 export/
drwxrwxrwx   3 root   root     4096 Jan 13 10:07 home/
lrwxrwxrwx   1 root   root       33 Jan 14 06:52 initrd.img -> /boot/initrd.img-3.2.0-35-generic
lrwxrwxrwx   1 root   root       33 Jan 13 09:50 initrd.img.old -> /boot/initrd.img-3.2.0-29-generic
drwxr-xr-x  21 root   root     4096 Jan 15 09:16 lib/
drwxr-xr-x   2 root   root     4096 Jan 13 10:16 lib64/
drwxrwxrwx  10 bvargo library  4096 Jan 13 19:42 library/
drwx------   2 root   root    16384 Jan 13 09:44 lost+found/
drwxr-xr-x   3 root   root     4096 Jan 13 09:49 media/
drwxr-xr-x   4 root   root     4096 Jan 13 21:36 mnt/
drwxr-xr-x   2 root   root     4096 Jan 13 09:45 opt/
dr-xr-xr-x 140 root   root        0 Jan 14 21:40 proc/
drwx------   4 root   root     4096 Jan 13 22:17 root/
drwxr-xr-x  25 root   root      920 Jan 15 09:16 run/
drwxr-xr-x   2 root   root    12288 Jan 15 09:16 sbin/
drwxr-xr-x   2 root   root     4096 Mar  5  2012 selinux/
drwxr-xr-x   2 root   root     4096 Jan 13 09:45 srv/
drwxr-xr-x  13 root   root        0 Jan 14 21:40 sys/
drwxrwxrwt   4 root   root     4096 Jan 15 09:39 tmp/
drwxr-xr-x  10 root   root     4096 Jan 13 09:45 usr/
drwxr-xr-x  13 root   root     4096 Jan 14 21:37 var/
lrwxrwxrwx   1 root   root       29 Jan 14 06:52 vmlinuz -> boot/vmlinuz-3.2.0-35-generic
lrwxrwxrwx   1 root   root       29 Jan 13 09:50 vmlinuz.old -> boot/vmlinuz-3.2.0-29-generic

```/library has the group set as library to which mpd belongs and its 777.

I'm not using mpc to configure mpd, I am using /etc/mpd.conf, but using it to add files to the playlist...which isn't working.

log file:
```

Jan 13 11:10 : avahi: Service 'Music Player' successfully established.
Jan 13 11:11 : avahi: Service 'Music Player' successfully established.
Jan 13 15:24 : avahi: Service 'Music Player' successfully established.
Jan 13 15:38 : avahi: Service 'Music Player' successfully established.
Jan 13 16:18 : avahi: Service 'Music Player' successfully established.
Jan 13 16:51 : avahi: Service 'Music Player' successfully established.
Jan 13 20:25 : mixer: Failed to read mixer for 'My ALSA Device': no such mixer control: PCM
Jan 13 20:42 : avahi: Service 'Music Player' successfully established.
Jan 13 20:42 : avahi: Service 'Music Player' successfully established.
Jan 13 20:44 : mixer: Failed to read mixer for 'My ALSA Device': failed to attach to default: No such file or directory
Jan 13 20:52 : avahi: Service 'Music Player' successfully established.
Jan 13 20:59 : avahi: Service 'Music Player' successfully established.
Jan 13 20:59 : mixer: Failed to read mixer for 'My ALSA Device': failed to attach to default: No such file or directory
Jan 13 21:10 : avahi: Service 'Music Player' successfully established.
Jan 13 21:10 : mixer: Failed to read mixer for 'My ALSA Device': failed to attach to default: No such file or directory
Jan 13 21:19 : avahi: Service 'Music Player' successfully established.
Jan 13 21:31 : avahi: Service 'Music Player' successfully established.
Jan 13 21:31 : mixer: Failed to read mixer for 'My ALSA Device': failed to attach to default: No such file or directory
Jan 14 09:18 : avahi: Service 'Music Player' successfully established.
Jan 14 09:18 : mixer: Failed to read mixer for 'My ALSA Device': failed to attach to default: No such file or directory
Jan 14 09:48 : avahi: Service 'Music Player' successfully established.
Jan 14 09:56 : avahi: Service 'Music Player' successfully established.
Jan 14 19:44 : avahi: Service 'Music Player' successfully established.
Jan 14 20:39 : mixer: Failed to read mixer for 'My ALSA Device': failed to attach to default: No such file or directory
Jan 14 21:00 : avahi: Service 'Music Player' successfully established.
Jan 14 21:14 : avahi: Service 'Music Player' successfully established.
Jan 14 16:36 : avahi: Service 'Music Player' successfully established.
Jan 14 21:40 : avahi: Service 'Music Player' successfully established.
Jan 14 21:40 : mixer: Failed to read mixer for 'My ALSA Device': failed to attach to default: No such file or directory
Jan 15 08:32 : avahi: Service 'Music Player' successfully established.

```

---

### Post by SlugSlug on 2013-01-15
I've only used it with gmpc

Have you tried 

```
mpc update
```

then check logs 

or maybe```
 mpc play
```

found a post saying run mpc update before mpc add

I'd ```
sudo /etc/init.d/mpd restart
``` first

---

### Post by bvargo on 2013-01-15
Ok...  so:

```

:~$ mpc update
Updating DB (#1) ...
volume: n/a   repeat: off   random: off   single: off   consume: off

```

```
:~$ mpc status
volume: n/a   repeat: off   random: off   single: off   consume: off

```

```
:/var/lib/mpd$ ll
total 324
drwxr-xr-x  4 mpd  audio   4096 Jan 13 21:33 ./
drwxr-xr-x 47 root root    4096 Jan 15 09:16 ../
-rw-r--r--  1 mpd  audio      0 Jan 13 21:34 db_file
-rw-r--r--  1 mpd  audio      0 Jan 13 21:34 log_file
drwxr-xr-x  2 mpd  audio   4096 Mar 16  2012 music/
-rw-r--r--  1 mpd  audio      0 Jan 13 21:34 pid_file
drwxr-xr-x  2 mpd  audio   4096 Mar 16  2012 playlists/
-rw-r--r--  1 mpd  audio    183 Jan 15 11:52 state
-rw-r--r--  1 mpd  audio      0 Jan 13 21:34 state_file
-rw-r--r--  1 mpd  audio   3072 Jan 13 21:34 sticker.sql
-rw-r--r--  1 mpd  audio 306180 Jan 15 11:51 tag_cache

```

```

:/var/log/mpd$ cat mpd.log
Jan 13 11:10 : state_file: failed to open /var/lib/mpd/state: No such file or di                                                                                                                                                                                               rectory
Jan 13 11:10 : avahi: Service 'Music Player' successfully established.
Jan 13 11:11 : avahi: Service 'Music Player' successfully established.
Jan 13 15:24 : avahi: Service 'Music Player' successfully established.
Jan 13 15:38 : avahi: Service 'Music Player' successfully established.
Jan 13 16:18 : avahi: Service 'Music Player' successfully established.
Jan 13 16:51 : avahi: Service 'Music Player' successfully established.
Jan 13 20:25 : mixer: Failed to read mixer for 'My ALSA Device': no such mixer c                                                                                                                                                                                               ontrol: PCM
Jan 13 20:42 : avahi: Service 'Music Player' successfully established.
Jan 13 20:42 : avahi: Service 'Music Player' successfully established.
Jan 13 20:44 : mixer: Failed to read mixer for 'My ALSA Device': failed to attac                                                                                                                                                                                               h to default: No such file or directory
Jan 13 20:52 : avahi: Service 'Music Player' successfully established.
Jan 13 20:59 : avahi: Service 'Music Player' successfully established.
Jan 13 20:59 : mixer: Failed to read mixer for 'My ALSA Device': failed to attac                                                                                                                                                                                               h to default: No such file or directory
Jan 13 21:10 : avahi: Service 'Music Player' successfully established.
Jan 13 21:10 : mixer: Failed to read mixer for 'My ALSA Device': failed to attac                                                                                                                                                                                               h to default: No such file or directory
Jan 13 21:19 : avahi: Service 'Music Player' successfully established.
Jan 13 21:31 : avahi: Service 'Music Player' successfully established.
Jan 13 21:31 : mixer: Failed to read mixer for 'My ALSA Device': failed to attac                                                                                                                                                                                               h to default: No such file or directory
Jan 14 09:18 : avahi: Service 'Music Player' successfully established.
Jan 14 09:18 : mixer: Failed to read mixer for 'My ALSA Device': failed to attac                                                                                                                                                                                               h to default: No such file or directory
Jan 14 09:48 : avahi: Service 'Music Player' successfully established.
Jan 14 09:56 : avahi: Service 'Music Player' successfully established.
Jan 14 19:44 : avahi: Service 'Music Player' successfully established.
Jan 14 20:39 : mixer: Failed to read mixer for 'My ALSA Device': failed to attac                                                                                                                                                                                               h to default: No such file or directory
Jan 14 21:00 : avahi: Service 'Music Player' successfully established.
Jan 14 21:14 : avahi: Service 'Music Player' successfully established.
Jan 14 16:36 : avahi: Service 'Music Player' successfully established.
Jan 14 21:40 : avahi: Service 'Music Player' successfully established.
Jan 14 21:40 : mixer: Failed to read mixer for 'My ALSA Device': failed to attac                                                                                                                                                                                               h to default: No such file or directory
Jan 15 08:32 : avahi: Service 'Music Player' successfully established.
Jan 15 11:51 : update: added Adele - 21/16 Adele - Don't You Remember (Live Acou                                                                                                                                                                                               stic).mp3
Jan 15 11:51 : update: added Adele - 21/01 Adele - Rolling In The Deep.mp3
Jan 15 11:51 : update: added Adele - 21/03 Adele - Turning Tabels.mp3
Jan 15 11:51 : mixer: Failed to read mixer for 'My ALSA Device': failed to attac                                                                                                                                                                                               h to default: No such file or directory
Jan 15 11:51 : update: added Adele - 21/10 Adele - Lovesong.mp3
Jan 15 11:51 : update: added Adele - 21/12 Adele - If It Hadn't Been For Love.mp                                                                                                                                                                                               3
Jan 15 11:51 : update: added Adele - 21/05 Adele - Set Fire To The Rain.mp3
Jan 15 11:51 : update: added Adele - 21/08 Adele - I'll Be Waiting.mp3
Jan 15 11:51 : update: added Adele - 21/02 Adele - Rumor Has It.mp3
Jan 15 11:51 : update: added Adele - 21/07 Adele - Take It All.mp3
Jan 15 11:51 : update: added Adele - 21/04 Adele - Don't You Remember.mp3
Jan 15 11:51 : update: added Adele - 21/09 Adele - One And Only.mp3
Jan 15 11:51 : update: added Adele - 21/06 Adele - He Won't Go.mp3
Jan 15 11:51 : update: added Adele - 21/15 Adele - Turning Tables (Live Acoustic                                                                                                                                                                                               ).mp3
Jan 15 11:51 : update: added Adele - 21/13 Adele - Hiding My Heart.mp3
Jan 15 11:51 : update: added Adele - 21/14 Adele - I Found A Boy.mp3
Jan 15 11:51 : update: added Adele - 21/17 Adele - Someone Like You (Live Acoust                                                                                                                                                                                               ic).mp3
Jan 15 11:51 : update: added Adele - 21/11 Adele - Someone Like You.mp3
Jan 15 11:51 : update: added Bob Dylan/Bob Dylan -- Standing in the Doorway.mp3
Jan 15 11:51 : update: added Bob Dylan/Bob Dylan -- Hard rain/07 You Are A Big G                                                                                                                                                                                               irl Now.mp3
Jan 15 11:51 : update: added Bob Dylan/Bob Dylan -- Hard rain/09 Idiot Wind.mp3
Jan 15 11:51 : update: added Bob Dylan/Bob Dylan -- Hard rain/01 Maggie's Farm.m                                                                                                                                                                                               p3
Jan 15 11:51 : update: added Bob Dylan/Bob Dylan -- Hard rain/02 One Too Many Mo                                                                                                                                                                                               rnings.mp3
Jan 15 11:51 : update: added Bob Dylan/Bob Dylan -- Hard rain/06 Shelter From Th                                                                                                                                                                                               e Storm.mp3
Jan 15 11:51 : update: added Bob Dylan/Bob Dylan -- Hard rain/04 Oh, Sister.mp3
Jan 15 11:51 : update: added Bob Dylan/Bob Dylan -- Hard rain/03 Stuck Inside Of                                                                                                                                                                                                Mobile With The Memphis Blues Again.mp3
Jan 15 11:51 : update: added Bob Dylan/Bob Dylan -- Hard rain/08 I Threw It All                                                                                                                                                                                                Away.mp3
Jan 15 11:51 : update: added Bob Dylan/Bob Dylan -- Hard rain/05 Lay Lady Lay.mp                                                                                                                                                                                               3
Jan 15 11:51 : update: added Bob Dylan/Oh Mercy/06 Most Of The Time.mp3
Jan 15 11:51 : update: added Bob Dylan/Oh Mercy/10 Shooting Star.mp3
Jan 15 11:51 : update: added Bob Dylan/Oh Mercy/08 Disease Of Conceit.mp3
Jan 15 11:51 : update: added Bob Dylan/Oh Mercy/01 Political World.mp3
Jan 15 11:51 : update: added Bob Dylan/Oh Mercy/02 Where Teardrops Fall.mp3
Jan 15 11:51 : update: added Bob Dylan/Oh Mercy/04 Ring Them Bells.mp3
Jan 15 11:51 : update: added Bob Dylan/Oh Mercy/07 What Good Am I.mp3
Jan 15 11:51 : update: added Bob Dylan/Oh Mercy/03 Everything Is Broken.mp3
Jan 15 11:51 : update: added Bob Dylan/Oh Mercy/09 What Was It You Wanted.mp3
Jan 15 11:51 : update: added Bob Dylan/Oh Mercy/05 Man In The Long Black Coat.mp                                                                                                                                                                                               3
Jan 15 11:51 : update: added Bob Dylan/Knocked Out Loaded/08 Under Your Spell.mp                                                                                                                                                                                               3
Jan 15 11:51 : update: added Bob Dylan/Knocked Out Loaded/03 Driftin' Too Far Fr                                                                                                                                                                                               om Shore.mp3
Jan 15 11:51 : update: added Bob Dylan/Knocked Out Loaded/05 Maybe Someday.mp3
Jan 15 11:51 : update: added Bob Dylan/Knocked Out Loaded/02 They Killed Him.mp3
Jan 15 11:51 : update: added Bob Dylan/Knocked Out Loaded/07 Got My Mind Made Up                                                                                                                                                                                               .mp3
Jan 15 11:51 : update: added Bob Dylan/Knocked Out Loaded/04 Precious Memories.m                                                                                                                                                                                               p3
Jan 15 11:51 : update: added Bob Dylan/Knocked Out Loaded/01 You Wanna Ramble.mp                                                                                                                                                                                               3
Jan 15 11:51 : update: added Bob Dylan/Knocked Out Loaded/06 Brownsville Girl.mp                                                                                                                                                                                               3
Jan 15 11:51 : update: added Bob Dylan/Blonde On Blonde/06 Stuck Inside Of Mobil                                                                                                                                                                                               e With The M.mp3
Jan 15 11:51 : update: added Bob Dylan/Blonde On Blonde/14 Sad Eyed Lady Of The                                                                                                                                                                                                Lowlands.mp3
Jan 15 11:51 : update: added Bob Dylan/Blonde On Blonde/you.mp3
Jan 15 11:51 : update: added Bob Dylan/Blonde On Blonde/11 Absolutely Sweet Mari                                                                                                                                                                                               e.mp3
Jan 15 11:51 : update: added Bob Dylan/Blonde On Blonde/12 4th Time Around.mp3
Jan 15 11:51 : update: added Bob Dylan/Blonde On Blonde/13 Obviously 5 Believers                                                                                                                                                                                               .mp3
Jan 15 11:51 : update: added Bob Dylan/Blonde On Blonde/08 Just Like A Woman.mp3
Jan 15 11:51 : update: added Bob Dylan/Blonde On Blonde/10 Temporary Like Achill                                                                                                                                                                                               es.mp3
Jan 15 11:51 : update: added Bob Dylan/Blonde On Blonde/05 I Want You.mp3
Jan 15 11:51 : update: added Bob Dylan/Blonde On Blonde/02 Pledging My Time.mp3
Jan 15 11:51 : update: added Bob Dylan/Blonde On Blonde/03 Visions Of Johanna.mp                                                                                                                                                                                               3
Jan 15 11:51 : update: added Bob Dylan/Blonde On Blonde/01 Rainy Day Women #12 &                                                                                                                                                                                                35.mp3
Jan 15 11:51 : update: added Bob Dylan/Blonde On Blonde/04 One Of Us Must Know (                                                                                                                                                                                               Sooner Or La.mp3
Jan 15 11:51 : update: added Bob Dylan/Blonde On Blonde/07 Leopard-Skin Pill-Box                                                                                                                                                                                                Hat.mp3
Jan 15 11:51 : update: added Bob Dylan/Blonde On Blonde/09 Most Likely You Go Yo                                                                                                                                                                                               ur Way And I.mp3
Jan 15 11:51 : update: added Bob Dylan/Bob Dylan -- Baby, Let Me Follow You Down                                                                                                                                                                                               .mp3
Jan 15 11:51 : update: added Bob Dylan/Bob Dylan/05 Fixin' To Die Blues.mp3
Jan 15 11:51 : update: added Bob Dylan/Bob Dylan/01 She's No Good.mp3
Jan 15 11:51 : update: added Bob Dylan/Bob Dylan/13 See That My Grave Is Kept Cl                                                                                                                                                                                               ean.mp3
Jan 15 11:51 : update: added Bob Dylan/Bob Dylan/10 House Of The Risin' Sun.mp3
Jan 15 11:51 : update: added Bob Dylan/Bob Dylan/09 Baby, Let Me Follow You Down                                                                                                                                                                                               .mp3
Jan 15 11:51 : update: added Bob Dylan/Bob Dylan/03 In My Time Of Dyin'.mp3
Jan 15 11:51 : update: added Bob Dylan/Bob Dylan/12 Song To Woody.mp3
Jan 15 11:51 : update: added Bob Dylan/Bob Dylan/11 Freight Train Blues.mp3
Jan 15 11:51 : update: added Bob Dylan/Bob Dylan/08 Gospel Plow.mp3
Jan 15 11:51 : update: added Bob Dylan/Bob Dylan/04 Man Of Constant Sorrow.mp3
Jan 15 11:51 : update: added Bob Dylan/Bob Dylan/02 Talkin' New York.mp3
Jan 15 11:51 : update: added Bob Dylan/Bob Dylan/06 Pretty Peggy-O.mp3
Jan 15 11:51 : update: added Bob Dylan/Bob Dylan/07 Highway 51 Blues.mp3
.
.
.
.

```

So from mpd.conf

```

# This setting sets the location of the MPD database. This file is used to
# load the database at server start up and store the database while the
# server is not up. This setting defaults to disabled which will allow
# MPD to accept files over ipc socket (using file:// protocol) or streaming
# files over an accepted protocol.
#
db_file                 "/var/lib/mpd/tag_cache"
#

```

So looking at the tag_cache:

```

:/var/lib/mpd$ ll
total 324
drwxr-xr-x  4 mpd  audio   4096 Jan 13 21:33 ./
drwxr-xr-x 47 root root    4096 Jan 15 09:16 ../
-rw-r--r--  1 mpd  audio      0 Jan 13 21:34 db_file
-rw-r--r--  1 mpd  audio      0 Jan 13 21:34 log_file
drwxr-xr-x  2 mpd  audio   4096 Mar 16  2012 music/
-rw-r--r--  1 mpd  audio      0 Jan 13 21:34 pid_file
drwxr-xr-x  2 mpd  audio   4096 Mar 16  2012 playlists/
-rw-r--r--  1 mpd  audio    183 Jan 15 11:52 state
-rw-r--r--  1 mpd  audio      0 Jan 13 21:34 state_file
-rw-r--r--  1 mpd  audio   3072 Jan 13 21:34 sticker.sql
-rw-r--r--  1 mpd  audio 306180 Jan 15 11:51 tag_cache

:/var/lib/mpd$ cat tag_cache |more
info_begin
format: 1
mpd_version: 0.16.5
fs_charset: UTF-8
tag: Artist
tag: ArtistSort
tag: Album
tag: AlbumArtist
tag: AlbumArtistSort
tag: Title
tag: Track
tag: Name
tag: Genre
tag: Date
tag: Composer
tag: Performer
tag: Disc
tag: MUSICBRAINZ_ARTISTID
tag: MUSICBRAINZ_ALBUMID
tag: MUSICBRAINZ_ALBUMARTISTID
tag: MUSICBRAINZ_TRACKID
info_end
directory: Adele - 21
mtime: 1357427655
begin: Adele - 21
song_begin: 01 Adele - Rolling In The Deep.mp3
Time: 229
Artist: Adele
AlbumArtist: Adele
Title: Rolling In The Deep
Album: 21
Track: 01
Date: 2011
Genre: Pop
mtime: 1357427654
song_end
song_begin: 02 Adele - Rumor Has It.mp3
Time: 223
Artist: Adele
AlbumArtist: Adele
Title: Rumor Has It
Album: 21
Track: 02
Date: 2011
Genre: Pop
mtime: 1357427655
song_end
song_begin: 03 Adele - Turning Tabels.mp3
Time: 250
Artist: Adele
AlbumArtist: Adele
Title: Turning Tabels
Album: 21
Track: 03
Date: 2011
Genre: Pop
mtime: 1357427655
song_end
song_begin: 04 Adele - Don't You Remember.mp3
Time: 243
Artist: Adele
AlbumArtist: Adele
Title: Don't You Remember
Album: 21
Track: 04
Date: 2011
Genre: Pop
mtime: 1357427654
song_end
song_begin: 05 Adele - Set Fire To The Rain.mp3
Time: 242
Artist: Adele
AlbumArtist: Adele
Title: Set Fire To The Rain
Album: 21
Track: 05
Date: 2011
Genre: Pop
mtime: 1357427654
song_end
song_begin: 06 Adele - He Won't Go.mp3
Time: 278
Artist: Adele
AlbumArtist: Adele
Title: He Won't Go
Album: 21
Track: 06
Date: 2011
Genre: Pop
mtime: 1357427646
song_end
song_begin: 07 Adele - Take It All.mp3
Time: 228
Artist: Adele
AlbumArtist: Adele
Title: Take It All
Album: 21
Track: 07
Date: 2011
Genre: Pop
mtime: 1357427654
song_end
song_begin: 08 Adele - I'll Be Waiting.mp3
Time: 242
Artist: Adele
AlbumArtist: Adele
Title: I'll Be Waiting
Album: 21
Track: 08
Date: 2011
Genre: Pop
mtime: 1357427654
song_end
song_begin: 09 Adele - One And Only.mp3
Time: 348
Artist: Adele
AlbumArtist: Adele
Title: One And Only
Album: 21
Track: 09
Date: 2011
Genre: Pop
mtime: 1357427654
song_end
.
.
.
.

```
Status:
```
:/var/lib/mpd$ mpc status
volume: n/a   repeat: off   random: off   single: off   consume: off

```

Restart:
```

:/var/lib/mpd$ sudo service mpd restart
[sudo] password for bvargo:
 * Stopping Music Player Daemon mpd                                      [ OK ]
 * Starting Music Player Daemon mpd                                      [ OK ]

```

and...

```
:/var/lib/mpd$ mpc add /library/music
error: directory or file not found

```

same error.

```
e:/var/lib/mpd$ mpc play
volume: n/a   repeat: off   random: off   single: off   consume: off

```

with nothing playing.

---

### Post by SlugSlug on 2013-01-15
It looks like the update has added songs to your db (in log)

I'd run mpc update and leave it a while (dnt restart the service as we did just then)

then maybe get a client to connect to it? Or do you plan on just using mpc?

---

### Post by bvargo on 2013-01-15
Well one part of it is solved, sort of, but now I have another problem...see below:

```

:/library/music$ mpc add *

:/library/music$ mpc playlist
Cornershop - Brimful Of Asha (Fatboy Slim Full Remix)
Cornershop - Brimful of Asha
Adele - Rolling In The Deep
Adele - Rumor Has It
Adele - Turning Tabels
Adele - Don't You Remember
Adele - Set Fire To The Rain
Adele - He Won't Go
Adele - Take It All
Adele - I'll Be Waiting
Adele - One And Only
Adele - Lovesong
Adele - Someone Like You
Adele - If It Hadn't Been For Love
Adele - Hiding My Heart
Adele - I Found A Boy
Adele - Turning Tables (Live Acoustic)
Adele - Don't You Remember (Live Acoustic)
Adele - Someone Like You (Live Acoustic)
Adele - Rolling In The Deep
Adele - Rumor Has It
Adele - Turning Tabels
Adele - Don't You Remember
Adele - Set Fire To The Rain
Adele - He Won't Go
Adele - Take It All
Adele - I'll Be Waiting
Adele - One And Only
Adele - Lovesong
Adele - Someone Like You
Adele - If It Hadn't Been For Love
Adele - Hiding My Heart
.
.
.
.
.

```

but when I try what should be the same thing, I get the error:

```
:/library/music$ mpc add /library/music/*
error: directory or file not found

```

At any rate, I believe that part is working, now I have to figure out why my outputs aren't working:

```

:/library/music$ mpc toggle
Cornershop - Brimful Of Asha (Fatboy Slim Full Remix)
[paused]  #1/1336   0:00/7:36 (0%)
volume: n/a   repeat: off   random: off   single: off   consume: off
ERROR: problems opening audio device

```

---

### Post by SlugSlug on 2013-01-15
I'd stick to adding the Music Folder in the config and just doing the mpc update.

As for sound are you using alsa or pulse?

try changing your config to this

```
/etc# cat mpd.conf # An example configuration file for MPD # See the mpd.conf man page for a more detailed description of each parameter.   # Files and directories ####################################################### # # This setting controls the top directory which MPD will search to discover the # available audio files and add them to the daemon's online database. This  # setting defaults to the XDG directory, otherwise the music directory will be # be disabled and audio files will only be accepted over ipc socket (using # file:// protocol) or streaming files over an accepted protocol. # music_directory        "/library/music/" # # This setting sets the MPD internal playlist directory. The purpose of this # directory is storage for playlists created by MPD. The server will use  # playlist files not created by the server but only if they are in the MPD # format. This setting defaults to playlist saving being disabled. # playlist_directory        "/var/lib/mpd/playlists" # # This setting sets the location of the MPD database. This file is used to # load the database at server start up and store the database while the  # server is not up. This setting defaults to disabled which will allow # MPD to accept files over ipc socket (using file:// protocol) or streaming # files over an accepted protocol. # db_file            "/var/lib/mpd/tag_cache" #  # These settings are the locations for the daemon log files for the daemon. # These logs are great for troubleshooting, depending on your log_level # settings. # # The special value "syslog" makes MPD use the local syslog daemon. This # setting defaults to logging to syslog, otherwise logging is disabled. # log_file            "/var/log/mpd/mpd.log" # # This setting sets the location of the file which stores the process ID # for use of mpd --kill and some init scripts. This setting is disabled by # default and the pid file will not be stored. # pid_file            "/var/run/mpd/pid" # # This setting sets the location of the file which contains information about # most variables to get MPD back into the same general shape it was in before # it was brought down. This setting is disabled by default and the server  # state will be reset on server start up. # state_file            "/var/lib/mpd/state" # # The location of the sticker database.  This is a database which # manages dynamic information attached to songs. # sticker_file                   "/var/lib/mpd/sticker.sql" # ###############################################################################   # General music daemon options ################################################ # # This setting specifies the user that MPD will run as. MPD should never run as # root and you may use this setting to make MPD change its user ID after # initialization. This setting is disabled by default and MPD is run as the # current user. # user                "mpd" # # This setting specifies the group that MPD will run as. If not specified # primary group of user specified with "user" setting will be used (if set). # This is useful if MPD needs to be a member of group such as "audio" to # have permission to use sound card. # group                          "library" # # This setting sets the address for the daemon to listen on. Careful attention # should be paid if this is assigned to anything other then the default, any. # This setting can deny access to control of the daemon. Choose any if you want # to have mpd listen on every address # # For network bind_to_address        "localhost" # # And for Unix Socket #bind_to_address        "/var/run/mpd/socket" # # This setting is the TCP port that is desired for the daemon to get assigned # to. # #port                "6600" # # This setting controls the type of information which is logged. Available  # setting arguments are "default", "secure" or "verbose". The "verbose" setting # argument is recommended for troubleshooting, though can quickly stretch # available resources on limited hardware storage. # #log_level            "default" # # If you have a problem with your MP3s ending abruptly it is recommended that  # you set this argument to "no" to attempt to fix the problem. If this solves # the problem, it is highly recommended to fix the MP3 files with vbrfix # (available as vbrfix in the debian archive), at which # point gapless MP3 playback can be enabled. # #gapless_mp3_playback            "yes" # # This setting enables MPD to create playlists in a format usable by other # music players. # #save_absolute_paths_in_playlists    "no" # # This setting defines a list of tag types that will be extracted during the  # audio file discovery process. Optionally, 'comment' can be added to this # list. # #metadata_to_use    "artist,album,title,track,name,genre,date,composer,performer,disc" # # This setting enables automatic update of MPD's database when files in  # music_directory are changed. # auto_update    "yes" # # Limit the depth of the directories being watched, 0 means only watch # the music directory itself.  There is no limit by default. # #auto_update_depth "3" # ###############################################################################   # Symbolic link behavior ###################################################### # # If this setting is set to "yes", MPD will discover audio files by following  # symbolic links outside of the configured music_directory. # #follow_outside_symlinks    "yes" # # If this setting is set to "yes", MPD will discover audio files by following # symbolic links inside of the configured music_directory. # #follow_inside_symlinks        "yes" # ###############################################################################   # Zeroconf / Avahi Service Discovery ########################################## # # If this setting is set to "yes", service information will be published with # Zeroconf / Avahi. # #zeroconf_enabled        "yes" # # The argument to this setting will be the Zeroconf / Avahi unique name for # this MPD server on the network. # #zeroconf_name            "Music Player" # ###############################################################################   # Permissions ################################################################# # # If this setting is set, MPD will require password authorization. The password # can setting can be specified multiple times for different password profiles. # #password                        "password@read,add,control,admin" # # This setting specifies the permissions a user has who has not yet logged in.  # #default_permissions             "read,add,control,admin" # ###############################################################################   # Input ####################################################################### #  input {         plugin "curl" #       proxy "proxy.isp.com:8080" #       proxy_user "user" #       proxy_password "password" }  # ###############################################################################  # Audio Output ################################################################ # # MPD supports various audio output types, as well as playing through multiple  # audio outputs at the same time, through multiple audio_output settings  # blocks. Setting this block is optional, though the server will only attempt # autodetection for one sound card. # # See <http://mpd.wikia.com/wiki/Configuration#Audio_Outputs> for examples of  # other audio outputs. # # An example of an ALSA output: # #audio_output { #    type        "alsa" #    name        "My ALSA Device" #    device        "hw:0,0"    # optional #    format        "44100:16:2"    # optional #    mixer_device    "default"    # optional #    mixer_control    "PCM"        # optional #    mixer_index    "0"        # optional #} # # An example of an OSS output: # #audio_output { #    type        "oss" #    name        "My OSS Device" #    device        "/dev/dsp"    # optional #    format        "44100:16:2"    # optional #    mixer_device    "/dev/mixer"    # optional #    mixer_control    "PCM"        # optional #} # # An example of a shout output (for streaming to Icecast): # #audio_output { #    type        "shout" #    encoding    "ogg"            # optional #    name        "My Shout Stream" #    host        "localhost" #    port        "8000" #    mount        "/mpd.ogg" #    password    "hackme" #    quality        "5.0" #    bitrate        "128" #    format        "44100:16:1" #    protocol    "icecast2"        # optional #    user        "source"        # optional #    description    "My Stream Description"    # optional #    genre        "jazz"            # optional #    public        "no"            # optional #    timeout        "2"            # optional #} # # An example of a recorder output: # #audio_output { #       type            "recorder" #       name            "My recorder" #       encoder         "vorbis"                # optional, vorbis or lame #       path            "/var/lib/mpd/recorder/mpd.ogg" ##      quality         "5.0"                   # do not define if bitrate is defined #       bitrate         "128"                   # do not define if quality is defined #       format          "44100:16:1" #} # # An example of a httpd output (built-in HTTP streaming server): # #audio_output { #    type        "httpd" #    name        "My HTTP Stream" #    encoder        "vorbis"        # optional, vorbis or lame #    port        "8000" #    quality        "5.0"            # do not define if bitrate is defined #    bitrate        "128"            # do not define if quality is defined #    format        "44100:16:1" #} # # An example of a pulseaudio output (streaming to a remote pulseaudio server) # audio_output {     type        "pulse"     name        "My Pulse Output"     server        "remote_server"        # optional     sink        "remote_server_sink"    # optional } # ## Example "pipe" output: # #audio_output { #    type        "pipe" #    name        "my pipe" #    command        "aplay -f cd 2>/dev/null" ## Or if you're want to use AudioCompress #    command        "AudioCompress -m | aplay -f cd 2>/dev/null" ## Or to send raw PCM stream through PCM: #    command        "nc example.org 8765" #    format        "44100:16:2" #} # ## An example of a null output (for no audio output): # #audio_output { #    type        "null" #    name        "My Null Output" #} # # This setting will change all decoded audio to be converted to the specified # format before being passed to the audio outputs. By default, this setting is # disabled. # #audio_output_format        "44100:16:2" # # If MPD has been compiled with libsamplerate support, this setting specifies  # the sample rate converter to use.  Possible values can be found in the  # mpd.conf man page or the libsamplerate documentation. By default, this is # setting is disabled. # #samplerate_converter        "Fastest Sinc Interpolator" # ###############################################################################   # Volume control mixer ######################################################## # # These are the global volume control settings. By default, this setting will # be detected to the available audio output device, with preference going to  # hardware mixing. Hardware and software mixers for individual audio_output # sections cannot yet be mixed. # # An example for controlling an ALSA, OSS or Pulseaudio mixer; If this # setting is used other sound applications will be affected by the volume # being controlled by MPD. # #mixer_type            "hardware" # # An example for controlling all mixers through software. This will control # all controls, even if the mixer is not supported by the device and will not # affect any other sound producing applications. # #mixer_type            "software" # # This example will not allow MPD to touch the mixer at all and will disable # all volume controls. # #mixer_type            "disabled" # ###############################################################################   # Normalization automatic volume adjustments ################################## # # This setting specifies the type of ReplayGain to use. This setting can have # the argument "album" or "track". See <http://www.replaygain.org> for more # details. This setting is disabled by default. # #replaygain            "album" # # This setting sets the pre-amp used for files that have ReplayGain tags. By # default this setting is disabled. # #replaygain_preamp        "0" # # This setting enables on-the-fly normalization volume adjustment. This will # result in the volume of all playing audio to be adjusted so the output has  # equal "loudness". This setting is disabled by default. # #volume_normalization        "no" # ###############################################################################   # MPD Internal Buffering ###################################################### # # This setting adjusts the size of internal decoded audio buffering. Changing # this may have undesired effects. Don't change this if you don't know what you # are doing. # #audio_buffer_size        "2048" # # This setting controls the percentage of the buffer which is filled before  # beginning to play. Increasing this reduces the chance of audio file skipping,  # at the cost of increased time prior to audio playback. # #buffer_before_play        "10%" # ###############################################################################   # Resource Limitations ######################################################## # # These settings are various limitations to prevent MPD from using too many # resources. Generally, these settings should be minimized to prevent security # risks, depending on the operating resources. # #connection_timeout        "60" #max_connections        "10" #max_playlist_length        "16384" #max_command_list_size        "2048" #max_output_buffer_size        "8192" # ###############################################################################   # Character Encoding ########################################################## # # If file or directory names do not display correctly for your locale then you  # may need to modify this setting. After modification of this setting mpd  # --create-db must be run to change the database. # filesystem_charset        "UTF-8" # # This setting controls the encoding that ID3v1 tags should be converted from. # id3v1_encoding            "UTF-8" # ############################################################################### # SIDPlay decoder ############################################################# # # songlength_database: #  Location of your songlengths file, as distributed with the HVSC. #  The sidplay plugin checks this for matching MD5 fingerprints. #  See http://www.c64.org/HVSC/DOCUMENTS/Songlengths.faq # # default_songlength: #  This is the default playing time in seconds for songs not in the #  songlength database, or in case you're not using a database. #  A value of 0 means play indefinitely. # # filter: #  Turns the SID filter emulation on or off. # #decoder { #       plugin                  "sidplay" #       songlength_database     "/media/C64Music/DOCUMENTS/Songlengths.txt" #       default_songlength      "120" #       filter "true" #} # ###############################################################################
```

Thats changed it from alsa to pulse (which I think is default in ubuntu) I use alsa and had to play around with the settings a bit 

my config bellow used my alsa pc sound and a bluetooth USB speaker (switched to this for bbq's ) 

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
music_directory        "/var/lib/mpd/music"
#
# This setting sets the MPD internal playlist directory. The purpose of this
# directory is storage for playlists created by MPD. The server will use 
# playlist files not created by the server but only if they are in the MPD
# format. This setting defaults to playlist saving being disabled.
#
playlist_directory        "/var/lib/mpd/playlists"
#
# This setting sets the location of the MPD database. This file is used to
# load the database at server start up and store the database while the 
# server is not up. This setting defaults to disabled which will allow
# MPD to accept files over ipc socket (using file:// protocol) or streaming
# files over an accepted protocol.
#
db_file            "/var/lib/mpd/tag_cache"
# 
# These settings are the locations for the daemon log files for the daemon.
# These logs are great for troubleshooting, depending on your log_level
# settings.
#
# The special value "syslog" makes MPD use the local syslog daemon. This
# setting defaults to logging to syslog, otherwise logging is disabled.
#
log_file            "/var/log/mpd/mpd.log"
#
# This setting sets the location of the file which stores the process ID
# for use of mpd --kill and some init scripts. This setting is disabled by
# default and the pid file will not be stored.
#
pid_file            "/var/run/mpd/pid"
#
# This setting sets the location of the file which contains information about
# most variables to get MPD back into the same general shape it was in before
# it was brought down. This setting is disabled by default and the server 
# state will be reset on server start up.
#
state_file            "/var/lib/mpd/state"
#
# The location of the sticker database.  This is a database which
# manages dynamic information attached to songs.
#
#sticker_file        "/var/lib/mpd/sticker.sqlite"
#
###############################################################################


# General music daemon options ################################################
#
# This setting specifies the user that MPD will run as. MPD should never run as
# root and you may use this setting to make MPD change its user ID after
# initialization. This setting is disabled by default and MPD is run as the
# current user.
#
user                "mpd"
#
# This setting specifies the group that MPD will run as. If not specified
# primary group of user specified with "user" setting will be used (if set).
# This is useful if MPD needs to be a member of group such as "audio" to
# have permission to use sound card.
#
group                "audio"
#
# This setting sets the address for the daemon to listen on. Careful attention
# should be paid if this is assigned to anything other then the default, any.
# This setting can deny access to control of the daemon.
#
# For network
bind_to_address        "localhost"
#
# And for Unix Socket
#bind_to_address        "/var/run/mpd/socket"
#
# This setting is the TCP port that is desired for the daemon to get assigned
# to.
#
#port                "6600"
#
# This setting controls the type of information which is logged. Available 
# setting arguments are "default", "secure" or "verbose". The "verbose" setting
# argument is recommended for troubleshooting, though can quickly stretch
# available resources on limited hardware storage.
#
#log_level            "default"
#
# If you have a problem with your MP3s ending abruptly it is recommended that 
# you set this argument to "no" to attempt to fix the problem. If this solves
# the problem, it is highly recommended to fix the MP3 files with vbrfix
# (available from <http://www.willwap.co.uk/Programs/vbrfix.php>), at which
# point gapless MP3 playback can be enabled.
#
#gapless_mp3_playback            "yes"
#
# This setting enables MPD to create playlists in a format usable by other
# music players.
#
#save_absolute_paths_in_playlists    "no"
#
# This setting defines a list of tag types that will be extracted during the 
# audio file discovery process. Optionally, 'comment' can be added to this
# list.
#
#metadata_to_use    "artist,album,title,track,name,genre,date,composer,performer,disc"
#
# This setting enables automatic update of MPD's database when files in 
# music_directory are changed.
#
auto_update    "yes"
##############################################################################


# Symbolic link behavior ######################################################
#
# If this setting is set to "yes", MPD will discover audio files by following 
# symbolic links outside of the configured music_directory.
#
#follow_outside_symlinks    "yes"
#
# If this setting is set to "yes", MPD will discover audio files by following
# symbolic links inside of the configured music_directory.
#
#follow_inside_symlinks        "yes"
#
###############################################################################


# Zeroconf / Avahi Service Discovery ##########################################
#
# If this setting is set to "yes", service information will be published with
# Zeroconf / Avahi.
#
#zeroconf_enabled        "yes"
#
# The argument to this setting will be the Zeroconf / Avahi unique name for
# this MPD server on the network.
#
#zeroconf_name            "Music Player"
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
#audio_output {
#    type        "alsa"
#    name        "My ALSA Device"
#    device        "hw:0,0"    # optional
#    format        "44100:16:2"    # optional
#    mixer_type      "hardware"    # optional
#    mixer_device    "default"    # optional
#    mixer_control    "PCM"        # optional
#    mixer_index    "0"        # optional
#}
#
audio_output {
    type        "alsa"
    name        "VIA VT1708S"
    device        "hw:0,0"    # optional
    format        "44100:16:2"    # optional
    mixer_device    "default"    # optional
    mixer_control    "MASTER"    # optional
    mixer_index    "0"        # optional
}
#
audio_output {
        type            "alsa"
        name            "USB"
       device          "hw:1,0"        # optional
       format          "44100:16:2"    # optional
       mixer_device    "default"       # optional
       mixer_control   "MASTER"        # optional
       mixer_index     "0"             # optional
}
# An example of an OSS output:
#
#audio_output {
#    type        "oss"
#    name        "My OSS Device"
##    device        "/dev/dsp"    # optional
##    format        "44100:16:2"    # optional
##    mixer_type      "hardware"    # optional
##    mixer_device    "/dev/mixer"    # optional
##    mixer_control    "PCM"        # optional
#}
#
# An example of a shout output (for streaming to Icecast):
#
#audio_output {
#    type        "shout"
#    encoding    "ogg"            # optional
#    name        "My Shout Stream"
#    host        "localhost"
#    port        "8000"
#    mount        "/mpd.ogg"
#    password    "hackme"
#    quality        "5.0"
#    bitrate        "128"
#    format        "44100:16:1"
##    protocol    "icecast2"        # optional
##    user        "source"        # optional
##    description    "My Stream Description"    # optional
##    genre        "jazz"            # optional
##    public        "no"            # optional
##    timeout        "2"            # optional
##    mixer_type      "software"        # optional
#}
#
# An example of a recorder output:
#
#audio_output {
#    type        "recorder"
#    name        "My recorder"
#    encoder        "vorbis"        # optional, vorbis or lame
#    path        "/var/lib/mpd/recorder/mpd.ogg"
##    quality        "5.0"            # do not define if bitrate is defined
#    bitrate        "128"            # do not define if quality is defined
#    format        "44100:16:1"
#}
#
# An example of a httpd output (built-in HTTP streaming server):
#
#audio_output {
#    type        "httpd"
#    name        "My HTTP Stream"
#    encoder        "vorbis"        # optional, vorbis or lame
#    port        "8000"
##    quality        "5.0"            # do not define if bitrate is defined
#    bitrate        "128"            # do not define if quality is defined
#    format        "44100:16:1"
#    max_clients    "0"            # optional 0=no limit
#}
#
# An example of a pulseaudio output (streaming to a remote pulseaudio server)
#
#audio_output {
#    type        "pulse"
#    name        "My Pulse Output"
##    server        "remote_server"        # optional
##    sink        "remote_server_sink"    # optional
#}
#
## Example "pipe" output:
#
#audio_output {
#    type        "pipe"
#    name        "my pipe"
#    command        "aplay -f cd 2>/dev/null"
## Or if you're want to use AudioCompress
#    command        "AudioCompress -m | aplay -f cd 2>/dev/null"
## Or to send raw PCM stream through PCM:
#    command        "nc example.org 8765"
#    format        "44100:16:2"
#}
#
## An example of a null output (for no audio output):
#
#audio_output {
#    type        "null"
#    name        "My Null Output"
#    mixer_type      "none"            # optional
#}
#
# This setting will change all decoded audio to be converted to the specified
# format before being passed to the audio outputs. By default, this setting is
# disabled.
#
#audio_output_format        "44100:16:2"
#
# If MPD has been compiled with libsamplerate support, this setting specifies 
# the sample rate converter to use.  Possible values can be found in the 
# mpd.conf man page or the libsamplerate documentation. By default, this is
# setting is disabled.
#
#samplerate_converter        "Fastest Sinc Interpolator"
#
###############################################################################


# Normalization automatic volume adjustments ##################################
#
# This setting specifies the type of ReplayGain to use. This setting can have
# the argument "off", "album" or "track". See <http://www.replaygain.org>
# for more details. This setting is off by default.
#
#replaygain            "album"
#
# This setting sets the pre-amp used for files that have ReplayGain tags. By
# default this setting is disabled.
#
#replaygain_preamp        "0"
#
# This setting enables on-the-fly normalization volume adjustment. This will
# result in the volume of all playing audio to be adjusted so the output has 
# equal "loudness". This setting is disabled by default.
#
#volume_normalization        "no"
#
###############################################################################


# MPD Internal Buffering ######################################################
#
# This setting adjusts the size of internal decoded audio buffering. Changing
# this may have undesired effects. Don't change this if you don't know what you
# are doing.
#
#audio_buffer_size        "2048"
#
# This setting controls the percentage of the buffer which is filled before 
# beginning to play. Increasing this reduces the chance of audio file skipping, 
# at the cost of increased time prior to audio playback.
#
#buffer_before_play        "10%"
#
###############################################################################


# Resource Limitations ########################################################
#
# These settings are various limitations to prevent MPD from using too many
# resources. Generally, these settings should be minimized to prevent security
# risks, depending on the operating resources.
#
#connection_timeout        "60"
#max_connections        "10"
#max_playlist_length        "16384"
#max_command_list_size        "2048"
#max_output_buffer_size        "8192"
#
###############################################################################


# Character Encoding ##########################################################
#
# If file or directory names do not display correctly for your locale then you 
# may need to modify this setting.
#
filesystem_charset        "UTF-8"
#
# This setting controls the encoding that ID3v1 tags should be converted from.
#
id3v1_encoding            "UTF-8"
#
###############################################################################
```

You might want to change 

```
group                          "library"
```

back to 
```
group                          "audio"
```


and add mpd to audio group

```
sudo adduser mpd audio
```

---

### Post by bvargo on 2013-01-15
> **SlugSlug said:**
> You might want to change 

```
group                          "library"
```

back to 
```
group                          "audio"
```


and add mpd to audio group

```
sudo adduser mpd audio
```

mpd was created in the audio group and then added to the system group "library".  I would like to have one "library" group for use by mpd, deluge, minidlna, etc., so that they don't all have their own groups.  in reality i'd like to eliminate audio, but i was under the impression that being in the audio group was important for controlling the sound card so i left it alone.

> **SlugSlug said:**
> I'd stick to adding the Music Folder in the config and just doing the mpc update.

As for sound are you using alsa or pulse?


Whatever is stock in 12.04.1 Server.  When I set it up the first time, I was able to get it to run with alsa but I'd added a gui environment before i got MPD set up.

```

root:~# ps -A |grep alsa
root:~# ps -A |grep pulse

```
gave no results.

> 
try changing your config to this

```
/etc# cat mpd.conf # An example configuration file for MPD # See the mpd.conf man page for a more detailed description of each parameter.   # Files and directories ####################################################### # # This setting controls the top directory which MPD will search to discover the # available audio files and add them to the daemon's online database. This  # setting defaults to the XDG directory, otherwise the music directory will be # be disabled and audio files will only be accepted over ipc socket (using # file:// protocol) or streaming files over an accepted protocol. # music_directory        "/library/music/" # # This setting sets the MPD internal playlist directory. The purpose of this # directory is storage for playlists created by MPD. The server will use  # playlist files not created by the server but only if they are in the MPD # format. This setting defaults to playlist saving being disabled. # playlist_directory        "/var/lib/mpd/playlists" # # This setting sets the location of the MPD database. This file is used to # load the database at server start up and store the database while the  # server is not up. This setting defaults to disabled which will allow # MPD to accept files over ipc socket (using file:// protocol) or streaming # files over an accepted protocol. # db_file            "/var/lib/mpd/tag_cache" #  # These settings are the locations for the daemon log files for the daemon. # These logs are great for troubleshooting, depending on your log_level # settings. # # The special value "syslog" makes MPD use the local syslog daemon. This # setting defaults to logging to syslog, otherwise logging is disabled. # log_file            "/var/log/mpd/mpd.log" # # This setting sets the location of the file which stores the process ID # for use of mpd --kill and some init scripts. This setting is disabled by # default and the pid file will not be stored. # pid_file            "/var/run/mpd/pid" # # This setting sets the location of the file which contains information about # most variables to get MPD back into the same general shape it was in before # it was brought down. This setting is disabled by default and the server  # state will be reset on server start up. # state_file            "/var/lib/mpd/state" # # The location of the sticker database.  This is a database which # manages dynamic information attached to songs. # sticker_file                   "/var/lib/mpd/sticker.sql" # ###############################################################################   # General music daemon options ################################################ # # This setting specifies the user that MPD will run as. MPD should never run as # root and you may use this setting to make MPD change its user ID after # initialization. This setting is disabled by default and MPD is run as the # current user. # user                "mpd" # # This setting specifies the group that MPD will run as. If not specified # primary group of user specified with "user" setting will be used (if set). # This is useful if MPD needs to be a member of group such as "audio" to # have permission to use sound card. # group                          "library" # # This setting sets the address for the daemon to listen on. Careful attention # should be paid if this is assigned to anything other then the default, any. # This setting can deny access to control of the daemon. Choose any if you want # to have mpd listen on every address # # For network bind_to_address        "localhost" # # And for Unix Socket #bind_to_address        "/var/run/mpd/socket" # # This setting is the TCP port that is desired for the daemon to get assigned # to. # #port                "6600" # # This setting controls the type of information which is logged. Available  # setting arguments are "default", "secure" or "verbose". The "verbose" setting # argument is recommended for troubleshooting, though can quickly stretch # available resources on limited hardware storage. # #log_level            "default" # # If you have a problem with your MP3s ending abruptly it is recommended that  # you set this argument to "no" to attempt to fix the problem. If this solves # the problem, it is highly recommended to fix the MP3 files with vbrfix # (available as vbrfix in the debian archive), at which # point gapless MP3 playback can be enabled. # #gapless_mp3_playback            "yes" # # This setting enables MPD to create playlists in a format usable by other # music players. # #save_absolute_paths_in_playlists    "no" # # This setting defines a list of tag types that will be extracted during the  # audio file discovery process. Optionally, 'comment' can be added to this # list. # #metadata_to_use    "artist,album,title,track,name,genre,date,composer,performer,disc" # # This setting enables automatic update of MPD's database when files in  # music_directory are changed. # auto_update    "yes" # # Limit the depth of the directories being watched, 0 means only watch # the music directory itself.  There is no limit by default. # #auto_update_depth "3" # ###############################################################################   # Symbolic link behavior ###################################################### # # If this setting is set to "yes", MPD will discover audio files by following  # symbolic links outside of the configured music_directory. # #follow_outside_symlinks    "yes" # # If this setting is set to "yes", MPD will discover audio files by following # symbolic links inside of the configured music_directory. # #follow_inside_symlinks        "yes" # ###############################################################################   # Zeroconf / Avahi Service Discovery ########################################## # # If this setting is set to "yes", service information will be published with # Zeroconf / Avahi. # #zeroconf_enabled        "yes" # # The argument to this setting will be the Zeroconf / Avahi unique name for # this MPD server on the network. # #zeroconf_name            "Music Player" # ###############################################################################   # Permissions ################################################################# # # If this setting is set, MPD will require password authorization. The password # can setting can be specified multiple times for different password profiles. # #password                        "password@read,add,control,admin" # # This setting specifies the permissions a user has who has not yet logged in.  # #default_permissions             "read,add,control,admin" # ###############################################################################   # Input ####################################################################### #  input {         plugin "curl" #       proxy "proxy.isp.com:8080" #       proxy_user "user" #       proxy_password "password" }  # ###############################################################################  # Audio Output ################################################################ # # MPD supports various audio output types, as well as playing through multiple  # audio outputs at the same time, through multiple audio_output settings  # blocks. Setting this block is optional, though the server will only attempt # autodetection for one sound card. # # See <http://mpd.wikia.com/wiki/Configuration#Audio_Outputs> for examples of  # other audio outputs. # # An example of an ALSA output: # #audio_output { #    type        "alsa" #    name        "My ALSA Device" #    device        "hw:0,0"    # optional #    format        "44100:16:2"    # optional #    mixer_device    "default"    # optional #    mixer_control    "PCM"        # optional #    mixer_index    "0"        # optional #} # # An example of an OSS output: # #audio_output { #    type        "oss" #    name        "My OSS Device" #    device        "/dev/dsp"    # optional #    format        "44100:16:2"    # optional #    mixer_device    "/dev/mixer"    # optional #    mixer_control    "PCM"        # optional #} # # An example of a shout output (for streaming to Icecast): # #audio_output { #    type        "shout" #    encoding    "ogg"            # optional #    name        "My Shout Stream" #    host        "localhost" #    port        "8000" #    mount        "/mpd.ogg" #    password    "hackme" #    quality        "5.0" #    bitrate        "128" #    format        "44100:16:1" #    protocol    "icecast2"        # optional #    user        "source"        # optional #    description    "My Stream Description"    # optional #    genre        "jazz"            # optional #    public        "no"            # optional #    timeout        "2"            # optional #} # # An example of a recorder output: # #audio_output { #       type            "recorder" #       name            "My recorder" #       encoder         "vorbis"                # optional, vorbis or lame #       path            "/var/lib/mpd/recorder/mpd.ogg" ##      quality         "5.0"                   # do not define if bitrate is defined #       bitrate         "128"                   # do not define if quality is defined #       format          "44100:16:1" #} # # An example of a httpd output (built-in HTTP streaming server): # #audio_output { #    type        "httpd" #    name        "My HTTP Stream" #    encoder        "vorbis"        # optional, vorbis or lame #    port        "8000" #    quality        "5.0"            # do not define if bitrate is defined #    bitrate        "128"            # do not define if quality is defined #    format        "44100:16:1" #} # # An example of a pulseaudio output (streaming to a remote pulseaudio server) # audio_output {     type        "pulse"     name        "My Pulse Output"     server        "remote_server"        # optional     sink        "remote_server_sink"    # optional } # ## Example "pipe" output: # #audio_output { #    type        "pipe" #    name        "my pipe" #    command        "aplay -f cd 2>/dev/null" ## Or if you're want to use AudioCompress #    command        "AudioCompress -m | aplay -f cd 2>/dev/null" ## Or to send raw PCM stream through PCM: #    command        "nc example.org 8765" #    format        "44100:16:2" #} # ## An example of a null output (for no audio output): # #audio_output { #    type        "null" #    name        "My Null Output" #} # # This setting will change all decoded audio to be converted to the specified # format before being passed to the audio outputs. By default, this setting is # disabled. # #audio_output_format        "44100:16:2" # # If MPD has been compiled with libsamplerate support, this setting specifies  # the sample rate converter to use.  Possible values can be found in the  # mpd.conf man page or the libsamplerate documentation. By default, this is # setting is disabled. # #samplerate_converter        "Fastest Sinc Interpolator" # ###############################################################################   # Volume control mixer ######################################################## # # These are the global volume control settings. By default, this setting will # be detected to the available audio output device, with preference going to  # hardware mixing. Hardware and software mixers for individual audio_output # sections cannot yet be mixed. # # An example for controlling an ALSA, OSS or Pulseaudio mixer; If this # setting is used other sound applications will be affected by the volume # being controlled by MPD. # #mixer_type            "hardware" # # An example for controlling all mixers through software. This will control # all controls, even if the mixer is not supported by the device and will not # affect any other sound producing applications. # #mixer_type            "software" # # This example will not allow MPD to touch the mixer at all and will disable # all volume controls. # #mixer_type            "disabled" # ###############################################################################   # Normalization automatic volume adjustments ################################## # # This setting specifies the type of ReplayGain to use. This setting can have # the argument "album" or "track". See <http://www.replaygain.org> for more # details. This setting is disabled by default. # #replaygain            "album" # # This setting sets the pre-amp used for files that have ReplayGain tags. By # default this setting is disabled. # #replaygain_preamp        "0" # # This setting enables on-the-fly normalization volume adjustment. This will # result in the volume of all playing audio to be adjusted so the output has  # equal "loudness". This setting is disabled by default. # #volume_normalization        "no" # ###############################################################################   # MPD Internal Buffering ###################################################### # # This setting adjusts the size of internal decoded audio buffering. Changing # this may have undesired effects. Don't change this if you don't know what you # are doing. # #audio_buffer_size        "2048" # # This setting controls the percentage of the buffer which is filled before  # beginning to play. Increasing this reduces the chance of audio file skipping,  # at the cost of increased time prior to audio playback. # #buffer_before_play        "10%" # ###############################################################################   # Resource Limitations ######################################################## # # These settings are various limitations to prevent MPD from using too many # resources. Generally, these settings should be minimized to prevent security # risks, depending on the operating resources. # #connection_timeout        "60" #max_connections        "10" #max_playlist_length        "16384" #max_command_list_size        "2048" #max_output_buffer_size        "8192" # ###############################################################################   # Character Encoding ########################################################## # # If file or directory names do not display correctly for your locale then you  # may need to modify this setting. After modification of this setting mpd  # --create-db must be run to change the database. # filesystem_charset        "UTF-8" # # This setting controls the encoding that ID3v1 tags should be converted from. # id3v1_encoding            "UTF-8" # ############################################################################### # SIDPlay decoder ############################################################# # # songlength_database: #  Location of your songlengths file, as distributed with the HVSC. #  The sidplay plugin checks this for matching MD5 fingerprints. #  See http://www.c64.org/HVSC/DOCUMENTS/Songlengths.faq # # default_songlength: #  This is the default playing time in seconds for songs not in the #  songlength database, or in case you're not using a database. #  A value of 0 means play indefinitely. # # filter: #  Turns the SID filter emulation on or off. # #decoder { #       plugin                  "sidplay" #       songlength_database     "/media/C64Music/DOCUMENTS/Songlengths.txt" #       default_songlength      "120" #       filter "true" #} # ###############################################################################
```


Can you repost this, it came in one long string without CRs.

> 
Thats changed it from alsa to pulse (which I think is default in ubuntu) I use alsa and had to play around with the settings a bit 

my config bellow used my alsa pc sound and a bluetooth USB speaker (switched to this for bbq's ) 

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
music_directory        "/var/lib/mpd/music"
#
# This setting sets the MPD internal playlist directory. The purpose of this
# directory is storage for playlists created by MPD. The server will use 
# playlist files not created by the server but only if they are in the MPD
# format. This setting defaults to playlist saving being disabled.
#
playlist_directory        "/var/lib/mpd/playlists"
#
# This setting sets the location of the MPD database. This file is used to
# load the database at server start up and store the database while the 
# server is not up. This setting defaults to disabled which will allow
# MPD to accept files over ipc socket (using file:// protocol) or streaming
# files over an accepted protocol.
#
db_file            "/var/lib/mpd/tag_cache"
# 
# These settings are the locations for the daemon log files for the daemon.
# These logs are great for troubleshooting, depending on your log_level
# settings.
#
# The special value "syslog" makes MPD use the local syslog daemon. This
# setting defaults to logging to syslog, otherwise logging is disabled.
#
log_file            "/var/log/mpd/mpd.log"
#
# This setting sets the location of the file which stores the process ID
# for use of mpd --kill and some init scripts. This setting is disabled by
# default and the pid file will not be stored.
#
pid_file            "/var/run/mpd/pid"
#
# This setting sets the location of the file which contains information about
# most variables to get MPD back into the same general shape it was in before
# it was brought down. This setting is disabled by default and the server 
# state will be reset on server start up.
#
state_file            "/var/lib/mpd/state"
#
# The location of the sticker database.  This is a database which
# manages dynamic information attached to songs.
#
#sticker_file        "/var/lib/mpd/sticker.sqlite"
#
###############################################################################


# General music daemon options ################################################
#
# This setting specifies the user that MPD will run as. MPD should never run as
# root and you may use this setting to make MPD change its user ID after
# initialization. This setting is disabled by default and MPD is run as the
# current user.
#
user                "mpd"
#
# This setting specifies the group that MPD will run as. If not specified
# primary group of user specified with "user" setting will be used (if set).
# This is useful if MPD needs to be a member of group such as "audio" to
# have permission to use sound card.
#
group                "audio"
#
# This setting sets the address for the daemon to listen on. Careful attention
# should be paid if this is assigned to anything other then the default, any.
# This setting can deny access to control of the daemon.
#
# For network
bind_to_address        "localhost"
#
# And for Unix Socket
#bind_to_address        "/var/run/mpd/socket"
#
# This setting is the TCP port that is desired for the daemon to get assigned
# to.
#
#port                "6600"
#
# This setting controls the type of information which is logged. Available 
# setting arguments are "default", "secure" or "verbose". The "verbose" setting
# argument is recommended for troubleshooting, though can quickly stretch
# available resources on limited hardware storage.
#
#log_level            "default"
#
# If you have a problem with your MP3s ending abruptly it is recommended that 
# you set this argument to "no" to attempt to fix the problem. If this solves
# the problem, it is highly recommended to fix the MP3 files with vbrfix
# (available from <http://www.willwap.co.uk/Programs/vbrfix.php>), at which
# point gapless MP3 playback can be enabled.
#
#gapless_mp3_playback            "yes"
#
# This setting enables MPD to create playlists in a format usable by other
# music players.
#
#save_absolute_paths_in_playlists    "no"
#
# This setting defines a list of tag types that will be extracted during the 
# audio file discovery process. Optionally, 'comment' can be added to this
# list.
#
#metadata_to_use    "artist,album,title,track,name,genre,date,composer,performer,disc"
#
# This setting enables automatic update of MPD's database when files in 
# music_directory are changed.
#
auto_update    "yes"
##############################################################################


# Symbolic link behavior ######################################################
#
# If this setting is set to "yes", MPD will discover audio files by following 
# symbolic links outside of the configured music_directory.
#
#follow_outside_symlinks    "yes"
#
# If this setting is set to "yes", MPD will discover audio files by following
# symbolic links inside of the configured music_directory.
#
#follow_inside_symlinks        "yes"
#
###############################################################################


# Zeroconf / Avahi Service Discovery ##########################################
#
# If this setting is set to "yes", service information will be published with
# Zeroconf / Avahi.
#
#zeroconf_enabled        "yes"
#
# The argument to this setting will be the Zeroconf / Avahi unique name for
# this MPD server on the network.
#
#zeroconf_name            "Music Player"
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
#audio_output {
#    type        "alsa"
#    name        "My ALSA Device"
#    device        "hw:0,0"    # optional
#    format        "44100:16:2"    # optional
#    mixer_type      "hardware"    # optional
#    mixer_device    "default"    # optional
#    mixer_control    "PCM"        # optional
#    mixer_index    "0"        # optional
#}
#
audio_output {
    type        "alsa"
    name        "VIA VT1708S"
    device        "hw:0,0"    # optional
    format        "44100:16:2"    # optional
    mixer_device    "default"    # optional
    mixer_control    "MASTER"    # optional
    mixer_index    "0"        # optional
}
#
audio_output {
        type            "alsa"
        name            "USB"
       device          "hw:1,0"        # optional
       format          "44100:16:2"    # optional
       mixer_device    "default"       # optional
       mixer_control   "MASTER"        # optional
       mixer_index     "0"             # optional
}
# An example of an OSS output:
#
#audio_output {
#    type        "oss"
#    name        "My OSS Device"
##    device        "/dev/dsp"    # optional
##    format        "44100:16:2"    # optional
##    mixer_type      "hardware"    # optional
##    mixer_device    "/dev/mixer"    # optional
##    mixer_control    "PCM"        # optional
#}
#
# An example of a shout output (for streaming to Icecast):
#
#audio_output {
#    type        "shout"
#    encoding    "ogg"            # optional
#    name        "My Shout Stream"
#    host        "localhost"
#    port        "8000"
#    mount        "/mpd.ogg"
#    password    "hackme"
#    quality        "5.0"
#    bitrate        "128"
#    format        "44100:16:1"
##    protocol    "icecast2"        # optional
##    user        "source"        # optional
##    description    "My Stream Description"    # optional
##    genre        "jazz"            # optional
##    public        "no"            # optional
##    timeout        "2"            # optional
##    mixer_type      "software"        # optional
#}
#
# An example of a recorder output:
#
#audio_output {
#    type        "recorder"
#    name        "My recorder"
#    encoder        "vorbis"        # optional, vorbis or lame
#    path        "/var/lib/mpd/recorder/mpd.ogg"
##    quality        "5.0"            # do not define if bitrate is defined
#    bitrate        "128"            # do not define if quality is defined
#    format        "44100:16:1"
#}
#
# An example of a httpd output (built-in HTTP streaming server):
#
#audio_output {
#    type        "httpd"
#    name        "My HTTP Stream"
#    encoder        "vorbis"        # optional, vorbis or lame
#    port        "8000"
##    quality        "5.0"            # do not define if bitrate is defined
#    bitrate        "128"            # do not define if quality is defined
#    format        "44100:16:1"
#    max_clients    "0"            # optional 0=no limit
#}
#
# An example of a pulseaudio output (streaming to a remote pulseaudio server)
#
#audio_output {
#    type        "pulse"
#    name        "My Pulse Output"
##    server        "remote_server"        # optional
##    sink        "remote_server_sink"    # optional
#}
#
## Example "pipe" output:
#
#audio_output {
#    type        "pipe"
#    name        "my pipe"
#    command        "aplay -f cd 2>/dev/null"
## Or if you're want to use AudioCompress
#    command        "AudioCompress -m | aplay -f cd 2>/dev/null"
## Or to send raw PCM stream through PCM:
#    command        "nc example.org 8765"
#    format        "44100:16:2"
#}
#
## An example of a null output (for no audio output):
#
#audio_output {
#    type        "null"
#    name        "My Null Output"
#    mixer_type      "none"            # optional
#}
#
# This setting will change all decoded audio to be converted to the specified
# format before being passed to the audio outputs. By default, this setting is
# disabled.
#
#audio_output_format        "44100:16:2"
#
# If MPD has been compiled with libsamplerate support, this setting specifies 
# the sample rate converter to use.  Possible values can be found in the 
# mpd.conf man page or the libsamplerate documentation. By default, this is
# setting is disabled.
#
#samplerate_converter        "Fastest Sinc Interpolator"
#
###############################################################################


# Normalization automatic volume adjustments ##################################
#
# This setting specifies the type of ReplayGain to use. This setting can have
# the argument "off", "album" or "track". See <http://www.replaygain.org>
# for more details. This setting is off by default.
#
#replaygain            "album"
#
# This setting sets the pre-amp used for files that have ReplayGain tags. By
# default this setting is disabled.
#
#replaygain_preamp        "0"
#
# This setting enables on-the-fly normalization volume adjustment. This will
# result in the volume of all playing audio to be adjusted so the output has 
# equal "loudness". This setting is disabled by default.
#
#volume_normalization        "no"
#
###############################################################################


# MPD Internal Buffering ######################################################
#
# This setting adjusts the size of internal decoded audio buffering. Changing
# this may have undesired effects. Don't change this if you don't know what you
# are doing.
#
#audio_buffer_size        "2048"
#
# This setting controls the percentage of the buffer which is filled before 
# beginning to play. Increasing this reduces the chance of audio file skipping, 
# at the cost of increased time prior to audio playback.
#
#buffer_before_play        "10%"
#
###############################################################################


# Resource Limitations ########################################################
#
# These settings are various limitations to prevent MPD from using too many
# resources. Generally, these settings should be minimized to prevent security
# risks, depending on the operating resources.
#
#connection_timeout        "60"
#max_connections        "10"
#max_playlist_length        "16384"
#max_command_list_size        "2048"
#max_output_buffer_size        "8192"
#
###############################################################################


# Character Encoding ##########################################################
#
# If file or directory names do not display correctly for your locale then you 
# may need to modify this setting.
#
filesystem_charset        "UTF-8"
#
# This setting controls the encoding that ID3v1 tags should be converted from.
#
id3v1_encoding            "UTF-8"
#
###############################################################################
```

I'll give this a try, at this point I am accessing it remotely, so I don't know what the speakers are doing at home.  My next step is to set up the built-in http stream.

---

### Post by SlugSlug on 2013-01-15
that bit that came out in one line I just hashed out the alsa settings and un-hashed the pulse

---

### Post by bvargo on 2013-01-15
Well I'll have to figure it out when I get home as I can't listen from work.  The httpd stream is up and running now though!

Do you have any idea where to look to see which (alsa or pulse) ships with 12.04 server?

I have this [http://ubuntuforums.org/showthread.php?t=1794581](http://ubuntuforums.org/showthread.php?t=1794581) bookmarked to give a better read at some point...  from the looks of it, pulse still requires alsa.

---

### Post by SlugSlug on 2013-01-15
Am not to sure on the old pulse alsa thing. On each install I remove pulseaudio as it does not play nice with my SoundBlaster 5.1 Live card (bit dated). So by default setting it to pulse should work and if memory serves me if you hash out all sound options it auto detects (not sure how well ;) )

---

### Post by bvargo on 2013-01-15
So I installed alsa as you can see below and I also installed the suggested packages.
```

:/var/log/mpd# apt-get install alsa alsa-tools
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting 'alsa-base' instead of 'alsa'
The following extra packages will be installed:
  alsa-utils linux-sound-base
Suggested packages:
  apmd alsa-oss
The following NEW packages will be installed:
  alsa-base alsa-tools alsa-utils linux-sound-base

```

The alsamixer works, but I'll know if the sound works when I get home...I know that there is an issue that you have to tweak because only one alsa stream works at once.  I forget exactly where I saw that and what I have to do to fix it...

At this point, I'm probably going to back up and create an lvm snapshot and then put the GUI on...or maybe get proftpd working before that.  This is the third time I've built this server in the past month so hopefully I'll get everything right this time.

Well I installed ALSA and PulseAudio and neither one is working locally, but I think that is a project for tomorrow.

I installed alsa and pulse and tried it both ways...  I tried 

> 
**Bugfix: Giving MPD proper permissions**

 Unfortunately, by default MPD does not have the proper permissions to access [PulseAudio]("https://help.ubuntu.com/community/PulseAudio"),  the default audio setup on most new Ubuntu systems. If MPD plays for  you without these steps, then that's great, but if you can play your  songs but no sound is emitted, try the following steps. 
What we need to do is add the user **mpd** to the groups **pulse** and **pulse-access** so that it can access the audio system. 
$ sudo usermod -aG pulse,pulse-access mpd

but that didn't work either.  Any thoughts?

Also
```
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)

```and

```
/lib/modules# aplay /usr/share/sounds/alsa/Front_Center.wav
```works...

I switched pulse for alsa and restarted mpd.  from /var/log/mpd.log

```

Jan 16 21:31 : listen: bind to '0.0.0.0:8000' failed: Address already in use (continuing anyway, because binding to '[::]:8000' succeeded)
Jan 16 21:31 : Failed to open mixer for 'My ALSA Device': no such mixer control: PCM
Jan 16 21:31 : avahi: Service 'Music Player' successfully established.
Jan 16 21:32 : player_thread: played "Bob Dylan/Bob Dylan -- Greatest Hits  -- Volume II Vinyl FLAC/d5.i.shall.be.released.flac"
Jan 16 21:32 : Failed to open mixer for 'My ALSA Device': no such mixer control: PCM

```

And this:
```

:/var/log/mpd# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: VT2020 Analog [VT2020 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: VT2020 Digital [VT2020 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 2: VT2020 HP [VT2020 HP]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Device [USB Sound Device], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by SlugSlug on 2013-01-17
You need to tweak 

```

audio_output {
    type        "alsa"
    name        "My ALSA Device"
#    device        "hw:0,0"    # optional
#    format        "44100:16:2"    # optional
#    mixer_type      "hardware"    # optional
#    mixer_device    "default"    # optional
#    mixer_control    "PCM"        # optional
#    mixer_index    "0"        # optional
}
```Try hash out the optional bits

---

### Post by bvargo on 2013-01-17
> **SlugSlug said:**
> You need to tweak 

```

audio_output {
    type        "alsa"
    name        "My ALSA Device"
#    device        "hw:0,0"    # optional
#    format        "44100:16:2"    # optional
#    mixer_type      "hardware"    # optional
#    mixer_device    "default"    # optional
#    mixer_control    "PCM"        # optional
#    mixer_index    "0"        # optional
}
```Try hash out the optional bits

I tried that and it didn't seem to solve the problem...

```

Jan 17 11:48 : player_thread: played "Bob Dylan/Highway 61 Revisited/02 Tombstone Blues.mp3"
Jan 17 11:48 : Failed to open mixer for 'My ALSA Device': no such mixer control: PCM
Jan 17 11:50 : player_thread: played "Bob Marley/Bob Marley & The Wailers - Wisdom (Disc 2)/03 Corner Stone.m4a"
Jan 17 11:50 : Failed to open mixer for 'My ALSA Device': no such mixer control: PCM

```

Given that it keeps saying "no such mixer control:  PCM," doesn't that indicate that there is a problem with PCM?  How to I troubleshoot PCM?

Is there any use in poking around in this portion of the /etc/mpd.conf file?

```

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
#mixer_type                     "hardware"
#
# An example for controlling all mixers through software. This will control
# all controls, even if the mixer is not supported by the device and will not
# affect any other sound producing applications.
#
#mixer_type                     "software"
#
# This example will not allow MPD to touch the mixer at all and will disable
# all volume controls.
#
#mixer_type                     "disabled"
#
###############################################################################


```

---

