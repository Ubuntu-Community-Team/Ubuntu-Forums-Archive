---
title: "mpd not outputting local sound"
date: 2013-01-17
forum: Multimedia Software
---

### Post by bvargo on 2013-01-17
I've gotten mpd to output to http and I'm currently listening to it via VLC @ [http://localhost:8000](http://localhost:8000) but I cannot get pulse or alsa to output directly.  I know this machine is capable of it because I'd gotten it to work on a previous installation of 12.04.1 LTS which I reinstalled from scratch, so it isn't a hardware problem.  Interestingly, gmpc will actually control the volume going to VLC but not by changing the output volume of VLC.

Any help would be appreciated.

A lot of the relevant info on the hardware, mpd, and alsa is in my previous post:
[http://ubuntuforums.org/showthread.php?t=2105007&page=3](http://ubuntuforums.org/showthread.php?t=2105007&page=3)

If there is anything else to post to troubleshoot, please let me know.

Here is my mpd.conf:
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
bind_to_address            "0.0.0.0"
###bind_to_address        "localhost"
#
# And for Unix Socket
#bind_to_address        "/var/run/mpd/socket"
#
# This setting is the TCP port that is desired for the daemon to get assigned
# to.
#
port                "6600"
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
password                        "seven314@read,add,control,admin"
#
# This setting specifies the permissions a user has who has not yet logged in. 
#
#default_permissions             "read,add,control,admin"
default_permissions             "read"
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
#    mixer_control    "PCM"        # optional
#    mixer_index    "0"        # optional
}
###audio_output {
###    type        "alsa"
###    name        "My ALSA Device"
###    device        "hw:0,0"    # optional
###    format        "44100:16:2"    # optional
###    mixer_device    "default"    # optional
###    mixer_control    "PCM"        # optional
###    mixer_index    "0"        # optional
###}
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
audio_output {
    type        "httpd"
    name        "My HTTP Stream"
    encoder        "lame"            # optional, vorbis or lame
    port        "8000"
    quality        "5.0"            # do not define if bitrate is defined
#    bitrate        "128"            # do not define if quality is defined
    format        "44100:16:1"
}
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
mixer_type            "software"
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


```

/var/mpd/mpd.log:

```

/var/log/mpd# tail -n 50 mpd.log
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
Jan 17 23:11 : output: Failed to open "My ALSA Device" [alsa]: Failed to open ALSA device "hw:0,0": No such file or directory
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
Jan 17 23:11 : output: Failed to open "My ALSA Device" [alsa]: Failed to open ALSA device "hw:0,0": No such file or directory
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
Jan 17 23:12 : output: Failed to open "My ALSA Device" [alsa]: Failed to open ALSA device "hw:0,0": No such file or directory
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
Jan 17 23:12 : output: Failed to open "My ALSA Device" [alsa]: Failed to open ALSA device "hw:0,0": No such file or directory
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
Jan 17 23:12 : output: Failed to open "My ALSA Device" [alsa]: Failed to open ALSA device "hw:0,0": No such file or directory
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
Jan 17 23:12 : output: Failed to open "My ALSA Device" [alsa]: Failed to open ALSA device "hw:0,0": No such file or directory
Jan 17 23:12 : player_thread: played "Bob Dylan/New Morning/12 Father Of Night.mp3"
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
Jan 17 23:12 : output: Failed to open "My ALSA Device" [alsa]: Failed to open ALSA device "hw:0,0": No such file or directory
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
Jan 17 23:12 : output: Failed to open "My ALSA Device" [alsa]: Failed to open ALSA device "hw:0,0": No such file or directory
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
Jan 17 23:13 : output: Failed to open "My ALSA Device" [alsa]: Failed to open ALSA device "hw:0,0": No such file or directory
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
Jan 17 23:13 : output: Failed to open "My ALSA Device" [alsa]: Failed to open ALSA device "hw:0,0": No such file or directory
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
Jan 17 23:13 : output: Failed to open "My ALSA Device" [alsa]: Failed to open ALSA device "hw:0,0": No such file or directory
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
Jan 17 23:13 : output: Failed to open "My ALSA Device" [alsa]: Failed to open ALSA device "hw:0,0": No such file or directory
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
Jan 17 23:13 : output: Failed to open "My ALSA Device" [alsa]: Failed to open ALSA device "hw:0,0": No such file or directory
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
Jan 17 23:13 : output: Failed to open "My ALSA Device" [alsa]: Failed to open ALSA device "hw:0,0": No such file or directory
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
Jan 17 23:14 : output: Failed to open "My ALSA Device" [alsa]: Failed to open ALSA device "hw:0,0": No such file or directory
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
Jan 17 23:14 : output: Failed to open "My ALSA Device" [alsa]: Failed to open ALSA device "hw:0,0": No such file or directory
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
Jan 17 23:14 : output: Failed to open "My ALSA Device" [alsa]: Failed to open ALSA device "hw:0,0": No such file or directory
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
Jan 17 23:14 : output: Failed to open "My ALSA Device" [alsa]: Failed to open ALSA device "hw:0,0": No such file or directory
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
Jan 17 23:14 : output: Failed to open "My ALSA Device" [alsa]: Failed to open ALSA device "hw:0,0": No such file or directory
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
Jan 17 23:14 : output: Failed to open "My ALSA Device" [alsa]: Failed to open ALSA device "hw:0,0": No such file or directory
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
Jan 17 23:15 : output: Failed to open "My ALSA Device" [alsa]: Failed to open ALSA device "hw:0,0": No such file or directory
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
Jan 17 23:15 : output: Failed to open "My ALSA Device" [alsa]: Failed to open ALSA device "hw:0,0": No such file or directory
Jan 17 23:15 : player_thread: played "Bob Dylan -- Live At Budokan/Bob Dylan -- I Want You.mp3"
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
Jan 17 23:15 : output: Failed to open "My ALSA Device" [alsa]: Failed to open ALSA device "hw:0,0": No such file or directory
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
Jan 17 23:15 : output: Failed to open "My ALSA Device" [alsa]: Failed to open ALSA device "hw:0,0": No such file or directory

```

---

### Post by papibe on 2013-01-17
Hi bvargo.

Is the mpd user member of the audio group? If not add it like this:
```
sudo usermod -a -G audio mpd 
```
You may need to restart your machine.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by bvargo on 2013-01-17
yep:

```
:/var/log/mpd# groups mpd
mpd : audio library pulse pulse-access

```

Any other thoughts?

After a restart mpd.log:

```
Jan 23 18:08 : listen: bind to '0.0.0.0:8000' failed: Address already in use (continuing anyway, because binding to '[::]:8000' succeeded)
Jan 23 18:08 : config: option 'mixer_device' on line 207 was not recognized
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
Jan 23 18:08 : output: Failed to open "My ALSA Device" [alsa]: Failed to open ALSA device "hw:0,0": No such file or directory
Jan 23 18:08 : avahi: Service 'Music Player' successfully established.
```

---

### Post by papibe on 2013-01-23
Try commenting the bind line, I had better luck if it is commented, as it assures mpd will bind to all addresses:
```
#bind_to_address            "0.0.0.0"
```
Could you also post the result of this commands?
```
aplay -l

aplay -L
```
Regards.

---

### Post by bvargo on 2013-01-24
I don't believe that the bind thing is an issue.  I'm sure if I restarted on a fresh reboot, it would work.  I can stream it remotely...although it seems like it is shutting off after 10 minutes for some reason, but that may just be the connection I was on.  When I stream it from [http://localhost:8000](http://localhost:8000) on VLC it works just fine.

Note that at present, I have Logitec (?) 5.1 speakers plugged into the analog jacks.

```

:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: VT2020 Analog [VT2020 Analog]
  Subdevices: 0/1
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

```

```

:~# aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
default:CARD=PCH
    HDA Intel PCH, VT2020 Analog
    Default Audio Device
sysdefault:CARD=PCH
    HDA Intel PCH, VT2020 Analog
    Default Audio Device
front:CARD=PCH,DEV=0
    HDA Intel PCH, VT2020 Analog
    Front speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, VT2020 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, VT2020 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, VT2020 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, VT2020 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, VT2020 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=PCH,DEV=0
    HDA Intel PCH, VT2020 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=PCH,DEV=0
    HDA Intel PCH, HDMI 0
    HDMI Audio Output
hdmi:CARD=PCH,DEV=1
    HDA Intel PCH, HDMI 1
    HDMI Audio Output
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, VT2020 Analog
    Direct sample mixing device
dmix:CARD=PCH,DEV=1
    HDA Intel PCH, VT2020 Digital
    Direct sample mixing device
dmix:CARD=PCH,DEV=2
    HDA Intel PCH, VT2020 HP
    Direct sample mixing device
dmix:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct sample mixing device
dmix:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, VT2020 Analog
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=1
    HDA Intel PCH, VT2020 Digital
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=2
    HDA Intel PCH, VT2020 HP
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, VT2020 Analog
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=1
    HDA Intel PCH, VT2020 Digital
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=2
    HDA Intel PCH, VT2020 HP
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, VT2020 Analog
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=1
    HDA Intel PCH, VT2020 Digital
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=2
    HDA Intel PCH, VT2020 HP
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Hardware device with all software conversions

```

and for good measure:
```

:~# lspci
00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.4 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 5 (rev c4)
00:1c.5 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c4)
00:1c.6 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 7 (rev c4)
00:1c.7 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 8 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
02:00.0 USB controller: VIA Technologies, Inc. Device 3432 (rev 03)
03:00.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 41)
05:00.0 Ethernet controller: Atheros Communications Inc. AR8161 Gigabit Ethernet (rev 10)
06:00.0 SATA controller: Marvell Technology Group Ltd. 88SE9172 SATA 6Gb/s Controller (rev 11)


