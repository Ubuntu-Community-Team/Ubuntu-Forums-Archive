---
title: "AMD64 / Flash10 / Digital Ouput / 2 sounds cards"
date: 2009-08-21
forum: Multimedia Software
---

### Post by Iced on 2009-08-21
I know there's a million threads on this, but I am at a roadblock and can't figure this one out.  It's quite frustrating, 

I'm running:
```
Linux box-ubuntu 2.6.28-15-server #49-Ubuntu SMP Tue Aug 18 20:09:37 UTC 2009 x86_64 GNU/Linux
```

My sound card connects to my A/V receiver via optical cable.

Sound works for the most part through PulseAudio (Version 0.9.15)

I can watch videos in YouTube
I can listen to MP3's in RhythmBox (DTS sound files also work, "DTS lights up on receiver")
System -> Preferences -> Sound, I can hear all "Test"s, all sample sounds I can hear.

All of the above applications show up in PulseAudio's Volume Control under the Playback tab just fine.

The only way YouTube would playback was with the following ~/.asoundrc

```
# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/chris/.asoundrc.asoundconf>

# Required for AMD64/Flash10
pcm.!dmix {
  type pulse
}

#pcm.!default {
#  type hw
#  card 1
#  device 1
#}
```

VLC will not do AC3 passthrough with the above configuration and I'm stuck without sound for movies I have.

Uncomment the pcm.!default entry{} and VLC works with AC3 passthrough and "*all the DTS etc, lights*" show up and I have the proper digital 5.1 surround sound through my receiver.

However, the downside is, YouTube no longer has sound, I cannot hear any of 'sample sounds' nor do any show up in PulseAudio volume manager.  Sound 'tests' work for some reason.

Anyone have a fix/workaround for this?  :confused:

(need me to post more info, configuration, please let me know)

---

### Post by Iced on 2009-08-21
I figured out that if I leave my ~/.asoundrc file as:

```

# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/chris/.asoundrc.asoundconf>

# Required for AMD64/Flash10
pcm.!dmix {
  type pulse
}
```

And I kill firefox, then start up VLC with the following it seems to be ok.  I just *can't have both running at the same time* which is more of an annoyance than anything.  I am also unable to hear movies without an AC3 track????
```

vlc --spdif --alsadev iec958:CARD=AV710,DEV=0

```

---

### Post by markbuntu on 2009-08-21
Well, I never had to edit my asoundrc to get flash10 working on amd64.

Set your sound up like this

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

Then do this

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Sometimes I need to reinstall flash after an update but that is about it. 

Some day the flash devs may stop trying to use deprecated output protocols but at least ubuntu has the libs necessary to deal with apps that call them. You need to get them yourself since they are not included by default but that is another issue entirely.

---

### Post by Iced on 2009-08-21
Hi markbuntu, 

Thanks for the information.  I had done the first link which is why I was able to get Flash10 sound working in Firefox.  There is a section on that page describing having to add the entry to ~/.asoundrc : **"Flash 10 on 64 bit"** and it's the only way Flash10 will work on my system with sound (video is not a problem).

I can get each application to work with sound to some degree but I have a lot of fiddling to do with configuration and careful not to run Firefox and VLC at the same time.  The additional problem is I can only play video in VLC with DTS/AC3... movies without I cannot hear.

I took a scan through the second link but I haven't read it thoroughly (I searched for digital/optical/spdif/ac3 in that thread and didn't find anything) I'll have a closer look.

---

### Post by markbuntu on 2009-08-22
Well, I used that second link to get flash10.0.r32 which I am using right now on my 64 bit system and I have no ~/.asoundrc file at all.

I have not updated that first link in a while so maybe I should remove that line since that problem seems to be fixed.

vlc has a lot of settings so you can really mess it up pretty easily. vlc uses the xine engine which you can control directly with ui-xine. It may have more options for you and multiply the confusion. Have you tried setting the Enable internal upmixng option in the Input/Codecs/Audio codecs/ A/52 settings?

With pulse0.9.15 you should be able to direct the vlc output to the digital ouput sink in the pa volume control. I am not sure but pulse should not do any resampling but connect vlc directly to the digital ouput. Have you tried that?

If vlc is bypassing pulse then vlc and flash or anything else playing through pulse will be mututally exclusive.

---

### Post by Iced on 2009-08-24
Hi markbuntu, thanks again for the reply!

