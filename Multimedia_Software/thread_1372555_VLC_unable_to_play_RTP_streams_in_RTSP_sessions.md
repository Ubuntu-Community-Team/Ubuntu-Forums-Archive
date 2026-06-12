---
title: "VLC unable to play RTP streams in RTSP sessions"
date: 2010-01-04
forum: Multimedia Software
---

### Post by aquarian09 on 2010-01-04
hey there,

I am working on my own RTSP server that streams a video to VLC.

The problem is that after all the RTSP negotiation is done (Options, Describe, Setup and Play), the VLC just goes into a halt state. it does nothing. Ive used wireshark to capture the packets, and within the wireshark trace i can see the client_ports that VLC is sending to the RTSP server. The rtsp server then has to stream RTP packets onto these ports. 

Just as a curiosity, i ran VLC in RTP mode and gave it the ports from above, and vallaah! the video played perfectly! now im wondering why VLC plays the video when i manually tell it to receive RTP over a certain port, but doesnt automatically run it when given the same information through RTSP.

Im attaching the VLC logs below:


```

VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc debug: checking builtin modules
[00000001] main libvlc debug: checking plugin modules
[00000001] main libvlc debug: loading plugins cache file /home/safi/.cache/vlc/plugins-04041e.dat
[00000001] main libvlc debug: recursively browsing `/usr/lib/vlc'
[00000001] main libvlc debug: module bank initialized, found 271 modules
[00000001] main libvlc debug: opening config file (/home/safi/.config/vlc/vlcrc)
[00000001] main libvlc debug: CPU has capabilities 486 586 MMX MMXEXT SSE SSE2 FPU 
[00000001] main libvlc debug: looking for memcpy module: 3 candidates
[00000001] main libvlc debug: using memcpy module "memcpymmxext"
[00000368] main interaction debug: thread 3080170384 (Interaction control) created at priority 0 (interface/interaction.c:382)
[00000368] main interaction debug: thread started
[00000370] main input debug: Creating an input for 'Media Library'
[00000370] main input debug: Input is a meta file: disabling unneeded options
[00000370] main input debug: `file/xspf-open:///home/safi/.local/share/vlc/ml.xspf' gives access `file' demux `xspf-open' path `/home/safi/.local/share/vlc/ml.xspf'
[00000370] main input debug: creating access 'file' path='/home/safi/.local/share/vlc/ml.xspf'
[00000371] main access debug: looking for access module: 3 candidates
[00000371] access_file access debug: opening file `/home/safi/.local/share/vlc/ml.xspf'
[00000371] main access debug: using access module "access_file"
[00000371] main access debug: TIMER module_Need() : 0.891 ms - Total 0.891 ms / 1 intvls (Avg 0.891 ms)
[00000376] main stream debug: Using AStream*Stream
[00000376] main stream debug: pre-buffering...
[00000376] main stream debug: received first data for our buffer
[00000370] main input debug: creating demux: access='file' demux='xspf-open' path='/home/safi/.local/share/vlc/ml.xspf'
[00000377] main demux debug: looking for demux module: 1 candidate
[00000377] playlist demux debug: using XSPF playlist reader
[00000377] main demux debug: using demux module "playlist"
[00000377] main demux debug: TIMER module_Need() : 0.521 ms - Total 0.521 ms / 1 intvls (Avg 0.521 ms)
[00000370] main input debug: `file/xspf-open:///home/safi/.local/share/vlc/ml.xspf' successfully opened
[00000392] main xml debug: looking for xml module: 2 candidates
[00000392] main xml debug: using xml module "xml"
[00000392] main xml debug: TIMER module_Need() : 0.920 ms - Total 0.920 ms / 1 intvls (Avg 0.920 ms)
[00000377] playlist demux debug: parsed 0 tracks successfully
[00000392] main xml debug: removing module "xml"
[00000370] main input debug: EOF reached
[00000370] main input debug: control type=1
[00000377] main demux debug: removing module "playlist"
[00000371] main access debug: removing module "access_file"
[00000370] main input debug: TIMER input launching for 'Media Library' : 5.525 ms - Total 5.525 ms / 1 intvls (Avg 5.525 ms)
[00000394] main preparser debug: waiting for thread initialization
[00000394] main preparser debug: thread started
[00000394] main preparser debug: thread 3071777680 (preparser) created at priority 0 (playlist/thread.c:79)
[00000395] main fetcher debug: thread started
[00000395] main fetcher debug: waiting for thread initialization
[00000395] main fetcher debug: thread 3057626000 (fetcher) created at priority 0 (playlist/thread.c:108)
[00000369] main playlist debug: thread started
[00000369] main playlist debug: waiting for thread initialization
[00000369] main playlist debug: rebuilding array of current - root Playlist
[00000369] main playlist debug: rebuild done - 0 items, index -1
[00000369] main playlist debug: thread 3049233296 (playlist) created at priority 0 (playlist/thread.c:117)
[00000396] main interface debug: looking for interface module: 1 candidate
[00000396] main interface debug: using interface module "hotkeys"
[00000396] main interface debug: TIMER module_Need() : 0.339 ms - Total 0.339 ms / 1 intvls (Avg 0.339 ms)
[00000396] main interface debug: thread started
[00000396] main interface debug: thread 3040840592 (interface) created at priority 0 (interface/interface.c:168)
[00000398] main interface debug: looking for interface module: 1 candidate
[00000398] main interface debug: using interface module "inhibit"
[00000398] main interface debug: TIMER module_Need() : 2.465 ms - Total 2.465 ms / 1 intvls (Avg 2.465 ms)
[00000398] main interface debug: thread started
[00000398] main interface debug: thread 3032447888 (interface) created at priority 0 (interface/interface.c:168)
[00000400] main interface debug: looking for interface module: 1 candidate
[00000400] main interface debug: using interface module "screensaver"
[00000400] main interface debug: TIMER module_Need() : 0.378 ms - Total 0.378 ms / 1 intvls (Avg 0.378 ms)
[00000400] main interface debug: thread started
[00000400] main interface debug: thread 3024055184 (interface) created at priority 0 (interface/interface.c:168)
[00000369] main playlist debug: adding item `rtsp://127.0.0.1/' ( rtsp://127.0.0.1/ )
[00000402] main interface debug: looking for interface module: 22 candidates
[00000402] main interface debug: using interface module "signals"
[00000402] main interface debug: TIMER module_Need() : 0.352 ms - Total 0.352 ms / 1 intvls (Avg 0.352 ms)
[00000402] main interface debug: thread started
[00000402] main interface debug: thread 3007269776 (interface) created at priority 0 (interface/interface.c:168)
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[00000404] main interface debug: looking for interface module: 4 candidates
[00000404] main interface debug: using interface module "qt4"
[00000404] main interface debug: TIMER module_Need() : 161.781 ms - Total 161.781 ms / 1 intvls (Avg 161.781 ms)
[00000404] main interface debug: thread 2984348560 (interface) created at priority 0 (interface/interface.c:168)
[00000369] main playlist debug: rebuilding array of current - root Playlist
[00000369] main playlist debug: rebuild done - 1 items, index -1
[00000369] main playlist debug: starting new item
[00000369] main playlist debug: processing request item null node Playlist skip 0
[00000369] main playlist debug: creating new input thread
[00000407] main input debug: Creating an input for 'rtsp://127.0.0.1/'
[00000407] main input debug: waiting for thread initialization
[00000404] main interface debug: thread started
[00000407] main input debug: thread started
[00000407] main input debug: thread 2975955856 (input) created at priority 10 (input/input.c:370)
[00000407] main input debug: `rtsp://127.0.0.1/' gives access `rtsp' demux `' path `127.0.0.1/'
[00000407] main input debug: creating demux: access='rtsp' demux='' path='127.0.0.1/'
[00000408] main demux debug: looking for access_demux module: 1 candidate
Sending request: OPTIONS rtsp://127.0.0.1/ RTSP/1.0
CSeq: 1
User-Agent: VLC media player (LIVE555 Streaming Media v2008.07.24)


Received OPTIONS response: RTSP/1.0 200 OK
CSeq: 1
Public: DESCRIBE, SETUP, TEARDOWN, PLAY, PAUSE, SPEED


Sending request: DESCRIBE rtsp://127.0.0.1/ RTSP/1.0
CSeq: 2
Accept: application/sdp
User-Agent: VLC media player (LIVE555 Streaming Media v2008.07.24)


Received DESCRIBE response:   RTSP/1.0 200 OK
CSeq: 2
Date: Sat, 05 Dec 2009,18:30:35
Content-Type: application/sdp
Content-Length: 148


Need to read 148 extra bytes
Read 148 extra bytes: v=0
o=Ourstreamer 1262640610 1262640610 IN IP4 127.0.0.1
s=News Sports
i=Toggling New and Sports
c=IN IP4 0.0.0.0
t=0 0
m=video 0 RTP/AVP 32

[00000408] live555 demux debug: RTP subsession 'video/MPV'
Sending request: SETUP rtsp://127.0.0.1/ RTSP/1.0
CSeq: 3
Transport: RTP/AVP;unicast;client_port=34636-34637
User-Agent: VLC media player (LIVE555 Streaming Media v2008.07.24)


Received SETUP response:   RTSP/1.0 200 OK
CSeq: 3
Date: Sat, 05 Dec 2009,18:30:35
Session: 5212d4c6
Transport: RTP/AVP;unicast;client_port=34636-34637;server_port=7000-7001


[00000407] main input debug: selecting program id=0
[00000408] live555 demux debug: setup start: 0 stop:0
Sending request: PLAY rtsp://127.0.0.1/ RTSP/1.0
CSeq: 4
Session: 5212d4c6
Range: npt=0.000-
User-Agent: VLC media player (LIVE555 Streaming Media v2008.07.24)


Received PLAY response:   RTSP/1.0 200 OK
Session: 5212d4c6
CSeq: 4


[00000408] live555 demux debug: play start: 0 stop:0
[00000408] main demux debug: using access_demux module "live555"
[00000408] main demux debug: TIMER module_Need() : 53.150 ms - Total 53.150 ms / 1 intvls (Avg 53.150 ms)
[00000411] main decoder debug: looking for decoder module: 30 candidates
[00000411] main decoder debug: using decoder module "libmpeg2"
[00000411] main decoder debug: TIMER module_Need() : 2.518 ms - Total 2.518 ms / 1 intvls (Avg 2.518 ms)
[00000411] main decoder debug: thread started
[00000411] main decoder debug: thread 2963200912 (decoder) created at priority 0 (input/decoder.c:217)
[00000407] main input debug: `rtsp://127.0.0.1/' successfully opened
[00000404] qt4 interface debug: Error while initializing qt-specific localization
[00000404] qt4 interface debug: Updating the stream status: 3

```After this last line, the VLC GUI pops up but nothing happens. No video is played. 
However i can see in wireshark that RTP packets are being sent from the correct server_ports to the correct client_ports (as defined in the RTSP SETUP message).

Is it something to do with the SDP that my RTSP server sends? 

The only error i can see in this log is "qt4 interface debug: Error while initializing qt-specific localization". What does this mean?

Thanks!

---

