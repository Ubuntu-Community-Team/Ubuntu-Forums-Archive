---
title: "Help with mpd and ncmpcpp"
date: 2015-06-07
forum: Multimedia Software
---

### Post by jeff115 on 2015-06-07
Hi,

I'm running Ubuntu 15.04 on a PC with the onboard soundcard and a Xonar DG. I'd like to switch between the two, as I have different speakers attached to each one, in ncmpcpp. Now, I can only see "MPD" as an output and if I try to run a pulse audio applet - pasystray - it says playback streams -> None. 

Firefox, for example, will show in playback streams, so I'm sure this is related to mpd/ncmpcpp. Any ideas what I can look into?
 
my mpd.conf
```

  # Required filesdb_file            "~/.config/mpd/database"
log_file           "~/.config/mpd/log"



user "jeff"
port "6601"
mixer_type "software"


# Optional
music_directory    "/media/Music"
playlist_directory "~/.config/mpd/playlists"
pid_file           "~/.config/mpd/pid"
state_file         "~/.config/mpd/state"
sticker_file       "~/.config/mpd/sticker.sql"

audio_output {
  type    "pulse"
  name    "pulse audio"                                         
  sink    "<alsa_output.pci-0000_00_1b.0.analog-stereo>"
  mixer_control "Master"
  server "localhost"
# server    "remote_server"   # optional
# sink    "remote_server_sink"  # optional
}


audio_output {
  type "pulse"
  name "Pulse HD Audio"
  sink "<alsa_output.pci-0000_09_00.0.analog-stereo>"
  mixer_control "Master"
  server "localhost"
}

```


my ncmpcpp/config:
```

mpd_host                   = "127.0.0.1"
mpd_port                   = "6600"
mpd_music_dir              = "/media/Music"
mpd_crossfade_time         = "1"
visualizer_in_stereo       = "no"
visualizer_fifo_path       = "/tmp/mpd.fifo"
visualizer_output_name     = "my_fifo"
visualizer_sync_interval   = "1"
song_list_format           = "$3{%A }|{%a }$7{%b }$0{%t}| $4$R{%7l}$9"
now_playing_prefix         = "$4"
now_playing_suffix         = "$9"
song_columns_list_format   = "(34)[green]{a} (34)[]{t|f} (32)[cyan]{b}"
playlist_display_mode      = "columns"
browser_display_mode       = "columns"
search_engine_display_mode = "columns"
autocenter_mode            = "yes"
centered_cursor            = "yes"
progressbar_look           = "   "
user_interface             = "alternative"
default_space_mode         = "select"
header_visibility          = "no"
statusbar_visibility       = "no"
titles_visibility           = "no"
follow_now_playing_lyrics    = "yes"
store_lyrics_in_song_dir      = "yes"
screen_switcher_mode           = "sequence: 2 -> 3  -> 9 -> 10"
ignore_leading_the              = "yes"
empty_tag_marker                  = "[empty]"
main_window_color                   = "default"
main_window_highlight_color         = "default"
visualizer_color                    = "default"



```


pacmd sinks (ignore the 1st one, from my video card)
```

$ pacmd list-sinks | grep name
    name: <alsa_output.pci-0000_02_00.1.hdmi-stereo>
        alsa.name = "HDMI 0"
        alsa.subdevice_name = "subdevice #0"
        alsa.card_name = "HDA NVidia"
        alsa.long_card_name = "HDA NVidia at 0xfb080000 irq 18"
        alsa.driver_name = "snd_hda_intel"
        device.vendor.name = "NVIDIA Corporation"
        device.product.name = "GF110 High Definition Audio Controller"
        device.profile.name = "hdmi-stereo"
        alsa.mixer_name = "Nvidia GPU 18 HDMI/DP"
        device.icon_name = "audio-card-pci"
                device.icon_name = "video-display"
    name: <alsa_output.pci-0000_00_1b.0.analog-stereo>
        alsa.name = "ALC892 Analog"
        alsa.subdevice_name = "subdevice #0"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xfb620000 irq 46"
        alsa.driver_name = "snd_hda_intel"
        device.vendor.name = "Intel Corporation"
        device.product.name = "6 Series/C200 Series Chipset Family High Definition Audio Controller"
        device.profile.name = "analog-stereo"
        alsa.mixer_name = "Realtek ALC892"
        device.icon_name = "audio-card-pci"
                device.icon_name = "audio-headphones"
    name: <alsa_output.pci-0000_09_00.0.analog-stereo>
        alsa.name = "Multichannel"
        alsa.subdevice_name = "subdevice #0"
        alsa.card_name = "Xonar DG"
        alsa.long_card_name = "C-Media Oxygen HD Audio at 0xc000, irq 18"
        alsa.driver_name = "snd_oxygen"
        device.vendor.name = "C-Media Electronics Inc"
        device.product.name = "CMI8788 [Oxygen HD Audio] (CMI8786 (Xonar DG))"
        device.profile.name = "analog-stereo"
        alsa.mixer_name = "CMI8786"
        device.icon_name = "audio-card-pci"
                device.icon_name = "audio-headphones"



 

```

I appreciate any help you can give me.

---

### Post by papibe on 2015-06-07
Hi jeff115.

A few thoughts regarding mpd.

I believe the mpd service is initiated by root and then forked using the user named on the config file. With that in mind, I recommend don't using the tilde (~), but the full path instead.

Also make sure user 'jeff' has read permissions to the files at "/media/Music".

If that doesn't make things better, could you post the content of the mpd log right after restarting the service?

Regards.

---

### Post by jeff115 on 2015-06-07
Papibe,

Thanks for the response. I see my music, so its not an access to my music content issue, but a 'how can I get multiple sound cards to work' issue. I'll take your advice and change the tilde, thanks for that.


The stdout from mpd:
```

 $ mpd --no-daemon --stdout --verboseconfig_file: loading file /home/jeff/.config/mpd/mpd.conf
server_socket: bind to '0.0.0.0:6601' failed: Address already in use (continuing anyway, because binding to '[::]:6601' succeeded)
path: SetFSCharset: fs charset is: UTF-8
libsamplerate: libsamplerate converter 'Fastest Sinc Interpolator'
vorbis: Xiph.Org libVorbis 1.3.4
opus: libopus 1.1
sndfile: libsndfile-1.0.25
wildmidi: configuration file does not exist: /etc/timidity/timidity.cfg
adplug: adplug 2.2.1
db: reading DB
curl: version 7.38.0
curl: with GnuTLS/3.3.8
avahi: Initializing interface
avahi: Client changed to state 2
avahi: Client is RUNNING
avahi: Registering service _mpd._tcp/Music Player
avahi: Service group changed to state 0
avahi: Service group is UNCOMMITED
state_file: Loading state file /home/jeff/.config/mpd/state
Failed to load cookie file from cookie: No such file or directory
Failed to load cookie file from cookie: No such file or directory
config: option 'mixer_control' on line 31 was not recognized
avahi: Service group changed to state 1
avahi: Service group is REGISTERING
decoder_thread: probing plugin mad
mad: detected LAME version 3.97 ("LAME3.97 ")
mad: LAME peak found: 0.000000
mad: encoder delay is 576, encoder padding is 1320
decoder: audio_format=44100:24:2, seekable=true
avahi: Service group changed to state 2
avahi: Service 'Music Player' successfully established.

```


the log at ~/.config/mpd/log is empty, which seems weird, although I did start mpd with --stdout.

---

