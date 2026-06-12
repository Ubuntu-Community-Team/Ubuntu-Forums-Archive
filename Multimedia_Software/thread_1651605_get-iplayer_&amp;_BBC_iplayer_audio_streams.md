---
title: "get-iplayer &amp; BBC iplayer audio streams"
date: 2010-12-23
forum: Multimedia Software
---

### Post by heyup on 2010-12-23
I use get-iplayer 2.68 to download radio programmes.

The default setting uses iphone to download mp3 files. Noticed this last week that default iphone no longer available, and it downloads wma files (yuck).

Has BBC made some change to stop mp3 downloads? Anyone else noticed this? Is there a way I can get around this?

---

### Post by ron999 on 2010-12-23
> **heyup said:**
> 

Has BBC made some change to stop mp3 downloads? Anyone else noticed this? Is there a way I can get around this?
Hi
Yes, something has changed approx 2 weeks ago.
I think it's necessary now to have **rtmpdump** installed.

I use commands like this now:-

For mp3
```
get_iplayer --get --type=radio --mode=flashaudio --pid=b00wnrv9

```

If such a command doesn't work for you then check if you have got **rtmpdump** installed by using command:-
```
rtmpdump -h
```
If you need to compile and install rtmpdump there are instructions here (post #7 is probably best):-
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1537278&highlight=Andrew.46]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1537278&highlight=Andrew.46")

Also get_iplayer is now at v2.78, maybe you'll need to upgrade.

---

### Post by heyup on 2010-12-24
Thanks for that information.

I thought I had installed rtmpdump sometime ago, but the check code you gave said command not found. I guess I must have done something wrong when I tried to complile and install it. It was so long ago I cannot even remember what I did.

I'll have a look at the instructions in the link and see what happens when I manage to get rtmpdump properly installed.

How do you find the programme pid? I usually use the programme index number in a simple script I made.

---

### Post by ron999 on 2010-12-24
> **heyup said:**
> 
How do you find the programme pid? 
It's part of the URL.
Like this:-
> ]http://www.bbc.co.uk/iplayer/episode/b00wnrv9/Bells_on_Sunday_19_12_2010/

---

### Post by heyup on 2010-12-24
Discovered I had rtmpdump 1.3 installed, but bash didn't recognise it.

Then got:

> WARNING: ffmpeg does not exist - not converting flv file

WARNING: rtmpdump >= 1.5 or flvstreamer is required - please upgrade


Installed ffmpeg & rtmpdump 2.3 

Now I get this warning when I tried to download a radio programme using get-iplayer:

> RTMPDump v2.3
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
INFO: Connected...
ERROR: rtmp server sent error
ERROR: rtmp server requested close
INFO: Command exit code 1 (raw code = 256)
 

Not sure what this problem is, or how to fix.

