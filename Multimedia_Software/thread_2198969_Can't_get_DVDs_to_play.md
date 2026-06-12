---
title: "Can't get DVDs to play"
date: 2014-01-11
forum: Multimedia Software
---

### Post by joeborg on 2014-01-11
I've followed the guide here [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs), but still can't play DVDs.  I get the following from vlc -vvv

```
[0x268db58] main playlist debug: adding item `MTD5496' ( dvd:///media/joe/MTD5496 )
[0x2487f18] qt4 interface debug: Adding a new MRL to recent ones: dvd:///media/joe/MTD5496
[0x268db58] main playlist debug: rebuilding array of current - root Playlist
[0x268db58] main playlist debug: rebuild done - 1 items, index -1
[0x268db58] main playlist debug: processing request item: MTD5496, node: null, skip: 0
[0x268db58] main playlist debug: resyncing on MTD5496
[0x268db58] main playlist debug: MTD5496 is at 0
[0x268db58] main playlist debug: starting playback of the new playlist item
[0x268db58] main playlist debug: resyncing on MTD5496
[0x268db58] main playlist debug: MTD5496 is at 0
[0x268db58] main playlist debug: creating new input thread
[0x7f1d9c000b78] main input debug: Creating an input for 'MTD5496'
[0x2487f18] qt4 interface debug: IM: Setting an input
[0x7f1d84000a28] main input debug: Creating an input for 'MTD5496'
[0x268db58] main playlist debug: meta ok for (null), need to fetch art
[0x7f1d84000d48] main demux meta debug: looking for meta fetcher module: 1 candidate
[0x7f1d84000d48] lua demux meta debug: Trying Lua scripts in /home/joe/.local/share/vlc/lua/meta/fetcher
[0x7f1d84000d48] lua demux meta debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/fetcher
[0x7f1d84000d48] lua demux meta debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/fetcher/tvrage.luac
[0x7f1d84000d48] main demux meta debug: using meta fetcher module "lua"
[0x7f1d84000d48] main demux meta debug: TIMER module_need() : 5.807 ms - Total 5.807 ms / 1 intvls (Avg 5.807 ms)
[0x7f1d84000d48] main demux meta debug: removing module "lua"
[0x268db58] main playlist debug: searching art for MTD5496
[0x7f1d9c000b78] main input debug: using timeshift granularity of 50 MiB, in path '/tmp'
[0x7f1d9c000b78] main input debug: `dvd:///media/joe/MTD5496' gives access `dvd' demux `' path `/media/joe/MTD5496'
[0x7f1d9c000b78] main input debug: creating demux: access='dvd' demux='' location='/media/joe/MTD5496' file='/media/joe/MTD5496'
[0x7f1d780011c8] main demux debug: looking for access_demux module: 2 candidates
libdvdnav: Using dvdnav version 4.2.0
libdvdread: Using libdvdcss version 1.2.13 for DVD access
libdvdread: Attempting to use device /dev/sr0 mounted on /media/joe/MTD5496 for CSS authentication
[0x7f1d84003ab8] main art finder debug: looking for art finder module: 2 candidates
[0x7f1d84003ab8] lua art finder debug: Trying Lua scripts in /home/joe/.local/share/vlc/lua/meta/art
[0x7f1d84003ab8] lua art finder debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/art
[0x7f1d84003ab8] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/00_musicbrainz.luac
[0x7f1d84003ab8] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/01_googleimage.luac
[0x7f1d84003ab8] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/02_frenchtv.luac
[0x7f1d84003ab8] lua art finder debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/03_lastfm.luac
[0x7f1d84003ab8] lua art finder debug: Trying Lua scripts in /usr/share/vlc/lua/meta/art
[0x7f1d84003ab8] main art finder debug: no art finder module matching "any" could be loaded
[0x7f1d84003ab8] main art finder debug: TIMER module_need() : 3.946 ms - Total 3.946 ms / 1 intvls (Avg 3.946 ms)
[0x268db58] main playlist debug: art not found for MTD5496
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2
[0x7f1d780011c8] dvdnav demux debug: trying to go to dvd menu
[0x7f1d780011c8] main demux debug: using access_demux module "dvdnav"
[0x7f1d780011c8] main demux debug: TIMER module_need() : 26.946 ms - Total 26.946 ms / 1 intvls (Avg 26.946 ms)
[0x7f1d78049d58] main demux meta debug: looking for meta reader module: 2 candidates
[0x7f1d78049d58] lua demux meta debug: Trying Lua scripts in /home/joe/.local/share/vlc/lua/meta/reader
[0x7f1d78049d58] lua demux meta debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/reader
[0x7f1d78049d58] lua demux meta debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/reader/filename.luac
[0x7f1d78049d58] lua demux meta debug: Trying Lua scripts in /usr/share/vlc/lua/meta/reader
[0x7f1d78049d58] main demux meta debug: no meta reader module matching "any" could be loaded
[0x7f1d78049d58] main demux meta debug: TIMER module_need() : 4.236 ms - Total 4.236 ms / 1 intvls (Avg 4.236 ms)
[0x7f1d9c000b78] main input debug: `dvd:///media/joe/MTD5496' successfully opened
[0x7f1d780011c8] dvdnav demux debug: DVDNAV_HOP_CHANNEL
[0x7f1d9c000b78] main input error: ES_OUT_RESET_PCR called


libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient


libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000017b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00010568
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x00010568)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002bd3c4
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x002bd3c4)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002bee45
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x002c76bf
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x002ccdab
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x002cda79
libdvdread: Elapsed time 0
libdvdread: Found 6 VTS's
libdvdread: Elapsed time 1
[0x7f1d780011c8] dvdnav demux debug: DVDNAV_VTS_CHANGE
[0x7f1d780011c8] dvdnav demux debug:      - vtsN=1
[0x7f1d780011c8] dvdnav demux debug:      - domain=8
[0x7f1d9c000b78] main input error: ES_OUT_RESET_PCR called
[0x7f1d780011c8] dvdnav demux debug: DVDNAV_CELL_CHANGE
[0x7f1d780011c8] dvdnav demux debug:      - cellN=1
[0x7f1d780011c8] dvdnav demux debug:      - pgN=1
[0x7f1d780011c8] dvdnav demux debug:      - cell_length=5425200
[0x7f1d780011c8] dvdnav demux debug:      - pg_length=5425200
[0x7f1d780011c8] dvdnav demux debug:      - pgc_length=5425200
[0x7f1d780011c8] dvdnav demux debug:      - cell_start=0
[0x7f1d780011c8] dvdnav demux debug:      - pg_start=0
[0x7f1d780011c8] dvdnav demux debug: DVDNAV_SPU_CLUT_CHANGE
[0x7f1d780011c8] dvdnav demux debug: DVDNAV_SPU_STREAM_CHANGE
[0x7f1d780011c8] dvdnav demux debug:      - physical_wide=0
[0x7f1d780011c8] dvdnav demux debug:      - physical_letterbox=1
[0x7f1d780011c8] dvdnav demux debug:      - physical_pan_scan=0
[0x7f1d780011c8] dvdnav demux debug: buttonUpdate not done b=1 t=0
[0x7f1d9c000b78] main input debug: selecting program id=0
[0x7f1d78054238] main decoder debug: looking for decoder module: 31 candidates
[0x7f1d78054238] main decoder debug: using decoder module "spudec"
[0x7f1d78054238] main decoder debug: TIMER module_need() : 3.098 ms - Total 3.098 ms / 1 intvls (Avg 3.098 ms)
[0x7f1d78054238] spudec decoder debug: invalid starting packet (size < 4 or pts <=0)
[0x7f1d78054238] spudec decoder debug: spu size: 0, i_pts: 0 i_buffer: 128
[0x7f1d780011c8] dvdnav demux debug: DVDNAV_AUDIO_STREAM_CHANGE
[0x7f1d780011c8] dvdnav demux debug:      - physical=0
[0x7f1d9c000b78] main input debug: Buffering 0%
[0x7f1d780011c8] dvdnav demux debug: buttonUpdate 1
[0x7f1d780011c8] dvdnav demux warning: cannot get next block (Error reading from DVD.)
[0x7f1d780011c8] dvdnav demux debug: jumping to first title
[0x7f1d780011c8] dvdnav demux debug: DVDNAV_HOP_CHANNEL
[0x7f1d9c000b78] main input error: ES_OUT_RESET_PCR called
[0x7f1d78054238] spudec decoder debug: invalid starting packet (size < 4 or pts <=0)
[0x7f1d78054238] spudec decoder debug: spu size: 0, i_pts: 0 i_buffer: 128
[0x7f1d780011c8] dvdnav demux debug: DVDNAV_VTS_CHANGE
[0x7f1d780011c8] dvdnav demux debug:      - vtsN=1
[0x7f1d780011c8] dvdnav demux debug:      - domain=2
[0x7f1d9c000b78] main input error: ES_OUT_RESET_PCR called
[0x7f1d78054238] spudec decoder debug: invalid starting packet (size < 4 or pts <=0)
[0x7f1d78054238] spudec decoder debug: spu size: 0, i_pts: 0 i_buffer: 128
[0x7f1d78054238] main decoder debug: removing module "spudec"
[0x7f1d78054238] main decoder debug: killing decoder fourcc `spu ', 0 PES in FIFO
[0x7f1d9c000b78] main input debug: Program doesn't contain anymore ES
[0x7f1d780011c8] dvdnav demux debug: DVDNAV_CELL_CHANGE
[0x7f1d780011c8] dvdnav demux debug:      - cellN=1
[0x7f1d780011c8] dvdnav demux debug:      - pgN=1
[0x7f1d780011c8] dvdnav demux debug:      - cell_length=43200
[0x7f1d780011c8] dvdnav demux debug:      - pg_length=43200
[0x7f1d780011c8] dvdnav demux debug:      - pgc_length=43200
[0x7f1d780011c8] dvdnav demux debug:      - cell_start=0
[0x7f1d780011c8] dvdnav demux debug:      - pg_start=0
[0x7f1d780011c8] dvdnav demux debug: DVDNAV_SPU_CLUT_CHANGE
[0x7f1d780011c8] dvdnav demux debug: DVDNAV_SPU_STREAM_CHANGE
[0x7f1d780011c8] dvdnav demux debug:      - physical_wide=-1
[0x7f1d780011c8] dvdnav demux debug:      - physical_letterbox=-1
[0x7f1d780011c8] dvdnav demux debug:      - physical_pan_scan=-1
[0x7f1d780011c8] dvdnav demux debug: buttonUpdate not done b=1 t=1
[0x7f1d780011c8] dvdnav demux debug: DVDNAV_AUDIO_STREAM_CHANGE
[0x7f1d780011c8] dvdnav demux debug:      - physical=0
[0x7f1d780011c8] dvdnav demux warning: cannot get next block (Error reading NAV packet.)
[0x268db58] main playlist debug: finished input
[0x7f1d9c000b78] main input debug: control: stopping input
[0x268db58] main playlist debug: dying input
[0x7f1d780011c8] main demux debug: removing module "dvdnav"
[0x268db58] main playlist debug: dead input
[0x268db58] main playlist debug: changing item without a request (current 0/1)
[0x268db58] main playlist debug: nothing to play
[0x2487f18] qt4 interface debug: IM: Deleting the input

```

