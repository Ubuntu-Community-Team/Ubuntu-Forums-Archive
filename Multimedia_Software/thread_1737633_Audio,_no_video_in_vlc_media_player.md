---
title: "Audio, no video in vlc media player"
date: 2011-04-23
forum: Multimedia Software
---

### Post by c0dege3k on 2011-04-23
I'm trying to play a dvd in vlc, but I only get the audio- no video. I tried it with just a regular video, same thing happens.

Ran it from the terminal and got this (all before starting the video)- don't know if it'll help:
```

VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x1c46120] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0x7f919e8f3b20, 0x7f919e8f3a80)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to srand(1303982417)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:3311): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)

```

EDIT: oh, and before I upgraded to x64, my videos were working.

---

### Post by handy on 2011-04-25
I just tested my vlc in the Terminal & got most of your Terminal output plus some more errors at the end, but it still worked fine.

Have you enabled & installed the Restricted Formats:

[https://help.ubuntu.com/community/RestrictedFormats/#Playing%20Restricted%20Formats](https://help.ubuntu.com/community/RestrictedFormats/#Playing%20Restricted%20Formats)

[edit:] Possibly VLC is experiencing a similar problem to mPlayer as seen here:

[http://ubuntuforums.org/showthread.php?t=1705713](http://ubuntuforums.org/showthread.php?t=1705713)

---

### Post by c0dege3k on 2011-04-25
I had installed the restricted extras, and ran the command again just for kicks- same result. And that post might be similar to my problem, but I don't have enough experience with Linux/media stuff to really be sure

---

### Post by Yellow Pasque on 2011-04-25
What kind of file are you trying to play?

---

### Post by c0dege3k on 2011-04-25
I think it's all video files, but I've only tried .avi, .mp4 and DVDs

---

### Post by Yellow Pasque on 2011-04-25
How did you "upgrade" to x64 (fresh install, i hope)?

---

### Post by c0dege3k on 2011-04-25
Yeah, it was a fresh install

---

### Post by Yellow Pasque on 2011-04-25
Ok, is it just vlc, or do other players have issues?

---

### Post by bcm67063 on 2011-04-25
I went to Ubuntu 64 Maverick and VLC would not play my "Super Natural" discs.  I started using MPLAYER and they play just fine also SMPLAYER works.  Linux has lots of choices and so I use these instead of VLC but I do use VLC for music.  I was busy at the time and didn't want to try for a fix.

---

### Post by c0dege3k on 2011-04-25
Well, the default movie player can play my video files, but not DVDs. But I haven't tried any other third party apps- just tried to get mPlayer and said it was an "untrusted source"

---

### Post by mc4man on 2011-04-25
Your best bet to get anything useful from the terminal is to run vlc in verbose mode. It will produce a lot  of output so maybe better to do in 2 steps
Start vlc
```
vlc -vvv
```
Look thru the output (90 - 100 lines), mainly for any failed plugins (whatever.so
It should stop with something like this at or near the end
>  main interface debug: using interface module "qt4"
Make note of where that is and then open a video file from vlc - look thru or post what additionally shows up in the terminal (could be another 100 lines or more - but possibly will have some relevant info

---

### Post by c0dege3k on 2011-04-25
Ok, for some reason, starting it this time I was able to play normal video files, but DVDs wouldn't even start. When it first started up, it gave me the warning on the third code line, don't know if that's affecting it.

```

[0x8286914] main libvlc debug: checking plugin modules
[0x8286914] main libvlc debug: loading plugins cache file /usr/lib/vlc/plugins/plugins-04041e-7e8.dat
[0x8286914] main libvlc warning: cannot read /usr/lib/vlc/plugins/plugins-04041e-7e8.dat (No such file or directory)

```

And here's what happened when I opened the DVD (I bolded the line that said it couldn't read from the DVD) :

```

[0x9f61cd4] main interface debug: TIMER module_need() : 360.068 ms - Total 360.068 ms / 1 intvls (Avg 360.068 ms)
[0x9f61cd4] qt4 interface warning: Input option: dvdnav-caching=300
[0xa0a0794] main playlist debug: adding item `dvd:///dev/dvd' ( dvd:///dev/dvd )
[0xa0a0794] main playlist debug: rebuilding array of current - root Playlist
[0xa0a0794] main playlist debug: rebuild done - 1 items, index -1
[0xa0a0794] main playlist debug: processing request item dvd:///dev/dvd node null skip 0
[0xa0a0794] main playlist debug: resyncing on dvd:///dev/dvd
[0xa0a0794] main playlist debug: dvd:///dev/dvd is at 0
[0xa0a0794] main playlist debug: starting new item
[0xa0a0794] main playlist debug: creating new input thread
[0xb57005f4] main input debug: Creating an input for 'dvd:///dev/dvd'
[0xb57005f4] main input debug: thread (input) created at priority 10 (input/input.c:214)
[0x9f61cd4] qt4 interface debug: Adding a new MRL to recent ones: dvd:///dev/dvd
[0x9f61cd4] qt4 interface debug: IM: Setting an input
[0xa0a0794] main playlist debug: meta ok for (null), need to fetch art
[0xb57005f4] main input debug: thread started
[0xb57005f4] main input debug: using timeshift granularity of 50 MiB
[0xb57005f4] main input debug: using timeshift path '/tmp'
[0xb57005f4] main input debug: `dvd:///dev/dvd' gives access `dvd' demux `' path `/dev/dvd'
[0xb57005f4] main input debug: creating demux: access='dvd' demux='' path='/dev/dvd'
[0xa31f3dc] main demux debug: looking for access_demux module: 2 candidates
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdnav: DVD Title: CHARLOTTE_DISC1
libdvdnav: DVD Serial Number: 330F6B49
libdvdnav: DVD Title (Alternative): CHARLOTTE_DISC1
libdvdnav: Unable to find map file '/home/c0dege3k/.dvdnav/CHARLOTTE_DISC1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
Warning: call to srand(130556)
[0xa31f3dc] dvdnav demux debug: trying to go to dvd menu
libdvdnav: Suspected RCE Region Protection!!!
Warning: call to rand()
[0xa31f3dc] main demux debug: using access_demux module "dvdnav"
[0xa31f3dc] main demux debug: TIMER module_need() : 29.236 ms - Total 29.236 ms / 1 intvls (Avg 29.236 ms)
[0xa317744] main demux meta debug: looking for meta reader module: 2 candidates
[0xa317744] lua demux meta debug: Trying Lua scripts in /home/c0dege3k/.local/share/vlc/lua/meta/reader
[0xa317744] lua demux meta debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/reader
[0xa317744] lua demux meta debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/reader/filename.luac
[0xa317744] lua demux meta debug: Trying Lua scripts in /usr/share/vlc/lua/meta/reader
[0xa317744] main demux meta debug: no meta reader module matching "any" could be loaded
[0xa317744] main demux meta debug: TIMER module_need() : 0.720 ms - Total 0.720 ms / 1 intvls (Avg 0.720 ms)
[0xa321adc] main demux meta debug: looking for meta fetcher module: 1 candidate
[0xa321adc] lua demux meta debug: Trying Lua scripts in /home/c0dege3k/.local/share/vlc/lua/meta/fetcher
[0xa321adc] lua demux meta debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/fetcher
[0xa321adc] lua demux meta debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/fetcher/tvrage.luac
[0xa321adc] main demux meta debug: using meta fetcher module "lua"
[0xa321adc] main demux meta debug: TIMER module_need() : 0.586 ms - Total 0.586 ms / 1 intvls (Avg 0.586 ms)
[0xa321adc] main demux meta debug: removing module "lua"
[0xa0a0794] main playlist debug: searching art for CHARLOTTE_DISC1
[0xa32117c] main art finder debug: looking for art finder module: 2 candidates
[0xa32117c] lua art finder debug: Trying Lua scripts in /home/c0dege3k/.local/share/vlc/lua/meta/art
[0xa32117c] lua art finder debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/art
[0xa32117c] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/01_googleimage.luac
[0xa32117c] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/02_frenchtv.luac
[0xa32117c] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/03_lastfm.luac
[0xa32117c] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/04_musicbrainz.luac
[0xa32117c] lua art finder debug: Trying Lua scripts in /usr/share/vlc/lua/meta/art
[0xa32117c] main art finder debug: no art finder module matching "any" could be loaded
[0xa32117c] main art finder debug: TIMER module_need() : 1.816 ms - Total 1.816 ms / 1 intvls (Avg 1.816 ms)
[0xa0a0794] main playlist debug: art not found for CHARLOTTE_DISC1
[0xb57005f4] main input debug: `dvd:///dev/dvd' successfully opened
[0xa31f3dc] dvdnav demux debug: DVDNAV_HOP_CHANNEL
[0xb57005f4] main input debug: ES_OUT_RESET_PCR called
[0xa31f3dc] dvdnav demux debug: DVDNAV_VTS_CHANGE
[0xa31f3dc] dvdnav demux debug:      - vtsN=7
[0xa31f3dc] dvdnav demux debug:      - domain=8
[0xb57005f4] main input debug: ES_OUT_RESET_PCR called
[0xa31f3dc] dvdnav demux debug: DVDNAV_CELL_CHANGE
[0xa31f3dc] dvdnav demux debug:      - cellN=1
[0xa31f3dc] dvdnav demux debug:      - pgN=1
[0xa31f3dc] dvdnav demux debug:      - cell_length=1620000
[0xa31f3dc] dvdnav demux debug:      - pg_length=1620000
[0xa31f3dc] dvdnav demux debug:      - pgc_length=1620000
[0xa31f3dc] dvdnav demux debug:      - cell_start=0
[0xa31f3dc] dvdnav demux debug:      - pg_start=0
[0xa31f3dc] dvdnav demux debug: DVDNAV_SPU_CLUT_CHANGE
[0xa31f3dc] dvdnav demux debug: DVDNAV_SPU_STREAM_CHANGE
[0xa31f3dc] dvdnav demux debug:      - physical_wide=0
[0xa31f3dc] dvdnav demux debug:      - physical_letterbox=0
[0xa31f3dc] dvdnav demux debug:      - physical_pan_scan=0
[0xa31f3dc] dvdnav demux debug: buttonUpdate not done b=1 t=0
[0xb57005f4] main input debug: selecting program id=0
[0xa3176ec] main decoder debug: looking for decoder module: 30 candidates
[0xa3176ec] avcodec decoder debug: libavcodec initialized (interface 0x344802)
[0xa3176ec] avcodec decoder warning: refusing to decode non validated subtitle codec
[0xa3176ec] main decoder debug: using decoder module "spudec"
[0xa3176ec] main decoder debug: TIMER module_need() : 0.988 ms - Total 0.988 ms / 1 intvls (Avg 0.988 ms)
[0xa3b06b4] main packetizer debug: looking for packetizer module: 21 candidates
[0xa3b06b4] main packetizer debug: using packetizer module "spudec"
[0xa3b06b4] main packetizer debug: TIMER module_need() : 0.113 ms - Total 0.113 ms / 1 intvls (Avg 0.113 ms)
[0xa3176ec] main decoder debug: thread (decoder) created at priority 0 (input/decoder.c:301)
[0xa3176ec] main decoder debug: thread started
[0xa3176ec] spudec decoder debug: invalid starting packet (size < 4 or pts <=0)
[0xa3176ec] spudec decoder debug: spu size: 0, i_pts: 0 i_buffer: 128
[0xa31f3dc] dvdnav demux debug: DVDNAV_AUDIO_STREAM_CHANGE
[0xa31f3dc] dvdnav demux debug:      - physical=0
[0xb57005f4] main input debug: Buffering 0%
[0xa31f3dc] dvdnav demux debug: buttonUpdate not done b=1 t=0
[0xb57005f4] main input debug: Buffering 0%
[0xa321a0c] main decoder debug: looking for decoder module: 30 candidates
[0xa321a0c] avcodec decoder debug: libavcodec already initialized
[0xa321a0c] avcodec decoder debug: trying to use direct rendering
[0xa321a0c] avcodec decoder debug: ffmpeg codec (MPEG-1/2 Video) started
[0xa321a0c] main decoder debug: using decoder module "avcodec"
[0xa321a0c] main decoder debug: TIMER module_need() : 0.967 ms - Total 0.967 ms / 1 intvls (Avg 0.967 ms)
[0xa3afcf4] main packetizer debug: looking for packetizer module: 21 candidates
[0xa3afcf4] main packetizer debug: using packetizer module "packetizer_mpegvideo"
[0xa3afcf4] main packetizer debug: TIMER module_need() : 0.138 ms - Total 0.138 ms / 1 intvls (Avg 0.138 ms)
[0xa321a0c] main decoder debug: thread (decoder) created at priority 0 (input/decoder.c:301)
[0xa321a0c] main decoder debug: thread started
[0xa31f3dc] dvdnav demux debug: buttonUpdate not done b=1 t=0
[0xb57005f4] main input debug: Buffering 1%
[0xb57005f4] main input debug: Buffering 1%
[0xb57005f4] main input debug: Buffering 2%
[0xb57005f4] main input debug: Buffering 2%
[0xb57005f4] main input debug: Buffering 3%
[0xa3af1dc] main decoder debug: looking for decoder module: 30 candidates
[0xa3af1dc] main decoder debug: using decoder module "mpeg_audio"
[0xa3af1dc] main decoder debug: TIMER module_need() : 0.248 ms - Total 0.248 ms / 1 intvls (Avg 0.248 ms)
[0xa3af1dc] main decoder debug: thread (decoder) created at priority 5 (input/decoder.c:301)
[0xa3afcf4] packetizer_mpegvideo packetizer debug: size 720x480 fps=29.970
[0xb57005f4] main input debug: no usable vout present, spawning one
[0xa3b794c] main spu text debug: looking for text renderer module: 2 candidates
[0xa3b794c] freetype spu text debug: Building font databases.
[0xa3b794c] freetype spu text debug: Using Serif Bold as font from file /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
[0xa3b794c] freetype spu text debug: using fontsize: 2
[0xa3b794c] main spu text debug: using text renderer module "freetype"
[0xa3b794c] main spu text debug: TIMER module_need() : 2.646 ms - Total 2.646 ms / 1 intvls (Avg 2.646 ms)
[0xa3bd0d4] main scale debug: looking for video filter2 module: 18 candidates
[0xa3bd0d4] swscale scale debug: 32x32 chroma: YUVA -> 16x16 chroma: YUVA with scaling using Bicubic (good quality)
[0xa3bd0d4] main scale debug: using video filter2 module "swscale"
[0xa3bd0d4] main scale debug: TIMER module_need() : 1.007 ms - Total 1.007 ms / 1 intvls (Avg 1.007 ms)
[0xa3be2e4] main scale debug: looking for video filter2 module: 18 candidates
[0xa3be2e4] yuvp scale debug: YUVP to YUVA converter
[0xa3be2e4] main scale debug: using video filter2 module "yuvp"
[0xa3be2e4] main scale debug: TIMER module_need() : 0.187 ms - Total 0.187 ms / 1 intvls (Avg 0.187 ms)
[0xa436b94] main video output debug: window size: 853x480
[0xa436b94] main video output debug: Deinterlacing available
[0xa436b94] main video output debug: deinterlace 0, mode blend, is_needed 0
[0xa3af1dc] main decoder debug: thread started
[0xb57005f4] main input debug: Buffering 3%
[0xb57005f4] main input debug: Buffering 4%
[0xb57005f4] main input debug: Buffering 4%
[0xa3af1dc] mpeg_audio decoder debug: waiting for PTS
[0xa436b94] main video output debug: looking for video output module: 1 candidate
[0xa436b94] vout_wrapper video output debug: Opening vout display wrapper
[0xa3fa14c] main generic debug: looking for vout display module: 7 candidates
[0xa3fa3cc] main window debug: looking for vout window xid module: 4 candidates
[0xa3fa3cc] qt4 window debug: requesting video...
[0x9f61cd4] qt4 interface debug: Title 12
[0x9f61cd4] qt4 interface debug: Chapter: 7
Warning: call to rand()
Warning: call to rand()
[0x9f61cd4] qt4 interface debug: Video was requested 0, 0
[0xa3fa3cc] main window debug: using vout window xid module "qt4"
[0xa3fa3cc] main window debug: TIMER module_need() : 210.930 ms - Total 210.930 ms / 1 intvls (Avg 210.930 ms)
[0xa4d0b8c] main inhibit debug: looking for inhibit module: 1 candidate
[0xa4d0b8c] main inhibit debug: using inhibit module "xdg_screensaver"
[0xa4d0b8c] main inhibit debug: TIMER module_need() : 0.224 ms - Total 0.224 ms / 1 intvls (Avg 0.224 ms)
[0xa4d0b8c] xdg_screensaver inhibit debug: started xdg-screensaver (PID = 6931)
[0xa3fa14c] xcb_xv generic debug: connected to X11.0 server
[0xa3fa14c] xcb_xv generic debug:  vendor : The X.Org Foundation
[0xa3fa14c] xcb_xv generic debug:  version: 10900000
[0xa3fa14c] xcb_xv generic debug: using screen 0x43
[0xa3fa14c] xcb_xv generic debug: using XVideo extension v2.2
[0xa3fa14c] xcb_xv generic error: no available XVideo adaptor
[0xa4d0b8c] main inhibit debug: removing module "xdg_screensaver"
[0xa3fa3cc] qt4 window debug: releasing video...
[0x9f61cd4] qt4 interface debug: Video is not needed anymore
[0xa3fa3cc] main window debug: removing module "qt4"
[0xa3fa3cc] main window debug: looking for vout window xid module: 4 candidates
[0xa3fa3cc] qt4 window debug: requesting video...
[0x9f61cd4] qt4 interface debug: Video was requested 0, 0
[0xa3fa3cc] main window debug: using vout window xid module "qt4"
[0xa3fa3cc] main window debug: TIMER module_need() : 169.728 ms - Total 169.728 ms / 1 intvls (Avg 169.728 ms)
[0xa23ac0c] main inhibit debug: looking for inhibit module: 1 candidate
[0xa23ac0c] main inhibit debug: using inhibit module "xdg_screensaver"
[0xa23ac0c] main inhibit debug: TIMER module_need() : 0.300 ms - Total 0.300 ms / 1 intvls (Avg 0.300 ms)
[0xa23ac0c] xdg_screensaver inhibit debug: started xdg-screensaver (PID = 6964)
[0xa3fa14c] xcb_x11 generic debug: connected to X11.0 server
[0xa3fa14c] xcb_x11 generic debug:  vendor : The X.Org Foundation
[0xa3fa14c] xcb_x11 generic debug:  version: 10900000
[0xa3fa14c] xcb_x11 generic debug: using screen 0x43
[0xa3fa14c] xcb_x11 generic debug: X11 visual with alpha-channel not supported
[0xa3fa14c] xcb_x11 generic debug: using X11 visual ID 0x21
[0xa3fa14c] xcb_x11 generic debug:  24 bits depth
[0xa3fa14c] xcb_x11 generic debug:  32 bits per pixel
[0xa3fa14c] xcb_x11 generic debug:  32 bits line pad
[0xa3fa14c] xcb_x11 generic debug: using X11 window 05200000
[0xa3fa14c] xcb_x11 generic debug: using X11 graphic context 05200001
[0xa3fa14c] main generic debug: VoutDisplayEvent 'fullscreen' 0
[0xa3fa14c] main generic debug: VoutDisplayEvent 'resize' 853x480 window
[0xa3fa14c] main generic debug: using vout display module "xcb_x11"
[0xa3fa14c] main generic debug: TIMER module_need() : 703.255 ms - Total 703.255 ms / 1 intvls (Avg 703.255 ms)
[0xa3fa14c] main generic debug: A filter to adapt decoder to display is needed
[0xa4d26c4] main filter debug: looking for video filter2 module: 18 candidates
[0xa4d26c4] swscale filter debug: 720x480 chroma: I420 -> 720x480 chroma: RV32 with scaling using Bicubic (good quality)
[0xa4d26c4] main filter debug: using video filter2 module "swscale"
[0xa4d26c4] main filter debug: TIMER module_need() : 0.261 ms - Total 0.261 ms / 1 intvls (Avg 0.261 ms)
[0xa3fa14c] main generic debug: Filter 'Swscale' (0xa4d26c4) appended to chain
[0xa436b94] main video output debug: using video output module "vout_wrapper"
[0xa436b94] main video output debug: TIMER module_need() : 703.844 ms - Total 703.844 ms / 1 intvls (Avg 703.844 ms)
[0xa436b94] main video output debug: got 1 direct buffer(s)
[0xa436b94] main video output debug: pic render sz 720x480, of (0,0), vsz 720x480, 4cc I420, sar 32:27, msk r0x0 g0x0 b0x0
[0xa436b94] main video output debug: pic in sz 720x480, of (0,0), vsz 720x480, 4cc I420, sar 32:27, msk r0x0 g0x0 b0x0
[0xa436b94] main video output debug: pic out sz 720x480, of (0,0), vsz 720x480, 4cc I420, sar 32:27, msk r0x0 g0x0 b0x0
[0xa436b94] main video output debug: direct render, mapping render pictures 0-23 to system pictures 1-24
[0xa321a0c] avcodec decoder debug: using direct rendering
ac-tex damaged at 5 7
ac-tex damaged at 9 23
invalid mb type in I Frame at 0 16
invalid mb type in I Frame at 0 17
invalid mb type in I Frame at 0 18
invalid mb type in I Frame at 0 19
invalid mb type in I Frame at 0 20
invalid mb type in I Frame at 0 21
invalid mb type in I Frame at 0 22
invalid mb type in I Frame at 0 23
invalid mb type in I Frame at 0 24
invalid mb type in I Frame at 0 25
invalid mb type in I Frame at 0 26
invalid mb type in I Frame at 0 27
invalid mb type in I Frame at 0 28
invalid mb type in I Frame at 0 29
Warning MVs not available
ac-tex damaged at 5 7
ac-tex damaged at 9 23
invalid mb type in I Frame at 0 16
invalid mb type in I Frame at 0 17
invalid mb type in I Frame at 0 18
invalid mb type in I Frame at 0 19
invalid mb type in I Frame at 0 20
invalid mb type in I Frame at 0 21
invalid mb type in I Frame at 0 22
invalid mb type in I Frame at 0 23
invalid mb type in I Frame at 0 24
invalid mb type in I Frame at 0 25
invalid mb type in I Frame at 0 26
invalid mb type in I Frame at 0 27
invalid mb type in I Frame at 0 28
invalid mb type in I Frame at 0 29
Warning MVs not available
[0xa321a0c] main decoder debug: End of video preroll
[0xa3fa14c] xcb_x11 generic debug: display is visible
[0xa3fa14c] main generic warning: VoutDisplayEvent 'pictures invalid'
[0xa3fa14c] main generic debug: Filter 0xa4d26c4 removed from chain
[0xa4d26c4] main filter debug: removing module "swscale"
[0xa3fa14c] main generic debug: A filter to adapt decoder to display is needed
[0xa3fd3ac] main filter debug: looking for video filter2 module: 18 candidates
[0xa3fd3ac] swscale filter debug: 720x480 chroma: I420 -> 853x480 chroma: RV32 with scaling using Bicubic (good quality)
[0xa3fd3ac] main filter debug: using video filter2 module "swscale"
[0xa3fd3ac] main filter debug: TIMER module_need() : 1.309 ms - Total 1.309 ms / 1 intvls (Avg 1.309 ms)
[0xa3fa14c] main generic debug: Filter 'Swscale' (0xa3fd3ac) appended to chain
[0xa321a0c] main decoder debug: Received first picture
[0xa3b794c] freetype spu text debug: using fontsize: 30
[0xa3fb834] main blend debug: looking for video blending module: 1 candidate
[0xa3fb834] blend blend debug: chroma: YUVA -> I420
[0xa3fb834] main blend debug: using video blending module "blend"
[0xa3fb834] main blend debug: TIMER module_need() : 0.181 ms - Total 0.181 ms / 1 intvls (Avg 0.181 ms)
[0xa436b94] main video output debug: Post-processing available
[0xa436b94] main video output warning: vlc_object_find_name(postproc) is not safe!
[0xb57005f4] main input debug: Buffering 5%
[0xb57005f4] main input debug: Buffering 5%
[0xb57005f4] main input debug: Buffering 6%
[0xb57005f4] main input debug: Buffering 49%
[0xa53732c] main decoder debug: looking for decoder module: 30 candidates
[0xa53732c] main decoder debug: using decoder module "a52"
[0xa53732c] main decoder debug: TIMER module_need() : 0.281 ms - Total 0.281 ms / 1 intvls (Avg 0.281 ms)
[0xa53732c] main decoder debug: thread (decoder) created at priority 5 (input/decoder.c:301)
[0xa53732c] main decoder debug: thread started
[0xa3af1dc] main decoder debug: removing module "mpeg_audio"
[0xa3af1dc] main decoder debug: killing decoder fourcc `mpga', 0 PES in FIFO
[0xa53732c] a52 decoder debug: emulated sync word (no sync on following frame)
[0xb57005f4] main input debug: Buffering 56%
[0xb57005f4] main input debug: Buffering 77%
[0xb57005f4] main input debug: Stream buffering done (317 ms in 2405 ms)
[0xb57005f4] main input debug: Decoder buffering done in 0 ms
[0xa53732c] a52 decoder debug: A/52 channels:2 samplerate:48000 bitrate:192000
[0xb57005f4] main input debug: creating aout
[0xa3bad74] main audio output debug: looking for audio output module: 4 candidates
[0xa3bad74] pulse audio output debug: 2 audio channels
skipped MB in I frame at 7 7
ac-tex damaged at 10 23
invalid mb type in I Frame at 0 16
invalid mb type in I Frame at 0 17
invalid mb type in I Frame at 0 18
invalid mb type in I Frame at 0 19
invalid mb type in I Frame at 0 20
invalid mb type in I Frame at 0 21
invalid mb type in I Frame at 0 22
invalid mb type in I Frame at 0 23
invalid mb type in I Frame at 0 24
invalid mb type in I Frame at 0 25
invalid mb type in I Frame at 0 26
invalid mb type in I Frame at 0 27
invalid mb type in I Frame at 0 28
invalid mb type in I Frame at 0 29
[0xa3bad74] pulse audio output debug: Pulse mainloop started
[0xa3bad74] pulse audio output debug: Pulse stream connected
[0xa3bad74] pulse audio output debug: Pulse initialized successfully
[0xa3bad74] pulse audio output debug: Buffer metrics: maxlength=153600, tlength=46080, prebuf=38400, minreq=7680
[0xa3bad74] pulse audio output debug: Using sample spec 'float32le 2ch 48000Hz', channel map 'front-left,front-right'.
[0xa3bad74] pulse audio output debug: Connected to device alsa_output.pci-0000_00_1b.0.analog-stereo (0, not suspended).
[0xa3bad74] main audio output debug: using audio output module "pulse"
[0xa3bad74] main audio output debug: TIMER module_need() : 116.073 ms - Total 116.073 ms / 1 intvls (Avg 116.073 ms)
[0xa3bad74] main audio output debug: output 'f32l' 48000 Hz Dolby frame=1 samples/8 bytes
[0xa3bad74] main audio output debug: mixer 'f32l' 48000 Hz Dolby frame=1 samples/8 bytes
[0xa3bad74] main audio output debug: no need for any filter
[0xa53932c] main generic debug: looking for audio mixer module: 3 candidates
[0xa53932c] main generic debug: using audio mixer module "float32_mixer"
[0xa53932c] main generic debug: TIMER module_need() : 0.219 ms - Total 0.219 ms / 1 intvls (Avg 0.219 ms)
[0xa3bad74] main audio output debug: input 'a52 ' 48000 Hz Dolby frame=1536 samples/768 bytes
[0xa53bf1c] main audio filter debug: looking for audio filter module: 1 candidate
[0xa53bf1c] scaletempo audio filter debug: format: 48000 rate, 2 nch, 4 bps, fl32
[0xa53bf1c] scaletempo audio filter debug: params: 30 stride, 0.200 overlap, 14 search
[0xa53bf1c] scaletempo audio filter debug: 1.000 scale, 1440.000 stride_in, 1440 stride_out, 1152 standing, 288 overlap, 672 search, 2400 queue, fl32 mode
[0xa53bf1c] main audio filter debug: using audio filter module "scaletempo"
[0xa53bf1c] main audio filter debug: TIMER module_need() : 0.242 ms - Total 0.242 ms / 1 intvls (Avg 0.242 ms)
[0xa3bad74] main audio output debug: filter(s) 'a52 '->'f32l' 48000 Hz->48000 Hz Dolby->Dolby
[0xa53c24c] main audio filter debug: looking for audio filter module: 14 candidates
[0xa53c24c] main audio filter debug: using audio filter module "a52tofloat32"
[0xa53c24c] main audio filter debug: TIMER module_need() : 0.908 ms - Total 0.908 ms / 1 intvls (Avg 0.908 ms)
[0xa3bad74] main audio output debug: found a filter for the whole conversion
[0xa3bad74] main audio output debug: filter(s) 'f32l'->'f32l' 52800 Hz->48000 Hz Dolby->Dolby
[0xa53c57c] main audio filter debug: looking for audio filter module: 14 candidates
[0xa53c57c] bandlimited_resampler audio filter debug: f32l/52800KHz/2->f32l/48000KHz/2
[0xa53c57c] main audio filter debug: using audio filter module "bandlimited_resampler"
[0xa53c57c] main audio filter debug: TIMER module_need() : 2.743 ms - Total 2.743 ms / 1 intvls (Avg 2.743 ms)
[0xa3bad74] main audio output debug: found a filter for the whole conversion
[0xa53732c] main decoder debug: End of audio preroll
[0xa3bad74] pulse audio output debug: Pulse stream started
[0xa53732c] a52 decoder debug: emulated sync word (no sync on following frame)
ac-tex damaged at 26 0
ac-tex damaged at 6 3
ac-tex damaged at 18 5
ac-tex damaged at 23 7
invalid mb type in I Frame at 33 9
skipped MB in I frame at 22 11
ac-tex damaged at 16 14
ac-tex damaged at 13 17
skipped MB in I frame at 42 18
skipped MB in I frame at 35 20
ac-tex damaged at 13 23
invalid mb type in I Frame at 29 25
skipped MB in I frame at 1 28
**[0xa31f3dc] dvdnav demux warning: cannot get next block (Error reading from DVD.)**
[0xa31f3dc] dvdnav demux debug: jumping to first title
libdvdnav: Suspected RCE Region Protection!!!
[0xa31f3dc] dvdnav demux debug: DVDNAV_HOP_CHANNEL
[0xb57005f4] main input debug: ES_OUT_RESET_PCR called
[0x9f61cd4] qt4 interface debug: Title 12
[0x9f61cd4] qt4 interface debug: Chapter: 51
[0x9f61cd4] qt4 interface debug: Title 12
[0x9f61cd4] qt4 interface debug: Chapter: 51
[0xa3176ec] spudec decoder debug: invalid starting packet (size < 4 or pts <=0)
[0xa3176ec] spudec decoder debug: spu size: 0, i_pts: 0 i_buffer: 128
[0xa436b94] main video output warning: early picture skipped
[0xa31f3dc] dvdnav demux debug: DVDNAV_VTS_CHANGE
[0xa31f3dc] dvdnav demux debug:      - vtsN=7
[0xa31f3dc] dvdnav demux debug:      - domain=2
[0xb57005f4] main input debug: ES_OUT_RESET_PCR called
[0xa3176ec] spudec decoder debug: invalid starting packet (size < 4 or pts <=0)
[0xa3176ec] spudec decoder debug: spu size: 0, i_pts: 0 i_buffer: 128
[0xa321a0c] avcodec decoder debug: ffmpeg codec (MPEG-1/2 Video) stopped
[0xa321a0c] main decoder debug: removing module "avcodec"
[0xa321a0c] main decoder debug: killing decoder fourcc `mpgv', 0 PES in FIFO
[0xa436b94] main video output debug: [0] 2 0
[0xa436b94] main video output debug: [1] 2 0
[0xa436b94] main video output debug: [2] 2 0
[0xa436b94] main video output debug: [3] 2 0
[0xa436b94] main video output debug: [4] 2 0
[0xa436b94] main video output debug: [5] 2 0
[0xa436b94] main video output debug: [6] 4 0
[0xa436b94] main video output debug: [7] 0 0
[0xa436b94] main video output debug: [8] 0 0
[0xa436b94] main video output debug: [9] 0 0
[0xa436b94] main video output debug: [10] 0 0
[0xa436b94] main video output debug: [11] 2 0
[0xa436b94] main video output debug: [12] 4 0
[0xa436b94] main video output debug: [13] 2 0
[0xa436b94] main video output debug: [14] 2 0
[0xa436b94] main video output debug: [15] 2 0
[0xa436b94] main video output debug: [16] 2 0
[0xa436b94] main video output debug: [17] 2 0
[0xa436b94] main video output debug: [18] 2 0
[0xa436b94] main video output debug: [19] 2 0
[0xa436b94] main video output debug: [20] 2 0
[0xa436b94] main video output debug: [21] 2 0
[0xa436b94] main video output debug: [22] 2 0
[0xa436b94] main video output debug: [23] 2 0
[0xb57005f4] main input debug: saving a free vout
[0xa3afcf4] main packetizer debug: removing module "packetizer_mpegvideo"
[0xa3176ec] main decoder debug: removing module "spudec"
[0xa3176ec] main decoder debug: killing decoder fourcc `spu ', 0 PES in FIFO
[0xa3b06b4] main packetizer debug: removing module "spudec"
[0xa53732c] main decoder debug: removing module "a52"
[0xa53732c] main decoder debug: killing decoder fourcc `a52 ', 0 PES in FIFO
[0xa53c24c] main audio filter debug: removing module "a52tofloat32"
[0xa53bf1c] main audio filter debug: removing module "scaletempo"
[0xa53c57c] main audio filter debug: removing module "bandlimited_resampler"
[0xa3bad74] pulse audio output debug: Pulse Close
[0xa3bad74] main audio output debug: removing module "pulse"
[0xa53932c] main generic debug: removing module "float32_mixer"
[0xb57005f4] main input debug: releasing aout
[0xb57005f4] main input debug: Program doesn't contain anymore ES
[0xa31f3dc] dvdnav demux debug: DVDNAV_CELL_CHANGE
[0xa31f3dc] dvdnav demux debug:      - cellN=1
[0xa31f3dc] dvdnav demux debug:      - pgN=1
[0xa31f3dc] dvdnav demux debug:      - cell_length=2073000
[0xa31f3dc] dvdnav demux debug:      - pg_length=2073000
[0xa31f3dc] dvdnav demux debug:      - pgc_length=755844000
[0xa31f3dc] dvdnav demux debug:      - cell_start=0
[0xa31f3dc] dvdnav demux debug:      - pg_start=0
[0xa31f3dc] dvdnav demux debug: DVDNAV_SPU_CLUT_CHANGE
[0xa31f3dc] dvdnav demux debug: DVDNAV_SPU_STREAM_CHANGE
[0xa31f3dc] dvdnav demux debug:      - physical_wide=128
[0xa31f3dc] dvdnav demux debug:      - physical_letterbox=129
[0xa31f3dc] dvdnav demux debug:      - physical_pan_scan=128
[0xa31f3dc] dvdnav demux debug: buttonUpdate not done b=1 t=1
[0xa31f3dc] dvdnav demux debug: DVDNAV_AUDIO_STREAM_CHANGE
[0xa31f3dc] dvdnav demux debug:      - physical=0
[0xb57005f4] main input debug: Buffering 0%
[0xa31f3dc] dvdnav demux debug: buttonUpdate not done b=1 t=1
[0xa3fa14c] main generic debug: auto hidding mouse
[0xb57005f4] main input debug: Buffering 0%
[0xa3176ec] main decoder debug: looking for decoder module: 30 candidates
[0xa3176ec] avcodec decoder debug: libavcodec already initialized
[0xa3176ec] avcodec decoder debug: trying to use direct rendering
[0xa3176ec] avcodec decoder debug: ffmpeg codec (MPEG-1/2 Video) started
[0xa3176ec] main decoder debug: using decoder module "avcodec"
[0xa3176ec] main decoder debug: TIMER module_need() : 0.932 ms - Total 0.932 ms / 1 intvls (Avg 0.932 ms)
[0xa3b06a4] main packetizer debug: looking for packetizer module: 21 candidates
[0xa3b06a4] main packetizer debug: using packetizer module "packetizer_mpegvideo"
[0xa3b06a4] main packetizer debug: TIMER module_need() : 0.167 ms - Total 0.167 ms / 1 intvls (Avg 0.167 ms)
[0xa3176ec] main decoder debug: thread (decoder) created at priority 0 (input/decoder.c:301)
[0xa3176ec] main decoder debug: thread started
[0xa31f3dc] dvdnav demux debug: buttonUpdate not done b=1 t=1
[0xa3b06a4] packetizer_mpegvideo packetizer debug: size 720x480 fps=29.970
[0xa31f3dc] dvdnav demux warning: cannot get next block (Error reading from DVD.)
[0xa0a0794] main playlist debug: finished input
[0xa0a0794] main playlist debug: dying input
[0xa3176ec] avcodec decoder debug: ffmpeg codec (MPEG-1/2 Video) stopped
[0xa3176ec] main decoder debug: removing module "avcodec"
[0xa3176ec] main decoder debug: killing decoder fourcc `mpgv', 0 PES in FIFO
[0xa3b06a4] main packetizer debug: removing module "packetizer_mpegvideo"
[0xb57005f4] main input debug: Program doesn't contain anymore ES
[0xa31f3dc] main demux debug: removing module "dvdnav"
[0xa0a0794] main playlist debug: dead input
[0xb57005f4] main input debug: thread ended
[0xa0a0794] main playlist debug: changing item without a request (current 0/1)
[0xa0a0794] main playlist debug: nothing to play
[0xa436b94] main video output debug: destroying useless vout
[0x9f61cd4] qt4 interface debug: IM: Deleting the input
[0xa3fa14c] main generic debug: Filter 0xa3fd3ac removed from chain
[0xa3fd3ac] main filter debug: removing module "swscale"
[0xa23ac0c] main inhibit debug: removing module "xdg_screensaver"
[0xa3fa3cc] qt4 window debug: releasing video...
[0x9f61cd4] qt4 interface debug: Video is not needed anymore
[0xa3fa3cc] main window debug: removing module "qt4"
[0xa3fa14c] main generic debug: removing module "xcb_x11"
[0xa436b94] main video output debug: removing module "vout_wrapper"
[0xa3fb834] main blend debug: removing module "blend"
[0xa3b794c] main spu text debug: removing module "freetype"
[0xa3be2e4] main scale debug: removing module "yuvp"
[0xa3bd0d4] main scale debug: removing module "swscale"

```

---

### Post by mc4man on 2011-04-25
You need to install libdvdcss2 (available from medibuntu repo or  - 
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```
> 
libvlc [COLOR="Blue"]warning[/COLOR]: cannot read /usr/lib/vlc/plugins/plugins-04041e-7e8.dat (No such file or directory)
Just a warning - pretty much meaningless

---

### Post by c0dege3k on 2011-04-25
Great! That worked, thanks for all the help :)

---

### Post by handy on 2011-04-25
So, libdvdcss2 isn't installed when you do the restricted formats thing on Ubuntu?

[https://help.ubuntu.com/community/RestrictedFormats/#Playing%20Restricted%20Formats](https://help.ubuntu.com/community/RestrictedFormats/#Playing%20Restricted%20Formats)

Thanks for bringing that to my attention, as I've made posts recently where I thought that it was included in the restricted formats repo.

---

### Post by david70 on 2011-04-25
I have the same question,study.thanks

---

### Post by c0dege3k on 2011-04-25
> **handy said:**
> So, libdvdcss2 isn't installed when you do the restricted formats thing on Ubuntu?

[https://help.ubuntu.com/community/RestrictedFormats/#Playing%20Restricted%20Formats](https://help.ubuntu.com/community/RestrictedFormats/#Playing%20Restricted%20Formats)

Thanks for bringing that to my attention, as I've made posts recently where I thought that it was included in the restricted formats repo.

I don't know... what's weird is that the command suggested by mc4man (the one that worked) is also the one in that link. Maybe it was a reboot thing?

---

### Post by handy on 2011-04-26
> **c0dege3k said:**
> I don't know... what's weird is that the command suggested by mc4man (the one that worked) is also the one in that link. Maybe it was a reboot thing?

I don't think you need to reboot for libdvdcss2 to work, so I don't know either. The main thing is that you got your solution. (Marking the thread [SOLVED] is a cool thing to do to.:))

I've just started giving some support here again after some years of giving very little, so I'm doing a bit of learning myself, as I've don't use Ubuntu & haven't been for over 3 years now. Understandably things do tend to change some... ;)

---

### Post by mc4man on 2011-04-26
> **c0dege3k said:**
>  Maybe it was a reboot thing?
While a restart, (a log out/in or even full reboot) shouldn't be needed in this case or for codecs in general, it does seem that recently there has been increasing occasions when it's all that's needed. (starting around  karmic 
So while I've never had an issue w/ libdvdcss2 being found directly after install, have seen more than a handful of times when it wasn't, but was after a restart.
It certainly could be considered something to try when it appears things are in order but not working as expected.

(if in fact that you'd previously run that command  - noting that libdvdread4 has to be installed _before_ running the command.
Installing ubuntu-restricted-extras or even just vlc itself will always install libdvdread4 if it wasn't previously

---

### Post by alyssia.nuke on 2011-04-26
:guitar:Vlc is a best player

---

### Post by Yellow Pasque on 2011-04-26
When you install shared libraries, you need to run ldconfig before they're recognized. That could be the issue with it not being recognized instantly. I see it a lot with manual installations of libflashplayer.so, but I'm not sure whether the install-css script automatically runs it when installing the .deb or not.

---