NB. I installed rtmpdump by following this post [http://art.ubuntuforums.org/showpost.php?p=9626752&postcount=6](http://art.ubuntuforums.org/showpost.php?p=9626752&postcount=6)

---

### Post by ron999 on 2010-12-24
> **heyup said:**
> 

Now I get this warning when I tried to download a radio programme using get-iplayer:
Show the command that you used.

---

### Post by heyup on 2010-12-25
The command I use is in a script. This is the command where $indexnum is the index number of the radio programme. 

```
get_iplayer --type=radio --get $indexnum --amode=flashaudio --rtmpdump='/usr/local/src/rtmpdump-2.3/rtmpdump' --output /home/richard/BBC_Radio
``` 

For example, I insert index number 11877 to get Old Harry's Game, like so: 

```
get_iplayer --type=radio --get 11877 --amode=flashaudio --rtmpdump='/usr/local/src/rtmpdump-2.3/rtmpdump' --output /home/richard/BBC_Radio
```

---

### Post by ron999 on 2010-12-25
OK
It's not necessary to use "**--rtmpdump='/usr/local/src/rtmpdump-2.3/rtmpdump'**".
Maybe rtmpdump is installed somewhere different now.
The get_iplayer program should find rtmpdump automatically.

Try the rest of your command without it, like this:-
```
get_iplayer --type=radio --get 11877 --amode=flashaudio --output /home/richard/BBC_Radio

```
That format works OK for me.

---

### Post by heyup on 2010-12-25
That command produced this warning:

> INFO: Trying flashaudio1 mode to record radio: Old Peter's Russian Tales: Series 1 - 1. Sadko 
WARNING: Required program flvstreamer/rtmpdump does not exist (see [http://linuxcentre.net/getiplayer/installation](http://linuxcentre.net/getiplayer/installation) and [http://linuxcentre.net/getiplayer/download](http://linuxcentre.net/getiplayer/download)) 
INFO: skipping flashaudio1 mode 
ERROR: Failed to record 'Old Peter's Russian Tales: Series 1 - 1. Sadko (b008hz9n)'


After much head scratching I updated to get-iplayer 2.78. Problem sorted. :D 

I can now enjoy get-iplayer again. Thank you for your help.

---

### Post by heyup on 2011-03-16
Now I'm having problems downloading to flashaudio. 

> The Men from the Ministry - A Sticky Business, BBC 7, Comedy,Radio,Sitcoms 

INFO: 1 Matching Programmes 
INFO: Checking existence of default version 
INFO: No specified modes (flashaudio) available for this programme with version 'default' (try using --modes=flashaaclow,flashaacstd,rtspaaclow,rtspaacstd,wma) 
ERROR: Failed to record 'The Men from the Ministry - A Sticky Business (b00z66dq)'[


I'm using v2.79. Trying to download to MP3. I can download to MP4, but I don't want MP4. 

Anyone able to solve this?

---

### Post by ron999 on 2011-03-16
> **heyup said:**
> . Trying to download to MP3. I can download to MP4, but I don't want MP4. 

Anyone able to solve this?

No :D

Hi
The BBC mp3 streams are being phased out.
So download the aac files and convert to mp3 with FFmpeg/WinFF etc.

Some guys on the get_iplayer mailing lists have developed patched versions that either:-

re-mux the aac into m4a for iTunes
or 
transcode the aac into mp3 automatically.

Here:- [http://lists.infradead.org/pipermail/get_iplayer/2011-March/date.html]("http://lists.infradead.org/pipermail/get_iplayer/2011-March/date.html")

---

### Post by heyup on 2011-03-17
Thanks for that info and the link. 

When I try to download to acc I get a corrupted mp4a file. I'm using mode --flashaccstd1 . Seems to be a problem with an unsupported audio codec. 

> Download complete 
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al. 
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr 
  libavutil version: 1d.49.3.0 
  libavcodec version: 1d.51.38.0 
  libavformat version: 1d.51.10.0 
  built on May  1 2010 18:17:41, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu4) 
[flv @ 0xb7791110]Unsupported audio codec (a) 
Input #0, flv, from '/home/richard/BBC_Radio/The_Men_from_the_Ministry_-_A_Sticky_Business_b00z66dq_default.partial.aac.flv': 
  Duration: 00:36:00.0, start: 0.000000, bitrate: N/A 
  Stream #0.0: Audio: 0x000a, 44100 Hz, stereo 
Output #0, adts, to '/home/richard/BBC_Radio/The_Men_from_the_Ministry_-_A_Sticky_Business_b00z66dq_default.partial.aac': 
  Stream #0.0: Audio: 0x000a, 44100 Hz, stereo 
Stream mapping: 
  Stream #0.0 -> #0.0 
Press [q] to stop encoding 
size=   33842kB time=2160.0 bitrate= 128.3kbits/s    
video:0kB audio:33842kB global headers:0kB muxing overhead 0.000000% 
INFO: Recorded /home/richard/BBC_Radio/The_Men_from_the_Ministry_-_A_Sticky_Business_b00z66dq_default.aac 

INFO: id3 tagging aac file 


I'm using 8.04 Hardy. FFmpeg installed from Medibuntu. Section C in post 1 of this HowTo:
[http://ubuntuforums.org/showthread.php?p=7020421#post7020421]("http://ubuntuforums.org/showthread.php?p=7020421#post7020421")

---

### Post by heyup on 2011-03-18
> **heyup said:**
> 
When I try to download to acc I get a corrupted mp4a file.

The problem was with FFmpeg. Installed complied FFmpeg using this guide (Hardy Heron 8.04):

[http://ubuntuforums.org/showpost.php?p=4907079&postcount=1]("http://ubuntuforums.org/showpost.php?p=4907079&postcount=1")

[http://ubuntuforums.org/showpost.php?p=6963607&postcount=360]("http://ubuntuforums.org/showpost.php?p=6963607&postcount=360")

That solved the problem. May help others.

---

### Post by shantiq on 2011-03-18
> **heyup said:**
> Now I'm having problems downloading to flashaudio. 



I'm using v2.79. Trying to download to MP3. I can download to MP4, but I don't want MP4. 

Anyone able to solve this?

go to terminal


simply change directory to where your mp4(s) ends up 

then write (for one or more files)


```
for f in *.mp4; do ffmpeg -i "$f" -ab 320k "${f%.mp4}.mp3"; done

```

or for just one file  


```
 ffmpeg -i nameoffile.mp4 -ab 320k nameoffile.mp3

```

**Of course** change 320 to what you want it to be

---

### Post by heyup on 2011-03-19
> **heyup said:**
> Now I'm having problems downloading to flashaudio.

I'm using v2.79. Trying to download to MP3. I can download to MP4, but I don't want MP4. 

Anyone able to solve this?

What I wrote was not quite accurate. My mistake/confusion. 

get_iplayer downloads mp4a audio codec to a file with acc extension. So it is a aac file, not a mp4 file.

---

### Post by shantiq on 2011-03-19
> **heyup said:**
> What I wrote was not quite accurate. My mistake/confusion. 

get_iplayer downloads mp4a audio codec to a file with acc extension. So it is a aac file, not a mp4 file.


```
 ffmpeg -i nameoffile.aac -ab 320k nameoffile.mp3

```
works too makes no difference

---

### Post by heyup on 2011-03-20
Version of get_iplayer with an option to automatically transcode aac audio to mp3:-

[http://lists.infradead.org/pipermail/get_iplayer/2011-March/001018.html](http://lists.infradead.org/pipermail/get_iplayer/2011-March/001018.html)

[https://github.com/dinkypumpkin/get_iplayer/blob/aactomp3/get_iplayer](https://github.com/dinkypumpkin/get_iplayer/blob/aactomp3/get_iplayer)

---

