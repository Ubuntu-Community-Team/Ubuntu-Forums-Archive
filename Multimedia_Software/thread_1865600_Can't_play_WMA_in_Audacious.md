---
title: "Can't play WMA in Audacious"
date: 2011-10-20
forum: Multimedia Software
---

### Post by mjwiech on 2011-10-20
Running Ubuntu 11.10 on Asus EEE PC 900.

Can't play Windows Media Audio (WMA) files in Audacious though the documentation states it is possible.
I have the plugins package installed. Besides, I found wma.so from Fedora and placed it together with other plugins. However, Audadocious does not see it.

Any help will be appreciated.
Regards
mjwiech

---

### Post by mjwiech on 2011-10-22
No clues?

---

### Post by andrew.46 on 2011-10-22
There are several different [types of wma files]("http://en.wikipedia.org/wiki/Windows_Media_Audio#Codecs") and I believe that audacious will not play them all. Can you post one of the troublesome files somewhere?

---

### Post by mc4man on 2011-10-22
ffaudio.so does not seem to be in 11.10's audacious-plugins
(/usr/lib/audacious/Input/ffaudio.so

So you'd need to build a new audacious & plugins or easier -  add this ppa, upgrade your audacious packages, then possibly disable the ppa (has a lot of packages, your choice there
[https://launchpad.net/~nilarimogard/+archive/webupd8](https://launchpad.net/~nilarimogard/+archive/webupd8)

The best way to add a ppa is thru terminal, to disable use software sources (software-properties-gtk

```
sudo add-apt-repository ppa:nilarimogard/webupd8
```

screen shows aud (3.X) playing a wma3(pro) file

Edit: wmal will not play in aud, only in mplayer:amarok w/  xine backend:totem-xine & occasionally on a self built vlc on 32 bit /w32codecs, at least till ffmpeg supports wmal

---

### Post by andrew.46 on 2011-10-22
> **mc4man said:**
> So you'd need to build a new audacious & plugins [...]

I was travelling down that path, recompiling the plugins on my 'other' distro :). Painfully enough the audacious plugins will not compile against the git FFmpeg and while I found a [patch for release 8 of FFmpeg]("http://git.atheme.org/audacious-plugins/patch/?id=4b1623bc9f124d95f0b44661ef317ab327b36634") this did not apply cleanly and I was not keen to spend too much more time with it. The plugins did not like 0.7.6 either so I eventually compiled against a local copy of 0.6.3 and ffaudio then built.

Nice to use a more recent FFmpeg but this is an old problem with FFmpeg changing the goal-posts so often. SoX has same problem with newer FFmpeg...

**Edit:** Hmmm.... I see version 3 is out as mc4man has mentioned, I will upgrade and see if this solves the FFmpeg problem.... except the audacious site is broken atm?

---

### Post by mc4man on 2011-10-22
Andrew - it seems pretty straightfoward to build on 11.10 though I think this is on one those cases where a ppa is selectively useful

Ex. on 11.10, new libmowgli (0.9.5), 3.0.3 source
                          
>    
  Output Plugins
  --------------
  Open Sound System (oss):                yes
  Open Sound System v4 (oss4):            no
  Advanced Linux Sound Arch. (alsa):      yes
  PulseAudio (pulse):                     yes
  RoarAudio (roaraudio):                  no
  Jack Audio Connection Kit (jack):       yes
  Mac OS X sound support (CoreAudio):     no
  Simple DirectMedia Layer (sdlout):      yes
  FileWriter:                             yes
    -> FileWriter MP3 output part:        yes
    -> FileWriter Vorbis output part:     yes
    -> FileWriter FLAC output part:       yes
  Null Audio output (null):               yes
  Windows waveOut (experimental):         no
  OpenAL (experimental):                  no

  Input Plugins
  -------------
  MPEG-1 Layer I/II/III (mpg123):         yes
  MPEG-2/4 AAC (aac):                     yes
  FFaudio (ffaudio):                      yes
  Module decoder (modplug):               yes
  MIDI modular plugin (amidi-plug):       yes
    -> ALSA backend:                      yes
    -> FluidSynth backend:                yes
  CD Digital Audio (cdaudio_ng):          yes
  sndfile extensions:                     yes
  Tone Generator:                         yes
  Ogg Vorbis (vorbis):                    yes
  Free Lossless Audio Codec (flacng):     yes
  Commodore 64 audio (SID):               yes (old style API)
    -> libSIDPlay1 support:               no
    -> libSIDPlay2 support:               yes
    -> distortion patched libSIDPlay2:    no
  Game music (spc, nsf & gbs):            yes
  PlayStation (psf/psf2) audio:           yes
  Nintendo 64 audio (usf) (experimental): no
  Nintendo DS audio (xsf):                yes
  AdLib synthesizer (adplug):             yes
  WavPack 4.31+ (wavpack):                yes
  Metronom:                               yes

  General
  -------
  Song Change:                            yes
  Status Icon:                            yes
  Audacious OSD:                          yes
    -> X Composite support:               yes
  libnotify OSD:                          no
  Global Hotkey Plugin:                   yes
  Gnome Shortcuts Plugin:                 yes
  AudioScrobbler Client:                  yes
  Upload to MTP device:                   yes
  MacOS Dock Album Art plugin:            no
  LyricWiki viewer:                       yes
  Album Art widget:                       yes

  Effect
  ------
  Dynamic Range Compressor:               yes
  Voice Removal:                          yes
  Extra Stereo:                           yes
  Echo/Surround:                          yes
  SndStretch:                             yes
  Crystalizer:                            yes
  Mixdown:                                yes
  Bauer stereophonic-to-binaural (bs2b):  no
  Sample Rate Converter (resample):       yes

  Visualization
  -------------
  Blur Scope:                             yes
  Cairo Spectrum Analyzer:                yes
  Moodbar data renderer:                  yes

  Transport
  ---------
  gio transport (experimental):           no
  neon-based http/https:                  yes
  libmms-based mms:                       yes
  SMB transport:                          no

  Container
  ---------
  Winamp PLS playlist format (pls):       yes
  M3U playlist format (m3u):              yes
  XML Sharable Playlist Format (xspf):    yes
  CUE playlist format (cue):              yes

  Interfaces
  ----------
  GTK (gtkui):                            yes
  Winamp Classic (skins):                 yes
As far as the provided audacious - it appears no one adjusted the configure.ac to reflect the new version # of libavcodec, ect.
That they needed to do that in the .ac in the 1st. place is due to using libav instead of FFMPEG
The whole business is a little tiresome at this point..

---

### Post by andrew.46 on 2011-10-22
Thanks mc4man! With a bit of scratching around I found the reasonably undocumented files:

```

http://distfiles.atheme.org/audacious-3.0.4.tar.bz2
http://distfiles.atheme.org/audacious-plugins-3.0.4.tar.bz2
http://distfiles.atheme.org/libmowgli-0.9.50.tar.bz2

```

and successfully built audacious plugins against the git FFmpeg. I am missing a few things:

```

  Output Plugins
  --------------
  Open Sound System (oss):                yes
  Open Sound System v4 (oss4):            no
  Advanced Linux Sound Arch. (alsa):      yes
  PulseAudio (pulse):                     no
  RoarAudio (roaraudio):                  no
  Jack Audio Connection Kit (jack):       no
  Mac OS X sound support (CoreAudio):     no
  Simple DirectMedia Layer (sdlout):      yes
  FileWriter:                             yes
    -> FileWriter MP3 output part:        yes
    -> FileWriter Vorbis output part:     yes
    -> FileWriter FLAC output part:       yes
  Null Audio output (null):               yes
  Windows waveOut (experimental):         no
  OpenAL (experimental):                  no

  Input Plugins
  -------------
  MPEG-1 Layer I/II/III (mpg123):         yes
  MPEG-2/4 AAC (aac):                     no
  FFaudio (ffaudio):                      yes
  Module decoder (modplug):               no
  MIDI modular plugin (amidi-plug):       yes
    -> ALSA backend:                      yes
    -> FluidSynth backend:                no
  CD Digital Audio (cdaudio_ng):          yes
  sndfile extensions:                     yes
  Tone Generator:                         yes
  Ogg Vorbis (vorbis):                    yes
  Free Lossless Audio Codec (flacng):     yes
  Commodore 64 audio (SID):               no 
    -> libSIDPlay1 support:               no
    -> libSIDPlay2 support:               no
    -> distortion patched libSIDPlay2:    
  Game music (spc, nsf & gbs):            yes
  PlayStation (psf/psf2) audio:           yes
  Nintendo 64 audio (usf) (experimental): no
  Nintendo DS audio (xsf):                yes
  AdLib synthesizer (adplug):             no
  WavPack 4.31+ (wavpack):                yes
  Metronom:                               yes

  General
  -------
  Song Change:                            yes
  Status Icon:                            yes
  Audacious OSD:                          yes
    -> X Composite support:               yes
  libnotify OSD:                          yes
  Global Hotkey Plugin:                   yes
  Gnome Shortcuts Plugin:                 yes
  AudioScrobbler Client:                  yes
  Upload to MTP device:                   yes
  MacOS Dock Album Art plugin:            no
  LyricWiki viewer:                       yes
  Album Art widget:                       yes

  Effect
  ------
  Dynamic Range Compressor:               yes
  Voice Removal:                          yes
  Extra Stereo:                           yes
  Echo/Surround:                          yes
  SndStretch:                             yes
  Crystalizer:                            yes
  Mixdown:                                yes
  Bauer stereophonic-to-binaural (bs2b):  no
  Sample Rate Converter (resample):       yes

  Visualization
  -------------
  Blur Scope:                             yes
  Cairo Spectrum Analyzer:                yes
  Moodbar data renderer:                  yes

  Transport
  ---------
  gio transport (experimental):           no
  neon-based http/https:                  yes
  libmms-based mms:                       no
  SMB transport:                          yes

  Container
  ---------
  Winamp PLS playlist format (pls):       yes
  M3U playlist format (m3u):              yes
  XML Sharable Playlist Format (xspf):    yes
  CUE playlist format (cue):              no

  Interfaces
  ----------
  GTK (gtkui):                            yes
  Winamp Classic (skins):                 yes

```

but as I am not a huge audacious user this might do me for the time being...

---

### Post by mc4man on 2011-10-22
Module decoder (modplug) = libmodplug-dev, maybe a min ver#, not that useful for most
Cue file support = libcue-dev, again not that common

The AAC is surprising - comes from libfadd-dev which is likely  to installed for you - version 2.7 here
Overall minor stuff except if the no AAC means no .aac/.m4a & one had those types

> I found the reasonably undocumented files:
I'm not sure they could make it any harder to locate aud source files other than to not have any.

---

### Post by andrew.46 on 2011-10-22
> **mc4man said:**
> The AAC is surprising - comes from libfaad-dev which is likely  to installed for you - version 2.7 here
Overall minor stuff except if the no AAC means no .aac/.m4a & one had those types

This is my slackware system where I have tighter control on files installed than on my Oneiric VM. Oddly enough aac/m4a files play fine, I presume using ffaudio?

---

### Post by mikeydeeeee on 2012-03-22
Excellent, thank you!

Even reads the ID3 tags now!

---

### Post by shantiq on 2012-03-22
using audacious 3.2.1  [the one from repositories] under oneiric   sample wma   from   [**here**]("http://www.wmatools.com/wma-file-samples.html") play fine    but wmal   noooooooooo:KS

---

### Post by Yellow Pasque on 2012-03-22
> **shantiq said:**
> using audacious 3.2.1  [the one from repositories] under oneiric   sample wma   from   [**here**]("http://www.wmatools.com/wma-file-samples.html") play fine    but wmal   noooooooooo:KS
I converted the few wma lossless files I had to FLAC (using foobar2000 under wine IIRC).

---

### Post by shantiq on 2012-03-22
tahnx temujin can also be done very well with dBpoweramp under wine    but i was just mentioning that to say that wma seems ok on audacious   but not wmal :KS

---

### Post by Yellow Pasque on 2012-03-22
It's not going to work in audacious until ffmpeg supports it (if that ever happens). mplayer and xine can support it with w32codecs package.

---

### Post by Yellow Pasque on 2012-03-22
Actually, I just saw in libav changelog that wmalossless is coming in 0.10: [http://www.libav.org/changelog.html](http://www.libav.org/changelog.html)
I already have the codec in Debian sid, but I have no idea when Ubuntu will have the necessary components.

---

### Post by mc4man on 2012-03-22
> **Temüjin said:**
> Actually, I just saw in libav changelog that wmalossless is coming in 0.10: [http://www.libav.org/changelog.html](http://www.libav.org/changelog.html)
I already have the codec in Debian sid, but I have no idea when Ubuntu will have the necessary components.

Support is in the current libav in 12.04 (& current FFmpeg

No players, plugins have support yet in 12.04, they may or may not
(mplayer  just added support, works fine, vlc tried a couple of weeks ago, didn't work out, upstream bug, may be ok now or soon

Edit: support can be enabled in aud if built (several build issues with the 3.3 git
screen shows

---

