---
title: "Problems with MPD and USB-Soundcard (Audio 2 DJ)"
date: 2014-01-17
forum: Multimedia Software
---

### Post by winfried.moser on 2014-01-17
Dear listers,

mpd is working well with the internal soundcard of  my ThinkPad Edge 13, but not with my external usb-soundcard "Audio 2 DJ"  by "Native Instruments" altough the external usb-soundcard works well  if I play a song with the Standard Software of my operating system  (ubuntu 12.04, Rhythmbox). Ubuntu identifies the external soundcard  without problems.

Using the Audio 2 DJ with mpd results in a  _very_ loud, _very_ distorted noise. Initially I thought, my headphones  are gone (not to mention my ears). By further investigations I found  out, that actually a song IS being played, but so loud and so distorted,  that one can decern just noise. 

If mpc-volume is set to 1  (one!) percent and the hardware-volume-control on my Audio 2 DJ is  raised just very little from zero, the song can be recognized well, but  still slightly distorted, with many clicks and ticks.

I tried to  tamper around with my audio output settings (see below). I tried to  uncomment all the lines, one after another, but no effect.
The only  thing that makes a difference is setting mixer_type to "hardware" - in  this case the situation worsens: just noise, no more song decernable.

audio_output {
type "alsa"
name "USB Soundcard"
device "hw:2,0"
# format "44100:16:2"
mixer_type "software"
# replay_gain_handler "mixer"
# encoding "flac"
# use_mmap "yes"
# auto_resample "yes"
# dsd_usb "yes"
}

My questions:

1. Does someone have any hints about this?
2. Does someone have an idea, in which direction to make further explorations?
3. Are there external DACs known to work well with MPD? (I already thought of buying a new one)

Thank You

Winfried

PS the whole mpd.conf ...

music_directory "/media/Archiv/musik"
playlist_directory "~/.mpd/playlists"
db_file "~/.mpd/tag_cache"
log_file "~/.mpd/mpd.log"
pid_file "~/.mpd/pid"
state_file "~/.mpd/state"
sticker_file "~/.mpd/sticker.sql"
bind_to_address "any"
input {
plugin "curl"
}
audio_output {
type "alsa"
name "My ALSA Device"
device "hw:0,0" # optional
format "44100:16:2" # optional
mixer_type "software"
}

audio_output {
type "alsa"
name "USB Soundcard"
device "hw:2,0"
# format "44100:16:2"
mixer_type "software"
# replay_gain_handler "mixer"
# encoding "flac"
# use_mmap "yes"
# auto_resample "yes"
dsd_usb "yes"
}

audio_output {
type  "httpd"
name  "My HTTP Stream"
encoder  "vorbis"  # optional, vorbis or lame
port  "8000"
# quality  "5.0"   # do not define if bitrate is defined
bitrate  "96"   # do not define if quality is defined, default: 128
format  "44100:16:2"
max_clients "0"   # optional 0=no limit
}

filesystem_charset "UTF-8"
id3v1_encoding "UTF-8"

---

### Post by winfried.moser on 2014-01-25
changing type "alsa" to type "pulse" solved the problem!

---

