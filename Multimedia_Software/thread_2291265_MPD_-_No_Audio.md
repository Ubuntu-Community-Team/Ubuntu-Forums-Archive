---
title: "MPD - No Audio"
date: 2015-08-18
forum: Multimedia Software
---

### Post by sniper8752 on 2015-08-18
[COLOR=#333333][FONT=Helvetica Neue]I setup MPD, and I get no audio playing. Here is some of my troubleshooting that I've done already:

[/FONT][/COLOR]```
mpd --stdout --no-daemon --verbosepath: path_set_fs_charset: fs charset is: UTF-8
output: No "audio_output" defined in config file
output: Attempt to detect audio output device
output: Attempting to detect a alsa audio device
output: Successfully detected a alsa audio device
disabling the last.fm playlist plugin because account is not configured
avahi: Initializing interface
avahi: Client changed to state 2
avahi: Client is RUNNING
avahi: Registering service _mpd._tcp/Music Player
avahi: Service group changed to state 0
avahi: Service group is UNCOMMITED
avahi: Service group changed to state 1
avahi: Service group is REGISTERING
avahi: Service group changed to state 2
avahi: Service 'Music Player' successfully established.
client: [0] opened from 192.168.1.2:49308
client: [0] process command "commands"
client: [0] command returned 0
client: [1] opened from 192.168.1.2:47016
client: [1] process command "commands"
client: [1] command returned 0
client: [0] process command "list "albumartist""
client: [0] command returned -1
client: [0] closed
client: [2] opened from 192.168.1.2:47726
client: [2] process command "list "albumartist""
client: [2] command returned -1
client: [2] closed
client: [3] opened from 192.168.1.2:58328
client: [3] process command "list "albumartist""
client: [3] command returned -1
client: [3] closed
client: [4] opened from 192.168.1.2:33778
client: [4] process command "stats"
client: [4] command returned 0
client: [4] process command "list "album""
client: [4] command returned -1
client: [4] closed
client: [5] opened from 192.168.1.2:55986
client: [5] process command "list "album""
client: [5] command returned -1
client: [5] closed
client: [6] opened from 192.168.1.2:44872
client: [6] process command "list "album""
client: [6] command returned -1
client: [6] closed
client: [7] opened from 192.168.1.2:60253
client: [7] process command "status"
client: [7] command returned 0
client: [7] process command "plchanges "2""
client: [7] command returned 0
client: [7] process command "playlistid"
client: [7] command returned 0
client: [1] process command "idle "database" "mixer" "options" "output" "player" "playlist" "sticker" "update""
client: [1] command returned 1
client: [8] opened from 192.168.1.2:44152
client: [8] process command "play"
client: [8] command returned 0
client: [7] closed
client: [1] closed
client: [8] closed
client: [9] opened from 192.168.1.2:40919
client: [9] process command "commands"
client: [9] command returned 0
client: [10] opened from 192.168.1.2:41359
client: [10] process command "commands"
client: [10] command returned 0
client: [9] process command "list "albumartist""
client: [9] command returned -1
client: [9] closed
client: [11] opened from 192.168.1.2:41000
client: [11] process command "list "albumartist""
client: [11] command returned -1
client: [11] closed
client: [12] opened from 192.168.1.2:33478
client: [12] process command "list "albumartist""
client: [12] command returned -1
client: [12] closed
client: [13] opened from 192.168.1.2:38200
client: [13] process command "stats"
client: [13] command returned 0
client: [13] process command "list "album""
client: [13] command returned -1
client: [13] closed
client: [14] opened from 192.168.1.2:59098
client: [14] process command "list "album""
client: [14] command returned -1
client: [14] closed
client: [15] opened from 192.168.1.2:46730
client: [15] process command "list "album""
client: [15] command returned -1
client: [15] closed
client: [16] opened from 192.168.1.2:58544
client: [16] process command "status"
client: [16] command returned 0
client: [16] process command "playlistid"
client: [16] command returned 0
client: [16] process command "playlistid"
client: [16] command returned 0
client: [10] process command "idle "database" "mixer" "options" "output" "player" "playlist" "sticker" "update""
client: [10] command returned 1
^Cavahi: Shutting down interface
client: [16] closed
client: [10] closed
listen: listen_global_finish called
db_finish took 0.000000 seconds
```

---

### Post by tgalati4 on 2015-08-18
Open a terminal on the computer that is running *mpd*.  Post the output of:

```
aplay -l
```

---

### Post by shantiq on 2015-08-19
maybe also to look at

```
sudo gedit /etc/mpd.conf
```

see what choices you have made for audio

run Ctrl+F and enter "Audio Output"

see what configuration has been picked so far; and modify it 
[i am saying this as you have this line in YOUR terminal output >>> [FONT=comic sans ms]output: No "audio_output" defined in config file [/FONT]  ]
YOU may need to uncomment [remove the # signs as where the red writing is in mine]
or scroll down and pick Pulse in same way if you so desire
OR    do same to LastFM plugin if it appears there

looks like this:

```
###############################################################################

# Audio Output ################################################################
#
# MPD supports various audio output types, as well as playing through multiple 
# audio outputs at the same time, through multiple audio_output settings 
# blocks. Setting this block is optional, though the server will only attempt
# autodetection for one sound card.
#
# An example of an ALSA output:
#
[B][COLOR=#800000]audio_output {
    type        "alsa"
    name        "My ALSA Device"[/COLOR][/B]
#    device        "hw:0,0"    # optional
#    mixer_type      "hardware"      # optional
#    mixer_device    "default"    # optional
#    mixer_control    "PCM"        # optional
#    mixer_index    "0"        # optional
}
#
# An example of an OSS output:
#
#audio_output {
#    type        "oss"
#    name        "My OSS Device"
#    device        "/dev/dsp"    # optional
#    mixer_type      "hardware"      # optional
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
#    url             "http://example.com"    # optional
#    genre        "jazz"            # optional
#    public        "no"            # optional
#    timeout        "2"            # optional
#    mixer_type      "software"              # optional
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
#    bind_to_address "0.0.0.0"               # optional, IPv4 or IPv6
#    quality        "5.0"            # do not define if bitrate is defined
#    bitrate        "128"            # do not define if quality is defined
#    format        "44100:16:1"
#    max_clients     "0"                     # optional 0=no limit
#}
#
# An example of a pulseaudio output (streaming to a remote pulseaudio server)
# Please see README.Debian if you want mpd to play through the pulseaudio
# daemon started as part of your graphical desktop session!
#
#audio_output {
#    type        "pulse"
#    name        "My Pulse Output"
#    server        "remote_server"        # optional
#    sink        "remote_server_sink"    # optional
#}
#
# An example of a winmm output (Windows multimedia API).
#
#audio_output {
#    type        "winmm"
#    name        "My WinMM output"
#    device        "Digital Audio (S/PDIF) (High Definition Audio Device)" # optional
#        or
#    device        "0"        # optional
#    mixer_type    "hardware"    # optional
#}
#
# An example of an openal output.
#
#audio_output {
#    type        "openal"
#    name        "My OpenAL output"
#    device        "Digital Audio (S/PDIF) (High Definition Audio Device)" # optional
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
#    mixer_type      "none"                  # optional
#}
#
# If MPD has been compiled with libsamplerate support, this setting specifies 
# the sample rate converter to use.  Possible values can be found in the 
# mpd.conf man page or the libsamplerate documentation. By default, this is
# setting is disabled.
#
#samplerate_converter        "Fastest Sinc Interpolator"
#
###############################################################################
```

---

### Post by sniper8752 on 2015-08-19
> **tgalati4 said:**
> Open a terminal on the computer that is running *mpd*.  Post the output of:

```
aplay -l
```

```


**** List of PLAYBACK Hardware Devices ****
card 0: ALSA [bcm2835 ALSA], device 0: bcm2835 ALSA [bcm2835 ALSA]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: ALSA [bcm2835 ALSA], device 1: bcm2835 ALSA [bcm2835 IEC958/HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by sniper8752 on 2015-08-19
> **shantiq said:**
> maybe also to look at

```
sudo gedit /etc/mpd.conf
```

see what choices you have made for audio

run Ctrl+F and enter "Audio Output"

see what configuration has been picked so far; and modify it 
[i am saying this as you have this line in YOUR terminal output >>> [FONT=comic sans ms]output: No "audio_output" defined in config file [/FONT]  ]
YOU may need to uncomment [remove the # signs as where the red writing is in mine]
or scroll down and pick Pulse in same way if you so desire
OR    do same to LastFM plugin if it appears there

looks like this:

```
###############################################################################

# Audio Output ################################################################
#
# MPD supports various audio output types, as well as playing through multiple 
# audio outputs at the same time, through multiple audio_output settings 
# blocks. Setting this block is optional, though the server will only attempt
# autodetection for one sound card.
#
# An example of an ALSA output:
#
[B][COLOR=#800000]audio_output {
    type        "alsa"
    name        "My ALSA Device"[/COLOR][/B]
#    device        "hw:0,0"    # optional
#    mixer_type      "hardware"      # optional
#    mixer_device    "default"    # optional
#    mixer_control    "PCM"        # optional
#    mixer_index    "0"        # optional
}
#
# An example of an OSS output:
#
#audio_output {
#    type        "oss"
#    name        "My OSS Device"
#    device        "/dev/dsp"    # optional
#    mixer_type      "hardware"      # optional
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
#    url             "http://example.com"    # optional
#    genre        "jazz"            # optional
#    public        "no"            # optional
#    timeout        "2"            # optional
#    mixer_type      "software"              # optional
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
#    bind_to_address "0.0.0.0"               # optional, IPv4 or IPv6
#    quality        "5.0"            # do not define if bitrate is defined
#    bitrate        "128"            # do not define if quality is defined
#    format        "44100:16:1"
#    max_clients     "0"                     # optional 0=no limit
#}
#
# An example of a pulseaudio output (streaming to a remote pulseaudio server)
# Please see README.Debian if you want mpd to play through the pulseaudio
# daemon started as part of your graphical desktop session!
#
#audio_output {
#    type        "pulse"
#    name        "My Pulse Output"
#    server        "remote_server"        # optional
#    sink        "remote_server_sink"    # optional
#}
#
# An example of a winmm output (Windows multimedia API).
#
#audio_output {
#    type        "winmm"
#    name        "My WinMM output"
#    device        "Digital Audio (S/PDIF) (High Definition Audio Device)" # optional
#        or
#    device        "0"        # optional
#    mixer_type    "hardware"    # optional
#}
#
# An example of an openal output.
#
#audio_output {
#    type        "openal"
#    name        "My OpenAL output"
#    device        "Digital Audio (S/PDIF) (High Definition Audio Device)" # optional
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
#    mixer_type      "none"                  # optional
#}
#
# If MPD has been compiled with libsamplerate support, this setting specifies 
# the sample rate converter to use.  Possible values can be found in the 
# mpd.conf man page or the libsamplerate documentation. By default, this is
# setting is disabled.
#
#samplerate_converter        "Fastest Sinc Interpolator"
#
###############################################################################
```

Here is what I have:

```
audio_output {        type            "alsa"
        name            "My ALSA Device"
        device          "hw:0,0"        # optional
        format          "44100:16:2"    # optional
        mixer_device    "default"       # optional
        mixer_control   "PCM"           # optional
        mixer_index     "0"             # optional
}



```

---

### Post by tgalati4 on 2015-08-19
Try 48000.  Many sound cards use 48kHz as the default decoding rate.  Which device do you want the sound to come out?  Analog or HDMI/SPDIF/Digital?  You have 2 output sound devices.

Open a terminal and check the settings in:

```
alsamixer
```

---

### Post by shantiq on 2015-08-19
yes maybe 48000 instead of 44100

Or   maybe ; I see **I do not have that Format line** in my conf ;  you could also place # [comment it] before that line to render it useless   or even remove it it may not be required

Try 48000 as suggested by Tgalati first see if that flies then try comment/remove  line   see which works :]

---

### Post by sniper8752 on 2015-08-19
> **tgalati4 said:**
> Try 48000.  Many sound cards use 48kHz as the default decoding rate.  Which device do you want the sound to come out?  Analog or HDMI/SPDIF/Digital?  You have 2 output sound devices.

Open a terminal and check the settings in:

```
alsamixer
```

This still doesn't work.  My two options are default and bcm2835 ALSA.
I would like it to come out of the headphone jack.

---

### Post by tgalati4 on 2015-08-19
Disconnect the HDMI cable. Reboot.  Some sound cards won't put out sound to both analog and digital at the same time.  Others will do both, but you need the correct sound configuration file.

---

### Post by sniper8752 on 2015-08-20
I don't have an HDMI currently tied into it.  I am using SSH.

---

### Post by tgalati4 on 2015-08-20
Install *mplayer2* on the machine that runs *mpd* and play some tracks.  Pay attention to the terminal output for errors.

```
sudo apt-get install mplayer2
mplayer anymusictrack.mp3
```

What audio modules do you have loaded?

```
lsmod | grep snd
```

---

### Post by sniper8752 on 2015-08-28
It does not play anything.

```
snd_bcm2835            21149  1snd_pcm                90778  1 snd_bcm2835
snd_seq                61097  0
snd_seq_device          7209  1 snd_seq
snd_timer              23007  2 snd_pcm,snd_seq
snd                    66325  7 snd_bcm2835,snd_timer,snd_pcm,snd_seq,snd_seq_device



```

---

### Post by tgalati4 on 2015-08-28
You won't get sound through *ssh*.  You need an *mpd* client to control *mpd* remotely.  Then sound will play only on the computer that is running *mpd*.  Did you plug in your headphones into the audio jack of the computer running *mpd*?  Do not use *ssh* to troubleshoot sound issues.

---

### Post by shantiq on 2015-08-29
maybe read[ this]("http://ubuntuforums.org/showthread.php?t=2287569&p=13324508#post13324508") sniper;   this works as Tg says you need a client with mpd

---

### Post by sniper8752 on 2015-08-29
I do have a speaker setup to the headphone jack, but I don't hear anything coming out of it.

---

### Post by tgalati4 on 2015-08-29
Is this a RaspberryPi?  When I search on bmc2835 I came up with a few fixes.

[https://jeffskinnerbox.wordpress.com/2012/11/15/getting-audio-out-working-on-the-raspberry-pi/](https://jeffskinnerbox.wordpress.com/2012/11/15/getting-audio-out-working-on-the-raspberry-pi/)

---

### Post by sniper8752 on 2015-08-29
Yes.  When I use [COLOR=black][FONT=Courier]omxplayer, there is audio.  So I don't think it's a driver issue.  I think it has to do with the software.[/FONT][/COLOR]

---

### Post by tgalati4 on 2015-08-30
The RaspberryPi is an ARM processor not an Intel/x86 processor, so linux that runs on it is slightly different.  Things like graphics and audio require tweaks to make them work.  *omxplayer* is compiled specifically for the RaspberryPi, so it works with the hardware correctly.

Searching on "mpd raspberry pi" comes up with a lot of hits.  Pick a tutorial and follow it carefully.  This problem can't be fixed with standard PC linux procedures.

[http://lesbonscomptes.com/pages/raspmpd.html](http://lesbonscomptes.com/pages/raspmpd.html)

[http://hempeldesigngroup.com/embedded/stories/raspberry-pi-setup-as-mpd-sever/](http://hempeldesigngroup.com/embedded/stories/raspberry-pi-setup-as-mpd-sever/)

[https://dbader.org/blog/crackle-free-audio-on-the-raspberry-pi-with-mpd-and-pulseaudio](https://dbader.org/blog/crackle-free-audio-on-the-raspberry-pi-with-mpd-and-pulseaudio)

The last link suggests using *pulseaudio* and updating the firmware on the Pi to get a working sound system.

---