---

### Post by ajgreeny on 2014-01-11
That webpage is now a bit outdated, so see [http://www.videolan.org/developers/libdvdcss.html](http://www.videolan.org/developers/libdvdcss.html) where you can see the following about installing libdvdcss2

Last version of libdvdcss is **1.2.13**. 

   Our Debian/Ubuntu repository can be accessed by adding the following content to /etc/apt/sources.list
 
deb [http://download.videolan.org/pub/debian/stable/](http://download.videolan.org/pub/debian/stable/) /
 deb-src [http://download.videolan.org/pub/debian/stable/](http://download.videolan.org/pub/debian/stable/) /
 And by running
 
wget -O - [http://download.videolan.org/pub/debian/videolan-apt.asc|sudo](http://download.videolan.org/pub/debian/videolan-apt.asc|sudo) apt-key add -

---

### Post by kostkon on 2014-01-12
> **ajgreeny said:**
> That webpage is now a bit outdated, so see [http://www.videolan.org/developers/libdvdcss.html](http://www.videolan.org/developers/libdvdcss.html) where you can see the following about installing libdvdcss2

Last version of libdvdcss is **1.2.13**. 

   Our Debian/Ubuntu repository can be accessed by adding the following content to /etc/apt/sources.list
 
deb [http://download.videolan.org/pub/debian/stable/](http://download.videolan.org/pub/debian/stable/) /
 deb-src [http://download.videolan.org/pub/debian/stable/](http://download.videolan.org/pub/debian/stable/) /
 And by running
 
wget -O - [http://download.videolan.org/pub/debian/videolan-apt.asc|sudo](http://download.videolan.org/pub/debian/videolan-apt.asc|sudo) apt-key add -
No need for that, the install-css.sh script has been updated to point to the vlc repo.

---

### Post by ajgreeny on 2014-01-12
> **kostkon said:**
> No need for that, the install-css.sh script has been updated to point to the vlc repo.
Thanks for that info.

I had not caught up with that fact, and as I previously used the medibuntu repos, I did not use the install-css.sh script either.

It does indeed save a bit of a fuss.

---

