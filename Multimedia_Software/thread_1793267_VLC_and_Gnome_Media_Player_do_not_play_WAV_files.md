---
title: "VLC and Gnome Media Player do not play WAV files"
date: 2011-06-29
forum: Multimedia Software
---

### Post by Paddy Landau on 2011-06-29
I usually use VLC because of its reliability.

Today, I need to play some WAV files. But VLC plays the WAV files silently.

Gnome Media Player also plays them silently.

Movie Player, on the other hand, plays them correctly.

Any ideas how to get VLC to play WAV files?

---

### Post by andrew.46 on 2011-06-29
Hmmm.... seems odd, vlc should have no such trouble:

```

andrew@skamandros~/music/YouTube$ **[COLOR="Red"]cvlc --list | grep -i wav[/COLOR]**
VLC media player 1.2.0-git Twoflower (revision 73cadb2)
  wave                   Wave video filter
  wav                    WAV demuxer
  mux_wav                WAV muxer

```

I presume your copy has identical results?

---

### Post by Paddy Landau on 2011-06-29
Yes, same results:
```
$ [COLOR=DarkRed]cvlc --list | grep -i wav[/COLOR]
VLC media player 1.1.2 The Luggage (revision exported)
  wave                   Wave video filter
  mux_wav                WAV muxer
  wav                    WAV demuxer
```I have also installed wavpack as suggested in another thread, but it made no difference.

---

### Post by andrew.46 on 2011-06-29
Can you play one of these troublesome wav files from the commandline with MPlayer and post the terminal output here? It would also be very handy if you could post one of the wav files online as well.

---

### Post by Paddy Landau on 2011-06-30
Mplayer was not installed, so I have installed it. It works. Here is the output:

```
$ [COLOR=DarkRed]mplayer finches.wav[/COLOR]
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing finches.wav.
Audio only file format detected.
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 11025 Hz, 1 ch, s16le, 176.4 kbit/100.00% (ratio: 22050->22050)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [pulse] 11025Hz 1ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   2.2 (02.1) of 2.0 (02.0)  0.0% 

Exiting... (End of file)
```The following two programs do not work: vlc; gnome-media-player.

The following two programs do work: totem; mplayer

