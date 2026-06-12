---
title: "[SOLVED] How do I save network streaming audio to a file, in a usable format? (mp3 or"
date: 2008-10-28
forum: Multimedia Software
---

### Post by tomjennings on 2008-10-28
VLC works great at playing streams, but I'm stumped as to saving a stream to disk in an encoding I can use later. .WAV would be fine, mp3 nicer, but I can do that manually.

Should not

:sout=#duplicate{dst=std{access=file,mux=wav,dst="foo.wav"}}

save the stream encoded as a WAVE format, in file foo.wav? No audio app (player, mplayer, audacity, etc) recognizes foo.wav as any audio file.

What am I missing?

---

### Post by cariboo on 2008-10-28
Have you had a look at streamtuner? When you install it, it also installs an application called streamripper. Streamtuner has a record button, just click the button and it starts recording. The default record output is mp3.

---

### Post by kattman on 2008-10-29
Check out Tunapie  Its a nice addon for VLC

---

### Post by andrew.46 on 2008-10-29
Hi tom:

> **tomjennings said:**
> VLC works great at playing streams, but I'm stumped as to saving a stream to disk in an encoding I can use later. .WAV would be fine, mp3 nicer, but I can do that manually.

MPlayer does this quite nicely:

[http://ubuntuforums.org/showthread.php?t=542276](http://ubuntuforums.org/showthread.php?t=542276)

There is an example of a scripted approach to saving a stream:

[http://andrews-corner.org/ftgws.html](http://andrews-corner.org/ftgws.html)

  Andrew

---

### Post by tomjennings on 2008-10-30
> **kattman said:**
> Check out Tunapie  Its a nice addon for VLC

Thanks!

Both (streamtuner, tunapie) are so close!!! But I want to catch a *particular* URL! 

It's not clear if Streamtuner will let me open a random URL, or pick from the Shoutcast list only, and it requires, which is problematic today. I guess I'll try hauling down the CVS version and seeing what happens...

Tunapie seems to handle ONLY shoutcast.


Shoutcast to me is the worst of broadcast radio with the worst of internet, only worse; I can't tune between stations! I wanna enter a URL not on the Shoutcast lists, adn I simply don't want to see all that shoutcast stuff.

VLC would be great, if it worked!

---

### Post by tomjennings on 2008-10-30
> **andrew.46 said:**
> Hi tom:



MPlayer does this quite nicely:
  Andrew

Aha! OK, now I'm getting somewhere!

I'm unfamiliar with streaming tech, and may have to RTFM to solve this, but it seems to connect, but I get no audio. Here's the result so far:

```

tomj@zx:~$ mplayer -playlist http://streamer.psyradio.org:8130 -vc null -vo null -ao pcm:fast:waveheader:file=psyradio.wav
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz (Family: 6, Model: 15, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Resolving streamer.psyradio.org for AF_INET6...
Couldn't resolve name for AF_INET6: streamer.psyradio.org
Resolving streamer.psyradio.org for AF_INET...
Connecting to server streamer.psyradio.org[81.88.36.42]: 8130...
Name   : p s y r a d i o * f m - psychannel
Genre  : Goa Psytrance Fullon Darkpsy
Website: http://psyradio.fm
Public : yes
Bitrate: 48kbit/s
Cache size set to 320 KBytes

ICY Info: StreamTitle='Acid Prophecy - Exosted (The Prophecy)';StreamUrl='http://psyradio.fm/';

ICY Info: StreamTitle='Cosmic Tone - Physical Reaction';StreamUrl='http://psyradio.fm/';


ICY Info: StreamTitle='Overlap - Dengerous Jungle';StreamUrl='http://psyradio.fm/';


```

(15 minutes elapsed; song title every 5 or so...)

So it gets all that title metadata, but no audio bits. (file never created). Encoding not PCM?

---

### Post by tomjennings on 2008-10-30
> **cariboo907 said:**
> Have you had a look at streamtuner

I used to love xmms! Then it fell out of all the repositories for reasons I've forgotten. 

It now seems to have fallen off the earth -- [http://www.xmms.org](http://www.xmms.org) doesn't answer when you knock on the door...


```
This server can't connect to the MySQL database. Please try http://www.xmms.org instead.

An error has occured, the webmaster has been notified.Can't connect to db.xmms.org (3 retrys giving up)
Can't connect to MySQL server on 'db.xmms.org' (4) : 2003
```

---

### Post by xc3RnbFO8P on 2008-10-30
You can change in 
Edit> Preferences> Application> xmms %q to totem %q or what ever you choose.
I use Totem, but I cant record stream,  just tries to buffer forever.
Streamtuner use Streamripper and I got it installed.
Record a stream = x-terminal-emulator -e streamripper %q

I am using Audacious.

> prefs_fn = /home/rob/.config/streamripper/streamripper.ini
Connecting...
stream: Die JukeBoX  BluePoint-Radio
server name: Icecast 2.3.2
bitrate: 128
meta interval: 16000

[ripping...    ] Sisqo - Thong Song [  203kb]
[ripping...    ] Sisqo - Thong Song [  343kb]
[ripping...    ] Jennifer Lopez - Im Gonna Be Alright [  2.54M]

The record files is in /home/your folder/name of the station
In Terminal window use CTRL S stop and start.

---

### Post by 080818jk on 2008-10-30
&#33635;&#38064;&#25995;&#30011;&#24266;&#20027;&#35201;&#32463;&#33829;&#21517;&#20154;&#23383;&#30011;[**&#21271;&#20140;&#30011;&#24266;**](http://www.danqingyuan.com/)&#31469;&#21147;&#32500;&#25252;&#23458;&#25143;&#30340;&#33402;&#26415;&#25237;&#36164;&#21033;&#30410;[**&#23383;&#30011;**](http://www.danqingyuan.com/sfzp/cgs.html)&#22312;&#30830;&#20445;&#30495;&#21697;&#12289;&#31934;&#21697;&#12289;&#26032;&#21697;&#30340;&#22522;&#30784;&#19978;[**&#23383;&#30011;**](http://www.danqingyuan.com/sfzp/cgs.html)&#36873;&#25321;&#26368;&#20855;&#26377;&#21319;&#20540;&#28508;&#21147;&#30340;&#20070;&#30011;&#23478;&#20316;&#21697;&#65292;&#21521;&#24191;&#22823;&#20070;&#30011;&#25910;&#34255;&#32773;&#21644;&#29233;&#22909;&#32773;&#25552;&#20379;&#39640;&#36136;&#37327;[**&#21271;&#20140;&#30011;&#24266;**](http://www.danqingyuan.com/)&#39640;&#21697;&#20301;&#30340;&#33402;&#26415;&#20339;&#20316;[**&#21271;&#20140;&#30011;&#24266;**](http://www.danqingyuan.com/)&#25552;&#20379;&#26368;&#20248;&#36136;&#30340;&#26381;&#21153;&#65292;&#35753;&#25237;&#36164;&#32773;&#26356;&#25918;&#24515;&#65292;&#26356;&#20445;&#38505;&#65292;&#33719;&#24471;&#26356;&#22823;&#30340;&#21033;&#30410;&#12290;

---

### Post by tomjennings on 2008-10-30
> **Ringi said:**
> You can change in 
Edit> Preferences> Application> xmms %q to totem %q or what ever you choose.

D'oh, my bad! Operator error -- the edit mechanism requires you to press RETURN after an edit in the field,I would just click CLOSE and the edit was not saved.

Unfortunately, streamripper generates bad data almost every time. 

```

streamripper http://streamer.psyradio.org:8130 -a -A -s -l 3600

```

Generates time-stamped file eg. sr_program_2008_10_30_14_42_58.aac (and .cue). The problem is that only 1 out of every 3, 4 streamripper invokations, as above, results in a file playable by VLC or mplayer. When it is good, I can convert it to wav then mp3 just fine. But when it is bad, the player either doesn't recognize it as an audio file or it plays as noise.

For one stream-rip, vlc complains:

```

[00000371] vcd access error: invalid entry points number

```

mplayer plays the resulting noise, with errors on stdout:

```

tomj@zx:~/Ripped$ mplayer sr_program_2008_10_30_14_42_58.aac

MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz (Family: 6, Model: 15, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing sr_program_2008_10_30_14_42_58.aac.
MPEG-PES file format detected.
MPEG: FATAL: EOF while searching for sequence header.
Video: Cannot read properties.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 1 ch, s16le, 352.0 kbit/45.83% (ratio: 44000->96000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] 48000Hz 1ch s16le (2 bytes per sample)
Video: no video
Starting playback...
Cannot sync MAD frame 496.7 (08:16.7) 207.4% 
Cannot sync MAD frame
Cannot sync MAD frame
Cannot sync MAD frame 496.7 (08:16.7) 201.3% 
A:  94.9 (01:34.9) of 496.7 (08:16.7) 201.3% 

Exiting... (End of file)

```

The stream itself is fine and plays every time, so it's definitely something with streamripper. Tell me it's more operator error!!! :-)

---

### Post by tomjennings on 2008-10-30
Oh bad, replying to my own posts :-)

Possible insight into the problem: with -a -A all audio goes into one file (as my intent). However in testing I resorted to default behavior of the directory and multiple split-up tracks. The first track was corrupt, the second was fine.

So it may be that streamripper doesn't wait for the start of a frame or block or whatever, it just saves bytes from the stream, and so the file begins in the middle of a frame or block and the file cannot be parsed.

All I'm trying to do is timeshift a stream, so that I can play it on my portable MP3 player. One long stream is for me much better in this instance than a directory of song tracks.

---

### Post by tagra123 on 2008-10-30
You can use the http url of some streams using mplayer if you cannot get it to connect use wget and look at the contents of the downloaded file, There is usually a usable url in the file

Then use mplayer

```
 mplayer  mms://a205.v50200.c5020.g.vm.akamaistream.net/7/205/5020/v0001/rushlimb.download.akamai.com/5020/New/obamahalloween.wma  -dumpstream -dumpfile obamahalloween.wma
```


You can then transcode it to mp3 using mplayer and lame

---

### Post by andrew.46 on 2008-10-30
Hi Tom:

> **tomjennings said:**
> 

```

tomj@zx:~$ mplayer -playlist http://streamer.psyradio.org:8130 -vc null -vo null \
-ao pcm:fast:waveheader:file=psyradio.wav
```

Odd. However the stream plays with the svn MPlayer as follows:

```
andrew@skamandros:~$ mplayer http://streamer.psyradio.org:8130
MPlayer dev-SVN-r27848-4.3.2 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz (Family: 6, Model: 15, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

Playing http://streamer.psyradio.org:8130.
Resolving streamer.psyradio.org for AF_INET6...
Couldn't resolve name for AF_INET6: streamer.psyradio.org
Resolving streamer.psyradio.org for AF_INET...
Connecting to server streamer.psyradio.org[81.88.36.42]: 8130...
Name   : p s y r a d i o * f m - psychannel
Genre  : Goa Psytrance Fullon Darkpsy
Website: http://psyradio.fm
Public : yes
Bitrate: 48kbit/s
Cache size set to 320 KBytes
Cache fill:  0.00% (0 bytes)   
ICY Info: StreamTitle='Sesto Sento - From Led To Gold';StreamUrl='http://psyradio.fm/';
Cache fill: 17.50% (57344 bytes)   
AAC file format detected.
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio) decoder)
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  40.4 (40.4) of 0.0 (unknown)  2.2% 46% 

```

and records well as follows (without the -playlist option):

```
$ mplayer -cache 1024 http://streamer.psyradio.org:8130 -vc null -vo null \
-ao pcm:fast:waveheader:file=psyradio.wav
```

This works well with the current svn, which is a much more powerful beast that the repository offering. Guide is [here]("http://ubuntuforums.org/showthread.php?t=558538").

  Andrew

---

### Post by tomjennings on 2008-10-31
OK! Working!

All I wanted to do was 'time shift' streaming audio onto my Creative Zen V player. I am not trying to rip individual tracks for my music collection (the quality is too low for that anyways). All I wanted was to snarf say 4 hours of streamed music and stuff it into the Zen, where I'd play it, then delete it.

I ended up not doing that.

It seems that streamripper has a bug, but it can be worked around. The bug (or operator error, which, truthfully, I would prefer,it's easier to fix!) is that the first track ripped from the stream is often corrupt. In default operation, this initial partial track is left in incomplete/. However, when using -a -A, eg. create one long stream file, this corrupt track is prepended to the subsequent good track rips, making the whole file corrupt.

The work around is to simply use it's default behaviour (heuristically split the stream into individual named tracks) and treat the result like a ripped CD "album" or disc. It is nice to have the track names I suppose, but I can't read the tiny Zen display in daylight and when driving my car so they're not generally useful.

The general process is:

* Rip the stream (for four hours in my case)
* For every good track rip, convert to mp3

Here's the code. It's a rough, non-error-handling shell script (eg. my notes) but it's a start.

This leaves 4 hours of Psyradio's psytrance channel stored in an "album" ~/Music/Streams/Psyradio-(date). I don't like the ID3 tag data used but that's a later project.

```

#!/bin/bash

MUSIC=/home/tomj/Music
STREAMS=Streams
CHAN=Psyradio-`date +%d%b%y`

mkdir -p $MUSIC/$STREAMS
cd $MUSIC/$STREAMS

# The first/partial track is usually corrupted; it and the final partial track are left in .../incomplete.
# -s -d FOO forces the dest dir name to FOO not the channel name
# -q prefixes with sequence number.
streamripper http://streamer.psyradio.org:8130 -s -d $CHAN -u "VLC media player 0.8.6e" -q -l 14400

# aargh, -a -A corrupts the file with the initial partial
# will -k 1 work? (skip first track)
# (no, doesnt seem to!)
# streamripper http://streamer.psyradio.org:8130 -u "VLC media player 0.8.6e" -q -a -A -s -l 14400

cd $CHAN

for t in *.aac ; do
	fn=${t/.aac/}
	mplayer --quiet -vo null -vc null "$t" -ao pcm:waveheader:file=tmp.wav
	lame --quiet -h --vbr-new tmp.wav "$fn.mp3"
	rm -f "$t" tmp.wav
done

rm -r incomplete
cd ..

```

Thanks Ringi for the lead on streamripper!!

---

### Post by markbuntu on 2008-10-31
You can edit your

~/.config/streamripper/streamripper.ini

You can change the id3 tags to v1 or v2 or get rid of them entirely with the

add_id3v1=0
add_id3v2=0

1 to use them 0 to not. You can also change the

rip_individual_tracks=0

to get one long rip.

I am about to try kstreamripper and will report back....

---

### Post by markbuntu on 2008-10-31
KStreamRipper is definitely the way to do this. No artifacts from incomplete streams. drag and drop urls. Start stop. A tune in button and command line for the application you want to tune in with. I switched that to amarok and it drops the stream into the playlist when you hit tune in. 

The only thing is that it saves the stream in aac from that url but soundKonverter takes care of that with no problem converting to mp3 or wav.

Amarok also has a drop in url function for streams. 

Amarok, KStreamRipper and soundKonverter will definitely solve your problems.

---

