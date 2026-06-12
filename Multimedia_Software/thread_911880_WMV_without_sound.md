---
title: "WMV without sound"
date: 2008-09-06
forum: Multimedia Software
---

### Post by DeMus on 2008-09-06
Hi,

I have downloaded a HD movie in WMV format and am trying to play the file. Picture quality is perfect but I have no sound.
M-Player gives a message 0x162: can't find suitable codec.
VLC plays the file without sound.
Totem does nothing, just a black picture.

How to solve the problem? How to get sound?

DeMus

---

### Post by cagljevic on 2008-09-06
Same here.  This is vlc debug output:

[COLOR="Red"][00000312] main decoder error: no suitable decoder module for fourcc `wmap'.
VLC probably does not support this sound or video format.[/COLOR]

Totem-xine debug output:

[COLOR="Red"][wmv3 @ 0x7fa0e7f17330]Extra data: 8 bits left, value: 0
[/COLOR]

The video will play fine, there is no audio.

ubuntu 8.04 amd64, all ubuntu extras installed...

Lenovo x61, 4GB, 320GB 7200rpm Seagate, ubuntu 8.04 amd64

---

### Post by bvanaerde on 2009-02-17
Same problem here (Ubuntu 8.10 64bit). Not sure if this can be fixed atm...

---

### Post by xinitrc on 2009-02-28
ok...it's a amd64 kernel related issue...spent a few hours downloading a back up copy of Afro Samurai, now I can't hear Samual "mothafu**" Jackson dubling. What's next? Opening a bug thread?

---

### Post by mc4man on 2009-02-28
> What's next? Opening a bug thread
Vlc doesn't support wmap or wmal in either 32 or 64 bit

On a 32 bit install you can w32 or win32 codecs and many other players can playback these files or you can convert to something vlc can handle (wma2 or other format

In 64 bit there is no way to play or convert wmap or wmal unless you install a 32bit version of mplayer and the w/win32 codecs (the w64codecs are pretty much worthless, only have 3 codecs included (vs. 120+ for w32

---

### Post by DeMus on 2009-03-01
> **mc4man said:**
> Vlc doesn't support wmap or wmal in either 32 or 64 bit

On a 32 bit install you can w32 or win32 codecs and many other players can playback these files or you can convert to something vlc can handle (wma2 or other format

In 64 bit there is no way to play or convert wmap or wmal unless you install a 32bit version of mplayer and the w/win32 codecs (the w64codecs are pretty much worthless, only have 3 codecs included (vs. 120+ for w32

So, I am not the only one. Today I downloaded another wmv movie and got the message in the attached picture.
Nice, very nice. Does somebody know if this is been taken care of?

---

### Post by bvanaerde on 2009-03-01
I got exactly the same message here.
No solution found so far...

---

### Post by markus_V on 2009-03-10
omg i just wasted the last 3 hours searching the net trying out different codecs and **** only to find this thread! so it seems it's impossible to watch files with this codec right now is it?

---

### Post by Debuggern on 2009-03-12
To be able to play wmv video files that is using the sound codec 0x162 with mplayer. This has only been tested on x86 Ubuntu version. I can't make any promises if this will work for 64-bit Ubuntu version.
I assume you have mplayer installed and either w32codecs or w64codecs installed depending on your architecture. For more info regarding this, goto [http://www.medibuntu.org/](http://www.medibuntu.org/) and install necessary packages.


First make sure you have rpm installed

```
sudo apt-get install rpm
```

Next get the 2 mplayer-codec rpm packages depending on architecture.

[COLOR="Red"]**[SIZE="4"]For x86 version[/SIZE]**[/COLOR]

```
wget http://www.mplayerhq.hu/MPlayer/releases/codecs/mplayer-codecs-20061022-1.i386.rpm
```

```
wget http://www.mplayerhq.hu/MPlayer/releases/codecs/mplayer-codecs-extra-20061022-1.i386.rpm
```

[COLOR="Black"][SIZE="4"][B]For 64-bit version
[/B][/SIZE][/COLOR]

```
wget http://www.mplayerhq.hu/MPlayer/releases/codecs/mplayer-codecs-20061022-1.x86_64.rpm
```

```
wget http://www.mplayerhq.hu/MPlayer/releases/codecs/mplayer-codecs-extra-20061022-1.x86_64.rpm
```

Finally, install the audio mplayer rpm packages depending on architecture

[COLOR="Red"]**[SIZE="4"]For x86 version[/SIZE]**[/COLOR]

```
sudo rpm -Uvh mplayer-codecs-20061022-1.i386.rpm
```

```
sudo rpm -Uvh mplayer-codecs-extra-20061022-1.i386.rpm
```

[COLOR="Black"][SIZE="4"][B]For 64-bit version
[/B][/SIZE][/COLOR]

```
sudo rpm -Uvh mplayer-codecs-20061022-1.x86_64.rpm
```

```
sudo rpm -Uvh mplayer-codecs-extra-20061022-1.x86_64.rpm
```

Cheers! :)

---

### Post by markus_V on 2009-03-12
yeah i just gave that a try but still didnt work :( im on amd64 and have the w64codecs and mplayer installed as well as pretty much everything else that's been suggested on the net but still no luck :(

---

### Post by Debuggern on 2009-03-12
> **markus_V said:**
> yeah i just gave that a try but still didnt work :( im on amd64 and have the w64codecs and mplayer installed as well as pretty much everything else that's been suggested on the net but still no luck :(



markus_v, it helps if you are a bit specific, were you able to install the rpm packages? A good place to try out wmv video files are from Nasa's multimedia hd video archive.

[http://www.nasa.gov/multimedia/hd/index.html](http://www.nasa.gov/multimedia/hd/index.html)

**Tour the International Space Station** is a wmv that is not using the 0x162 audio codec, should play with sound with the w32/w64-codecs installed. It uses WMV3 video codec and WMA2 audio codec.

**Endeavour Launches on Mission STS-126** and [B]50 Years of Exploration
[/B] requires 0x162 audio codec. The rpm codec packages for mplayer needs to be installed for sound to be able to work.

Both use WMV3 video codec and WMA3  audio codec "0x162".

get mediainfo to check the codecs by your self for the wmv video files that you can't play with sound, that might help, sounds like you are missing another audio codec that is not 0x162 that those wma video files you try to play requires.

[http://www.getdeb.net/app/MediaInfo](http://www.getdeb.net/app/MediaInfo)

---

### Post by markus_V on 2009-03-12
i installed everything u mentioned, the "Tour the International Space Station" works fine but the "Endeavour Launches on Mission STS-126" like before has no sound.

---

### Post by mc4man on 2009-03-12
I think it's pretty simple, on a 64 bit install your not going to playback wmap or wmal audio without installing w/win/32codecs and a 32 bit player. Or if so inclined purchase the appropriate fluendo media pack and use a gstreamer player.

Whether the .rpm  i386 version has anything additional to w/win/32codecs I don't know, but if so it's not involving wmap or wmal.
They playback fine in everything but vlc with the w/win/32codecs

As far as the .rpm vs w/win/64codecs there may be a few extra .so's, but they're all realplayer, real audio codecs. All the 64 bit versions have pretty much nothing other than realplayer codecs

Edit: it's also pretty simple to convert your wmv, wma's to something you can play using a small 32 bit install, virtualbox or with windows media encoder

---

### Post by markus_V on 2009-03-12
how do i install the 32 bit version of mplayer? when i search on synaptic it only shows what i've already installed which i presume is the 64 bit version, so what command can i type in terminal to get the 32 bit version?

---

### Post by mc4man on 2009-03-12
> how do i install the 32 bit version of mplayer
I think that's less than trival, but did just find a possible solution that's very simple.

I just tested it on a 32 bit install but that shouldn't matter.
What you could do is install wine, go in the 'applications menu -> wine ->  'configure wine". Set the windows version to xp and configure the audio (just click on the audio tab, wait and set probably for alsa 

Then you 'install' the windows version of mplayer and put the w32codecs in the same folder as mplayer. (in the case of the script you don't install, just run 

You could probably 'install' the win mplayer like a program (and maybe even smplayer) but what is easier is to run this script (that's what I tested and plays the aforementioned nasa wmv fine, ( though I downloaded it for playback, not thru firefox

Thread and script (post # 40
[http://ubuntuforums.org/showthread.php?t=848535&page=4](http://ubuntuforums.org/showthread.php?t=848535&page=4)


 What i did was create a folder on the desktop, cd to it in a terminal and ran the script commands one by one (already had wine so didn't want to run as a script
Then just opened up folder, right clicked on gmplayer -> open with wine.....


Edit: the portable version of smplayer works well also (no install), just put w32codecs inside in the mplayer folder (replace the existing empty codecs folder

---

### Post by Debuggern on 2009-03-13
markus_V, download the mplayer-codecs-20061022-1.i386.rpm package and try testing the wma,wmv dll files. Read the documentation of mplayer where the codecs are located, usually it is /usr/local/lib/codecs, put the codecs files there and give it a try. The wma*.dll "audio" codecs files are the ones that needs to be tested with your mplayer. The wma9dmod.dll  and wmadmod.dll that is.

To extract the mplayer-codecs-20061022-1.i386.rpm in your current directory

```

