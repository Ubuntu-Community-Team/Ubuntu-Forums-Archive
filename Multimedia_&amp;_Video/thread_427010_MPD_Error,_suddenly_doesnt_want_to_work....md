---
title: "MPD Error, suddenly doesnt want to work..."
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by Valehru on 2007-04-29
Hey peeps,

I'm having a problem with MPD.  When I try and start it up I am getting the following error:


```
 
sudo /etc/init.d/mpd start
Starting Music Player Daemon: ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

client-conf-x11.c: XOpenDisplay() failed
No audio_output specified and unable to detect a default audio output device
failed.

```

Here is the mpd.conf file  ```

# An example configuration file for MPD
# See the mpd.conf man page for a more detailed description of each parameter.

######################## REQUIRED PATHS ########################
# You can put symlinks in here, if you like. Make sure that
# the user that mpd runs as (see the 'user' config parameter)
# can read the files in this directory.
music_directory		"/media/backup/Media/Audio"
playlist_directory	"/var/lib/mpd/playlists"
db_file			"/var/lib/mpd/tag_cache"
log_file		"/var/log/mpd/mpd.log"
error_file		"/var/log/mpd/errors.log"
pid_file		"/var/run/mpd/pid"
################################################################


######################## OPTIONAL PATHS ########################
#
# If specified, MPD will save its current state (playlist,
# current song, playing/paused, etc.) at exit.  This will be
# used to restore the session the next time it is run.
#
state_file		"/var/lib/mpd/state"
#
################################################################


######################## DAEMON OPTIONS ########################
#
# If started as root, MPD will drop root privileges and run as
# this user instead.  Otherwise, MPD will run as the user it was
# started by.  If left unspecified, MPD will not drop root
# privileges at all (not recommended).
#
user                            "mpd"
#
# The address and port to listen on.
#
bind_to_address                 "192.168.1.15"
port                            "6600"
#
# Controls the amount of information that is logged.  Can be
# "default", "secure", or "verbose".
#
#log_level                       "default"
#
################################################################


########################## PERMISSIONS #########################
#
# MPD can require that users specify a password before using it.
# You may specify one ore more here, along with what users who
# log in with that password are allowed to do.
#
#password                        "password@read,add,control,admin"
#
# Specifies what permissions a user who has not logged in with a
# password has.  By default, all users have full access to MPD
# if no password is specified above, or no access if one or
# more passwords are specified.
#
#default_permissions             "read,add,control,admin"
#
################################################################


########################## AUDIO OUTPUT ########################
#
# MPD supports many audio output types, as well as playing
# through multiple audio outputs at the same time.  You can
# specify one or more here.  If you don't specify any, MPD will
# automatically scan for a usable audio output.
#
# See <http://mpd.wikia.com/wiki/Configuration#Audio_Outputs>
# for examples of other audio outputs.
#
# An example of an ALSA output:
#
#audio_output {
#        type                    "alsa"
#        name                    "My ALSA Device"
#        device                  "hw:0,0"     # optional
#        format                  "44100:16:2" # optional
#}
#
# An example of an OSS output:
#
#audio_output {
#        type                    "oss"
#        name                    "My OSS Device"
#        device                  "/dev/dsp"   # optional
#        format                  "44100:16:2" # optional
#}
#
# An example of a shout output (for streaming to Icecast):
#
#audio_output {
#        type                    "shout"
#        name                    "My Shout Stream"
#        host                    "localhost"
#        port                    "8000"
#        mount                   "/mpd.ogg"
#        password                "hackme"
#        quality                 "5.0"
#        bitrate                 "128"
#        format                  "44100:16:1"
#        user                    "source"                # optional
#        description             "My Stream Description" # optional
#        genre                   "jazz"                  # optional
#        public                  "no"                    # optional
#}
#
# Force all decoded audio to be converted to this format before
# being passed to the audio outputs.
#
#audio_output_format             "44100:16:2"
#
################################################################


############################# MIXER ############################
#
# MPD needs to know what mixer settings to change when you
# adjust the volume.  If you don't specify one here, MPD will
# pick one based on which ones it was compiled with support for.
#
# An example for controlling an ALSA mixer:
#
#mixer_type                      "alsa"
#mixer_device                    "default"
#mixer_control                   "PCM"
#
# An example for controlling an OSS mixer:
#
#mixer_type                      "oss"
#mixer_device                    "/dev/mixer"
#mixer_control                   "PCM"
#
# If you want MPD to adjust the volume of audio sent to the
# audio outputs, you can tell it to use the software mixer:
#
#mixer_type                      "software"
#
################################################################


######################### NORMALIZATION ########################
#
# Specifies the type of ReplayGain to use.  Can be "album" or
# "track".  ReplayGain will not be used if not specified.  See
# <http://www.replaygain.org> for more details.
#
#replaygain                      "album"
#
# Sets the pre-amp used for files that have ReplayGain tags.
#
#replaygain_preamp               "0"
#
# Enable on the fly volume normalization.  This will cause the
# volume of all songs played to be adjusted so that they sound
# as though they are of equal loudness.
#
#volume_normalization            "no"
#
################################################################


########################### BUFFERING ##########################
#
# The size of the buffer containing decoded audio.  You probably
# shouldn't change this.
#
#audio_buffer_size               "2048"
#
# How much of the buffer to fill before beginning to play.
#
#buffer_before_play              "0%"
#
# Similar options for the HTTP stream buffer.  If you hear
# skipping while playing HTTP streams, you may wish to increase
# these.
#
#http_buffer_size                "128"
#http_prebuffer_size             "25%"
#
################################################################


########################### HTTP PROXY #########################
#
# Specifies the HTTP proxy to use for playing HTTP streams.
#
#http_proxy_host                 "proxy.isp.com"
#http_proxy_port                 "8080"
#http_proxy_user                 "user"
#http_proxy_password             "password"
#
################################################################


############################# LIMITS ###########################
#
# These are various limits to prevent MPD from using too many
# resources.  You should only change them if they start
# restricting your usage of MPD.
#
#connection_timeout              "60"
#max_connections                 "5"
#max_playlist_length             "16384"
#max_command_list_size           "2048"
#max_output_buffer_size          "8192"
#
################################################################


###################### CHARACTER ENCODINGS #####################
#
# If file or directory names do not display correctly, then you
# may need to change this.  In most cases it should be either
# "ISO-8859-1" or "UTF-8".  You must recreate your database
# after changing this (use mpd --create-db).
#
#filesystem_charset              "ISO-8859-1"
#
# The encoding that ID3v1 tags should be converted from.
#
#id3v1_encoding                  "ISO-8859-1"
#
################################################################


######################### OTHER OPTIONS ########################
#
# The metadata types MPD will recognize.
#
#metadata_to_use                  "artist,album,title,track,name,genre,date,composer,performer,disc"
#
# Enable this if you wish to use your MPD created playlists in
# other music players.
#
#save_absolute_paths_in_playlists "no"
#
################################################################

```

