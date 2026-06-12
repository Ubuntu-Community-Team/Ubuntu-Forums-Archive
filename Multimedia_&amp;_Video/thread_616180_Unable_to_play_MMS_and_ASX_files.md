---
title: "Unable to play MMS and ASX files"
date: 2007-11-17
forum: Multimedia &amp; Video
---

### Post by Slasher Fun on 2007-11-17
Hi,

I'm using Ubuntu Gutsy, and I think having enough installed codecs (gstreamer0.10-ffmpeg, w32codecs, libmms0, etc... are installed) to play mms:// and .asx files, but it does not work...

Here is what happens for example with mms://sdmc.contents.edgestreams.net/horsgv/regions/siege/infos/f2/20h/HD_20h_20071117.wmv (same behavior with every other mms or asx file) :
* Mozilla-mplayer : says "connected" and takes 100% of the CPU
* Mplayer in a terminal : says "connected" and... that's all.
* Totem : stops responding during about one or two minutes, then say "Unable to open, maybe you don't have permission to open this file".
* VLC : Displays the "pause" button instead of "play", meaning it tries to read, but no sound or image, and the time stays on 0:00:00/0:00:00

Works fine on Windows XP on the same internet connexion (DSL behind a D-Link router).

Any idea? Thank you !

---

### Post by Slasher Fun on 2007-11-18
View -> Messages in VLC says :
access_mms warning: cannot fill buffer
access_mms warning: failed to receive command (aborting)
access_mms error: unknown answer (0x2 instead of 0x06)
access_mms debug: Connection closed

---

### Post by Slasher Fun on 2007-11-18
Oops, full output of messages :
```
main debug: CPU has capabilities 486 586 MMX MMXEXT SSE SSE2 FPU 
main debug: looking for memcpy module: 1 candidate
main debug: using memcpy module "memcpy"
main debug: waiting for thread completion
main debug: thread 3085151120 (playlist) created at priority 0 (playlist/playlist.c:184)
main debug: waiting for thread completion
main debug: thread 3076758416 (preparser) created at priority 0 (playlist/playlist.c:210)
main debug: looking for interface module: 1 candidate
main debug: using interface module "hotkeys"
main debug: thread 3068365712 (interface) created at priority 0 (interface/interface.c:231)
main debug: looking for interface module: 1 candidate
main debug: using interface module "screensaver"
main debug: thread 3059973008 (interface) created at priority 0 (interface/interface.c:231)
main debug: adding playlist item `mms://sdmc.contents.edgestreams.net/horsgv/regions/siege/infos/f2/20h/HD_20h_20071117.wmv' ( mms://sdmc.contents.edgestreams.net/horsgv/regions/siege/infos/f2/20h/HD_20h_20071117.wmv )
main debug: looking for interface module: 5 candidates
main debug: using interface module "wxwidgets"
main debug: thread 3046230928 (manager) created at priority 0 (interface/interface.c:216)
wxwidgets debug: Using last windows config '(-1,0,0,1440,900)(0,15,96,460,90)(2,4,308,410,564)(6,0,0,-1,150)'
wxwidgets debug: id=0 p=(15,96) s=(460,90)
wxwidgets debug: id=2 p=(4,308) s=(410,564)
wxwidgets debug: id=6 p=(0,0) s=(-1,150)
main debug: nothing requested, starting
main debug: creating new input thread
main debug: waiting for thread completion
main debug: creating statistics handler
main debug: `mms://sdmc.contents.edgestreams.net/horsgv/regions/siege/infos/f2/20h/HD_20h_20071117.wmv' gives access `mms' demux `' path `sdmc.contents.edgestreams.net/horsgv/regions/siege/infos/f2/20h/HD_20h_20071117.wmv'
main debug: creating demux: access='mms' demux='' path='sdmc.contents.edgestreams.net/horsgv/regions/siege/infos/f2/20h/HD_20h_20071117.wmv'
main debug: looking for access_demux module: 0 candidates
main warning: no access_demux module matched "mms"
main debug: creating access 'mms' path='sdmc.contents.edgestreams.net/horsgv/regions/siege/infos/f2/20h/HD_20h_20071117.wmv'
main debug: looking for access2 module: 6 candidates
access_mms debug: waiting for connection...
main debug: net: connecting to sdmc.contents.edgestreams.net port 1755
main debug: thread 3024038800 (input) created at priority 0 (input/input.c:265)
main debug: connection in progress
access_mms debug: connection(tcp) with "sdmc.contents.edgestreams.net:1755" successful
access_mms debug: generated guid: babac001-802e-deca-ef101f9ec31ab58c
access_mms debug: recv command start_sequence:0x00000001 command_id:0xb00bface length:128 len8:16 sequence 0x00000000 len8_II:14 dir_comm:0x00040001
access_mms debug: 0x01 --> server_version:"9.01.01.3842" tool_version:"" update_player_url:"" encryption_type:"NTLM"
access_mms debug: recv command start_sequence:0x00000001 command_id:0xb00bface length:80 len8:10 sequence 0x00000001 len8_II:8 dir_comm:0x00040002
access_mms warning: cannot fill buffer
access_mms warning: failed to receive command (aborting)
access_mms error: unknown answer (0x2 instead of 0x06)
access_mms debug: Connection closed

```

---

