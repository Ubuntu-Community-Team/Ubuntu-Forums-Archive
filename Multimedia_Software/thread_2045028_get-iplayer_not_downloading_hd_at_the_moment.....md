---
title: "get-iplayer not downloading hd at the moment....?"
date: 2012-08-20
forum: Multimedia Software
---

### Post by shantiq on 2012-08-20
on this version on 12.04


[ATTACH]222936[/ATTACH]


and finding in the last 10 days none of the hd programs are downloading


i get this


> get_iplayer   --vmode=flashhd  --get 280
get_iplayer v2.80, Copyright (C) 2008-2010 Phil Lewis
  This program comes with ABSOLUTELY NO WARRANTY; for details use --warranty.
  This is free software, and you are welcome to redistribute it under certain
  conditions; use --conditions for details.

Matches:
280:	Exploring China - A Culinary Adventure: Episode 3, BBC Two, Audio Described,Factual,Food & Drink,HD,Highlights,History,Lifestyle & Leisure,Popular,TV, default,audiodescribed,

INFO: 1 Matching Programmes
INFO: Checking existence of default version
**INFO: No specified modes (flashhd) available for this programme with version 'default' (try using --**modes=flashhigh,flashlow,flashstd,flashvhigh,rtsphigh,rtsplow,rtspstd,rtspvhigh,subtitles)
ERROR: Failed to record 'Exploring China - A Culinary Adventure: Episode 3 (b01m7tcp)'




maybe a recent update has upset something  [ those files are in hd and play in hd on the site but once i get to get-iplayer this happens]



any ideas how to correct and return to healthy hd downloads??

---

### Post by ron999 on 2012-08-20
> **shantiq said:**
> 
any ideas how to correct and return to healthy hd downloads??
Upgrade :P
(There's a Jon Davies PPA)
> ron@ubuntu:~$ get_iplayer --get --mode=flashhd --pid=b01m7tcp
get_iplayer [COLOR="Red"]v2.82[/COLOR], Copyright (C) 2008-2010 Phil Lewis
  This program comes with ABSOLUTELY NO WARRANTY; for details use --warranty.
  This is free software, and you are welcome to redistribute it under certain
  conditions; use --conditions for details.

INFO: Episode-only pid detected
INFO: Trying pid: b01m7tcp using type: tv
INFO Trying to stream pid using type tv
INFO: pid not found in tv cache
INFO: Checking existence of default version
INFO: flashhd1,flashhd2 modes will be tried for version default
INFO: Trying flashhd1 mode to record tv: Exploring China - A Culinary Adventure: Episode 3
INFO: File name prefix = Exploring_China_-_A_Culinary_Adventure_Episode_3_b01m7tcp_default                 
RTMPDump v2.4 e0056c5
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
INFO: Connected...
Starting download at: 0.000 kB
INFO: Metadata:
INFO:   duration              3542.10
INFO:   moovPosition          32.00
INFO:   width                 1280.00
INFO:   height                720.00
INFO:   videocodecid          avc1
INFO:   audiocodecid          mp4a
INFO:   avcprofile            100.00
INFO:   avclevel              41.00
INFO:   aacaot                2.00
INFO:   videoframerate        25.00
INFO:   audiosamplerate       24000.00
INFO:   audiochannels         2.00
INFO: trackinfo:
INFO:   length                88550000.00
INFO:   timescale             25000.00
INFO:   language              eng
INFO: sampledescription:
INFO:   sampletype            avc1
INFO:   length                85010432.00
INFO:   timescale             24000.00
INFO:   language              eng
INFO: sampledescription:
INFO:   sampletype            mp4a
15839.561 kB / 42.64 sec (1.2%)

---

### Post by ajgreeny on 2012-08-20
Here is my output from the Exploring China program that you were after, which shows that it is OK with the 2.82 version of GIP, which in my case came from [get-iplayer]("http://git.infradead.org/get_iplayer.git") and is working well in HD, shown in [COLOR=Red]red[/COLOR].  I simply replaced the get_iplayer perl script in /usr/bin that came from the repos with this new one from the archive I downloaded.

Ignore the error at the end; it is because I stopped the download with Ctrl+C
```
  get_iplayer --vmode=flashhd --get 279
[COLOR=Red]get_iplayer v2.82[/COLOR], Copyright (C) 2008-2010 Phil Lewis
  This program comes with ABSOLUTELY NO WARRANTY; for details use --warranty.
  This is free software, and you are welcome to redistribute it under certain
  conditions; use --conditions for details.

Matches:
279:    Exploring China - A Culinary Adventure: Episode 3, BBC Two, Audio Described,Factual,Food & Drink,HD,Highlights,History,Lifestyle & Leisure,Popular,TV, default,audiodescribed,

INFO: 1 Matching Programmes
INFO: Checking existence of default version
INFO: flashhd1,flashhd2 modes will be tried for version default
[COLOR=Red]INFO: Trying flashhd1 mode to record tv: Exploring China - A Culinary Adventure: Episode 3[/COLOR]
INFO: File name prefix = Exploring_China_-_A_Culinary_Adventure_Episode_3_b01m7tcp_default                 
WARNING: Your version of flvstreamer/rtmpdump does not support SWF Verification
FLVStreamer v2.1c1
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
ERROR: HandleCtrl: Ignoring SWFVerification request, no CRYPTO support!
Starting download at: 0.000 kB
Metadata:
  duration              3542.10
  moovPosition          32.00
  [COLOR=Red]width                 1280.00
  height                720.00[/COLOR]
  videocodecid          avc1
  audiocodecid          mp4a
  avcprofile            100.00
  avclevel              41.00
  aacaot                2.00
  videoframerate        25.00
  audiosamplerate       24000.00
  audiochannels         2.00
trackinfo:
  length                88550000.00
  timescale             25000.00
  language              eng
sampledescription:
  sampletype            avc1
  length                85010432.00
  timescale             24000.00
  language              eng
sampledescription:
  sampletype            mp4a
7325.996 kB / 20.92 sec (0.5%)^C
INFO: Cleaning up (signal = INT), killing PID=8964:.
Caught signal: 2, cleaning up, just a second...
ERROR: RTMP_ReadPacket, failed to read RTMP packet body. len: 68748
Download may be incomplete (downloaded about 0.50%), try resuming
..

```

---

### Post by shantiq on 2012-08-20
thanx Ron...



this might help others in the same bateau   


```
sudo ppa-purge ppa:jon-hedgerows/get-iplayer

```

ENTER

```
sudo apt-get update
```

```
sudo apt-get install get-iplayer
```





IF YOUR HD download REFUSES TO start updating to the latest available version of get-iplayer is likely the key...

---

### Post by ericalism on 2012-09-03
> **shantiq said:**
> thanx Ron...



this might help others in the same bateau   


```
sudo ppa-purge ppa:jon-hedgerows/get-iplayer

```ENTER

```
sudo apt-get update
``````
sudo apt-get install get-iplayer
```

IF YOUR HD download REFUSES TO start updating to the latest available version of get-iplayer is likely the key...

Hello,
could you show me how to do this in Debian?

---

### Post by shantiq on 2012-09-03
[FONT="Century Gothic"]  well eric


could not find a deb so made one with "alien" from rpm and zipped and attached here. so unzip then install... hope it works for you...[/FONT]

---

### Post by ericalism on 2012-09-03
> **shantiq said:**
> [FONT=Century Gothic]  well eric


could not find a deb so made one with "alien" from rpm and zipped and attached here. so unzip then install... hope it works for you...[/FONT]

Oh,thank you for your help!:p

---