Thanks for any help in advance...

---

### Post by gyaresu on 2007-04-30
Same here:
mpd is a member of the audio group and this was working before the upgrade to feisty.


```
May 01 10:11 : Error opening alsa device "default": Permission denied
May 01 10:11 : problems opening audio device while playing "Esthero - Breath From Another (1998)/03 - Esthero - Anywayz.flac"
ALSA lib confmisc.c:558:(snd_determine_driver) could not open control for card 0
ALSA lib conf.c:2712:(snd_config_hooks_call) function snd_config_hook_load_for_all_cards returned error: Permission denied
ALSA lib confmisc.c:558:(snd_determine_driver) could not open control for card 0
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: Permission denied
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: Permission denied
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: Permission denied
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: Permission denied
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.default
May 01 10:13 : Error opening alsa device "default": Permission denied
May 01 10:13 : problems opening audio device while playing "Esthero - Breath From Another (1998)/11 - Esthero - Swallow Me.flac"
```

---

### Post by gyaresu on 2007-05-23
Still not working. Don't know why. 


*bump*

---

### Post by Klobas on 2007-06-27
same with me.. it looks like broken alsa or something like that. after this error all my sounds are replaced with silence :-/

---

### Post by DiamondX on 2007-07-31
> **Klobas said:**
> same with me.. it looks like broken alsa or something like that. after this error all my sounds are replaced with silence :-/

I get the same error sometimes with rhythmbox. I can fix it by rebooting, but thats irritating. Anyone know how to fix it?

---

### Post by Spookster on 2007-10-19
Apols for reviving this old thread, but I now have the same problem too after upgrading to Gutsy. Sound working fine elsewhere (e.g. mplayer).

Any ideas?

---

### Post by ghandi69_ on 2007-10-30
Same problem here, except I have never used mpd before, so I have never had it working before.

Amarok, VLC, Exhaile, Streamtuner, Xmms, all work fine.

---