rpm2cpio mplayer-codecs-20061022-1.i386.rpm  | cpio -dimv
```

Then just moves files to your codecs folder that should be /usr/local/lib/codecs.

---

### Post by markus_V on 2009-03-16
Debuggern: i just d/l the mplayer-codecs-20061022-1.i386.rpm file and moved all the codecs to /usr/local/lib/codecs but im afraid the same thing happens as in no audio plays and it says "Cannot find codec for audio format 0x162"

---

### Post by kamitsukai on 2009-04-22
Has anyone managed to get this working yet? or is the only way to buy the fluendo codecs? I dont really mind buying them if it means I can watch my wmv videos which have the sound problem =[

and is this problem fixed in jaunty?

---

### Post by mc4man on 2009-04-22
You may patch the source for a 64 bit mplayer and it will play wma3 audio (wmapro)
see here
[http://ubuntuforums.org/showthread.php?p=7105111#post7105111](http://ubuntuforums.org/showthread.php?p=7105111#post7105111)
and here
[http://ubuntuforums.org/showthread.php?t=1081070&page=10](http://ubuntuforums.org/showthread.php?t=1081070&page=10) (post 94

Also the fluendo appear to work well (post 16
[http://ubuntuforums.org/showthread.php?p=7115917#post7115917](http://ubuntuforums.org/showthread.php?p=7115917#post7115917)

Note that the fluendo are just for gstreamer players

---

### Post by kamitsukai on 2009-04-22
> **mc4man said:**
> You may patch the source for a 64 bit mplayer and it will play wma3 audio (wmapro)
see here
[http://ubuntuforums.org/showthread.php?p=7105111#post7105111](http://ubuntuforums.org/showthread.php?p=7105111#post7105111)
and here
[http://ubuntuforums.org/showthread.php?t=1081070&page=10](http://ubuntuforums.org/showthread.php?t=1081070&page=10) (post 94

Also the fluendo appear to work well (post 16
[http://ubuntuforums.org/showthread.php?p=7115917#post7115917](http://ubuntuforums.org/showthread.php?p=7115917#post7115917)

Note that the fluendo are just for gstreamer players

that sounds brilliant but I have a quick question I'm currentley using mint 6 (basically intrepid) how would I build mplayer on this? and when would you do the patch bit?

Don't often build...more of a copy & paste person:lolflag:

---

### Post by mc4man on 2009-04-22
your best bet for building would be to follow Andrews guide (I would think it would be ok for for mint though can't say 100%

[http://ubuntuforums.org/showthread.php?t=1024592](http://ubuntuforums.org/showthread.php?t=1024592)

In that same thread post 94 shows how to patch

You would do the patch between lines 3 and 4 of the mplayer build instr.

I use a different method than Andrew's to build but in the end should be the same.

If you read thru the post I first linked you'll see I did experience some build failures with the patch after at first having none. Would love to have someone else try and see what happens.
(I worked a solution, not sure if 100% 'proper'..,



Worst case I saved most of one of the package sets I made, very vanilla (uses repo livemedia, runtime cpu detection, no vdpau, didn't save the mplayer_doc .deb, I think it was r 29154 (or 29174

---

### Post by kamitsukai on 2009-04-22
> **mc4man said:**
> your best bet for building would be to follow Andrews guide (I would think it would be ok for for mint though can't say 100%

[http://ubuntuforums.org/showthread.php?t=1024592](http://ubuntuforums.org/showthread.php?t=1024592)

In that same thread post 94 shows how to patch

You would do the patch between lines 3 and 4 of the mplayer build instr.

I use a different method than Andrew's to build but in the end should be the same.

If you read thru the post I first linked you'll see I did experience some build failures with the patch after at first having none. Would love to have someone else try and see what happens.
(I worked a solution, not sure if 100% 'proper'..,



Worst case I saved most of one of the package sets I made, very vanilla (uses repo livemedia, runtime cpu detection, no vdpau, didn't save the mplayer_doc .deb, I think it was r 29154 (or 29174

What do I do if I've already built:lolflag: do I just build again and apply the patch? also did you mean apply the patch between lines 3&4 of "Download and Compile the svn mplayer"?

Thanks again!

---

### Post by mc4man on 2009-04-22
Andrew may be better suited than I for his guide but yes rebuild from scratch.
The 3&4 is
> $ cd $HOME
$ svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
$ cd $HOME/mplayer
[COLOR="Red"]do the patch commands[/COLOR] starting with the line "svn checkout svn://svn.ffmpeg.org/soc/wmapro wmapro"
$ ./configure


Can stand corrected if need be, as noted I use a diff. method (Usually build debian packages instead of checkinstall packages


I may be mixing up threads so to clarify

Intrepid build thread

[http://ubuntuforums.org/showthread.php?t=1024592](http://ubuntuforums.org/showthread.php?t=1024592)

Patch post 94
[http://ubuntuforums.org/showthread.php?t=1081070&page=10](http://ubuntuforums.org/showthread.php?t=1081070&page=10)

---

### Post by kamitsukai on 2009-04-22
Unfortunatley I'm getting build errors =[

Pastebin Link...

> [http://pastebin.com/f72cc31d2]("http://pastebin.com/f72cc31d2")

Thanks for helping! and congratulations on your 3,000th post!

---

### Post by mc4man on 2009-04-22
Ok, those are the exact errors I got.  (well to an extent, the obvious initial 'fix' reduced them to three, that's where a 'proper' fix comes to mind. What I've found is a 'hack' in my opinion

What's odd is when I was building some .debs for others it sailed right thru. (still don't get it.

Would be very useful if you posted them in the jaunty mplayer thread, maybe nullack could advise.

If you wish I'll post my work around
 (if so you'll need 1 file from this source, so download, unpack on the desktop and post back. 

[http://www.ffmpeg.org/download.html](http://www.ffmpeg.org/download.html)

scroll all the way to bottom and download **the 0.5 source**
right under this line
FFmpeg 0.5 "half-way to world domination A.K.A. the belligerent blue bike shed"


Edit: If you haven't touched your build folder or entered any futher commands let me know, will save some time.

---

### Post by mc4man on 2009-04-23
Went back to a live intrepid amd_64 cd and as of the latest mplayer and wmapro patch it's very simple.

A few days ago I needed to patch, build, let it fail, insert a file, resume the build. If I inserted the file first the build would still fail but just with a few minor errors that seemed correctable with some source editing. (this may or may not be because I build off of a debian rules versus ./configure, make (The let it fail part

As of tonights sources you just need to insert a file. (if someone knows a better solution I'd love to know.

While your pastebin didn't show the initial error it's probably this (you can increase your scrollback lines by opening a terminal -> edit -> profile preferences, I think there's a max, I set it to 3000

> 
 -I/usr/include/schroedinger-1.0 -I/usr/include/liboil-0.3     -c -o wmaenc.o wmaenc.c
cc -DHAVE_AV_CONFIG_H -I.. -I.. -Wundef -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -std=gnu99 -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -I.  -D_REENTRANT -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT -I/usr/include/kde/artsc -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -D_REENTRANT   -Ilibdvdread4  -I/usr/include/freetype2 -I/usr/include   -I/usr/include/schroedinger-1.0 -I/usr/include/liboil-0.3     -c -o wma3dec.o wma3dec.c
[COLOR="Red"]wma3dec.c:29:23: error: bitstream.h: No such file or directory[/COLOR]
In file included from wma3dec.c:30:
wma3.h:97: error: expected specifier-qualifier-list before 'VLC'
wma3dec.c: In function 'dump_context':
wma3dec.c:49: error: 'WMA3DecodeContext' has no member named 'sample_bit_depth'
wma3dec.c:50: error: 'WMA3DecodeContext' has no member named 'decode_flags'
...............major clipping..................
wma3dec.c:1630: error: 'WMA3DecodeContext' has no member named 'packet_loss'
make[1]: *** [wma3dec.o] Error 1
make[1]: Leaving directory `/home/ubuntu/mplayer/libavcodec'
make: *** [libavcodec/libavcodec.a] Error 2



