---
title: "Looks like I'm blocked from a music stream"
date: 2010-09-12
forum: Multimedia Software
---

### Post by Silvernail on 2010-09-12
I seem to be blocked from the music stream.
I am using this command line:
rhythmbox [http://www.wholewheatradio.org:8100/listen.pls](http://www.wholewheatradio.org:8100/listen.pls)
for the last year or so. I worked until last week.

I get a service forbidden error, and this:
dave@dave:~$ rhythmbox --debug [http://www.wholewheatradio.org:8100/listen.pls](http://www.wholewheatradio.org:8100/listen.pls) &> rhythmbox-debug.txt
dave@dave:~$ cat rhythmbox-debug.txt> 
(15:25:56) [0x8e2e028] [rb_debug_init_match] rb-debug.c:213: Debugging enabled
(15:25:56) [0x8e2e028] [main] main.c:177: initializing Rhythmbox 0.12.8
(15:25:56) [0x8e2e028] [rb_threads_init] rb-util.c:482: GMutex isn't recursive
(15:25:56) [0x8e2e028] [main] main.c:185: going to create DBus object
(15:25:56) [0x8e2e028] [load_uri_args] main.c:375: examining argument [http://www.wholewheatradio.org:8100/listen.pls](http://www.wholewheatradio.org:8100/listen.pls)
(15:25:56) [0x8e2e028] [dbus_load_uri] main.c:400: Sending loadURI for [http://www.wholewheatradio.org:8100/listen.pls](http://www.wholewheatradio.org:8100/listen.pls)
(15:25:56) [0x8e2e028] [main] main.c:352: THE END
dave@dave:~$

rhythmbox plays all the other station on the play list.
vlc, mplayer, audacious - exhibit the same results.

vlc log:> 
main error: ES_OUT_SET_(GROUP_)PCR  is called too late, increasing pts_delay to 182 ms
main error: ES_OUT_RESET_PCR called
mux_ogg: Close
v4l2 error: unable to set white_balance_temperature (98091a) to 4000 (Input/output error)
v4l2 error: unable to set exposure_(absolute) (9a0902) to 166 (Input/output error)
-- logger module started --
v4l2 error: unable to set white_balance_temperature (98091a) to 4000 (Input/output error)
v4l2 error: unable to set exposure_(absolute) (9a0902) to 166 (Input/output error)

Is there anything that indicates the problem might be originating from my end and is only affecting that Internet radio station.

I have gone so far as to apt-get purge rhythmbox and reinstall.

Thanks
Dave

---

### Post by andrew.46 on 2010-09-12
Hi Silvernail,

Seems a little odd, for what its worth the radio station works well for me with MPlayer. Does the following work for you?

```

mplayer -cache 2048 -cache-min 80 -playlist 'http://www.wholewheatradio.org:8100/listen.pls'

```

Andrew

---

### Post by tgalati4 on 2010-09-12
Works for me using rhythmbox under Linux Mint (Jaunty), although I do get an error that it needs to search for a plug-in.  It plays OK though.

---

### Post by Silvernail on 2010-09-12
> **andrew.46 said:**
> Hi Silvernail,

Seems a little odd, for what its worth the radio station works well for me with MPlayer. Does the following work for you?

```

mplayer -cache 2048 -cache-min 80 -playlist 'http://www.wholewheatradio.org:8100/listen.pls'

```

Andrew

Does not work for me. Same error as always.
> dave@dave:~$ mplayer -cache 2048 -cache-min 80 -playlist 'http://www.wholewheatradio.org:8100/listen.pls'
Resolving [www.wholewheatradio.org](www.wholewheatradio.org) for AF_INET6...
Couldn't resolve name for AF_INET6: [www.wholewheatradio.org](www.wholewheatradio.org)
Resolving [www.wholewheatradio.org](www.wholewheatradio.org) for AF_INET...
Connecting to server [www.wholewheatradio.org](www.wholewheatradio.org)[207.150.188.54]: 8100...
Cache size set to 2048 KBytes
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing [http://www.wholewheatradio.org:8100/](http://www.wholewheatradio.org:8100/).
Resolving [www.wholewheatradio.org](www.wholewheatradio.org) for AF_INET6...
Couldn't resolve name for AF_INET6: [www.wholewheatradio.org](www.wholewheatradio.org)
Resolving [www.wholewheatradio.org](www.wholewheatradio.org) for AF_INET...
Connecting to server [www.wholewheatradio.org](www.wholewheatradio.org)[207.150.188.54]: 8100...
Error: ICY-Server return 'Service Forbidden'
STREAM_ASF, URL: [http://www.wholewheatradio.org:8100/](http://www.wholewheatradio.org:8100/)
Resolving [www.wholewheatradio.org](www.wholewheatradio.org) for AF_INET6...
Couldn't resolve name for AF_INET6: [www.wholewheatradio.org](www.wholewheatradio.org)
Resolving [www.wholewheatradio.org](www.wholewheatradio.org) for AF_INET...
Connecting to server [www.wholewheatradio.org](www.wholewheatradio.org)[207.150.188.54]: 8100...
Server returned 403:Service Forbidden
Failed to parse header.
Failed, exiting.
Resolving [www.wholewheatradio.org](www.wholewheatradio.org) for AF_INET6...
Couldn't resolve name for AF_INET6: [www.wholewheatradio.org](www.wholewheatradio.org)
Resolving [www.wholewheatradio.org](www.wholewheatradio.org) for AF_INET...
Connecting to server [www.wholewheatradio.org](www.wholewheatradio.org)[207.150.188.54]: 8100...
Error: ICY-Server return 'Service Forbidden'
No stream found to handle url [http://www.wholewheatradio.org:8100/](http://www.wholewheatradio.org:8100/)


Exiting... (End of file)
dave@dave:~$ 


---

### Post by andrew.46 on 2010-09-12
Hi dave,

Very odd.... the successful connection should look like this:

```

andrew@skamandros~$ mplayer -cache 2048 -cache-min 80 -playlist 'http://www.wholewheatradio.org:8100/listen.pls'
Resolving www.wholewheatradio.org for AF_INET6...

Couldn't resolve name for AF_INET6: www.wholewheatradio.org
Resolving www.wholewheatradio.org for AF_INET...
Connecting to server www.wholewheatradio.org[207.150.188.54]: 8100...

Cache size set to 2048 KBytes
MPlayer SVN-r32141-4.4.4 (C) 2000-2010 MPlayer Team

Playing http://www.wholewheatradio.org:8100/.
Resolving www.wholewheatradio.org for AF_INET6...

Couldn't resolve name for AF_INET6: www.wholewheatradio.org
Resolving www.wholewheatradio.org for AF_INET...
Connecting to server www.wholewheatradio.org[207.150.188.54]: 8100...

Name   : Whole Wheat Radio For Grownups - Talkeetna, Alaska - All Independent Singer-Songwriters, Folk, Blues, Jazz
Genre  : Folk Blues Jazz Indie
Website: http://wholewheatradio.org
Public : yes
Bitrate: 56kbit/s
Cache size set to 2048 KBytes
Cache fill:  8.98% (188416 bytes)   
ICY Info: StreamTitle='Niki Leeman - The Other Side';StreamUrl='http://wholewheatradio.org';
Cache fill: 79.69% (1671168 bytes)   

Audio only file format detected.
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
mpg123: Can't rewind stream by 792 bits!
AUDIO: 22050 Hz, 2 ch, s16le, 56.0 kbit/7.94% (ratio: 7000->88200)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [oss] 22050Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
mpg123: Can't rewind stream by 238 bits!
A:   6.4 (06.4) of 0.0 (unknown)  0.4% 79% 

```

The only 2 things I can think of are that perhaps indeed your IP is banned, or perhaps you have a firewall that is interfering with the stream?

Andrew

---