```

---

### Post by papibe on 2013-01-24
Have you tested alsa manually?

For instance, from the console.

From your user using hw:0,0
```
speaker-test -Dhw:0,0 -c2 -tw
```

From your user using defualt
```
speaker-test -Ddefault -c2 -tw
```

From mpd user using defualt:
```
sudo su -p  -c "/usr/bin/speaker-test -Ddefault -c2 -tw" mpd

```
Let us know how it goes.
Regards.

---

### Post by bvargo on 2013-02-01
alsa is working, mpd isn't connecting to it...

```

root@# speaker-test -Dhw:0,0 -c2 -tw

speaker-test 1.0.25

Playback device is hw:0,0
Stream parameters are 48000Hz, S16_LE, 2 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 1 - Front Right
Time per period = 2.730700
 0 - Front Left
 1 - Front Right
Time per period = 2.986816
 0 - Front Left
 1 - Front Right
Time per period = 2.986641
 0 - Front Left
^C


root@# speaker-test -Ddefault -c2 -tw

speaker-test 1.0.25

Playback device is default
Stream parameters are 48000Hz, S16_LE, 2 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 96 to 1048576
Period size range from 32 to 349526
Using max buffer size 1048576
Periods = 4
was set period_size = 262144
was set buffer_size = 1048576
 0 - Front Left
 1 - Front Right
Time per period = 3.236024
 0 - Front Left
 1 - Front Right
Time per period = 3.236418
 0 - Front Left
 1 - Front Right
Time per period = 3.234975
 0 - Front Left
 1 - Front Right
^C
root@# sudo su -p  -c "/usr/bin/speaker-test -Ddefault -c2 -tw" mpd

speaker-test 1.0.25

Playback device is default
Stream parameters are 48000Hz, S16_LE, 2 channels
WAV file(s)
No protocol specified
xcb_connection_has_error() returned true
Home directory /root not ours.
W: [pulseaudio] core-util.c: Failed to open configuration file '/root/.pulse//daemon.conf': Permission denied
W: [pulseaudio] daemon-conf.c: Failed to open configuration file: Permission denied
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
Playback open error: -16,Device or resource busy

```

I'd already troubleshot to make sure alsa was working but the last command seems like it said something important, I just can't figure it means.

---

