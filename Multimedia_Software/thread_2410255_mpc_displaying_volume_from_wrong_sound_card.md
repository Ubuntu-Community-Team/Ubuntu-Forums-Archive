---
title: "mpc displaying volume from wrong sound card"
date: 2019-01-13
forum: Multimedia Software
---

### Post by CatKiller on 2019-01-13
OK, this one's pretty niche, but the solution is probably quite simple, and is the kind of thing that people might have encountered before.

I have a raspberry pi running volumio. It has an IQaudio DAC attached. That is all working perfectly, volume control is good, and so on.

The only issue is that mpc, when run from the command line, displays the volume of the on-board audio rather than the sound card that mpd is actually outputting sound. That, in itself wouldn't be an issue at all, because running mpc from the command line isn't something that one would normally do: there is a really great browser interface for volumio. Except, and this is the really niche bit, that means the conky that I have running on a completely different computer elsewhere in the house displays the incorrect volume.

I'd like to get mpc to pick up the correct mixer device without breaking the mpd config that volumio uses.

```

cat /etc/mpd.conf       
# Volumio MPD Configuration File

# Files and directories #######################################################
music_directory         "/var/lib/mpd/music"
playlist_directory              "/var/lib/mpd/playlists"
db_file                 "/var/lib/mpd/tag_cache"
#log_file                       "/var/log/mpd/mpd.log"
#pid_file                       "/var/run/mpd/pid"
#state_file                     "/var/lib/mpd/state"
#sticker_file                   "/var/lib/mpd/sticker.sql"
###############################################################################

# General music daemon options ################################################
user                            "mpd"
group                          "audio"
bind_to_address         "any"
#port                           "6600"
#log_level                      "default"
gapless_mp3_playback                    "no"
#save_absolute_paths_in_playlists       "no"
#metadata_to_use        "artist,album,title,track,name,genre,date,composer,performer,disc"
auto_update    "yes"
#auto_update_depth "3"
###############################################################################
# Symbolic link behavior ######################################################
follow_outside_symlinks "yes"
follow_inside_symlinks          "yes"
###############################################################################
# Input #######################################################################
#
input {
        plugin "curl"
#       proxy "proxy.isp.com:8080"
#       proxy_user "user"
#       proxy_password "password"
}
###############################################################################

# Decoder ################################################################

 

 

###############################################################################

# Audio Output ################################################################

resampler {      
                plugin "soxr"
                quality "high"
                threads "1"
}

audio_output {
                type            "alsa"
                name            "alsa"
                device          "hw:1,0"
                dop                     "no"



}





audio_output {
    type            "fifo"
    enabled         "no"
    name            "multiroom"
    path            "/tmp/snapfifo"
    format          "44100:16:2"
}

#replaygain                     "album"
#replaygain_preamp              "0"
volume_normalization            "no"
###############################################################################

# MPD Internal Buffering ######################################################
audio_buffer_size               "8192"
buffer_before_play              "10%"
###############################################################################


# Resource Limitations ########################################################
#connection_timeout             "60"
max_connections                 "20"
max_playlist_length             "81920"
max_command_list_size           "81920"
max_output_buffer_size          "81920"
###############################################################################

# Character Encoding ##########################################################
filesystem_charset              "UTF-8"
id3v1_encoding                  "UTF-8"
###############################################################################

```

```

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ALSA [bcm2835 ALSA], device 0: bcm2835 ALSA [bcm2835 ALSA]
  Subdevices: 7/7
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
card 0: ALSA [bcm2835 ALSA], device 1: bcm2835 ALSA [bcm2835 IEC958/HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: IQaudIODAC [IQaudIODAC], device 0: IQaudIO DAC HiFi pcm512x-hifi-0 []
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

---

### Post by CatKiller on 2019-01-15
I added ```
                mixer_device    "hw:1"
                mixer_control   "Digital"
```
to /etc/mpd.conf and mpc (and conky) show the volume of the correct sound card now, without breaking volumio.

---