I have attached the WAV file that I used for this (compressed,  because I'm not allowed to upload a WAV file uncompressed).

---

### Post by andrew.46 on 2011-06-30
> **Paddy Landau said:**
> I have attached the WAV file that I used for this (compressed,  because I'm not allowed to upload a WAV file uncompressed).

Thanks for the file which plays perfectly with vlc on my system. Do you have problems playing other sound files with vlc? If so have a look at the 
output module under Preferences --> Audio --> Output --> Output Module and select a different value. Seems a little odd though...

---

### Post by Paddy Landau on 2011-06-30
OK, this is bizarre...

Since my last post, I had done nothing apart from a little browsing and answering emails. Most of the time I was away from my desk.

Yet, VLC unexpectedly played the WAV files, but interrupted every few seconds with white noise.

So, I rebooted. At first, VLC played the WAV files perfectly. Then suddenly it stopped. It is still not playing them. That happened without me touching any settings, or installing or uninstalling anything.

I don't understand what could have changed. :confused:

I have played with Tools > Preferences > Audio > Output Module, but it seems to make no difference.

By the way, I've never had a problem in VLC with OGG and MP3 files; they still work perfectly.

---

### Post by Duncan Williams on 2011-06-30
I have been getting inconsistent results from vlc and it has started to lock up at times.
Also media player sometimes locks when surfing web and playing videos.

I am pretty sure it has something to do with the window manager.

So the problem maybe >compiz > unity > video driver (open gl)
and 3d desktop affect.

It always seems to comeback to these issues, if I run a 2d desktop the problems usually disappear.

---

### Post by Paddy Landau on 2011-07-01
> **Duncan Williams said:**
> ... So the problem maybe >compiz...
I have Compiz disabled anyway, so in my case that seems unlikely. The only problem I've had with VLC has been WAV files; everything else (video and audio) plays perfectly.

---

### Post by andrew.46 on 2011-07-01
The vlc logs can be very verbose but might be well worth a look. Below is an example of a successful vlc vs your wav file:

```

andrew@skamandros~/Desktop$ **[COLOR="Red"]cvlc -vvv finches.wav [/COLOR]**
VLC media player 1.2.0-git Twoflower (revision 73cadb2)
[0x8066194] main libvlc debug: VLC media player - 1.2.0-git Twoflower
[0x8066194] main libvlc debug: Copyright © 1996-2011 the VideoLAN team
[0x8066194] main libvlc debug: revision 73cadb2
[0x8066194] main libvlc debug: configured with ./configure  '--prefix=/usr' '--mandir=/usr/man' '--with-live555-tree=/usr/lib/live' '--enable-real' '--enable-realrtsp' '--enable-aa' '--enable-snapshot' '--enable-merge-ffmpeg' '--enable-loader' '--enable-ncurses' '--disable-taglib' 'CFLAGS=-O2 -march=i486 -mtune=i686' 'CXXFLAGS=-O2 -march=i486 -mtune=i686' 'PKG_CONFIG_PATH=/usr/local/lib/pkgconfig:/usr/lib/pkgconfig'
[0x8066194] main libvlc debug: translation test: code is "C"
[0x8066194] main libvlc debug: checking plugin modules
[0x8066194] main libvlc debug: loading plugins cache file /usr/lib/vlc/plugins/plugins.dat
[0x8066194] main libvlc warning: cannot read /usr/lib/vlc/plugins/plugins.dat (No such file or directory)
[0x8066194] main libvlc debug: recursively browsing `/usr/lib/vlc/plugins'
[0x8066194] main libvlc debug: saving plugins cache /usr/lib/vlc/plugins/plugins.dat
[0x8066194] main libvlc debug: module bank initialized (394 modules)
[0x8066194] main libvlc debug: opening config file (/home/andrew/.config/vlc/vlcrc)
[0x8066194] main libvlc debug: CPU has capabilities MMX MMXEXT SSE SSE2 SSE3 SSSE3 FPU 
[0x8066194] main libvlc debug: looking for memcpy module: 4 candidates
[0x8066194] main libvlc debug: using memcpy module "memcpymmxext"
[0x816300c] main input debug: Creating an input for 'Media Library'
[0x816300c] main input debug: Input is a meta file: disabling unneeded options
[0x816300c] main input debug: using timeshift granularity of 50 MiB, in path '/tmp'
[0x816300c] main input debug: `file/xspf-open:///home/andrew/.local/share/vlc/ml.xspf' gives access `file' demux `xspf-open' path `/home/andrew/.local/share/vlc/ml.xspf'
[0x816300c] main input debug: creating demux: access='file' demux='xspf-open' location='/home/andrew/.local/share/vlc/ml.xspf' file='/home/andrew/.local/share/vlc/ml.xspf'
[0x808a07c] main demux debug: looking for access_demux module: 2 candidates
[0x808a07c] main demux debug: no access_demux module matching "file" could be loaded
[0x808a07c] main demux debug: TIMER module_need() : 1.275 ms - Total 1.275 ms / 1 intvls (Avg 1.275 ms)
[0x816300c] main input debug: creating access 'file' location='/home/andrew/.local/share/vlc/ml.xspf', path='/home/andrew/.local/share/vlc/ml.xspf'
[0x808bdcc] main access debug: looking for access module: 2 candidates
[0x808bdcc] filesystem access debug: opening file `/home/andrew/.local/share/vlc/ml.xspf'
[0x808bdcc] main access debug: using access module "filesystem"
[0x808bdcc] main access debug: TIMER module_need() : 0.771 ms - Total 0.771 ms / 1 intvls (Avg 0.771 ms)
[0x808b17c] main stream debug: Using stream method for AStream*
[0x808b17c] main stream debug: starting pre-buffering
[0x808b17c] main stream debug: received first data after 17 ms
[0x808b17c] main stream debug: pre-buffering done 296 bytes in 0s - 16 KiB/s
[0x808afcc] main stream debug: looking for stream_filter module: 6 candidates
[0x808afcc] main stream debug: no stream_filter module matching "any" could be loaded
[0x808afcc] main stream debug: TIMER module_need() : 1.699 ms - Total 1.699 ms / 1 intvls (Avg 1.699 ms)
[0x808afcc] main stream debug: looking for stream_filter module: 1 candidate
[0x808afcc] main stream debug: using stream_filter module "stream_filter_record"
[0x808afcc] main stream debug: TIMER module_need() : 0.358 ms - Total 0.358 ms / 1 intvls (Avg 0.358 ms)
[0x816300c] main input debug: creating demux: access='file' demux='xspf-open' location='/home/andrew/.local/share/vlc/ml.xspf' file='/home/andrew/.local/share/vlc/ml.xspf'
[0x808ca14] main demux debug: looking for demux module: 1 candidate
[0x808ca14] playlist demux debug: using XSPF playlist reader
[0x808ca14] main demux debug: using demux module "playlist"
[0x808ca14] main demux debug: TIMER module_need() : 0.635 ms - Total 0.635 ms / 1 intvls (Avg 0.635 ms)
[0x808ce3c] main demux meta debug: looking for meta reader module: 1 candidate
[0x808ce3c] lua demux meta debug: Trying Lua scripts in /home/andrew/.local/share/vlc/lua/meta/reader
[0x808ce3c] lua demux meta debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/reader
[0x808ce3c] lua demux meta debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/reader/filename.luac
[0x808ce3c] lua demux meta debug: Trying Lua scripts in /usr/share/vlc/lua/meta/reader
[0x808ce3c] main demux meta debug: no meta reader module matching "any" could be loaded
[0x808ce3c] main demux meta debug: TIMER module_need() : 60.643 ms - Total 60.643 ms / 1 intvls (Avg 60.643 ms)
[0x816300c] main input debug: `file/xspf-open:///home/andrew/.local/share/vlc/ml.xspf' successfully opened
[0x808ce3c] main xml reader debug: looking for xml reader module: 1 candidate
[0x808ce3c] main xml reader debug: using xml reader module "xml"
[0x808ce3c] main xml reader debug: TIMER module_need() : 11.056 ms - Total 11.056 ms / 1 intvls (Avg 11.056 ms)
[0x808ca14] playlist demux debug: parsed 0 tracks successfully
[0x816300c] main input debug: EOF reached
[0x808ca14] main demux debug: removing module "playlist"
[0x808afcc] main stream debug: removing module "stream_filter_record"
[0x808bdcc] main access debug: removing module "filesystem"
[0x816300c] main input debug: TIMER input launching for 'Media Library' : 103.731 ms - Total 103.731 ms / 1 intvls (Avg 103.731 ms)
[0x808ce3c] main interface debug: looking for interface module: 1 candidate
[0x808ce3c] main interface debug: using interface module "hotkeys"
[0x808ce3c] main interface debug: TIMER module_need() : 0.303 ms - Total 0.303 ms / 1 intvls (Avg 0.303 ms)
[0x808b41c] main interface debug: looking for interface module: 1 candidate
[0x8074c64] main playlist debug: playlist threads correctly activated
[0x8074c64] main playlist debug: rebuilding array of current - root Playlist
[0x8074c64] main playlist debug: rebuild done - 0 items, index -1
[0x808b41c] main interface debug: using interface module "inhibit"
[0x808b41c] main interface debug: TIMER module_need() : 1.552 ms - Total 1.552 ms / 1 intvls (Avg 1.552 ms)
[0x8074c64] main playlist debug: adding item `finches.wav' ( file:///home/andrew/Desktop/finches.wav )
[0x808e524] main input debug: Creating an input for 'finches.wav'
[0xb5a00504] main interface debug: looking for interface module: 1 candidate
[0xb5a00504] main interface debug: using interface module "globalhotkeys"
[0xb5a00504] main interface debug: TIMER module_need() : 1.330 ms - Total 1.330 ms / 1 intvls (Avg 1.330 ms)
[0x8090d7c] main interface debug: looking for interface module: 1 candidate
[0x8090d7c] dummy interface: using the dummy interface module...
[0x8090d7c] main interface debug: using interface module "dummy"
[0x8090d7c] main interface debug: TIMER module_need() : 0.462 ms - Total 0.462 ms / 1 intvls (Avg 0.462 ms)
[0x8074c64] main playlist debug: processing request item: null, node: Playlist, skip: 0
[0x8074c64] main playlist debug: rebuilding array of current - root Playlist
[0x8074c64] main playlist debug: rebuild done - 1 items, index -1
[0x8074c64] main playlist debug: starting playback of the new playlist item
[0x8074c64] main playlist debug: creating new input thread
[0x8090ad4] main input debug: Creating an input for 'finches.wav'
[0x8090ad4] main input debug: using timeshift granularity of 50 MiB, in path '/tmp'
[0x8090ad4] main input debug: `file:///home/andrew/Desktop/finches.wav' gives access `file' demux `' path `/home/andrew/Desktop/finches.wav'
[0x8090ad4] main input debug: creating demux: access='file' demux='' location='/home/andrew/Desktop/finches.wav' file='/home/andrew/Desktop/finches.wav'
[0x80975fc] main demux debug: looking for access_demux module: 2 candidates
[0x80975fc] main demux debug: no access_demux module matching "file" could be loaded
[0x80975fc] main demux debug: TIMER module_need() : 0.165 ms - Total 0.165 ms / 1 intvls (Avg 0.165 ms)
[0x8090ad4] main input debug: creating access 'file' location='/home/andrew/Desktop/finches.wav', path='/home/andrew/Desktop/finches.wav'
[0x80977a4] main access debug: looking for access module: 2 candidates
[0x80977a4] filesystem access debug: opening file `/home/andrew/Desktop/finches.wav'
[0x80977a4] main access debug: using access module "filesystem"
[0x80977a4] main access debug: TIMER module_need() : 0.204 ms - Total 0.204 ms / 1 intvls (Avg 0.204 ms)
[0x81637f4] main stream debug: Using stream method for AStream*
[0x81637f4] main stream debug: starting pre-buffering
[0x81637f4] main stream debug: received first data after 0 ms
[0x81637f4] main stream debug: pre-buffering done 1024 bytes in 0s - 33333 KiB/s
[0x8163994] main stream debug: looking for stream_filter module: 6 candidates
[0x8163994] main stream debug: no stream_filter module matching "any" could be loaded
[0x8163994] main stream debug: TIMER module_need() : 0.124 ms - Total 0.124 ms / 1 intvls (Avg 0.124 ms)
[0x8163994] main stream debug: looking for stream_filter module: 1 candidate
[0x8163994] main stream debug: using stream_filter module "stream_filter_record"
[0x8163994] main stream debug: TIMER module_need() : 0.127 ms - Total 0.127 ms / 1 intvls (Avg 0.127 ms)
[0x8090ad4] main input debug: creating demux: access='file' demux='' location='/home/andrew/Desktop/finches.wav' file='/home/andrew/Desktop/finches.wav'
[0x8092f44] main demux debug: looking for demux module: 52 candidates
[0x8092f44] wav demux debug: chunk: fcc=`fmt ` size=16
[0x8092f44] wav demux debug: format: 0x0001, fourcc: araw, channels: 1, freq: 11025 Hz, bitrate: 21Ko/s, blockalign: 2, bits/samples: 16, extra size: 0
[0x8092f44] wav demux debug: found Raw audio audio format
[0x8092f44] wav demux debug: chunk: fcc=`data` size=54128
[0x8090ad4] main input debug: selecting program id=0
**[COLOR="Red"][0x8092f44] main demux debug: using demux module "wav"[/COLOR]**
[0x8092f44] main demux debug: TIMER module_need() : 0.428 ms - Total 0.428 ms / 1 intvls (Avg 0.428 ms)
[0x8090ad4] main input debug: looking for a subtitle file in /home/andrew/Desktop
[0x8074c64] main playlist debug: meta ok for (null), need to fetch art
[0x80936e4] main decoder debug: looking for decoder module: 31 candidates
[0x80935e4] main demux meta debug: looking for meta fetcher module: 1 candidate
[0x80935e4] lua demux meta debug: Trying Lua scripts in /home/andrew/.local/share/vlc/lua/meta/fetcher
[0x80935e4] lua demux meta debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/fetcher
[0x80935e4] lua demux meta debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/fetcher/tvrage.luac
[0x80935e4] main demux meta debug: using meta fetcher module "lua"
[0x80935e4] main demux meta debug: TIMER module_need() : 6.907 ms - Total 6.907 ms / 1 intvls (Avg 6.907 ms)
[0x80935e4] main demux meta debug: removing module "lua"
[0x8074c64] main playlist debug: searching art for finches.wav
[0x80935e4] main art finder debug: looking for art finder module: 2 candidates
[0x80936e4] araw decoder debug: samplerate:11025Hz channels:1 bits/sample:16
[0x80936e4] main decoder debug: using decoder module "araw"
[0x80936e4] main decoder debug: TIMER module_need() : 7.194 ms - Total 7.194 ms / 1 intvls (Avg 7.194 ms)
[0x80935e4] lua art finder debug: Trying Lua scripts in /home/andrew/.local/share/vlc/lua/meta/art
[0x80935e4] lua art finder debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/art
[0x8168eb4] main demux meta debug: looking for meta reader module: 1 candidate
[0x8168eb4] lua demux meta debug: Trying Lua scripts in /home/andrew/.local/share/vlc/lua/meta/reader
[0x8168eb4] lua demux meta debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/reader
[0x8168eb4] lua demux meta debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/reader/filename.luac
[0x80935e4] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/01_googleimage.luac
[0x8168eb4] lua demux meta debug: Trying Lua scripts in /usr/share/vlc/lua/meta/reader
[0x8168eb4] main demux meta debug: no meta reader module matching "any" could be loaded
[0x8168eb4] main demux meta debug: TIMER module_need() : 0.874 ms - Total 0.874 ms / 1 intvls (Avg 0.874 ms)
[0x8090ad4] main input debug: `file:///home/andrew/Desktop/finches.wav' successfully opened
[0x8090ad4] main input debug: Buffering 0%
[0x80935e4] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/02_frenchtv.luac
[0x8090ad4] main input debug: Buffering 16%
[0x8074c64] main playlist debug: creating audio output
[0x8090ad4] main input debug: Buffering 33%
[0x8090ad4] main input debug: Buffering 49%
[0x8090ad4] main input debug: Buffering 66%
[0x8090ad4] main input debug: Buffering 83%
[0x8090ad4] main input debug: Buffering 99%
[0x8090ad4] main input debug: Stream buffering done (349 ms in 0 ms)
[0x80935e4] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/03_lastfm.luac
[0x80935e4] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/04_musicbrainz.luac
[0x80935e4] lua art finder debug: Trying Lua scripts in /usr/share/vlc/lua/meta/art
[0x80935e4] main art finder debug: no art finder module matching "any" could be loaded
[0x80935e4] main art finder debug: TIMER module_need() : 4.512 ms - Total 4.512 ms / 1 intvls (Avg 4.512 ms)
[0x8074c64] main playlist debug: art not found for finches.wav
[0x81650c4] main audio output debug: looking for audio output module: 3 candidates
[0x81650c4] alsa audio output debug: opening ALSA device `default'
[0x81650c4] alsa audio output warning: resampling from 11025 Hz to 48000 Hz
[0x81650c4] alsa audio output debug: Available ALSA PCM devices:
[0x81650c4] alsa audio output debug: Discard all samples (playback) or generate zero samples (capture) (null)
[0x81650c4] alsa audio output debug: HDA Intel, STAC92xx Analog Default Audio Device (default:CARD=Intel)
[0x81650c4] alsa audio output debug: HDA Intel, STAC92xx Analog Front speakers (front:CARD=Intel,DEV=0)
[0x81650c4] alsa audio output debug: HDA Intel, STAC92xx Analog 4.0 Surround output to Front and Rear speakers (surround40:CARD=Intel,DEV=0)
[0x81650c4] alsa audio output debug: HDA Intel, STAC92xx Analog 4.1 Surround output to Front, Rear and Subwoofer speakers (surround41:CARD=Intel,DEV=0)
[0x81650c4] alsa audio output debug: HDA Intel, STAC92xx Analog 5.0 Surround output to Front, Center and Rear speakers (surround50:CARD=Intel,DEV=0)
[0x81650c4] alsa audio output debug: HDA Intel, STAC92xx Analog 5.1 Surround output to Front, Center, Rear and Subwoofer speakers (surround51:CARD=Intel,DEV=0)
[0x81650c4] alsa audio output debug: HDA Intel, STAC92xx Analog 7.1 Surround output to Front, Center, Side, Rear and Woofer speakers (surround71:CARD=Intel,DEV=0)
[0x81650c4] alsa audio output debug: HDA Intel, STAC92xx Digital IEC958 (S/PDIF) Digital Audio Output (iec958:CARD=Intel,DEV=0)
[0x81650c4] main audio output debug: using audio output module "alsa"
[0x81650c4] main audio output debug: TIMER module_need() : 91.214 ms - Total 91.214 ms / 1 intvls (Avg 91.214 ms)
[0x81650c4] main audio output debug: output 's16l' 48000 Hz Mono frame=1 samples/2 bytes
[0x81650c4] main audio output debug: mixer 'f32l' 48000 Hz Mono frame=1 samples/4 bytes
[0x81650c4] main audio output debug: filter(s) 'f32l'->'s16l' 48000 Hz->48000 Hz Mono->Mono
[0x8189384] main audio filter debug: looking for audio filter module: 12 candidates
[0x8189384] audio_format audio filter debug: f32l->s16l, bits per sample: 32->16
[0x8189384] main audio filter debug: using audio filter module "audio_format"
[0x8189384] main audio filter debug: TIMER module_need() : 1.786 ms - Total 1.786 ms / 1 intvls (Avg 1.786 ms)
[0x81650c4] main audio output debug: conversion pipeline completed
[0x81875fc] main generic debug: looking for audio mixer module: 3 candidates
[0x81875fc] main generic debug: using audio mixer module "float32_mixer"
[0x81875fc] main generic debug: TIMER module_need() : 0.238 ms - Total 0.238 ms / 1 intvls (Avg 0.238 ms)
[0x81650c4] main audio output debug: input 's16l' 11025 Hz Mono frame=1 samples/2 bytes
[0x816bdac] main audio filter debug: looking for audio filter module: 1 candidate
[0x816bdac] scaletempo audio filter debug: format: 11025 rate, 1 nch, 4 bps, fl32
[0x816bdac] scaletempo audio filter debug: params: 30 stride, 0.200 overlap, 14 search
[0x816bdac] scaletempo audio filter debug: 1.000 scale, 330.000 stride_in, 330 stride_out, 264 standing, 66 overlap, 154 search, 550 queue, fl32 mode
[0x816bdac] main audio filter debug: using audio filter module "scaletempo"
[0x816bdac] main audio filter debug: TIMER module_need() : 0.334 ms - Total 0.334 ms / 1 intvls (Avg 0.334 ms)
[0x81650c4] main audio output debug: filter(s) 's16l'->'f32l' 11025 Hz->11025 Hz Mono->Mono
[0x819b51c] main audio filter debug: looking for audio filter module: 12 candidates
[0x819b51c] audio_format audio filter debug: s16l->f32l, bits per sample: 16->32
[0x819b51c] main audio filter debug: using audio filter module "audio_format"
[0x819b51c] main audio filter debug: TIMER module_need() : 0.154 ms - Total 0.154 ms / 1 intvls (Avg 0.154 ms)
[0x81650c4] main audio output debug: conversion pipeline completed
[0x81650c4] main audio output debug: filter(s) 'f32l'->'f32l' 11025 Hz->11025 Hz Mono->Mono
[0x81650c4] main audio output debug: conversion pipeline completed
[0x81650c4] main audio output debug: filter(s) 'f32l'->'f32l' 52800 Hz->48000 Hz Mono->Mono
[0x819b84c] main audio filter debug: looking for audio filter module: 12 candidates
[0x819b84c] main audio filter debug: using audio filter module "ugly_resampler"
[0x819b84c] main audio filter debug: TIMER module_need() : 0.127 ms - Total 0.127 ms / 1 intvls (Avg 0.127 ms)
[0x81650c4] main audio output debug: conversion pipeline completed
[0x80936e4] main decoder debug: End of audio preroll
[0x8090ad4] main input debug: Decoder buffering done in 98 ms
[0x81650c4] main audio output warning: PTS is out of range (-9877), dropping buffer
[0x8090ad4] main input debug: EOF reached
[0x8090ad4] main input debug: waiting decoder fifos to empty
[0x8090ad4] main input debug: waiting decoder fifos to empty
[0x8090ad4] main input debug: waiting decoder fifos to empty
[0x8090ad4] main input debug: waiting decoder fifos to empty
[0x81650c4] alsa audio output debug: recovered from buffer underrun
[0x8090ad4] main input debug: waiting decoder fifos to empty
[0x8074c64] main playlist debug: finished input
[0x80936e4] main decoder debug: removing module "araw"
[0x80936e4] main decoder debug: killing decoder fourcc `s16l', 0 PES in FIFO
[0x819b51c] main audio filter debug: removing module "audio_format"
[0x816bdac] main audio filter debug: removing module "scaletempo"
[0x819b84c] main audio filter debug: removing module "ugly_resampler"
[0x81650c4] main audio output debug: removing module "alsa"
[0x8189384] main audio filter debug: removing module "audio_format"
[0x81875fc] main generic debug: removing module "float32_mixer"
[0x8074c64] main playlist debug: releasing audio output
[0x8092f44] main demux debug: removing module "wav"
[0x8163994] main stream debug: removing module "stream_filter_record"
[0x80977a4] main access debug: removing module "filesystem"
[0x8090ad4] main input debug: Program doesn't contain anymore ES
[0x8074c64] main playlist debug: dead input
[0x8074c64] main playlist debug: changing item without a request (current 0/1)
[0x8074c64] main playlist debug: nothing to play
[0x8074c64] main playlist: end of playlist, exiting
[0x8066194] main libvlc debug: exiting
[0x8066194] main libvlc debug: deactivating the playlist
[0x8074c64] main playlist debug: deactivating the playlist
[0x8186b4c] main playlist export debug: saving Media Library to file /home/andrew/.local/share/vlc/ml.xspf
[0x8186b4c] main playlist export debug: looking for playlist export module: 1 candidate
[0x8186b4c] main playlist export debug: using playlist export module "export"
[0x8186b4c] main playlist export debug: TIMER module_need() : 0.521 ms - Total 0.521 ms / 1 intvls (Avg 0.521 ms)
[0x8186b4c] main playlist export debug: removing module "export"
[0x8074c64] main playlist debug: playlist correctly deactivated
[0x8066194] main libvlc debug: removing all services discovery tasks
[0x8066194] main libvlc debug: removing all interfaces
[0x8090d7c] main interface debug: removing module "dummy"
[0xb5a00504] main interface debug: removing module "globalhotkeys"
[0x808b41c] main interface debug: removing module "inhibit"
[0x8090ad4] main input debug: TIMER input launching for 'finches.wav' : 18.258 ms - Total 18.258 ms / 1 intvls (Avg 18.258 ms)
[0x808ce3c] main interface debug: removing module "hotkeys"
[0x8074c64] main playlist debug: destroying
[0x8066194] main libvlc debug: TIMER ML Load : Total 115.273 ms / 1 intvls (Avg 115.273 ms)
[0x8066194] main libvlc debug: TIMER Items array build : Total 0.106 ms / 2 intvls (Avg 0.053 ms)
[0x8066194] main libvlc debug: TIMER Preparse run : Total 11.952 ms / 1 intvls (Avg 11.952 ms)
[0x8066194] main libvlc debug: TIMER ML Dump : Total 19.377 ms / 1 intvls (Avg 19.377 ms)
[0x8066194] main libvlc debug: removing stats
[0x8066194] main libvlc debug: removing module "memcpymmxext"

```

The problem on your copy of vlc should be revealed with this hopefully...

---

### Post by John-B on 2011-07-01
I also seem to have a similar problem with .wav files.  Using VLC trying to play a wav file the program seems to only play half of the file, but like Paddy Landau other programs play them fine.  So I tried andrew.46 advice and got this error code: **main audio output warning: PTS is out of range (-9691), dropping buffer**
What would cause this?
Interested to see if Paddy Landau has the same or similar..

---

### Post by mister_p_1998 on 2011-07-01
I get this sometimes with all audio files, if I restart gnome or log out and back in again it suddenly works, its as if something has grabbed the audio device (Flash in firefox?) and isnt handing it back to other programs.

---

### Post by Paddy Landau on 2011-07-01
> **andrew.46 said:**
> The vlc logs...
Here are my results. Curiously, it stopped near the end ("nothing to play"), and I had to press Ctrl-C to continue.
```
$ **[COLOR=DarkRed]cvlc -vvv finches.wav[/COLOR]**
VLC media player 1.1.2 The Luggage (revision exported)
[0x1d93910] main libvlc debug: VLC media player - 1.1.2 The Luggage
[0x1d93910] main libvlc debug: Copyright © 1996-2010 the VideoLAN team
[0x1d93910] main libvlc debug: revision exported
[0x1d93910] main libvlc debug: configured with ./configure   '--build=x86_64-linux-gnu' '--config-cache' '--disable-maintainer-mode'  '--disable-silent-rules' '--disable-update-check'  '--enable-fast-install' '--prefix=/usr' '--sysconfdir=/etc'  '--with-binary-version=1~ppa1' '--enable-a52' '--enable-aa'  '--enable-bonjour' '--enable-caca' '--enable-dca' '--enable-dirac'  '--enable-dvb' '--enable-dvbpsi' '--enable-dvdnav' '--enable-faad'  '--enable-flac' '--enable-fluidsynth' '--enable-freetype'  '--enable-fribidi' '--enable-ggi' '--enable-gnutls' '--enable-jack'  '--enable-kate' '--enable-libass' '--enable-libmpeg2'  '--enable-libproxy' '--enable-libxml2' '--enable-lirc'  '--enable-live555' '--enable-mad' '--enable-mkv' '--enable-mod'  '--enable-mozilla' '--enable-mpc' '--enable-mtp' '--enable-mux_ogg'  '--enable-ncurses' '--enable-notify' '--enable-ogg' '--enable-pulse'  '--enable-qt4' '--enable-realrtsp' '--enable-schroedinger'  '--enable-sdl' '--enable-shout' '--enable-skins2' '--enable-smb'  '--enable-speex' '--enable-svg' '--enable-taglib' '--enable-theora'  '--enable-twolame' '--enable-upnp' '--enable-vcd' '--enable-vcdx'  '--enable-vorbis' '--enable-x264' '--enable-zvbi'  '--with-kde-solid=/usr/share/kde4/apps/' '--with-mozilla-pkg=libxul'  '--disable-dxva2' '--disable-gnomevfs' '--disable-goom'  '--disable-libva' '--disable-osso_screensaver' '--disable-portaudio'  '--disable-projectm' '--disable-sqlite' '--disable-telx' '--enable-alsa'  '--enable-atmo' '--enable-dc1394' '--enable-dv' '--enable-pvr'  '--enable-udev' '--enable-v4l' '--enable-v4l2' '--enable-svgalib'  'build_alias=x86_64-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed'  'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[0x1d93910] main libvlc debug: translation test: code is "en_GB"
[0x1d93910] main libvlc debug: checking plugin modules
[0x1d93910] main libvlc debug: loading plugins cache file /usr/lib/vlc/plugins/plugins-04081e-3e8.dat
[0x1d93910] main libvlc debug: recursively browsing `/usr/lib/vlc/plugins'
[0x1d93910] main libvlc debug: saving plugins cache /usr/lib/vlc/plugins/plugins-04081e-3e8.dat
[0x1d93910] main libvlc debug: module bank initialized (396 modules)
[0x1d93910] main libvlc debug: opening config file (/home/paddy/.config/vlc/vlcrc)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
Warning: call to signal(13, 0x1)
[0x1d93910] main libvlc debug: No Media Player is running. Continuing normally.
[0x1d93910] main libvlc debug: CPU has capabilities MMX MMXEXT SSE SSE2 SSE3 SSSE3 FPU 
[0x1d93910] main libvlc debug: looking for memcpy module: 3 candidates
[0x1d93910] main libvlc debug: using memcpy module "memcpymmxext"
[0x1dcec20] main input debug: Creating an input for 'Media Library'
[0x1dcec20] main input debug: Input is a meta file: disabling unneeded options
[0x1dcec20] main input debug: using timeshift granularity of 50 MiB
[0x1dcec20] main input debug: using timeshift path '/tmp'
[0x1dcec20] main input debug:  `file/xspf-open:///home/paddy/.local/share/vlc/ml.xspf' gives access  `file' demux `xspf-open' path `/home/paddy/.local/share/vlc/ml.xspf'
[0x1dcec20] main input debug: creating demux: access='file' demux='xspf-open' path='/home/paddy/.local/share/vlc/ml.xspf'
[0x1dd54a0] main demux debug: looking for access_demux module: 2 candidates
[0x1dd54a0] main demux debug: no access_demux module matching "file" could be loaded
[0x1dd54a0] main demux debug: TIMER module_need() : 0.221 ms - Total 0.221 ms / 1 intvls (Avg 0.221 ms)
[0x1dcec20] main input debug: creating access 'file' path='/home/paddy/.local/share/vlc/ml.xspf'
[0x1dd59b0] main access debug: looking for access module: 2 candidates
[0x1dd59b0] filesystem access debug: opening file `/home/paddy/.local/share/vlc/ml.xspf'
[0x1dd59b0] main access debug: using access module "filesystem"
[0x1dd59b0] main access debug: TIMER module_need() : 0.115 ms - Total 0.115 ms / 1 intvls (Avg 0.115 ms)
[0x1dd5620] main stream debug: Using AStream*Stream
[0x1dd5620] main stream debug: pre buffering
[0x1dd5620] main stream debug: received first data after 0 ms
[0x1dd5620] main stream debug: pre-buffering done 296 bytes in 0s - 16059 KiB/s
[0x1fe8940] main stream debug: looking for stream_filter module: 5 candidates
[0x1fe8940] main stream debug: no stream_filter module matching "any" could be loaded
[0x1fe8940] main stream debug: TIMER module_need() : 0.081 ms - Total 0.081 ms / 1 intvls (Avg 0.081 ms)
[0x1fe8940] main stream debug: looking for stream_filter module: 1 candidate
[0x1fe8940] main stream debug: using stream_filter module "stream_filter_record"
[0x1fe8940] main stream debug: TIMER module_need() : 0.076 ms - Total 0.076 ms / 1 intvls (Avg 0.076 ms)
[0x1dcec20] main input debug: creating demux: access='file' demux='xspf-open' path='/home/paddy/.local/share/vlc/ml.xspf'
[0x1fe8cc0] main demux debug: looking for demux module: 1 candidate
[0x1fe8cc0] playlist demux debug: using XSPF playlist reader
[0x1fe8cc0] main demux debug: using demux module "playlist"
[0x1fe8cc0] main demux debug: TIMER module_need() : 0.100 ms - Total 0.100 ms / 1 intvls (Avg 0.100 ms)
[0x1fe8e90] main demux meta debug: looking for meta reader module: 2 candidates
[0x1fe8e90] lua demux meta debug: Trying Lua scripts in /home/paddy/.local/share/vlc/lua/meta/reader
[0x1fe8e90] lua demux meta debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/reader
[0x1fe8e90] lua demux meta debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/reader/filename.luac
[0x1fe8e90] lua demux meta debug: Trying Lua scripts in /usr/share/vlc/lua/meta/reader
[0x1fe8e90] main demux meta debug: no meta reader module matching "any" could be loaded
[0x1fe8e90] main demux meta debug: TIMER module_need() : 0.651 ms - Total 0.651 ms / 1 intvls (Avg 0.651 ms)
[0x1dcec20] main input debug: `file/xspf-open:///home/paddy/.local/share/vlc/ml.xspf' successfully opened
[0x1fe8e90] main xml debug: looking for xml module: 2 candidates
[0x1fe8e90] main xml debug: using xml module "xml"
[0x1fe8e90] main xml debug: TIMER module_need() : 0.156 ms - Total 0.156 ms / 1 intvls (Avg 0.156 ms)
[0x1fe8cc0] playlist demux debug: parsed 0 tracks successfully
[0x1fe8e90] main xml debug: removing module "xml"
[0x1dcec20] main input debug: EOF reached
[0x1fe8cc0] main demux debug: removing module "playlist"
[0x1fe8940] main stream debug: removing module "stream_filter_record"
[0x1dd59b0] main access debug: removing module "filesystem"
[0x1dcec20] main input debug: TIMER input launching for 'Media Library' : 1.858 ms - Total 1.858 ms / 1 intvls (Avg 1.858 ms)
[0x1dd57f0] main interface debug: looking for interface module: 1 candidate
[0x1dd57f0] main interface debug: using interface module "hotkeys"
[0x1dd57f0] main interface debug: TIMER module_need() : 0.113 ms - Total 0.113 ms / 1 intvls (Avg 0.113 ms)
[0x1fe8940] main interface debug: looking for interface module: 1 candidate
[0x1dcc9c0] main playlist debug: Activated
[0x1fe8940] main interface debug: using interface module "dbus"
[0x1fe8940] main interface debug: TIMER module_need() : 2.255 ms - Total 2.255 ms / 1 intvls (Avg 2.255 ms)
[0x1fe8940] main interface debug: thread (interface) created at priority 0 (interface/interface.c:160)
[0x1dcc9c0] main playlist debug: rebuilding array of current - root Playlist
[0x1dcc9c0] main playlist debug: rebuild done - 0 items, index -1
[0x1fe8940] main interface debug: thread started
[0x1dd3f60] main interface debug: looking for interface module: 1 candidate
[0x1dd3f60] main interface debug: using interface module "inhibit"
[0x1dd3f60] main interface debug: TIMER module_need() : 0.274 ms - Total 0.274 ms / 1 intvls (Avg 0.274 ms)
[0x1dcc9c0] main playlist debug: adding item `finches.wav' (  file:///home/paddy/Music/NoBackup-Misc/Sound%20effects/Birdsong/finches.wav  )
[0x1fe8cf0] main input debug: Creating an input for 'finches.wav'
[0x7fa3cc000b40] main interface debug: looking for interface module: 1 candidate
[0x7fa3cc000b40] main interface debug: using interface module "signals"
[0x7fa3cc000b40] main interface debug: TIMER module_need() : 0.151 ms - Total 0.151 ms / 1 intvls (Avg 0.151 ms)
[0x1dd3c90] main interface debug: looking for interface module: 1 candidate
[0x1dd3c90] main interface debug: using interface module "globalhotkeys"
[0x1dd3c90] main interface debug: TIMER module_need() : 0.751 ms - Total 0.751 ms / 1 intvls (Avg 0.751 ms)
[0x7fa3cc004a60] main interface debug: looking for interface module: 1 candidate
[0x7fa3cc004a60] dummy interface: **using the dummy interface module...**
[0x7fa3cc004a60] main interface debug: using interface module "dummy"
[0x7fa3cc004a60] main interface debug: TIMER module_need() : 0.207 ms - Total 0.207 ms / 1 intvls (Avg 0.207 ms)
[0x1dcc9c0] main playlist debug: processing request item null node Playlist skip 0
[0x1dcc9c0] main playlist debug: rebuilding array of current - root Playlist
[0x1dcc9c0] main playlist debug: rebuild done - 1 items, index -1
[0x1dcc9c0] main playlist debug: starting new item
[0x1dcc9c0] main playlist debug: creating new input thread
[0x1dcfcf0] main input debug: Creating an input for 'finches.wav'
[0x1dcfcf0] main input debug: thread (input) created at priority 10 (input/input.c:214)
[0x1dcc9c0] main playlist debug: meta ok for (null), need to fetch art
[0x1dcfcf0] main input debug: thread started
[0x1dcfcf0] main input debug: using timeshift granularity of 50 MiB
[0x1dcfcf0] main input debug: using timeshift path '/tmp'
[0x1dcfcf0] main input debug:  `file:///home/paddy/Music/NoBackup-Misc/Sound%20effects/Birdsong/finches.wav'  gives access `file' demux `' path  `/home/paddy/Music/NoBackup-Misc/Sound effects/Birdsong/finches.wav'
[0x1dcfcf0] main input debug: creating demux: access='file' demux=''  path='/home/paddy/Music/NoBackup-Misc/Sound  effects/Birdsong/finches.wav'
[0x1fef200] main demux meta debug: looking for meta fetcher module: 1 candidate
[0x1fef200] lua demux meta debug: Trying Lua scripts in /home/paddy/.local/share/vlc/lua/meta/fetcher
[0x1fef200] lua demux meta debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/fetcher
[0x1fef200] lua demux meta debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/fetcher/tvrage.luac
[0x1fef200] main demux meta debug: using meta fetcher module "lua"
[0x1fef200] main demux meta debug: TIMER module_need() : 0.658 ms - Total 0.658 ms / 1 intvls (Avg 0.658 ms)
[0x1fef200] main demux meta debug: removing module "lua"
[0x1dcc9c0] main playlist debug: searching art for finches.wav
[0x1feaa60] main art finder debug: looking for art finder module: 2 candidates
[0x1feaa60] lua art finder debug: Trying Lua scripts in /home/paddy/.local/share/vlc/lua/meta/art
[0x1feaa60] lua art finder debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/art
[0x1feaa60] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/01_googleimage.luac
[0x1feaa60] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/02_frenchtv.luac
[0x1feaa60] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/03_lastfm.luac
[0x1feaa60] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/04_musicbrainz.luac
[0x1feaa60] lua art finder debug: Trying Lua scripts in /usr/share/vlc/lua/meta/art
[0x1feaa60] main art finder debug: no art finder module matching "any" could be loaded
[0x1feaa60] main art finder debug: TIMER module_need() : 1.827 ms - Total 1.827 ms / 1 intvls (Avg 1.827 ms)
[0x1dcc9c0] main playlist debug: art not found for finches.wav
[0x1dd0d10] main demux debug: looking for access_demux module: 2 candidates
[0x1dd0d10] main demux debug: no access_demux module matching "file" could be loaded
[0x1dd0d10] main demux debug: TIMER module_need() : 2.824 ms - Total 2.824 ms / 1 intvls (Avg 2.824 ms)
[0x1dcfcf0] main input debug: creating access 'file' path='/home/paddy/Music/NoBackup-Misc/Sound effects/Birdsong/finches.wav'
[0x1dd1890] main access debug: looking for access module: 2 candidates
[0x1dd1890] filesystem access debug: opening file `/home/paddy/Music/NoBackup-Misc/Sound effects/Birdsong/finches.wav'
[0x1dd1890] main access debug: using access module "filesystem"
[0x1dd1890] main access debug: TIMER module_need() : 0.151 ms - Total 0.151 ms / 1 intvls (Avg 0.151 ms)
[0x1dd1ad0] main stream debug: Using AStream*Stream
[0x1dd1ad0] main stream debug: pre buffering
[0x1dd1ad0] main stream debug: received first data after 0 ms
[0x1dd1ad0] main stream debug: pre-buffering done 1024 bytes in 0s - 55555 KiB/s
[0x1dd2430] main stream debug: looking for stream_filter module: 5 candidates
[0x1dd2430] main stream debug: no stream_filter module matching "any" could be loaded
[0x1dd2430] main stream debug: TIMER module_need() : 0.098 ms - Total 0.098 ms / 1 intvls (Avg 0.098 ms)
[0x1dd2430] main stream debug: looking for stream_filter module: 1 candidate
[0x1dd2430] main stream debug: using stream_filter module "stream_filter_record"
[0x1dd2430] main stream debug: TIMER module_need() : 0.095 ms - Total 0.095 ms / 1 intvls (Avg 0.095 ms)
[0x1dcfcf0] main input debug: creating demux: access='file' demux=''  path='/home/paddy/Music/NoBackup-Misc/Sound  effects/Birdsong/finches.wav'
[0x1dd54f0] main demux debug: looking for demux module: 52 candidates
[0x1dd54f0] wav demux debug: chunk: fcc=`fmt ` size=16
[0x1dd54f0] wav demux debug: format: 0x0001, fourcc: araw, channels: 1,  freq: 11025 Hz, bitrate: 21Ko/s, blockalign: 2, bits/samples: 16, extra  size: 0
[0x1dd54f0] wav demux debug: found Raw audio audio format
[0x1dd54f0] wav demux debug: chunk: fcc=`data` size=54128
[0x1dcfcf0] main input debug: selecting program id=0
[0x1dd54f0] main demux debug: using demux module "wav"
[0x1dd54f0] main demux debug: TIMER module_need() : 0.275 ms - Total 0.275 ms / 1 intvls (Avg 0.275 ms)
[0x1dcfcf0] main input debug: looking for a subtitle file in /home/paddy/Music/NoBackup-Misc/Sound effects/Birdsong/
[0x1fee5e0] main decoder debug: looking for decoder module: 32 candidates
[0x1fee5e0] araw decoder debug: samplerate:11025Hz channels:1 bits/sample:16
[0x1fee5e0] main decoder debug: using decoder module "araw"
[0x1fee5e0] main decoder debug: TIMER module_need() : 0.228 ms - Total 0.228 ms / 1 intvls (Avg 0.228 ms)
[0x1fee5e0] main decoder debug: thread (decoder) created at priority 5 (input/decoder.c:301)
[0x1fee5e0] main decoder debug: thread started
[0x1dd0d80] main demux meta debug: looking for meta reader module: 2 candidates
[0x1dd0d80] lua demux meta debug: Trying Lua scripts in /home/paddy/.local/share/vlc/lua/meta/reader
[0x1dd0d80] lua demux meta debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/reader
[0x1dd0d80] lua demux meta debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/reader/filename.luac
[0x1dd0d80] lua demux meta debug: Trying Lua scripts in /usr/share/vlc/lua/meta/reader
[0x1dd0d80] main demux meta debug: no meta reader module matching "any" could be loaded
[0x1dd0d80] main demux meta debug: TIMER module_need() : 0.709 ms - Total 0.709 ms / 1 intvls (Avg 0.709 ms)
[0x1dcfcf0] main input debug: `file:///home/paddy/Music/NoBackup-Misc/Sound%20effects/Birdsong/finches.wav' successfully opened
[0x1dcfcf0] main input debug: Buffering 0%
[0x1dcfcf0] main input debug: creating aout
[0x1dcfcf0] main input debug: Buffering 16%
[0x1dcfcf0] main input debug: Buffering 33%
[0x1dcfcf0] main input debug: Buffering 49%
[0x1feef30] main audio output debug: looking for audio output module: 4 candidates
[0x1dcfcf0] main input debug: Buffering 66%
[0x1feef30] pulse audio output debug: 1 audio channels
[0x1dcfcf0] main input debug: Buffering 83%
[0x1feef30] pulse audio output debug: Pulse mainloop started
[0x1dcfcf0] main input debug: Buffering 99%
[0x1dcfcf0] main input debug: Stream buffering done (349 ms in 22 ms)
[0x1feef30] pulse audio output debug: Pulse stream connected
[0x1feef30] pulse audio output debug: Pulse initialized successfully
[0x1feef30] pulse audio output debug: Buffer metrics: maxlength=17640, tlength=5292, prebuf=4412, minreq=880
[0x1feef30] pulse audio output debug: Using sample spec 'float32le 1ch 11025Hz', channel map 'mono'.
[0x1feef30] pulse audio output debug: Connected to device alsa_output.pci-0000_00_1b.0.analog-stereo (0, not suspended).
[0x1feef30] main audio output debug: using audio output module "pulse"
[0x1feef30] main audio output debug: TIMER module_need() : 59.492 ms - Total 59.492 ms / 1 intvls (Avg 59.492 ms)
[0x1feef30] main audio output debug: output 'f32l' 11025 Hz Mono frame=1 samples/4 bytes
[0x1feef30] main audio output debug: mixer 'f32l' 11025 Hz Mono frame=1 samples/4 bytes
[0x1feef30] main audio output debug: no need for any filter
[0x2bf09d0] main generic debug: looking for audio mixer module: 3 candidates
[0x2bf09d0] main generic debug: using audio mixer module "float32_mixer"
[0x2bf09d0] main generic debug: TIMER module_need() : 0.293 ms - Total 0.293 ms / 1 intvls (Avg 0.293 ms)
[0x1feef30] main audio output debug: input 's16l' 11025 Hz Mono frame=1 samples/2 bytes
[0x2bf1e90] main audio filter debug: looking for audio filter module: 1 candidate
[0x2bf1e90] scaletempo audio filter debug: format: 11025 rate, 1 nch, 4 bps, fl32
[0x2bf1e90] scaletempo audio filter debug: params: 30 stride, 0.200 overlap, 14 search
[0x2bf1e90] scaletempo audio filter debug: 1.000 scale, 330.000  stride_in, 330 stride_out, 264 standing, 66 overlap, 154 search, 550  queue, fl32 mode
[0x2bf1e90] main audio filter debug: using audio filter module "scaletempo"
[0x2bf1e90] main audio filter debug: TIMER module_need() : 0.197 ms - Total 0.197 ms / 1 intvls (Avg 0.197 ms)
[0x1feef30] main audio output debug: filter(s) 's16l'->'f32l' 11025 Hz->11025 Hz Mono->Mono
[0x2bfadd0] main audio filter debug: looking for audio filter module: 14 candidates
[0x2bfadd0] audio_format audio filter debug: s16l->f32l, bits per sample: 16->32
[0x2bfadd0] main audio filter debug: using audio filter module "audio_format"
[0x2bfadd0] main audio filter debug: TIMER module_need() : 0.130 ms - Total 0.130 ms / 1 intvls (Avg 0.130 ms)
[0x1feef30] main audio output debug: found a filter for the whole conversion
[0x1feef30] main audio output debug: filter(s) 'f32l'->'f32l' 12127 Hz->11025 Hz Mono->Mono
[0x2bfb1c0] main audio filter debug: looking for audio filter module: 14 candidates
[0x2bfb1c0] bandlimited_resampler audio filter debug: f32l/12127KHz/1->f32l/11025KHz/1
[0x2bfb1c0] main audio filter debug: using audio filter module "bandlimited_resampler"
[0x2bfb1c0] main audio filter debug: TIMER module_need() : 0.112 ms - Total 0.112 ms / 1 intvls (Avg 0.112 ms)
[0x1feef30] main audio output debug: found a filter for the whole conversion
[0x1fee5e0] main decoder debug: End of audio preroll
[0x1dcfcf0] main input debug: Decoder buffering done in 38 ms
[0x1feef30] main audio output warning: **[COLOR=Orange]PTS is out of range (-9909), dropping buffer[/COLOR]**
[0x1feef30] pulse audio output debug: Pulse stream started
[0x1dcfcf0] main input debug: EOF reached
[0x1dcc9c0] main playlist debug: finished input
[0x1fee5e0] main decoder debug: removing module "araw"
[0x1fee5e0] main decoder debug: killing decoder fourcc `s16l', 0 PES in FIFO
[0x2bfadd0] main audio filter debug: removing module "audio_format"
[0x2bf1e90] main audio filter debug: removing module "scaletempo"
[0x2bfb1c0] main audio filter debug: removing module "bandlimited_resampler"
[0x1feef30] pulse audio output debug: Pulse Close
[0x1feef30] main audio output debug: removing module "pulse"
[0x2bf09d0] main generic debug: removing module "float32_mixer"
[0x1dcfcf0] main input debug: releasing aout
[0x1dd54f0] main demux debug: removing module "wav"
[0x1dd2430] main stream debug: removing module "stream_filter_record"
[0x1dd1890] main access debug: removing module "filesystem"
[0x1dcfcf0] main input debug: Program doesn't contain anymore ES
[0x1dcc9c0] main playlist debug: dead input
[0x1dcfcf0] main input debug: thread ended
[0x1dcc9c0] main playlist debug: changing item without a request (current 0/1)
[0x1dcc9c0] main playlist debug: nothing to play
**[COLOR=DarkRed]^C[/COLOR]**[0x7fa3cc000b40] signals interface error: [COLOR=Red]**Caught Interrupt signal, exiting...**[/COLOR]
[0x1d93910] main libvlc debug: deactivating the playlist
[0x1dcc9c0] main playlist debug: Deactivate
[0x2bf09d0] main playlist export debug: saving Media Library to file /home/paddy/.local/share/vlc/ml.xspf
[0x2bf09d0] main playlist export debug: looking for playlist export module: 1 candidate
[0x2bf09d0] main playlist export debug: using playlist export module "export"
[0x2bf09d0] main playlist export debug: TIMER module_need() : 0.457 ms - Total 0.457 ms / 1 intvls (Avg 0.457 ms)
[0x2bf09d0] main playlist export debug: removing module "export"
[0x1dcc9c0] main playlist debug: Deactivated
[0x1d93910] main libvlc debug: removing all services discovery tasks
[0x1d93910] main libvlc debug: removing all interfaces
[0x7fa3cc004a60] main interface debug: removing module "dummy"
[0x1dd3c90] main interface debug: removing module "globalhotkeys"
[0x7fa3cc000b40] main interface debug: removing module "signals"
[0x1dd3f60] main interface debug: removing module "inhibit"
[0x1dcfcf0] main input debug: TIMER input launching for 'finches.wav' : 5.424 ms - Total 5.424 ms / 1 intvls (Avg 5.424 ms)
[0x1fe8940] main interface debug: removing module "dbus"
[0x1dd57f0] main interface debug: removing module "hotkeys"
[0x1dcc9c0] main playlist debug: destroying
[0x1d93910] main libvlc debug: TIMER ML Load : Total 2.443 ms / 1 intvls (Avg 2.443 ms)
[0x1d93910] main libvlc debug: TIMER Items array build : Total 0.061 ms / 2 intvls (Avg 0.031 ms)
[0x1d93910] main libvlc debug: TIMER Preparse run : Total 1.719 ms / 1 intvls (Avg 1.719 ms)
[0x1d93910] main libvlc debug: TIMER ML Dump : Total 1.148 ms / 1 intvls (Avg 1.148 ms)
[0x1d93910] main libvlc debug: removing stats
[0x1d93910] main libvlc debug: removing module "memcpymmxext"
```> **John-B said:**
> **main audio output warning: PTS is out of range (-9691), dropping buffer**
andrew.46 had the same error, as did I, so I suspect it's nothing.

> **mister_p_1998 said:**
> ... if I restart gnome or log out and back in again it suddenly worksNope, that doesn't work for me.

---

### Post by mc4man on 2011-07-01
It's also curious that you've reported gnome-mplayer as unable to play while mplayer can - gnome-mplayer is just a frontend to mplayer that adds quite a # of parameters to mplayer's cli

Are you able to play more typical .wav's with either? (like those from an audio cd

For vlc I'd try either this command to start vlc, then drag and drop the .wav onto and see
```
vlc --reset-config --reset-plugins-cache
```

or probably  better to just go into home folder (view > show hidden files) and delete these 3 folders at below locations
.cache/[COLOR="Blue"]vlc[/COLOR]
.config/[COLOR="Blue"]vlc[/COLOR]
.local/share/[COLOR="Blue"]vlc[/COLOR]

---

### Post by Paddy Landau on 2011-07-01
> **mc4man said:**
> It's also curious that you've reported gnome-mplayer as unable to play while mplayer can
Not gnome-mplayer, but gnome-media-player. I've just discovered that gnome-media-player is a front-end to some players including VLC, so we dismiss that as a red herring.

> **mc4man said:**
> Are you able to play more typical .wav's with either? (like those from an audio cd
Ah, you've got something there. I searched my disk for other WAV files, and some play; some play greatly distorted; and others don't play.

> **mc4man said:**
> ```
vlc --reset-config --reset-plugins-cache
```or probably  better to just go into home folder (view > show hidden files) and delete these 3 folders at below locations
.cache/[COLOR=Blue]vlc[/COLOR]
.config/[COLOR=Blue]vlc[/COLOR]
.local/share/[COLOR=Blue]vlc[/COLOR]
I deleted the folders and started VLC with the two options, but it made no difference.

Oh well, it's not a deal-killer. I'll VLC for all audio other than WAV, and Media Player for WAV.

Thanks for all your help!

---

### Post by mc4man on 2011-07-01
Some  times things seem to defy explanation

If continued curious you could try a different aout, though without making some changes in pref's will still go thru pulseaudio (not going to suggest bypassing pulse for such a 'minor' issue

For instance install the vlc-plugin-sdl, then to start vlc, ect.
```
vlc --aout sdl
```

---

### Post by Paddy Landau on 2011-07-02
> **mc4man said:**
> ... install the vlc-plugin-sdl ...```
vlc --aout sdl
```That works! Testing other files, they still work, too.

I see that I make the change permanent through Tools > Preferences > Audio > Output Module > Simple DirectMedia Layer audio output.

I'll mark this solved. Thank you.

---

### Post by John-B on 2011-07-02
> **mc4man said:**
> For instance install the vlc-plugin-sdl, then to start vlc, ect.
```
vlc --aout sdl
```
mc4man thanks it worked for me also :)

> **Paddy Landau said:**
> I see that I make the change permanent through Tools > Preferences > Audio > Output Module > Simple DirectMedia Layer audio output.
Paddy Landau and thanks to you... I followed your advise and set it permanent :)

---

