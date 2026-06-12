---
title: "dvd::rip problems"
date: 2007-01-29
forum: Multimedia &amp; Video
---

### Post by tommoyer324 on 2007-01-29
I have installed dvd::rip, and am trying to make a backup of some DVDs I have lying around, but when it tries to grab the preview image, it hangs.  I have seen posts that say this is a libmpeg2 issue, and others that say this is a transcode issue, but I have both installed from Synaptic, and should be working correctly.  When I run the Grab Preview command listed in dvd::rip on the command line, it hangs somewhere around libmpeg2 doing some processing.  Any idea why this is causing me problems?

---

### Post by deadgobby on 2007-01-29
I am thinking you do not have the dvd codecs installed. Do you have the DVD codecs installed?
If not here is a couple of links
[https://help.ubuntu.com/community/RestrictedFormats?highlight=%28Restrict%29](https://help.ubuntu.com/community/RestrictedFormats?highlight=%28Restrict%29)
 For automatix
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)
Easyubie
[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

GObby

---

### Post by tommoyer324 on 2007-01-29
I am able to watch the dvd's in question in totem/mplayer/gxine etc.  So I don't think my issue stems from that.

---

### Post by deadgobby on 2007-01-30
[https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs](https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs)

Gobby

---

### Post by tictacman on 2007-01-30
I was trying to do the same thing with k9copy.  The application seems to sit there doing nothing.  Wonder if it has anything to do with the arccos anti-copy on discs?  I came across a thread last night by a developer of dvd2hdd in which he said there wasn't anything on linux at the moment that could deal with this.  They seem to be running dvd decryptor and something else using the wine emulator, though from the postings it seems a bit hit and miss.  

[http://forum.doom9.org/showthread.php?t=115787&page=3](http://forum.doom9.org/showthread.php?t=115787&page=3) - about half way down the page

I just found some information on ripitforme [http://forum.doom9.org/showthread.php?t=118916](http://forum.doom9.org/showthread.php?t=118916) - it might be of use to you.

---

### Post by tommoyer324 on 2007-01-30
I see that dvd::rip might not be able to handle some newer DVDs which I am okay with, but what I am trying to do fails no matter what DVD I try.  I have some from maybe 5 years ago that play fine, as well as some released two weeks ago or so, and none of them rip correctly with dvd::rip which indicates that it isn't a copy protection problem, it is something missing/broken in dvd::rip and its dependencies.

---

### Post by tictacman on 2007-01-30
I thought it might help if I downloaded dvdrip on my new kubuntu install and tried to recreate the problem.  This is what I did:


Installed dvdrip1:0.98.1-0.1ubuntu1 from Adept Manager. Once installed the preference dialogue box said something like this:


Default DVD device: /dev/hda exists : Ok
Default data base directory: /home/ubuntu/dvdrip-data not found Not ok
Default directory for .rip project files: /home/ubuntu/dvdrip-data not found Not ok
Preferred language: not tested : Ok
-----------------------------------------------------------

So I created dvdrip-data folder  clicked on check settings

DVD player command: /usr/bin/mplayer executable : Ok
File player command: /usr/bin/mplayer executable : Ok
STDIN player command: xine not found : NOT Ok
rar command (for vobsub compression): rar-2.80 not found : NOT Ok

installed libxine1, xine-ui and rar packages

found this command was necessary ([www.ubuntuguide.org](www.ubuntuguide.org))

sudo ln -fs /usr/bin/rar /usr/bin/rar-2.80

Program loaded up noticed that most of the menus were greyed out. Gave project a name
and folder location. Greyed out menus replaced by full menus.

In the debug menu clicked on check dependencies - noted that rar was still in red - version 3.51 installed when maximum was 2.99

Here's a list of dependent packages and version numbers I've got installed:

dvd:riop 0.98.1
transcode 1.0.2 emaximum should be 1.0.99
imagemagick 6.2.4
lsdvd 0.16
rar 3.51 the maximum here should be 2.99
mjpegtools 1.8.0
xine 0.99.4
fping 2.4
hal 2.4

Tried ripping an old disc. Quickly ripped, had a go at grabbing frames by putting in different frame numbers - works fine. 

What was the terminal command that you used to grab preview? I could try that to see what happens.

---

### Post by tommoyer324 on 2007-01-30
I will try what they say on ubuntuguide.com, but I don't think it can be my dvd drive, because before I was able to do this, then I needed to reinstall because of a HD crash and now it doesn't work.

---

### Post by tommoyer324 on 2007-01-30
So I tried to install the other packages listed at ubuntuguide.com for dvd::rip, but it still hangs at the same point.  Another reason I don't think it is the DVD drive is 1: I am able to watch DVD's and 2: The grab preview stage occurs after the DVD is ripped, so it doesn't have anything to do with the DVD drive.  The command in question is

transcode  -H 10 --print_status 25 -o snapshot -y ppm,null -x vob,null -i /home/tom/.dvdrip/data/Volcano/vob/001/ -S 8 -c 4-5 -L 1605486

where it hangs after this output

transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
[transcode] (probe) suggested AV correction -D 0 (0 ms) | AV -23 ms | -23 ms
[transcode] auto-probing source /home/tom/.dvdrip/data/Volcano/vob/001/ (ok)
[transcode] V: import format    | MPEG-2  (V=vob|A=null)
[transcode] V: AV demux/sync    | (2) initial MPEG sequence / enforce frame rate
[transcode] V: import frame     | 720x480  1.50:1  encoded @ 4:3
[transcode] V: bits/pixel       | 0.217
[transcode] V: decoding fps,frc | 23.976,1
[transcode] V: Y'CbCr           | YV12/I420
[transcode] A: import format    | 0x2000  AC3          [48000,16,2]  192 kbps
[transcode] A: export           | disabled
[transcode] V: encoding fps,frc | 23.976,1
[transcode] A: bytes per frame  | 8008 (8008.000000)
[transcode] A: adjustment       | 0@1000
[transcode] A: AV shift         | -23 ms [ 0 (A) | -23 ms ]
[transcode] V: IA32/AMD64 accel | sse2 (sse2 sse mmxext mmx asm C)
tc_memcpy: using sse for memcpy
[transcode] V: video buffer     | 10 @ 720x480
[import_null.so] v0.2.0 (2002-01-19) (video) null | (audio) null
[import_vob.so] v0.6.0 (2003-10-02) (video) MPEG-2 | (audio) MPEG/AC3/PCM | (subtitle)
[export_null.so] v0.1.2 (2001-08-17) (video) null | (audio) null
[export_ppm.so] v0.1.1 (2002-02-14) (video) PPM/PGM | (audio) MPEG/AC3/PCM
[import_vob.so] tccat -i "/home/tom/.dvdrip/data/Volcano/vob/001/" -t vob -d 0 -S 1605486 | tcdemux -s 0x80 -x mpeg2 -S 8 -M 2 -f 23.976024 -P /tmp/filevXPFOU   -d 0 | tcextract -t vob -a 0 -x mpeg2 -d 0 | tcdecode -x mpeg2 -d 0 -y yv12
tc_memcpy: using sse for memcpy
[decode_mpeg2.c] libmpeg2 0.4.0b loop decoder
[decode_mpeg2.c] libmpeg2 acceleration: mmxext

where it hangs indefintely

---

### Post by tictacman on 2007-01-30
BTW i didn't follow the [www.ubuntuguide](www.ubuntuguide) info apart from the command to get rar working with dvdrip, i just thought i'd reference it.  Everything I did when installing dvdrip is written out for you.  I tried the command you gave only altering the path:

transcode -H 10 --print_status 25 -o snapshot -y ppm,nu
ll -x vob,null -i /home/tictacman/dvdrip-data/unnamed/vob/001 -S 8 -c 4-5 -L 1605486

This is what was returned:

transcode v1.0.2 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
[transcode] (probe) suggested AV correction -D 2 (80 ms) | AV 80 ms | 0 ms
[transcode] auto-probing source /home/ubuntu/dvdrip-data/unnamed/vob/001 (ok)
[transcode] V: import format    | MPEG-2  (V=vob|A=null)
[transcode] V: AV demux/sync    | (1) sync AV at initial MPEG sequence
[transcode] V: import frame     | 720x576  1.25:1  encoded @ 4:3
[transcode] V: bits/pixel       | 0.174
[transcode] V: decoding fps,frc | 25.000,3
[transcode] V: Y'CbCr           | YV12/I420
[transcode] A: import format    | 0x2000  AC3          [48000,16,2]  192 kbps
[transcode] A: export           | disabled
[transcode] V: encoding fps,frc | 25.000,3
[transcode] A: bytes per frame  | 7680 (7680.000000)
[transcode] A: adjustment       | 0@1000
[transcode] V: IA32/AMD64 accel | sse3 (sse3 sse2 sse 3dnowext 3dnow mmxext mmx                                                                                                   asm C)
tc_memcpy: using sse for memcpy
[transcode] V: video buffer     | 10 @ 720x576
[import_null.so] v0.2.0 (2002-01-19) (video) null | (audio) null
[import_vob.so] v0.6.0 (2003-10-02) (video) MPEG-2 | (audio) MPEG/AC3/PCM | (sub                                                                                                  title)
[export_null.so] v0.1.2 (2001-08-17) (video) null | (audio) null
[export_ppm.so] v0.1.1 (2002-02-14) (video) PPM/PGM | (audio) MPEG/AC3/PCM
[import_vob.so] tccat -i "/home/ubuntu/dvdrip-data/unnamed/vob/001" -t vob -d 0                                                                                                   -S 1605486 | tcdemux -s 0x80 -x mpeg2 -S 8 -M 1 -d 0 | tcextract -t vob -a 0 -x                                                                                                   mpeg2 -d 0 | tcdecode -x mpeg2 -d 0 -y yv12
tc_memcpy: using sse for memcpy
[decode_mpeg2.c] libmpeg2 0.4.0b loop decoder
[decode_mpeg2.c] libmpeg2 acceleration: 3dnow

clean up | frame threads | unload modules | cancel signal | internal threads | d                                                                                                  one
[transcode] encoded 0 frames (0 dropped, 0 cloned), clip length   0.00 s

Apart from the version numbers of the package numbers, I can't think what could be different.  Could it be I have different version of transcode? 

For me dpkg -s transcode | grep Version = 2:1.0.2-0.8ubuntu2

Is the post any use to you? 

"Lately I've come accross a couple DVDs where dvdrip was unable to grab the 
preview. I figured that for some reason searching via transcodes -L doesn't 
work properly. Transcodes reads the whole movie, but doesn't produce anything 
useful.
I solved the problem by not using -L and increasing the Framenumber via the -c 
option. Of course, doing this is a bit slower since the file has to be 
decoded up to that image, but at least it works reliable."

[http://www.exit1.org/archive/dvdrip-users/2005-03/msg00041.html](http://www.exit1.org/archive/dvdrip-users/2005-03/msg00041.html)

Hope you manage to get it working

---

### Post by tommoyer324 on 2007-01-30
I have the same version of transcode as you, I think I am going to try reinstalling everything, and tyring to follow where something might have gone wrong.  Everything looks almost identical.  How long did the command on the command line take to run?

---

### Post by tictacman on 2007-01-31
It was virtually instantaneous.

The only difference between the output of yours and mine is the line:

Yours


 [decode_mpeg2.c] libmpeg2 acceleration: mmxext


Mine


 [decode_mpeg2.c] libmpeg2 acceleration: 3dnow
 
I'm thinking that mmxext could be at the root of the problem.  Wonder why it opted to use 3dnow in my case?  What version of ubuntu are you running?  Is it i386 or 64bit version? I've got the i386 version here.  Have you googled for mmxext and transcode together?  There seems to be quite alot of posts and I'm not sure which might be relevent to you.

Also did you try the command without the -L switch like it said in my last post?

---

### Post by tommoyer324 on 2007-01-31
I really don't see a point in doing so, as this is the command used by dvd::rip so even if the command without -L works, it will still fail when I run dvd::rip.  I will look through the google results for transcode and mmxext and see what comes up.

---

### Post by pgilmon on 2007-02-17
Have you tried just transcoding the video with VLC video player? By doing that, you will obtain a video in any format VLC is capable to produce, then you can make a DVD out of that video file by following instructions in [this thread]("http://www.ubuntuforums.org/showthread.php?t=320788").

---

### Post by HearWa on 2007-06-28
For those of you with the "rar-2.80 not found" problem with dvdrip, I just figured it out. I almost went ahead and installed that exact application version, but you don't have to.

In the edit -> preferences menu in the commands tab you'll see an input field named "rar command (for vobsub compression)." You'll notice that it's looking for 'rar-2.80' in your path, while most of us have plain vanilla 'rar' installed. Just change the text field to 'rar' and it'll work.

It's a simple fix, and easy to overlook.

---

### Post by MeathooK427 on 2007-08-22
As far as the hanging problem grabbing the preview image...compile the newest version of dvd::rip from their website 0.98.8. It fixes that problem beautifully. Now I just need to work on the audio/video sync. Nice program though :)

---