You need to have a bitstream.h file available and from what I see there is none in the mplayer source, none in /usr/include, nor is one produced during the build.
If you download a svn of ffmpeg there isn't one there either, nor in the rev. mplayer uses. But there is in the 0.5 source I linked above

So unpack the 0.5 source, go into the libavcodec folder and right click -> copy bitstream.h
Then go into your mplayer source folder and paste bitstream.h into the libavcodec folder.

Then either cd to your mplayer source and run make or if you wish run make clean or make distclean.

If you run make clean then just go make, if you run make distclean then go back to  ./configure
ect.

So with this mplayer and this wmapro it's
get source, patch, insert bitstream.h, configure, make and install (I can't remember if I configured before inserting bitstream.h, don't believe it matters

> mplayer....
Checked out revision 29220.
ubuntu@ubuntu:~/mplayer1$ cd mplayer
ubuntu@ubuntu:~/mplayer1/mplayer$ svn checkout svn://svn.ffmpeg.org/soc/wmapro wmapro
..................
Checked out revision 4231.


For consistency I used Andrews guide exactly for intrepid on a live cd

For curiosity I did the build 4 times on fresh sources

lived cd + andrews guide (build failed
As described above (build succeeded
added the repo ffmpeg libraries and devs to see if affected (failed
removed the libraries, built and installed the latest ffmpeg (failed

---

### Post by kamitsukai on 2009-04-23
Brilliant!!!!!!  Thanks ever so much! you've finaly solved my one and only problem with my 64 bit install =]

I've always wonderd why this audio codec dosent come in w64codecs? like it does in w32codecs =[

Thanks again!


:guitar: :lolflag: :guitar: :lolflag: :guitar: :lolflag: :guitar:

---

### Post by mc4man on 2009-04-23
> I've always wonderd why this audio codec dosent come in w64codecs? like it does in w32codecs

It doesn't appear w64codecs will ever amount to much though I'm not up on whether there any work being done there (i gather it's far from trivial to convert the win runtime files to .so's

I'd think the wma3 support will make it's way into the mplayer's libavcodec at some point.

Hopefully there be something for wmal at some point also (wma lossless

(overall I'm impressed with how well the 64 bit live cd ran on my little core2duo laptop, my main box and tester are p4's

---

### Post by kamitsukai on 2009-05-19
I'm having problems now](*,)](*,)](*,)

followed your guide today after i reinstalled but I'm getting this error after building with the bitstream.h file in the libavcodec folder

```
carl@carl-desktop ~/mplayer $ make
make -C libavcodec
make[1]: Entering directory `/home/carl/mplayer/libavcodec'
cc -DHAVE_AV_CONFIG_H -I.. -I.. -Wundef -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -std=gnu99 -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -Ilibdvdread4 -I.  -D_REENTRANT -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT -I/usr/include/kde/artsc -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -D_REENTRANT    -I/usr/include/freetype2 -I/usr/include   -I/usr/include/schroedinger-1.0 -I/usr/include/liboil-0.3     -c -o wma3dec.o wma3dec.c
wma3dec.c: In function 'wma3_decode_init':
wma3dec.c:315: error: too few arguments to function 'ff_mdct_init'
make[1]: *** [wma3dec.o] Error 1
make[1]: Leaving directory `/home/carl/mplayer/libavcodec'
make: *** [libavcodec/libavcodec.a] Error 2


```

---

### Post by mc4man on 2009-05-19
That was a time and place thing, adding bitstream.h was what was needed then.
Every svn of mplayer changes, ffmpeg changes, ect.

Try it with just applying the patch, maybe it will work fine now.

The first time I did it I didn't need to include bitstream.h, shortly afterwards I did.

In the latest mplayer of a few days ago it built fine without adding, today's who knows....?

---

### Post by kamitsukai on 2009-05-19
> **mc4man said:**
> That was a time and place thing, adding bitstream.h was what was needed then.
Every svn of mplayer changes, ffmpeg changes, ect.

Try it with just applying the patch, maybe it will work fine now.

The first time I did it I didn't need to include bitstream.h, shortly afterwards I did.

In the latest mplayer of a few days ago it built fine without adding, today's who knows....?

Ok Thank you:D I'll give that a whirl

---

### Post by kamitsukai on 2009-05-19
Well it's still not building but I'm sure if I keep trying and re-downloading the svn every now and then it will =]

here's a selection of the error if anyone's interested;)

```
cc -DHAVE_AV_CONFIG_H -I.. -I.. -Wundef -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -std=gnu99 -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -Ilibdvdread4 -I.  -D_REENTRANT -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT -I/usr/include/kde/artsc -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -D_REENTRANT    -I/usr/include/freetype2 -I/usr/include   -I/usr/include/schroedinger-1.0 -I/usr/include/liboil-0.3     -c -o wavpack.o wavpack.c
cc -DHAVE_AV_CONFIG_H -I.. -I.. -Wundef -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -std=gnu99 -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -Ilibdvdread4 -I.  -D_REENTRANT -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT -I/usr/include/kde/artsc -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -D_REENTRANT    -I/usr/include/freetype2 -I/usr/include   -I/usr/include/schroedinger-1.0 -I/usr/include/liboil-0.3     -c -o wmadec.o wmadec.c
cc -DHAVE_AV_CONFIG_H -I.. -I.. -Wundef -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -std=gnu99 -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -Ilibdvdread4 -I.  -D_REENTRANT -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT -I/usr/include/kde/artsc -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -D_REENTRANT    -I/usr/include/freetype2 -I/usr/include   -I/usr/include/schroedinger-1.0 -I/usr/include/liboil-0.3     -c -o wma.o wma.c
cc -DHAVE_AV_CONFIG_H -I.. -I.. -Wundef -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -std=gnu99 -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -Ilibdvdread4 -I.  -D_REENTRANT -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT -I/usr/include/kde/artsc -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -D_REENTRANT    -I/usr/include/freetype2 -I/usr/include   -I/usr/include/schroedinger-1.0 -I/usr/include/liboil-0.3     -c -o wmaenc.o wmaenc.c
cc -DHAVE_AV_CONFIG_H -I.. -I.. -Wundef -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -std=gnu99 -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -Ilibdvdread4 -I.  -D_REENTRANT -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT -I/usr/include/kde/artsc -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -D_REENTRANT    -I/usr/include/freetype2 -I/usr/include   -I/usr/include/schroedinger-1.0 -I/usr/include/liboil-0.3     -c -o wma3dec.o wma3dec.c
wma3dec.c: In function 'wma3_decode_init':
wma3dec.c:315: error: too few arguments to function 'ff_mdct_init'
make[1]: *** [wma3dec.o] Error 1
make[1]: Leaving directory `/home/carl/mplayer/libavcodec'
make: *** [libavcodec/libavcodec.a] Error 2

```

---

### Post by mc4man on 2009-05-19
> but I'm sure if I keep trying and re-downloading the svn every now and then it will
Hopefully it will, who knows

The problem is not with todays mplayer svn version, (r29317), but with the ffmpeg version it's using (todays 18875
[COLOR="Blue"]Edit: also a factor is the wmapro version, a working combo is mplayer r29317, ffmpeg revision 18839, wmapro -r 4279  (as of 05/ 20[/COLOR]

Even if you downloaded an earlier rev. of mplayer it wouldn't matter, you'd still get the current ffmpeg svn.

What's interesting is the error's on line 316, read line 314. (and that may have not been the last error, 316 is fairly early.

Atm, if you wished you could successfully patch and build todays mplayer by either fixing wma3dec.c or by replacing the 5 ffmpeg folders in the mplayer source with ones from a recent ffmpeg source that works.


Considering the changes to both mplayer and ffmpeg are insignificant r to r it's hardly worth the time to find the last ffmpeg to work

Took a quess and used the folders from ffmpeg revision 18839 and it works fine. (needs bitstream.h added

> doug@doug-desktop:~/Desktop/mtest4/mplayer$ ./mplayer ~/wpro.wma -ao alsa
MPlayer SVN-r29317-4.3.2 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/doug/wpro.wma.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
Clip info:
 name: 
 author: 
 copyright: 
 comments: 
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
[wmapro @ 0x9fb68a0][18] [0] [3] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [e0] [0] [0] [0] 
[wmapro @ 0x9fb68a0] ed sample bit depth = 16
[wmapro @ 0x9fb68a0] ed decode flags = e0
[wmapro @ 0x9fb68a0] samples per frame = 2048
[wmapro @ 0x9fb68a0] log2 frame size = 18
[wmapro @ 0x9fb68a0] max num subframes = 16
[wmapro @ 0x9fb68a0] len prefix = 1
[wmapro @ 0x9fb68a0] num channels = 2
[wmapro @ 0x9fb68a0] lossless = 0
AUDIO: 48000 Hz, 2 ch, s16le, 287.5 kbit/18.71% (ratio: 35932->192000)
Selected audio codec: [ffwmapro] afm: ffmpeg (FFmpeg WMA Pro audio)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   7.0 (06.9) of 77.0 (01:17.0)  0.5% 
Exiting... (Quit)



---

### Post by mc4man on 2009-05-19
As a note:
As far as checking mplayer svn's tommorrow, the next day ,ect., ect.

Considering that the mplayer build, if it fails, is almost at the end of the build,  a quicker (and somewhat useful in it's own right) method to ck. is to build a patched ffmpeg itself.
If the -r used works, then an mplayer build with the same ffmpeg -r will also work

Inside of your wmapro folder is a script to checkout and patch the latest svn.
Configure as you see fit, build, and if it succeeds, quickly the grap the mplayer svn which should have the same ffmpeg -r (noting it may or may not need a bitstream.h added

> doug@doug-desktop:~/Desktop/fftest$ svn checkout svn://svn.ffmpeg.org/soc/wmapro wmapro
A    wmapro/wma3dec.c
A    wmapro/TODO
A    wmapro/audioframesize.patch
A    wmapro/mplayer.patch
A    wmapro/wma3data.h
A    wmapro/wmapro_ffmpeg.patch
A    wmapro/wma3.h
A    wmapro/checkout.sh
Checked out revision 4279.
doug@doug-desktop:~/Desktop/ftest$ cd wmapro
doug@doug-desktop:~/Desktop/ftest/wmapro$ ./checkout.sh
.........................clipped
Checked out revision 18876. [COLOR="Red"]<- notice it just went up in the last hour[/COLOR]
patching file libavcodec/Makefile
Hunk #1 succeeded at 255 (offset 22 lines).
patching file libavcodec/allcodecs.c
Hunk #1 succeeded at 231 (offset 20 lines).
patching file libavcodec/avcodec.h
Hunk #1 succeeded at 398 (offset 12 lines).
doug@doug-desktop:~/Desktop/ftest/wmapro$ 
doug@doug-desktop:~/Desktop/ftest/wmapro$ cd ffmpeg
doug@doug-desktop:~/Desktop/ftest/wmapro/ffmpeg$ ./configure <whatever>

One of several possible uses for a patched ffmpeg

 > ffmpeg -i wpro.wma -acodec libfaac -aq 320 wpro.m4a
................clipped
Input #0, asf, from 'wpro.wma':
  Duration: 00:01:14.34, start: 1.451000, bitrate: 293 kb/s
    Stream #0.0: Audio: wmapro, 48000 Hz, stereo, s16, 287 kb/s
[wmapro @ 0x9026430][18] [0] [3] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [0] [e0] [0] [0] [0] 
[wmapro @ 0x9026430] ed sample bit depth = 16
[wmapro @ 0x9026430] ed decode flags = e0
[wmapro @ 0x9026430] samples per frame = 2048
[wmapro @ 0x9026430] log2 frame size = 18
[wmapro @ 0x9026430] max num subframes = 16
[wmapro @ 0x9026430] len prefix = 1
[wmapro @ 0x9026430] num channels = 2
[wmapro @ 0x9026430] lossless = 0
Output #0, ipod, to 'wpro.m4a':
    Stream #0.0: Audio: libfaac, 48000 Hz, stereo, s16, 64 kb/s [COLOR="Blue"]< -actually comes out a vbr around  207 Kbps[/COLOR]
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=    1937kB time=75.63 bitrate= [COLOR="Blue"]209.8kbits/s [/COLOR]   
video:0kB audio:1909kB global headers:0kB muxing overhead 1.486046%


---

### Post by kamitsukai on 2009-05-21
Built perfectly today without any problems =] just a quick question but the deb file which it created and put on my desktop "mplayer_3:1.0~svn-r29318-1_amd64.deb" could I potentially use that to install on a different machine without building from source? or even the same machine if I have to reinstall?

Thanks for all your help =]

---

### Post by mc4man on 2009-05-21
> could I potentially use that to install on a different machine without building from source? or even the same machine if I have to reinstall?

potentially yes but.. potentially issues

Honestly I don't use checkinstall very much but my impression is that it's not very well suited for either, (I tend to use make install or build a .deb off of debian rules

If you want to share, building a proper debian package or package set is a better way to go.

For yourself I believe you'd need to install all the run dep.'s first using at a min. the versions in place when you built.

---

### Post by sharaq on 2009-06-11
> **DeMus said:**
> Hi,

I have downloaded a HD movie in WMV format and am trying to play the file. Picture quality is perfect but I have no sound.
M-Player gives a message 0x162: can't find suitable codec.
VLC plays the file without sound.
Totem does nothing, just a black picture.

How to solve the problem? How to get sound?

DeMus

Had the same problem........installing the "_[COLOR=Red]**Fluendo Complete Playback Pack**[/COLOR]_" will do.
But there is a small issue....these formats [wma 9 decoder etc] are not free software...
So you'll have to buy the Fluendo Complete playback pack....
If you dont wanna buy ... there are many other ways to get that pack... but its against the spirit of GNU/Linux ...he he.... 
USE a[COLOR=Red] **TORRENT**[/COLOR] !!!!! [COLOR=Red]**Download the pack**[/COLOR] .....
Have fun guys...

---

### Post by johnstamos12 on 2010-01-13
can somebody please give me a step by step expanation im totally new at this and ive tried to do this forever but i cant get it, you say download it, but to where and extract to this place but then i dont have permission to do that i dont know how to install codecs at all and i tried the medibuntu but it said no such thing as 1sb or something, so if someone could just give me a step by step tutorial on exactl what to do it'd be very helpfu;l

---

### Post by expresspotato on 2010-01-16
Hmmm these patches seem to have already been applied in the latest SVN of ffmpeg, but video with the WMA Pro Audio codec still fail to be decoded.

---

### Post by mc4man on 2010-01-16
Wma3(pro support has been in ffmpeg for sometime and atm is excellent

As far as ubuntu it's not, the latest ffmpeg shared libs as seen in karmic and atm lucid don't support wma3. (for good support they'd need to move up to at least -r 19778

So your best bet is to either build or install from a ppa a  more recent mplayer (though wma3 decoding is available thru w32codecs, ffwmapro does a better job 
For vlc it must be built off  wma3 enabled libs, you'd need to do that yourself (for 1.0.2 source ff -r 19777 or less, 1.0.3/.4 -r 19778 or higher

Depending on the video codec used for mplayer it's sometimes better to force the video decoding to ff also, for ex. ff does a better job at vc1 (at least I think so with the hardware here

Ex.
> doug@doug-laptop:~$ mplayer -vc ffvc1 -fs '/home/doug/Downloads/Elephant'\''s Dream_10-25_440.wmv' 
MPlayer SVN-r30271-4.3.4 (C) 2000-2009 MPlayer Team.
Playing /home/doug/Downloads/Elephant's Dream_10-25_440.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WVC1]  1920x1080  24bpp  1000.000 fps  10155.7 kbps (1239.7 kbyte/s)
Clip info:
 title: Elephant's Dream
 author: Encoded by Ben Waggoner
 copyright: (c) copyright 2006, Blender Foundation / Netherlands Media Art Institute / [www.elephantsdream.org](www.elephantsdream.org)
 comments: Elephant's Dream, encoded to Windows Media VC-1 using the v11 codecs and optimal settings
==========================================================================
Forced video codec: ffvc1
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffvc1] vfm: ffmpeg (FFmpeg WVC1)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 6 ch, floatle, 440.0 kbit/4.77% (ratio: 55000->1152000)
Selected audio codec: [ffwmapro] afm: ffmpeg (WMA Pro audio (FFmpeg))
==========================================================================
AO: [pulse] 48000Hz 6ch floatle (4 bytes per sample)
Starting playback...


---

### Post by Dreamer Fithp Apprentice on 2011-09-12
> **Debuggern said:**
> To be able to play wmv video files that is using the sound codec 0x162 with mplayer. This has only been tested on x86 Ubuntu version. I can't make any promises if this will work for 64-bit Ubuntu version.
I assume you have mplayer installed and either w32codecs or w64codecs installed depending on your architecture. For more info regarding this, goto [http://www.medibuntu.org/](http://www.medibuntu.org/) and install necessary packages.


First make sure you have rpm installed

```
sudo apt-get install rpm
```Next get the 2 mplayer-codec rpm packages depending on architecture.

[COLOR=Red]**[SIZE=4]For x86 version[/SIZE]**[/COLOR]

```
wget http://www.mplayerhq.hu/MPlayer/releases/codecs/mplayer-codecs-20061022-1.i386.rpm
``````
wget http://www.mplayerhq.hu/MPlayer/releases/codecs/mplayer-codecs-extra-20061022-1.i386.rpm
```[COLOR=Black][SIZE=4][B]For 64-bit version
[/B][/SIZE][/COLOR]

```
wget http://www.mplayerhq.hu/MPlayer/releases/codecs/mplayer-codecs-20061022-1.x86_64.rpm
``````
wget http://www.mplayerhq.hu/MPlayer/releases/codecs/mplayer-codecs-extra-20061022-1.x86_64.rpm
```Finally, install the audio mplayer rpm packages depending on architecture

[COLOR=Red]**[SIZE=4]For x86 version[/SIZE]**[/COLOR]

```
sudo rpm -Uvh mplayer-codecs-20061022-1.i386.rpm
``````
sudo rpm -Uvh mplayer-codecs-extra-20061022-1.i386.rpm
```[COLOR=Black][SIZE=4][B]For 64-bit version
[/B][/SIZE][/COLOR]

```
sudo rpm -Uvh mplayer-codecs-20061022-1.x86_64.rpm
``````
sudo rpm -Uvh mplayer-codecs-extra-20061022-1.x86_64.rpm
```Cheers! :)

Worked fine for me on 10.04 32bit. I needed an extra switch " --force-debian" after rpm in the last 2 commands.

Thanks, Debuggern.:D

---