You're right, I removed the extra configuration from ~/.asoundrc and I can still get sound from Flash10 (AMD64) in Firefox as well as as everything else (Sound Panel tests, Rhythmbox, Totem Movie Player).  RhythmBox even plays files with DTS and passes the encoded stream to my A/V receiver.  I think in my testing, I should have closed all applications first before retrying(!).  However, like you say, this probably only boils down to a VLC configuration issue now.  I cannot get VLC to pass the encoded DTS stream in movies HOWEVER there is sound but it must be passing an already decoded stream.  

> Have you tried setting the Enable internal upmixng option in the Input/Codecs/Audio codecs/ A/52 settings?
yes, but unfortunately still no go :(

> With pulse0.9.15 you should be able to direct the vlc output to the digital ouput sink in the pa volume control. I am not sure but pulse should not do any resampling but connect vlc directly to the digital ouput. Have you tried that?

I only have digital output on my PC.  I think PA is working, and like u say, I think it's just a VLC configuration problem now.  VLC shows up in PA Volume Control and there is sound, i just think the DTS audio is already decoded within VLC (no "DTS" lights on my A/V receiver).  "DTS" lights show up in Rhythmbox/Totem Movie Player for .wav audio files with DTS encoded tracks but not in VLC (but there is sound).  .flac files also come through fine in Totem but as static/white noise in VLC.

I'll see if I can dig through the 'vlc --advanced -H'

---

### Post by markbuntu on 2009-08-24
Good luck with that and please let us know what you figure out.

---

### Post by Iced on 2009-08-25
i cry 'uncle' haha..  This is painful... :-/  Tried everything I can think of... redid everything in the 2 links u mentioned after first 'removing completely'.  First link put me in the same state.  2nd link broke sound in flash.  I'm going to have to revert to my old configuration with the ~/.asoundrc change and only have VLC or Firefox open.  Unfortunately, getting sound to work has been far from trivial.    If I ever do come across a solution I'll be sure to post.

---

### Post by Iced on 2009-08-27
After messing around with the numerous amount of VLC options, I've come down to the following I just wanted to share so far:

This command-line shows it not working through pulse (--aout pulse),  I end up with downmixed 2-channel audio thru spdif

[FONT="Courier New"]**vlc --spdif --aout pulse --audio-filter a52tospdif --verbose-objects=+"audio output",-all -vvv /tmp/movie.mkv**[/FONT]

```
chris@box-ubuntu:~$ vlc --spdif --aout pulse --audio-filter a52tospdif --verbose-objects=+"audio output",-all -vvv /tmp/movie.mkv
VLC media player 1.0.1 Goldeneye
[0x1e75888] main libvlc debug: VLC media player - version 1.0.1 Goldeneye - (c) 1996-2009 the VideoLAN team
[0x1e75888] main libvlc debug: libvlc was configured with ./configure  '--build=x86_64-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--config-cache' '--enable-fast-install' '--with-binary-version=1~ppa4' '--disable-update-check' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--enable-dvb' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--enable-flac' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-mod' '--enable-theora' '--enable-dvdnav' '--enable-gnutls' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-dca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[0x1e75888] main libvlc debug: translation test: code is "C"
[0x1e75888] main libvlc debug: checking plugin modules
[0x1e75888] main libvlc debug: loading plugins cache file /home/chris/.cache/vlc/plugins-04081e.dat
[0x1e75888] main libvlc debug: recursively browsing `/usr/lib/vlc'
[0x1e75888] main libvlc debug: module bank initialized (382 modules)
[0x1e75888] main libvlc debug: opening config file (/home/chris/.config/vlc/vlcrc)
 m_el[mi_level] == NULL
 arrrrrrrrrrrrrg Up cannot escape itself
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[0x7fa78402ea88] main audio output debug: looking for audio output module: 4 candidates
[0x7fa78402ea88] pulse audio output: No. of Audio Channels: 6
[0x7fa78402ea88] pulse audio output debug: Pulse mainloop started
[0x7fa78402ea88] pulse audio output debug: Pulse stream connected
[0x7fa78402ea88] pulse audio output debug: Pulse initialized successfully
[0x7fa78402ea88] pulse audio output debug: Buffer metrics: maxlength=460800, tlength=138240, prebuf=115200, minreq=23040
[0x7fa78402ea88] pulse audio output debug: Using sample spec 'float32le 6ch 48000Hz', channel map 'front-left,front-right,rear-left,rear-right,front-center,lfe'.
[0x7fa78402ea88] pulse audio output debug: Connected to device alsa_output.pci_1412_1724_sound_card_0 (0, not suspended).
[0x7fa78402ea88] main audio output debug: using audio output module "pulse"
[0x7fa78402ea88] main audio output debug: TIMER module_need() : 49.107 ms - Total 49.107 ms / 1 intvls (Avg 49.107 ms)
[0x7fa78402ea88] main audio output debug: output 'fl32' 48000 Hz 3F2R/LFE frame=1 samples/24 bytes
[0x7fa78402ea88] main audio output debug: mixer 'fl32' 48000 Hz 3F2R/LFE frame=1 samples/24 bytes
[0x7fa78402ea88] main audio output debug: no need for any filter
[0x7fa78402ea88] main audio output debug: looking for audio mixer module: 3 candidates
[0x7fa78402ea88] main audio output debug: using audio mixer module "float32_mixer"
[0x7fa78402ea88] main audio output debug: TIMER module_need() : 0.584 ms - Total 0.584 ms / 1 intvls (Avg 0.584 ms)
[0x7fa78402ea88] main audio output debug: input 'a52 ' 48000 Hz 3F2R/LFE frame=1536 samples/2560 bytes
[0x7fa78402ea88] main audio output debug: filter(s) 'a52 '->'fl32' 48000 Hz->48000 Hz 3F2R/LFE->3F2R/LFE
[0x3875588] main audio output debug: looking for audio filter module: 24 candidates
[0x3875588] main audio output debug: using audio filter module "a52tofloat32"
[0x3875588] main audio output debug: TIMER module_need() : 1.873 ms - Total 1.873 ms / 1 intvls (Avg 1.873 ms)
[0x7fa78402ea88] main audio output debug: found a filter for the whole conversion
[0x7fa78402ea88] main audio output error: cannot add user filter a52tospdif (skipped)
[0x7fa78402ea88] main audio output debug: filter(s) 'fl32'->'fl32' 52800 Hz->48000 Hz 3F2R/LFE->3F2R/LFE
[0x3877a28] main audio output debug: looking for audio filter module: 24 candidates
[0x3877a28] main audio output debug: using audio filter module "bandlimited_resampler"
[0x3877a28] main audio output debug: TIMER module_need() : 1.026 ms - Total 1.026 ms / 1 intvls (Avg 1.026 ms)
[0x7fa78402ea88] main audio output debug: found a filter for the whole conversion
[0x7fa78402ea88] pulse audio output debug: Pulse stream started
[0x7fa78402ea88] main audio output warning: output date isn't PTS date, requesting resampling (123597)
[0x7fa78402ea88] main audio output warning: audio drift is too big (123597), dropping buffer
[0x7fa78402ea88] main audio output warning: buffer is 91597 late, triggering upsampling
[0x7fa78402ea88] main audio output warning: output date isn't PTS date, requesting resampling (70847)
[0x7fa78402ea88] main audio output warning: audio drift is too big (162256), dropping buffer
[0x7fa78402ea88] main audio output warning: audio drift is too big (130256), dropping buffer
[0x7fa78402ea88] main audio output warning: output date isn't PTS date, requesting resampling (62028)
[0x7fa78402ea88] main audio output warning: audio drift is too big (160263), dropping buffer
[0x7fa78402ea88] main audio output warning: audio drift is too big (128263), dropping buffer
[0x7fa78402ea88] main audio output warning: output date isn't PTS date, requesting resampling (62642)
[0x7fa78402ea88] main audio output warning: audio drift is too big (158905), dropping buffer
[0x7fa78402ea88] main audio output warning: audio drift is too big (126905), dropping buffer
[0x7fa78402ea88] main audio output debug: audio output is starving (25142), playing silence
[0x7fa78402ea88] main audio output debug: audio output is starving (25771), playing silence
[0x7fa78402ea88] main audio output debug: audio output is starving (20713), playing silence
[0x7fa78402ea88] main audio output debug: audio output is starving (22006), playing silence
[0x7fa78402ea88] main audio output debug: audio output is starving (21788), playing silence
[0x7fa78402ea88] main audio output debug: audio output is starving (25102), playing silence
[0x7fa78402ea88] main audio output debug: audio output is starving (20072), playing silence
[0x7fa78402ea88] main audio output debug: audio output is starving (23806), playing silence
[0x7fa78402ea88] main audio output debug: audio output is starving (23672), playing silence
[0x7fa78402ea88] main audio output debug: audio output is starving (23897), playing silence
[0x7fa78402ea88] main audio output debug: audio output is starving (23327), playing silence
[0x7fa78402ea88] main audio output debug: audio output is starving (20803), playing silence
[0x7fa78402ea88] main audio output debug: audio output is starving (22253), playing silence
[0x3875588] main audio output debug: removing module "a52tofloat32"
[0x3877a28] main audio output debug: removing module "bandlimited_resampler"
[0x7fa78402ea88] pulse audio output debug: Pulse Close
[0x7fa78402ea88] main audio output debug: removing module "pulse"
[0x7fa78402ea88] main audio output debug: removing module "float32_mixer"
chris@box-ubuntu:~$ 

```

This command-line shows it working through alsa (--aout alsa),  I end up passing through spdif the raw audio stream to A/V receiver for 5.1-channel DTS audio (yay lights!)

[FONT="Courier New"]**vlc --spdif --aout alsa --audio-filter a52tospdif --verbose-objects=+"audio output",-all -vvv /tmp/movie.mkv**[/FONT]

```
chris@box-ubuntu:~$ vlc --spdif --aout alsa --audio-filter a52tospdif --verbose-objects=+"audio output",-all -vvv /tmp/movie.mkv
VLC media player 1.0.1 Goldeneye
[0x1904888] main libvlc debug: VLC media player - version 1.0.1 Goldeneye - (c) 1996-2009 the VideoLAN team
[0x1904888] main libvlc debug: libvlc was configured with ./configure  '--build=x86_64-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--config-cache' '--enable-fast-install' '--with-binary-version=1~ppa4' '--disable-update-check' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--enable-dvb' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--enable-flac' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-mod' '--enable-theora' '--enable-dvdnav' '--enable-gnutls' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-dca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[0x1904888] main libvlc debug: translation test: code is "C"
[0x1904888] main libvlc debug: checking plugin modules
[0x1904888] main libvlc debug: loading plugins cache file /home/chris/.cache/vlc/plugins-04081e.dat
[0x1904888] main libvlc debug: recursively browsing `/usr/lib/vlc'
[0x1904888] main libvlc debug: module bank initialized (382 modules)
[0x1904888] main libvlc debug: opening config file (/home/chris/.config/vlc/vlcrc)
 m_el[mi_level] == NULL
 arrrrrrrrrrrrrg Up cannot escape itself
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[0x2a1bbb8] main audio output debug: looking for audio output module: 4 candidates
[0x2a1bbb8] main audio output debug: thread started
[0x2a1bbb8] main audio output debug: thread (aout) created at priority 15 (alsa.c:687)
[0x2a1bbb8] main audio output debug: using audio output module "alsa"
[0x2a1bbb8] main audio output debug: TIMER module_need() : 16.722 ms - Total 16.722 ms / 1 intvls (Avg 16.722 ms)
[0x2a1bbb8] main audio output debug: output 'spdi' 48000 Hz 3F2R/LFE frame=1536 samples/6144 bytes
[0x2a1bbb8] main audio output debug: mixer 'a52 ' 48000 Hz 3F2R/LFE frame=1536 samples/6144 bytes
[0x2a1bbb8] main audio output debug: filter(s) 'a52 '->'spdi' 48000 Hz->48000 Hz 3F2R/LFE->3F2R/LFE
[0x2a37428] main audio output debug: looking for audio filter module: 24 candidates
[0x2a37428] main audio output debug: using audio filter module "a52tospdif"
[0x2a37428] main audio output debug: TIMER module_need() : 4.341 ms - Total 4.341 ms / 1 intvls (Avg 4.341 ms)
[0x2a1bbb8] main audio output debug: found a filter for the whole conversion
[0x2a1bbb8] main audio output debug: looking for audio mixer module: 3 candidates
[0x2a1bbb8] main audio output debug: using audio mixer module "spdif_mixer"
[0x2a1bbb8] main audio output debug: TIMER module_need() : 0.668 ms - Total 0.668 ms / 1 intvls (Avg 0.668 ms)
[0x2a1bbb8] main audio output debug: input 'a52 ' 48000 Hz 3F2R/LFE frame=1536 samples/2560 bytes
[0x2a1bbb8] main audio output debug: thread ended
[0x2a1bbb8] main audio output debug: removing module "alsa"
[0x2a37428] main audio output debug: removing module "a52tospdif"
[0x2a1bbb8] main audio output debug: removing module "spdif_mixer"
```

I'm still working on whether I can get this working through pulse.  Hopefully my next post is a successful one.

---

