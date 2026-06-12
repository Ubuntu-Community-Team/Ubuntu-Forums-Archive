---
title: "cvlc recording issues - early terminations"
date: 2013-02-05
forum: Multimedia Software
---

### Post by MakOwner on 2013-02-05
ron99 and haqking gave me some excellent pointers to record some FM radio broadcasts off the net in this thread 
[http://ubuntuforums.org/showthread.php?t=2103483&page=2](http://ubuntuforums.org/showthread.php?t=2103483&page=2)

Thanks, BTW!

I like the size and quality of the recordings, however, it's not even being close to dependable to record via cvlc.  I get random early terminations of the recording, with no discernible reason for the recording stopping.

I use a cron job on a server to launch a script that uses the following command to record about 420 minutes of an FM broadcast over the internet.
The command line I use in the script is this - this points initially to surfmusic.de which appears to the hand off the connection and the recording occurs directly from the local radio station source through akamai/icelink.

```

cvlc -vvv -I dummy --stop-time=$SECONDS $SOURCELINK --sout="#transcode{acodec=s16l,channels=2,samplerate=44100}:std{access=file,mux=wav,dst='${WAVDIR}/${DATAFILE}.wav'}" vlc://quit

```

I have enabled increased verbosity via the -vvv parameter and was hoping someone could point me to the source of the disconnection and early termination of the recording and a way to prevent the disconnection:

```


+ print 'begin recording at Mon Feb  4 15:03:02 CST 2013 ...'
begin recording at Mon Feb  4 15:03:02 CST 2013 ...
+ cvlc -vvv -I dummy '--stop-time=15600' http://www.surfmusic.de/media/kegl-fm.m3u $'--sout=#transcode{acodec=s16l,channels=2,samplerate=44100}:std{access=file,mux=wav,dst=\'/media/recording_20130204.wav\'}' vlc://quit
[0x159f108] main libvlc debug: VLC media player - 2.0.5 Twoflower
[0x159f108] main libvlc debug: Copyright © 1996-2012 VLC authors and VideoLAN
[0x159f108] main libvlc debug: revision 2.0.5-0-g1661b7d
[0x159f108] main libvlc debug: configured with ./configure  '--enable-static' '--build=x86_64-linux-gnu' 'CFLAGS=-g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -Werror=format-security' 'CPPFLAGS=-D_FORTIFY_SOURCE=2' 'CXXFLAGS=-g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -Werror=format-security' 'LDFLAGS=-Wl,-Bsymbolic-functions -Wl,-z,relro' '--config-cache' '--disable-maintainer-mode' '--disable-silent-rules' '--disable-update-check' '--enable-fast-install' '--prefix=/usr' '--docdir=/usr/share/doc/vlc-nox' '--sysconfdir=/etc' '--with-binary-version=0ubuntu0.12.04.1' '--enable-a52' '--enable-aa' '--enable-bluray' '--enable-bonjour' '--enable-caca' '--enable-dbus' '--enable-dca' '--enable-dirac' '--enable-directfb' '--enable-dvbpsi' '--enable-dvdnav' '--enable-faad' '--enable-flac' '--enable-fluidsynth' '--enable-freetype' '--enable-fribidi' '--enable-gnutls' '--enable-jack' '--enable-kate' '--enable-libass' '--enable-libmpeg2' '--enable-libproxy' '--enable-libxml2' '--enable-lirc' '--enable-live555' '--enable-mad' '--enable-mkv' '--enable-mod' '--enable-mpc' '--enable-mtp' '--enable-mux_ogg' '--enable-ncurses' '--enable-notify' '--enable-ogg' '--enable-oss' '--enable-pulse' '--enable-qt4' '--enable-realrtsp' '--enable-samplerate' '--enable-schroedinger' '--enable-sdl' '--enable-shout' '--enable-skins2' '--enable-smb' '--enable-speex' '--enable-svg' '--enable-taglib' '--enable-theora' '--enable-twolame' '--enable-upnp' '--enable-vcd' '--enable-vcdx' '--enable-vorbis' '--enable-x264' '--enable-zvbi' '--with-kde-solid=/usr/share/kde4/apps/solid/actions/' '--disable-dxva2' '--disable-gnomevfs' '--disable-goom' '--disable-portaudio' '--disable-projectm' '--disable-sqlite' '--disable-telx' '--enable-alsa' '--enable-atmo' '--enable-dc1394' '--enable-dv' '--enable-fbosd' '--enable-libva' '--enable-linsys' '--enable-omxil' '--enable-pvr' '--enable-udev' '--enable-v4l2' '--enable-crystalhd' '--enable-mmx' '--enable-sse' '--disable-neon' '--disable-altivec' 'build_alias=x86_64-linux-gnu'
[0x159f108] main libvlc debug: searching plug-in modules
[0x159f108] main libvlc debug: loading plugins cache file /usr/lib/vlc/plugins/plugins.dat
[0x159f108] main libvlc debug: recursively browsing `/usr/lib/vlc/plugins'
[0x159f108] main libvlc debug: saving plugins cache /usr/lib/vlc/plugins/plugins.dat
[0x159f108] main libvlc debug: plug-ins loaded: 392 modules
[0x159f108] main libvlc debug: opening config file (/home/dale/.config/vlc/vlcrc)
[0x159f108] main libvlc debug: translation test: code is "C"
[0x159f108] main libvlc debug: CPU has capabilities MMX MMXEXT SSE SSE2 SSE3 FPU 
[0x159f108] main libvlc debug: looking for memcpy module: 4 candidates
[0x159f108] main libvlc debug: using memcpy module "memcpymmxext"
[0x15b3908] main input debug: Creating an input for 'Media Library'
[0x15b3908] main input debug: Input is a meta file: disabling unneeded options
[0x15b3908] main input debug: using timeshift granularity of 50 MiB, in path '/tmp'
[0x15b3908] main input debug: `file/xspf-open:///home/dale/.local/share/vlc/ml.xspf' gives access `file' demux `xspf-open' path `/home/dale/.local/share/vlc/ml.xspf'
[0x15b3908] main input debug: creating demux: access='file' demux='xspf-open' location='/home/dale/.local/share/vlc/ml.xspf' file='/home/dale/.local/share/vlc/ml.xspf'
[0x15cd0b8] main demux debug: looking for access_demux module: 3 candidates
[0x15cd0b8] main demux debug: no access_demux module matching "file" could be loaded
[0x15cd0b8] main demux debug: TIMER module_need() : 1.157 ms - Total 1.157 ms / 1 intvls (Avg 1.157 ms)
[0x15b3908] main input debug: creating access 'file' location='/home/dale/.local/share/vlc/ml.xspf', path='/home/dale/.local/share/vlc/ml.xspf'
[0x166b4f8] main access debug: looking for access module: 2 candidates
[0x166b4f8] filesystem access debug: opening file `/home/dale/.local/share/vlc/ml.xspf'
[0x166b4f8] main access debug: using access module "filesystem"
[0x166b4f8] main access debug: TIMER module_need() : 0.564 ms - Total 0.564 ms / 1 intvls (Avg 0.564 ms)
[0x166c268] main stream debug: Using stream method for AStream*
[0x166c268] main stream debug: starting pre-buffering
[0x166c268] main stream debug: received first data after 3 ms
[0x166c268] main stream debug: pre-buffering done 296 bytes in 0s - 85 KiB/s
[0x166c4c8] main stream debug: looking for stream_filter module: 7 candidates
[0x166c4c8] main stream debug: no stream_filter module matching "any" could be loaded
[0x166c4c8] main stream debug: TIMER module_need() : 1.436 ms - Total 1.436 ms / 1 intvls (Avg 1.436 ms)
[0x166c4c8] main stream debug: looking for stream_filter module: 1 candidate
[0x166c4c8] main stream debug: using stream_filter module "stream_filter_record"
[0x166c4c8] main stream debug: TIMER module_need() : 0.259 ms - Total 0.259 ms / 1 intvls (Avg 0.259 ms)
[0x15b3908] main input debug: creating demux: access='file' demux='xspf-open' location='/home/dale/.local/share/vlc/ml.xspf' file='/home/dale/.local/share/vlc/ml.xspf'
[0x166d118] main demux debug: looking for demux module: 1 candidate
[0x166d118] playlist demux debug: using XSPF playlist reader
[0x166d118] main demux debug: using demux module "playlist"
[0x166d118] main demux debug: TIMER module_need() : 0.447 ms - Total 0.447 ms / 1 intvls (Avg 0.447 ms)
[0x166d9f8] main demux meta debug: looking for meta reader module: 2 candidates
[0x166d9f8] lua demux meta debug: Trying Lua scripts in /home/dale/.local/share/vlc/lua/meta/reader
[0x166d9f8] lua demux meta debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/reader
[0x166d9f8] lua demux meta debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/reader/filename.luac
[0x166d9f8] lua demux meta debug: Trying Lua scripts in /usr/share/vlc/lua/meta/reader
[0x166d9f8] main demux meta debug: no meta reader module matching "any" could be loaded
[0x166d9f8] main demux meta debug: TIMER module_need() : 13.499 ms - Total 13.499 ms / 1 intvls (Avg 13.499 ms)
[0x15b3908] main input debug: `file/xspf-open:///home/dale/.local/share/vlc/ml.xspf' successfully opened
[0x15d2fb8] main xml reader debug: looking for xml reader module: 1 candidate
[0x15d2fb8] main xml reader debug: using xml reader module "xml"
[0x15d2fb8] main xml reader debug: TIMER module_need() : 20.612 ms - Total 20.612 ms / 1 intvls (Avg 20.612 ms)
[0x166d118] playlist demux debug: parsed 0 tracks successfully
[0x15b3908] main input debug: EOF reached
[0x166d118] main demux debug: removing module "playlist"
[0x166c4c8] main stream debug: removing module "stream_filter_record"
[0x166b4f8] main access debug: removing module "filesystem"
[0x15b3908] main input debug: TIMER input launching for 'Media Library' : 21.779 ms - Total 21.779 ms / 1 intvls (Avg 21.779 ms)
[0x15cce78] main interface debug: looking for interface module: 1 candidate
[0x15cce78] main interface debug: using interface module "hotkeys"
[0x15cce78] main interface debug: TIMER module_need() : 0.387 ms - Total 0.387 ms / 1 intvls (Avg 0.387 ms)
[0x15b3908] main interface debug: looking for interface module: 1 candidate
[0x15b3908] inhibit interface error: Failed to connect to the D-Bus session daemon: Unable to autolaunch a dbus-daemon without a $DISPLAY for X11
[0x15b3908] main interface debug: no interface module matching "inhibit,none" could be loaded
[0x15b3908] main interface debug: TIMER module_need() : 0.327 ms - Total 0.327 ms / 1 intvls (Avg 0.327 ms)
[0x15b3908] main interface error: no suitable interface module
[0x1796588] main playlist debug: playlist threads correctly activated
[0x1796588] main playlist debug: adding item `quit' ( vlc://quit )
[0x1796588] main playlist debug: rebuilding array of current - root Playlist
[0x1796588] main playlist debug: rebuild done - 0 items, index -1
[0x1796588] main playlist debug: adding item `http://www.surfmusic.de/media/kegl-fm.m3u' ( http://www.surfmusic.de/media/kegl-fm.m3u )
[0x7f9500000a28] main input debug: Creating an input for 'quit'
[0x15b3908] main interface debug: looking for interface module: 0 candidates
[0x15b3908] main interface debug: no interface module matched "globalhotkeys,none"
[0x15b3908] main interface debug: TIMER module_need() : 0.261 ms - Total 0.261 ms / 1 intvls (Avg 0.261 ms)
[0x15b3908] main interface error: no suitable interface module
[0x1796588] main playlist debug: no fetch required for (null) (art currently (null))
[0x1796588] main playlist debug: no fetch required for (null) (art currently (null))
[0x159f108] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x15b3908] main interface debug: looking for interface module: 1 candidate
[0x15b3908] dummy interface: using the dummy interface module...
[0x15b3908] main interface debug: using interface module "dummy"
[0x15b3908] main interface debug: TIMER module_need() : 0.331 ms - Total 0.331 ms / 1 intvls (Avg 0.331 ms)
[0x1796588] main playlist debug: processing request item: null, node: Playlist, skip: 0
[0x1796588] main playlist debug: rebuilding array of current - root Playlist
[0x1796588] main playlist debug: rebuild done - 2 items, index -1
[0x1796588] main playlist debug: starting playback of the new playlist item
[0x1796588] main playlist debug: resyncing on http://www.surfmusic.de/media/kegl-fm.m3u
[0x1796588] main playlist debug: http://www.surfmusic.de/media/kegl-fm.m3u is at 0
[0x1796588] main playlist debug: creating new input thread
[0x7f9508000b28] main input debug: Creating an input for 'http://www.surfmusic.de/media/kegl-fm.m3u'
[0x7f9500004108] main stream output debug: using sout chain=`transcode{acodec=s16l,channels=2,samplerate=44100}:std{access=file,mux=wav,dst='/media/recording_20130204.wav'}'
[0x7f9500004108] main stream output debug: stream=`std'
[0x7f9500001538] main stream out debug: looking for sout stream module: 1 candidate
[0x7f9500001538] main stream out debug: set config option: sout-standard-access to file
[0x7f9500001538] main stream out debug: set config option: sout-standard-mux to wav
[0x7f9500001538] main stream out debug: set config option: sout-standard-dst to /media/recording_20130204.wav
[0x7f95000021a8] main access out debug: looking for sout access module: 1 candidate
[0x7f95000021a8] access_output_file access out debug: file access output opened (/media/recording_20130204.wav)
[0x7f95000021a8] main access out debug: using sout access module "access_output_file"
[0x7f95000021a8] main access out debug: TIMER module_need() : 23.931 ms - Total 23.931 ms / 1 intvls (Avg 23.931 ms)
[0x7f95000017e8] main mux debug: looking for sout mux module: 1 candidate
[0x7f95000017e8] main mux debug: using sout mux module "mux_wav"
[0x7f95000017e8] main mux debug: TIMER module_need() : 0.338 ms - Total 0.338 ms / 1 intvls (Avg 0.338 ms)
[0x7f9500001538] stream_out_standard stream out debug: using `file/wav:///media/recording_20130204.wav'
[0x7f9500001538] main stream out debug: using sout stream module "stream_out_standard"
[0x7f9500001538] main stream out debug: TIMER module_need() : 24.892 ms - Total 24.892 ms / 1 intvls (Avg 24.892 ms)
[0x7f9500004108] main stream output debug: stream=`transcode'
[0x7f9500002ea8] main stream out debug: looking for sout stream module: 1 candidate
[0x7f9500002ea8] main stream out debug: set config option: sout-transcode-acodec to s16l
[0x7f9500002ea8] main stream out debug: set config option: sout-transcode-channels to 2
[0x7f9500002ea8] main stream out debug: set config option: sout-transcode-samplerate to 44100
[0x7f9500002ea8] stream_out_transcode stream out debug: codec audio=s16l 44100Hz 2 channels 96Kb/s
[0x7f9500002ea8] main stream out debug: using sout stream module "stream_out_transcode"
[0x7f9500002ea8] main stream out debug: TIMER module_need() : 0.625 ms - Total 0.625 ms / 1 intvls (Avg 0.625 ms)
[0x7f9508000b28] main input debug: using timeshift granularity of 50 MiB, in path '/tmp'
[0x7f9508000b28] main input debug: `http://www.surfmusic.de/media/kegl-fm.m3u' gives access `http' demux `' path `www.surfmusic.de/media/kegl-fm.m3u'
[0x7f9508000b28] main input debug: creating demux: access='http' demux='' location='www.surfmusic.de/media/kegl-fm.m3u' file='(null)'
[0x7f95000066c8] main demux debug: looking for access_demux module: 0 candidates
[0x7f95000066c8] main demux debug: no access_demux module matched "http"
[0x7f95000066c8] main demux debug: TIMER module_need() : 0.127 ms - Total 0.127 ms / 1 intvls (Avg 0.127 ms)
[0x7f9508000b28] main input debug: creating access 'http' location='www.surfmusic.de/media/kegl-fm.m3u', path='(null)'
[0x7f9500007338] main access debug: looking for access module: 2 candidates
[0x7f9500007338] access_http access debug: asking libproxy about url 'http://www.surfmusic.de/media/kegl-fm.m3u'
[0x7f9500007338] access_http access debug: libproxy suggest to use 'direct://'
[0x7f9500007338] access_http access debug: http: server='www.surfmusic.de' port=80 file='/media/kegl-fm.m3u'
[0x7f9500007338] main access debug: net: connecting to www.surfmusic.de port 80
[0x7f9500007338] main access debug: connection succeeded (socket = 6)
[0x7f9500007338] access_http access debug: protocol 'HTTP' answer code 206
[0x7f9500007338] access_http access debug: Server: Apache/2.2.16 (Debian)
[0x7f9500007338] access_http access debug: this frame size=92
[0x7f9500007338] access_http access debug: stream size=92,pos=0,remaining=92
[0x7f9500007338] access_http access debug: Connection: close
[0x7f9500007338] access_http access debug: Content-Type: audio/x-mpegurl
[0x7f9500007338] main access debug: using access module "access_http"
[0x7f9500007338] main access debug: TIMER module_need() : 862.251 ms - Total 862.251 ms / 1 intvls (Avg 862.251 ms)
[0x7f95000080d8] main stream debug: Using stream method for AStream*
[0x7f95000080d8] main stream debug: starting pre-buffering
[0x7f95000080d8] main stream debug: received first data after 0 ms
[0x7f9500008368] main stream debug: looking for stream_filter module: 7 candidates
[0x7f9500008368] main stream debug: no stream_filter module matching "any" could be loaded
[0x7f9500008368] main stream debug: TIMER module_need() : 0.183 ms - Total 0.183 ms / 1 intvls (Avg 0.183 ms)
[0x7f9500008368] main stream debug: looking for stream_filter module: 1 candidate
[0x7f9500008368] main stream debug: using stream_filter module "stream_filter_record"
[0x7f9500008368] main stream debug: TIMER module_need() : 0.132 ms - Total 0.132 ms / 1 intvls (Avg 0.132 ms)
[0x7f9508000b28] main input debug: creating demux: access='http' demux='' location='www.surfmusic.de/media/kegl-fm.m3u' file='(null)'
[0x7f95000085b8] main demux debug: looking for demux module: 54 candidates
[0x7f95000085b8] es demux error: cannot peek
[0x7f95000085b8] mod demux debug: MOD validation failed (ext=)
[0x7f95000085b8] playlist demux debug: found valid M3U playlist
[0x7f95000085b8] main demux debug: using demux module "playlist"
[0x7f95000085b8] main demux debug: TIMER module_need() : 13.278 ms - Total 13.278 ms / 1 intvls (Avg 13.278 ms)
[0x7f9508000b28] main input debug: starting in sync mode
[0x7f9500c0d948] main demux meta debug: looking for meta reader module: 2 candidates
[0x7f9500c0d948] lua demux meta debug: Trying Lua scripts in /home/dale/.local/share/vlc/lua/meta/reader
[0x7f9500c0d948] lua demux meta debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/reader
[0x7f9500c0d948] lua demux meta debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/reader/filename.luac
[0x7f9500c0d948] lua demux meta debug: Trying Lua scripts in /usr/share/vlc/lua/meta/reader
[0x7f9500c0d948] main demux meta debug: no meta reader module matching "any" could be loaded
[0x7f9500c0d948] main demux meta debug: TIMER module_need() : 0.995 ms - Total 0.995 ms / 1 intvls (Avg 0.995 ms)
[0x7f9508000b28] main input debug: `http://www.surfmusic.de/media/kegl-fm.m3u' successfully opened
[0x1796588] main playlist: stopping playback
[0x1796588] main playlist debug: deleting item `http://www.surfmusic.de/media/kegl-fm.m3u'
[0x1796588] main playlist debug: no fetch required for http://kegl-fm.akacast.akamaistream.net/7/379/20090/v1/auth.akacast.akamaistream.net/kegl-fm (art currently (null))
[0x7f9508000b28] main input debug: EOF reached
[0x1796588] main playlist debug: incoming request - stopping current input
[0x7f9500007338] main access debug: waitpipe: object killed
[0x1796588] main playlist debug: dying input
[0x1796588] main playlist debug: dying input
[0x7f95000085b8] main demux debug: removing module "playlist"
[0x7f9500008368] main stream debug: removing module "stream_filter_record"
[0x7f9500007338] main access debug: removing module "access_http"
[0x1796588] main playlist debug: dead input
[0x7f9500004108] main stream output debug: destroying useless sout
[0x7f9500002ea8] main stream out debug: destroying chain... (name=transcode)
[0x7f9500002ea8] main stream out debug: removing module "stream_out_transcode"
[0x7f9500002ea8] main stream out debug: destroying chain done
[0x7f9500001538] main stream out debug: destroying chain... (name=std)
[0x7f9500001538] main stream out debug: removing module "stream_out_standard"
[0x7f95000017e8] main mux debug: removing module "mux_wav"
[0x7f95000021a8] main access out debug: removing module "access_output_file"
[0x7f95000021a8] access_output_file access out debug: file access output closed
[0x7f9500001538] main stream out debug: destroying chain done
[0x7f9508000b28] main input debug: TIMER input launching for 'http://www.surfmusic.de/media/kegl-fm.m3u' : 903.703 ms - Total 903.703 ms / 1 intvls (Avg 903.703 ms)
[0x1796588] main playlist debug: processing request item: http://kegl-fm.akacast.akamaistream.net/7/379/20090/v1/auth.akacast.akamaistream.net/kegl-fm, node: Playlist, skip: 0
[0x1796588] main playlist debug: rebuilding array of current - root Playlist
[0x1796588] main playlist debug: rebuild done - 2 items, index 0
[0x1796588] main playlist debug: starting playback of the new playlist item
[0x1796588] main playlist debug: resyncing on http://kegl-fm.akacast.akamaistream.net/7/379/20090/v1/auth.akacast.akamaistream.net/kegl-fm
[0x1796588] main playlist debug: http://kegl-fm.akacast.akamaistream.net/7/379/20090/v1/auth.akacast.akamaistream.net/kegl-fm is at 0
[0x1796588] main playlist debug: creating new input thread
[0x7f9508000b28] main input debug: Creating an input for 'http://kegl-fm.akacast.akamaistream.net/7/379/20090/v1/auth.akacast.akamaistream.net/kegl-fm'
[0x7f9500002aa8] main stream output debug: using sout chain=`transcode{acodec=s16l,channels=2,samplerate=44100}:std{access=file,mux=wav,dst='/media/recording_20130204.wav'}'
[0x7f9500002aa8] main stream output debug: stream=`std'
[0x7f9500002ea8] main stream out debug: looking for sout stream module: 1 candidate
[0x7f9500002ea8] main stream out debug: set config option: sout-standard-access to file
[0x7f9500002ea8] main stream out debug: set config option: sout-standard-mux to wav
[0x7f9500002ea8] main stream out debug: set config option: sout-standard-dst to /media/recording_20130204.wav
[0x7f95000021a8] main access out debug: looking for sout access module: 1 candidate
[0x7f95000021a8] access_output_file access out debug: file access output opened (/media/recording_20130204.wav)
[0x7f95000021a8] main access out debug: using sout access module "access_output_file"
[0x7f95000021a8] main access out debug: TIMER module_need() : 0.215 ms - Total 0.215 ms / 1 intvls (Avg 0.215 ms)
[0x7f95000019a8] main mux debug: looking for sout mux module: 1 candidate
[0x7f95000019a8] main mux debug: using sout mux module "mux_wav"
[0x7f95000019a8] main mux debug: TIMER module_need() : 0.126 ms - Total 0.126 ms / 1 intvls (Avg 0.126 ms)
[0x7f9500002ea8] stream_out_standard stream out debug: using `file/wav:///media/recording_20130204.wav'
[0x7f9500002ea8] main stream out debug: using sout stream module "stream_out_standard"
[0x7f9500002ea8] main stream out debug: TIMER module_need() : 0.764 ms - Total 0.764 ms / 1 intvls (Avg 0.764 ms)
[0x7f9500002aa8] main stream output debug: stream=`transcode'
[0x7f9500001538] main stream out debug: looking for sout stream module: 1 candidate
[0x7f9500001538] main stream out debug: set config option: sout-transcode-acodec to s16l
[0x7f9500001538] main stream out debug: set config option: sout-transcode-channels to 2
[0x7f9500001538] main stream out debug: set config option: sout-transcode-samplerate to 44100
[0x7f9500001538] stream_out_transcode stream out debug: codec audio=s16l 44100Hz 2 channels 96Kb/s
[0x7f9500001538] main stream out debug: using sout stream module "stream_out_transcode"
[0x7f9500001538] main stream out debug: TIMER module_need() : 0.362 ms - Total 0.362 ms / 1 intvls (Avg 0.362 ms)
[0x7f9508000b28] main input debug: using timeshift granularity of 50 MiB, in path '/tmp'
[0x7f9508000b28] main input debug: `http://kegl-fm.akacast.akamaistream.net/7/379/20090/v1/auth.akacast.akamaistream.net/kegl-fm' gives access `http' demux `' path `kegl-fm.akacast.akamaistream.net/7/379/20090/v1/auth.akacast.akamaistream.net/kegl-fm'
[0x7f9508000b28] main input debug: creating demux: access='http' demux='' location='kegl-fm.akacast.akamaistream.net/7/379/20090/v1/auth.akacast.akamaistream.net/kegl-fm' file='(null)'
[0x7f9500c0ded8] main demux debug: looking for access_demux module: 0 candidates
[0x7f9500c0ded8] main demux debug: no access_demux module matched "http"
[0x7f9500c0ded8] main demux debug: TIMER module_need() : 0.155 ms - Total 0.155 ms / 1 intvls (Avg 0.155 ms)
[0x7f9508000b28] main input debug: creating access 'http' location='kegl-fm.akacast.akamaistream.net/7/379/20090/v1/auth.akacast.akamaistream.net/kegl-fm', path='(null)'
[0x7f9500c0e728] main access debug: looking for access module: 2 candidates
[0x7f9500c0e728] access_http access debug: asking libproxy about url 'http://kegl-fm.akacast.akamaistream.net/7/379/20090/v1/auth.akacast.akamaistream.net/kegl-fm'
[0x7f9500c0e728] access_http access debug: libproxy suggest to use 'direct://'
[0x7f9500c0e728] access_http access debug: http: server='kegl-fm.akacast.akamaistream.net' port=80 file='/7/379/20090/v1/auth.akacast.akamaistream.net/kegl-fm'
[0x7f9500c0e728] main access debug: net: connecting to kegl-fm.akacast.akamaistream.net port 80
[0x7f9500c0e728] main access debug: connection succeeded (socket = 6)
[0x7f9500c0e728] access_http access debug: protocol 'ICY' answer code 200
[0x7f9500c0e728] access_http access debug: Content-Type: audio/aacp
[0x7f9500c0e728] access_http access debug: Meta-Info: icy-br: 64
[0x7f9500c0e728] access_http access debug: Meta-Info: ice-audio-info: ice-bitrate=64;ice-samplerate=44100;ice-channels=2
[0x7f9500c0e728] access_http access debug: Meta-Info: icy-br: 64
[0x7f9500c0e728] access_http access debug: Meta-Info: icy-description: KEGL-FM iPhone Akamai
[0x7f9500c0e728] access_http access debug: Icy-Genre: Various
[0x7f9500c0e728] access_http access debug: Icy-Name: KEGL-FM iPhone Akamai
[0x7f9500c0e728] access_http access debug: Meta-Info: icy-pub: 0
[0x7f9500c0e728] access_http access debug: Meta-Info: icy-url: http://www.iheartradio.com
[0x7f9500c0e728] access_http access debug: Server: Akacast 1.0
[0x7f9500c0e728] access_http access debug: Icy-MetaInt: 16000
[0x7f9500c0e728] access_http access warning: ICY metaint=16000
[0x7f9500c0e728] access_http access: Raw-audio server found, m4a demuxer selected
[0x7f9500c0e728] access_http access debug: auto re-connect enabled
[0x7f9500c0e728] main access debug: using access module "access_http"
[0x7f9500c0e728] main access debug: TIMER module_need() : 601.913 ms - Total 601.913 ms / 1 intvls (Avg 601.913 ms)
[0x7f9500c0ded8] main stream debug: Using stream method for AStream*
[0x7f9500c0ded8] main stream debug: starting pre-buffering
[0x7f9500c0ded8] main stream debug: received first data after 0 ms
[0x7f9500c0ded8] main stream debug: pre-buffering done 1024 bytes in 0s - 26315 KiB/s
[0x7f950000b608] main stream debug: looking for stream_filter module: 7 candidates
[0x7f950000b608] main stream debug: no stream_filter module matching "any" could be loaded
[0x7f950000b608] main stream debug: TIMER module_need() : 0.172 ms - Total 0.172 ms / 1 intvls (Avg 0.172 ms)
[0x7f950000b608] main stream debug: looking for stream_filter module: 1 candidate
[0x7f950000b608] main stream debug: using stream_filter module "stream_filter_record"
[0x7f950000b608] main stream debug: TIMER module_need() : 0.117 ms - Total 0.117 ms / 1 intvls (Avg 0.117 ms)
[0x7f9508000b28] main input debug: creating demux: access='http' demux='m4a' location='kegl-fm.akacast.akamaistream.net/7/379/20090/v1/auth.akacast.akamaistream.net/kegl-fm' file='(null)'
[0x7f9500c0ef98] main demux debug: looking for demux module: 1 candidate
[0x7f9500c0ef98] es demux debug: detected format mp4a
[0x7f9500c0e918] main demux packetizer debug: looking for packetizer module: 21 candidates
[0x7f9500c0e918] packetizer_mpeg4audio demux packetizer debug: running MPEG4 audio packetizer
[0x7f9500c0e918] packetizer_mpeg4audio demux packetizer debug: no decoder specific info, must be an ADTS or LOAS stream
[0x7f9500c0e918] main demux packetizer debug: using packetizer module "packetizer_mpeg4audio"
[0x7f9500c0e918] main demux packetizer debug: TIMER module_need() : 2.747 ms - Total 2.747 ms / 1 intvls (Avg 2.747 ms)
[0x7f9500c0e918] packetizer_mpeg4audio demux packetizer debug: detected ADTS format
[0x7f9500c0e918] packetizer_mpeg4audio demux packetizer: AAC channels: 2 samplerate: 44100
[0x7f9508000b28] main input debug: selecting program id=0
[0x7f9500c0ef98] main demux debug: using demux module "es"
[0x7f9500c0ef98] main demux debug: TIMER module_need() : 6.409 ms - Total 6.409 ms / 1 intvls (Avg 6.409 ms)
[0x7f9500009a08] main decoder debug: looking for packetizer module: 21 candidates
[0x7f9500009a08] packetizer_mpeg4audio decoder debug: running MPEG4 audio packetizer
[0x7f9500009a08] packetizer_mpeg4audio decoder debug: AAC 44100Hz 1024 samples/frame
[0x7f9500009a08] main decoder debug: using packetizer module "packetizer_mpeg4audio"
[0x7f9500009a08] main decoder debug: TIMER module_need() : 0.254 ms - Total 0.254 ms / 1 intvls (Avg 0.254 ms)
[0x7f9508000b28] main input debug: starting in sync mode
[0x7f950000a648] main demux meta debug: looking for meta reader module: 2 candidates
[0x7f950000a648] lua demux meta debug: Trying Lua scripts in /home/dale/.local/share/vlc/lua/meta/reader
[0x7f950000a648] lua demux meta debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/reader
[0x7f950000a648] lua demux meta debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/reader/filename.luac
[0x7f950000a648] lua demux meta debug: Trying Lua scripts in /usr/share/vlc/lua/meta/reader
[0x7f950000a648] main demux meta debug: no meta reader module matching "any" could be loaded
[0x7f950000a648] main demux meta debug: TIMER module_need() : 0.907 ms - Total 0.907 ms / 1 intvls (Avg 0.907 ms)
[0x7f9508000b28] main input debug: `http://kegl-fm.akacast.akamaistream.net/7/379/20090/v1/auth.akacast.akamaistream.net/kegl-fm' successfully opened
[0x7f9508000b28] main input debug: Buffering 0%
[0x7f9508000b28] main input debug: switching to async mode
[0x7f9508000b28] main input debug: Buffering 2%
[0x7f9508000b28] main input debug: Buffering 4%
[0x7f9508000b28] main input debug: Buffering 6%
[0x7f9508000b28] main input debug: Buffering 9%
[0x7f9508000b28] main input debug: Buffering 11%
[0x7f9508000b28] main input debug: Buffering 13%
[0x7f9508000b28] main input debug: Buffering 16%
[0x7f9508000b28] main input debug: Buffering 18%
[0x7f9508000b28] main input debug: Buffering 20%
[0x7f9508000b28] main input debug: Buffering 23%
[0x7f9508000b28] main input debug: Buffering 25%
[0x7f9508000b28] main input debug: Buffering 27%
[0x7f9508000b28] main input debug: Buffering 30%
[0x7f9508000b28] main input debug: Buffering 32%
[0x7f9508000b28] main input debug: Buffering 34%
[0x7f9508000b28] main input debug: Buffering 37%
[0x7f9508000b28] main input debug: Buffering 39%
[0x7f9508000b28] main input debug: Buffering 41%
[0x7f9508000b28] main input debug: Buffering 44%
[0x7f9508000b28] main input debug: Buffering 46%
[0x7f9500002aa8] main stream output debug: adding a new sout input (sout_input:0x7f94f80008e0)
[0x7f9500001538] stream_out_transcode stream out debug: creating audio transcoding from fcc=`mp4a' to fcc=`s16l'
[0x7f9508000b28] main input debug: Buffering 48%
[0x7f9508000b28] main input debug: Buffering 51%
[0x7f9508000b28] main input debug: Buffering 53%
[0x7f9508000b28] main input debug: Buffering 55%
[0x7f9508000b28] main input debug: Buffering 58%
[0x7f9508000b28] main input debug: Buffering 60%
[0x7f94f80009e8] main generic debug: looking for decoder module: 28 candidates
[0x7f9508000b28] main input debug: Buffering 62%
[0x7f9508000b28] main input debug: Buffering 65%
[0x7f9508000b28] main input debug: Buffering 67%
[0x7f9508000b28] main input debug: Buffering 69%
[0x7f9508000b28] main input debug: Buffering 71%
[0x7f9508000b28] main input debug: Buffering 74%
[0x7f9508000b28] main input debug: Buffering 76%
[0x7f9508000b28] main input debug: Buffering 78%
[0x7f9508000b28] main input debug: Buffering 81%
[0x7f9508000b28] main input debug: Buffering 83%
[0x7f9508000b28] main input debug: Buffering 85%
[0x7f9508000b28] main input debug: Buffering 88%
[0x7f9508000b28] main input debug: Buffering 90%
[0x7f9508000b28] main input debug: Buffering 92%
[0x7f9508000b28] main input debug: Buffering 95%
[0x7f9508000b28] main input debug: Buffering 97%
[0x7f9508000b28] main input debug: Buffering 99%
[0x7f9508000b28] main input debug: Stream buffering done (1021 ms in 2 ms)
[0x7f94f80009e8] main generic debug: using decoder module "faad"
[0x7f94f80009e8] main generic debug: TIMER module_need() : 15.460 ms - Total 15.460 ms / 1 intvls (Avg 15.460 ms)
[0x7f94f8000e28] main encoder debug: looking for encoder module: 12 candidates
[0x7f94f8000e28] araw encoder debug: samplerate:44100Hz channels:2 bits/sample:16
[0x7f94f8000e28] main encoder debug: using encoder module "araw"
[0x7f94f8000e28] main encoder debug: TIMER module_need() : 0.939 ms - Total 0.939 ms / 1 intvls (Avg 0.939 ms)
[0x7f9500001538] stream_out_transcode stream out debug: Looking for filter (f32l->s16l, channels 2->2, rate 44100->44100)
[0x7f94f8002e48] main filter debug: looking for audio filter module: 13 candidates
[0x7f94f8002e48] audio_format filter debug: f32l->s16l, bits per sample: 32->16
[0x7f94f8002e48] main filter debug: using audio filter module "audio_format"
[0x7f94f8002e48] main filter debug: TIMER module_need() : 2.506 ms - Total 2.506 ms / 1 intvls (Avg 2.506 ms)
[0x7f9500001538] main stream out debug: Filter 'audio_format' (0x7f94f8002e48) appended to chain
[0x7f9500001538] stream_out_transcode stream out debug: Got complete audio filter chain
[0x7f95000019a8] main mux debug: adding a new input
[0x7f95000019a8] mux_wav mux debug: adding 2 input channels, 44100Hz
[0x7f9508000b28] main input debug: Decoder buffering done in 18 ms
[0x7f94f80009e8] faad generic warning: decoded zero sample
[0x7f9500c0e728] access_http access debug: New Title=Red Hot Chili Peppers - text="Give It Away" song_spot="M" MediaBaseId="1128705" itunesTrackId="309577580" amgTrackId="0" amgArtistId="0" TAID="6771" TPID="1056863" cartcutId="0703751001"
[0x7f95000019a8] mux_wav mux debug: writing header data
[0x7f9500c0e728] access_http access debug: New Title=Where DFW ROCKS! - text="TheEagle" song_spot="T" MediaBaseId="0" itunesTrackId="0" amgTrackId="0" amgArtistId="0" TAID="0" TPID="0" cartcutId="0"
[0x7f9500c0e728] access_http access debug: New Title=Queen - text="We Will Rock You/we Are The Champions" song_spot="M" MediaBaseId="1109281" itunesTrackId="214404911" amgTrackId="0" amgArtistId="0" TAID="4258" TPID="586169" cartcutId="0703646001"
[0x7f9500c0e728] access_http access debug: New Title=Where DFW ROCKS! - text="TheEagle" song_spot="T" MediaBaseId="0" itunesTrackId="0" amgTrackId="0" amgArtistId="0" TAID="0" TPID="0" cartcutId="0"
[0x7f9500c0e728] access_http access debug: New Title=Shinedown - text="Bully" song_spot="M" MediaBaseId="1846600" itunesTrackId="0" amgTrackId="0" amgArtistId="0" TAID="58653" TPID="16238460" cartcutId="0858067001"
[0x7f9500c0e728] access_http access debug: New Title=Where DFW ROCKS! - text="TheEagle" song_spot="T" MediaBaseId="0" itunesTrackId="0" amgTrackId="0" amgArtistId="0" TAID="0" TPID="0" cartcutId="0"
[0x7f9500c0e728] access_http access debug: New Title=Lit - text="My Own Worst Enemy" song_spot="M" MediaBaseId="1183511" itunesTrackId="303187112" amgTrackId="0" amgArtistId="0" TAID="39825" TPID="2554149" cartcutId="0705828001"
[0x7f9500c0e728] access_http access debug: New Title=Where DFW ROCKS! - text="TheEagle" song_spot="T" MediaBaseId="0" itunesTrackId="0" amgTrackId="0" amgArtistId="0" TAID="0" TPID="0" cartcutId="0"
[0x7f9500c0e728] access_http access debug: New Title=Black Sabbath - text="War Pigs" song_spot="M" MediaBaseId="1096861" itunesTrackId="168392764" amgTrackId="0" amgArtistId="0" TAID="2358" TPID="583356" cartcutId="0704862001"
[0x7f9500c0e728] access_http access debug: New Title=Where DFW ROCKS! - text="TheEagle" song_spot="T" MediaBaseId="0" itunesTrackId="0" amgTrackId="0" amgArtistId="0" TAID="0" TPID="0" cartcutId="0"
[0x7f9500c0e728] access_http access debug: New Title=Foo Fighters - text="Rope" song_spot="M" MediaBaseId="1783785" itunesTrackId="0" amgTrackId="0" amgArtistId="0" TAID="72280" TPID="13092959" cartcutId="0708740001"
[0x7f9500c0e728] access_http access debug: New Title=Where DFW ROCKS! - text="TheEagle" song_spot="T" MediaBaseId="0" itunesTrackId="0" amgTrackId="0" amgArtistId="0" TAID="0" TPID="0" cartcutId="0"
[0x7f9500c0e728] access_http access debug: New Title=Metallica / San Francisco Symphony - text="No Leaf Clover" song_spot="M" MediaBaseId="1189330" itunesTrackId="308922082" amgTrackId="0" amgArtistId="0" TAID="58269" TPID="0" cartcutId="0709324001"
[0x7f9500c0e728] access_http access debug: New Title=Where DFW ROCKS! - text="TheEagle" song_spot="T" MediaBaseId="0" itunesTrackId="0" amgTrackId="0" amgArtistId="0" TAID="0" TPID="0" cartcutId="0"
[0x7f9500c0e728] access_http access debug: New Title=Led Zeppelin - text="Immigrant Song" song_spot="M" MediaBaseId="1095221" itunesTrackId="267651231" amgTrackId="0" amgArtistId="0" TAID="1807" TPID="1093840" cartcutId="0702762001"
[0x7f9500c0e728] access_http access debug: New Title=Where DFW ROCKS! - text="TheEagle" song_spot="T" MediaBaseId="0" itunesTrackId="0" amgTrackId="0" amgArtistId="0" TAID="0" TPID="0" cartcutId="0"
[0x7f9500c0e728] access_http access debug: got disconnected, trying to reconnect
[0x7f9500c0e728] main access debug: net: connecting to kegl-fm.akacast.akamaistream.net port 80
[0x7f9500c0e728] main access debug: connection succeeded (socket = 6)
[0x7f9500c0e728] access_http access debug: protocol 'HTTP' answer code 302
[0x7f9508000b28] main input debug: EOF reached
[0x7f9508000b28] main input debug: waiting decoder fifos to empty
[0x1796588] main playlist debug: finished input
[0x7f9500c0e728] main access debug: waitpipe: object killed
[0x7f9500009a08] main decoder debug: removing module "packetizer_mpeg4audio"
[0x7f9500009a08] main decoder debug: killing decoder fourcc `mp4a', 0 PES in FIFO
[0x7f9500002aa8] main stream output debug: removing a sout input (sout_input:0x7f94f80008e0)
[0x7f94f8000e28] main encoder debug: TIMER encoding audio frame : 0.001 ms - Total 385.169 ms / 341770 intvls (Avg 0.001 ms)
[0x7f94f80009e8] main generic debug: removing module "faad"
[0x7f94f8000e28] main encoder debug: removing module "araw"
[0x7f9500001538] main stream out debug: Filter 0x7f94f8002e48 removed from chain
[0x7f94f8002e48] main filter debug: removing module "audio_format"
[0x7f95000019a8] mux_wav mux debug: removing input
[0x7f95000019a8] mux_wav mux debug: writing header data
[0x7f95000019a8] main mux warning: no more input streams for this mux
[0x7f9500c0ef98] main demux debug: removing module "es"
[0x7f9500c0e918] main demux packetizer debug: removing module "packetizer_mpeg4audio"
[0x7f950000b608] main stream debug: removing module "stream_filter_record"
[0x7f9500c0e728] main access debug: removing module "access_http"
[0x7f9508000b28] main input debug: Program doesn't contain anymore ES
[0x1796588] main playlist debug: dead input
[0x7f9500002aa8] main stream output debug: destroying useless sout
[0x7f9500001538] main stream out debug: destroying chain... (name=transcode)
[0x7f9500001538] main stream out debug: removing module "stream_out_transcode"
[0x7f9500001538] main stream out debug: destroying chain done
[0x7f9500002ea8] main stream out debug: destroying chain... (name=std)
[0x7f9500002ea8] main stream out debug: removing module "stream_out_standard"
[0x7f95000019a8] main mux debug: removing module "mux_wav"
[0x7f95000021a8] main access out debug: removing module "access_output_file"
[0x7f95000021a8] access_output_file access out debug: file access output closed
[0x7f9500002ea8] main stream out debug: destroying chain done
[0x7f9508000b28] main input debug: TIMER input launching for 'http://kegl-fm.akacast.akamaistream.net/7/379/20090/v1/auth.akacast.akamaistream.net/kegl-fm' : 612.423 ms - Total 612.423 ms / 1 intvls (Avg 612.423 ms)
[0x1796588] main playlist debug: changing item without a request (current 0/2)
[0x1796588] main playlist debug: using item 1
[0x1796588] main playlist debug: starting playback of the new playlist item
[0x1796588] main playlist debug: resyncing on quit
[0x1796588] main playlist debug: quit is at 1
[0x1796588] main playlist debug: creating new input thread
[0x7f9508005228] main input debug: Creating an input for 'quit'
[0x7f9508005228] main input debug: using timeshift granularity of 50 MiB, in path '/tmp'
[0x7f9508005228] main input debug: `vlc://quit' gives access `vlc' demux `' path `quit'
[0x7f9508005228] main input debug: creating demux: access='vlc' demux='' location='quit' file='(null)'
[0x7f9500001538] main demux debug: looking for access_demux module: 1 candidate
[0x7f9500001538] idummy demux: command `quit'
[0x159f108] main libvlc debug: exiting
[0x7f9500001538] main demux debug: using access_demux module "idummy"
[0x7f9500001538] main demux debug: TIMER module_need() : 11.780 ms - Total 11.780 ms / 1 intvls (Avg 11.780 ms)
[0x159f108] main libvlc debug: deactivating the playlist
[0x1796588] main playlist debug: deactivating the playlist
[0x1796588] main playlist debug: incoming request - stopping current input
[0x1796588] main playlist debug: dying input
[0x7f9500c0e728] main demux meta debug: looking for meta reader module: 2 candidates
[0x7f9500c0e728] lua demux meta debug: Trying Lua scripts in /home/dale/.local/share/vlc/lua/meta/reader
[0x7f9500c0e728] lua demux meta debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/reader
[0x7f9500c0e728] lua demux meta debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/reader/filename.luac
[0x7f9500c0e728] lua demux meta debug: Trying Lua scripts in /usr/share/vlc/lua/meta/reader
[0x7f9500c0e728] main demux meta debug: no meta reader module matching "any" could be loaded
[0x7f9500c0e728] main demux meta debug: TIMER module_need() : 1.047 ms - Total 1.047 ms / 1 intvls (Avg 1.047 ms)
[0x7f9508005228] main input debug: `vlc://quit' successfully opened
[0x1796588] main playlist debug: dying input
[0x1796588] main playlist debug: dying input
[0x7f9500001538] main demux debug: removing module "idummy"
[0x1796588] main playlist debug: dead input
[0x7f9508005228] main input debug: TIMER input launching for 'quit' : 13.476 ms - Total 13.476 ms / 1 intvls (Avg 13.476 ms)
[0x15b5e88] main playlist export debug: saving Media Library to file /home/dale/.local/share/vlc/ml.xspf
[0x15b5e88] main playlist export debug: looking for playlist export module: 1 candidate
[0x15b5e88] main playlist export debug: using playlist export module "export"
[0x15b5e88] main playlist export debug: TIMER module_need() : 11.629 ms - Total 11.629 ms / 1 intvls (Avg 11.629 ms)
[0x15b5e88] main playlist export debug: removing module "export"
[0x1796588] main playlist debug: playlist correctly deactivated
[0x159f108] main libvlc debug: removing all services discovery tasks
[0x159f108] main libvlc debug: removing all interfaces
[0x15b3908] main interface debug: removing module "dummy"
[0x15cce78] main interface debug: removing module "hotkeys"
[0x1796588] main playlist debug: destroying
[0x159f108] main libvlc debug: TIMER ML Load : Total 50.190 ms / 1 intvls (Avg 50.190 ms)
[0x159f108] main libvlc debug: TIMER Items array build : Total 0.182 ms / 3 intvls (Avg 0.061 ms)
[0x159f108] main libvlc debug: TIMER Preparse run : Total 0.446 ms / 1 intvls (Avg 0.446 ms)
[0x159f108] main libvlc debug: TIMER ML Dump : Total 11.949 ms / 1 intvls (Avg 11.949 ms)
[0x159f108] main libvlc debug: removing stats
[0x159f108] main libvlc debug: removing module "memcpymmxext"
+ date
+ print 'end recording at Mon Feb  4 17:15:23 CST 2013 ...'



```

---

### Post by MakOwner on 2013-03-25
Really?  Nothing?

---

### Post by raydar on 2013-11-29
I wonder whether the --sout-keep option might help in your situation, MakOwner; I just came across it in trying to figure out why my own vlc command that I intend to schedule with cron doesn't work. According to [https://wiki.videolan.org/VLC_command-line_help/](https://wiki.videolan.org/VLC_command-line_help/) ,
> --sout-keep, --no-sout-keep
                                 Keep stream output open (default disabled)
          This allows you to keep an unique stream output instance across
          multiple playlist item (automatically insert the gather stream output
          if not specified) (default disabled)
and maybe that's what's happening to cut off your recordings early. I've run into streaming sites that do that. I've also seen some that change the valid "listen" url every so often, such that you have to click the website link anew each time and can't just do that once, grab the url, plug it into cron, and forget about it. :\

(I'm having the opposite problem--the following script records just fine, but never stops recording (after --run-time) or exits vlc (vlc://quit):
> vlc http:// . . . .m3u --sout="#duplicate{dst=file{dst=/home/ . . . /Desktop/ . . . .ts},dst=display} --no-sout-rtp-sap --no-sout-standard-sap --ttl=1 --sout-keep --run-time=7200" vlc://quit
If you see anything screwy with that that could be responsible, please let me know.)

---

