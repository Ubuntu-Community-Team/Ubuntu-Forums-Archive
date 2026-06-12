---
title: "mkvtoolnix 5.5 crashes after a few seconds"
date: 2012-04-17
forum: Multimedia Software
---

### Post by Russell Burrows on 2012-04-17
Xubuntu oneiric

When I had this problem in toolnix 4.4 I upgraded to toolnix 4.9 and the fix was press control p and turn off automatic updates and it was solved for that version.

Now in toolnix 4.9 I again have the problem so I turned off automatic updates but the problems persisted so uninstall and then Synaptic install Toolnix version 5.5 and crash, turn off updateting and crash, crash and crash!!

I also tried via ubuntu software but it gave me dependencies not met :
Matroska lib5

I am running Xubuntu but I forgot what version so I guess its latest stable???

---

### Post by BicyclerBoy on 2012-04-17
The latest versions of mkvtoolnix & libmatroska etc behaves okay on lucid..

I think you can get the latest pre-compiled packages from the author.
[http://www.bunkus.org/videotools/mkvtoolnix/downloads.html](http://www.bunkus.org/videotools/mkvtoolnix/downloads.html)

The oneiric ppa links are near bottom of webpage..
This ppa updates libebml and libmatroska & toolnix progs..

If you still have issues at least you can contact the author..

---

### Post by Russell Burrows on 2012-04-17
Aha! it was update to latest version and the launch MKVToolnix and quickly!! press control P and deselect the automatic updates then press ok and quickly! press close to save changes since if it autocloses then we have to start over to get the changes saved.

Updated to latest version and it works!!

Mosu is very good on support for mkvtoolnix and it is fixed!!!! since I only need to remove compressed headers thats makeing TsMuxer crash as part of MKV2Vob.

What really has me going but why??? is the use of compressed headers in MKV files?? since a file with compressed headers versus uncompressed headers and the diff. is one megabyte out of a 13 Gigabyte file(compressed versus uncompressed headers).:confused::confused::confused:

---

### Post by andrew.46 on 2012-04-17
> **Russell Burrows said:**
> Mosu is very good on support for mkvtoolnix.... 

It is indeed good to see a really nice guy who makes truly great software :). Now if he would only stop raising the boost requirements.....

---

### Post by Russell Burrows on 2012-04-17
> **andrew.46 said:**
> It is indeed good to see a really nice guy who makes truly great software :). Now if he would only stop raising the boost requirements.....

Yeah agreed on that since it looks like boostlib requirements are expanding???:confused::confused:
However 30 seconds to mux a movie file for MKVToolnix 5.5 is very good!!

---

### Post by BicyclerBoy on 2012-04-17
The other problem with building from source (lucid) is the gcc version requirement. 
So in lucid you have to upgrade the toolchain before you can compile mkvtoolnix.

An issue with mkvtoolnix is the lack of support (or graceful warning) with LATM-AAC.
If you load a file with LATM-AAC, mkvtoolnix consumes all available RAM & crashes.

---

### Post by Russell Burrows on 2012-04-17
> **BicyclerBoy said:**
> The other problem with building from source (lucid) is the gcc version requirement. 
So in lucid you have to upgrade the toolchain before you can compile mkvtoolnix.

An issue with mkvtoolnix is the lack of support (or graceful warning) with LATM-AAC.
If you load a file with LATM-AAC, mkvtoolnix consumes all available RAM & crashes.

Ahh! hmmm so far I was unaware of that detail but all of my files so far have DTS sound in either 5.1 or 7.1 and as a fallback as AC3 Dolby Digital 7.1 or 5.1 sound.

I tend to run from any file that has AAC since I much prefer Digital Theater Sound.

I guess thats another reason I much prefer MKV instead of MP4.

---

### Post by BicyclerBoy on 2012-04-18
I can't avoid it.
Broadcast HD material is commonly mpeg-ts H264/AAC & H264/LATM-AAC with AC3 as an additional stream.

Was considering mkvtoonix as a ts cutter because it is robust & supports H264 in mpeg-ts & cutlists & has a cmd line interface.

AAC will be directly supported eventually in HT amps etc..
The American digital TV standard was a major setback.

---

### Post by Russell Burrows on 2012-04-18
When I need to quickly cut mpeg-ts H264/AAC & H264 files/streams I use freeware MKV2Vob(Wine/Xubuntu) and also when the audio needs a transcode to AC3 and leaving the video untouched for a fast remux to proper audio(for that particular amplifier/aplication).

MKVToolnix I use when I need to provide uncompressed headers since a lot of webstreaming videos have compressed headers to enable fast start.

---

### Post by BicyclerBoy on 2012-04-18
I'll have a look at MKV2Vob to see if it supports cutlists..shame it's not a native app..Thanks.

There are many windows mpeg-ts cutting programs to choose from.

That fast start stuff is something to do with streaming quicktime container MOV atom placed at the beginning of the file/stream instead of end.
I've not heard about compressed headers...

---

### Post by Russell Burrows on 2012-04-19
MKV2Vob is usefull when you need a 1GB sample cut/split and you need it before the customer finishes watching a quick youtube video.

When I need to cut a lot of files to 2GB or 1GB splits then I just select add directory and one button press and its done.

The downside to this is being unable to specify exact to the second or kilobyte cuts on MKV2Vob so then I use Ubuntu Studio to create music or fine tune cuts.

The reason I know about compressed headers is some folks will do this to save a few megabytes in file size but the usefullness of that is debatable when most files are four gigabytes to twenty five gigs and up.

I use Linux but if you use Windows for video processing then you have a lot more options as to variety of cut/split programs unless you run WINE on top of either Ubuntu/Mint/Xubuntu.

The problem with most Windows Cutting/split programs is that they are long on promises but very short on features/stability/performance and its very problematic to have the work computer get a Windows virus just as the customer needs that edited video right now!! so I tend to only use Linux Operating Systems to avoid those problems.

Editing video or adding music/effects and my shortlist of programs is:
Ubuntu Studio, OpenShot, MKVToolnix, MKV2vob and FFMpeg on Wine for those times when folks want an .avi 

I find it better to use specialist programs per task instead of trying to find the golden video/music/effects editing/creation program that will do it all.

---

### Post by BicyclerBoy on 2012-04-19
The linux way is a specialist tool for every job..

If you want to cut quick & inaccurate then "dd" is perfect.

Tools that support non-GUI (script-able) cutlists & frame accurate cutting (to I frame) are:
avidemux (flakey & no LATM-AAC)
ffmpeg (must decode for frame accurate)
mkvtoolnix (no LATM-AAC)

ffmpeg is a native linux program..no need for wine but you need to compile it yourself.

---

