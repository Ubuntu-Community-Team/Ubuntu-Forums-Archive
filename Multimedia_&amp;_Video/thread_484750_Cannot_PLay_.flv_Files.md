---
title: "Cannot PLay .flv Files"
date: 2007-06-26
forum: Multimedia &amp; Video
---

### Post by Catsworth on 2007-06-26
Hi Guys,

I can't get .flv files to play.

VLC player will play the sound but not the video, and MPlayer just crashes (error:  "LAVF_header: av_find_stream_info() failed").

I've tried ffmpeg, but it fails after complaining (many times) about an "Unsupported video codec".

Can anybody help me get this sorted please?

I've searched around the forums, but none of the posts I've found seem to offer a solution - just lots of people with the same problems.

---

### Post by ABCC on 2007-06-26
There are tons of scripts floating around that will allow you to convert them to avi which out to sort out your bother. To give you an idea, check out [this blog post]("http://www.elecboy.com/index.php/2007/04/30/how-to-convert-youtube-videos-to-divx/")

Youll need mencoder installed to run this, available from the repos. If this litte script doesnt work, just google flv2avi.

hth,

abcc

---

### Post by Gremlinzzz on 2007-06-26
How to enable lame for FFMPEG (needed to encode FLV with sound)

KINO FLVs silent? You need to recompile FFMPEG with LAME enabled. FFMPEG can be installed via apt-get as a package, but is not able encode MP3, which is the audio stream in FLV video (like Google & YouTube).

    * Ensure Ubuntu Universe repository is selected #How to add extra repositories
    * Download and install lame liblame-dev and gcc packages (mp3 encoder + GNU compiler collection) 

sudo apt-get build-dep ffmpeg
sudo apt-get install liblame-dev libfaad2-dev libfaac-dev libxvidcore4-dev liba52-0.7.4 \
liba52-0.7.4-dev libx264-dev libdts-dev libgsm1-dev libvorbis-dev libdc1394-13-dev \
checkinstall build-essential gcc

    * Download and extract FFMPEG source to current working directory 

cd /usr/local/src
sudo apt-get source ffmpeg

    * Compile FFMPEG from source 

cd ffmpeg-*
sudo ./configure --enable-gpl --enable-pp --enable-vorbis --enable-libogg \
--enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug \
--enable-mp3lame --enable-faad --enable-faac --enable-xvid --enable-pthreads \
--enable-x264

maybe try instead = 
sudo ./configure --enable-gpl --enable-pp --enable-libvorbis --enable-libogg \
--enable-liba52 --enable-libdts --enable-dc1394 --enable-libgsm --disable-debug \ 
--enable-libmp3lame --enable-libfaad --enable-libfaac --enable-xvid --enable-pthreads \
--enable-x264


sudo make
sudo checkinstall [accept defaults, set version to 3:0.cvs20060823-3.1ubuntu2]

If during the make it dies at 'x264.c:147: error: `struct <anonymous>` has no member name `i_rf_constant` you need to do the following. Open libavcodec/x264.c and goto line 147. Change 'i_rf_constant' to 'f_rf_constant' and retry.

If an application you are using employs FFMPEG to encode FLV, it should now work properly. You can also call FFMPEG directly from the command line. The extension/suffix of the outfile tells FFMPEG which audio or video format to encode to.

ffmpeg [-i infile] [outfile]

from the guide [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---

### Post by Zalbor on 2007-06-28
> **ABCC said:**
> There are tons of scripts floating around that will allow you to convert them to avi which out to sort out your bother. To give you an idea, check out [this blog post]("http://www.elecboy.com/index.php/2007/04/30/how-to-convert-youtube-videos-to-divx/")

Youll need mencoder installed to run this, available from the repos. If this litte script doesnt work, just google flv2avi.

hth,

abcc
I've tried the script from there, and while I can play the resulting file in ubuntu, I can't play it in windows. Windows has the latest divx codec, and I do choose divx for the script.

---

### Post by aimran on 2007-06-28
If you still can't solve it and can't be arsed anymore consider this: Get a program to convert the .flv files to .ogg. At least that's what I do with videos I download off youtube. I get better sound quality as well after conversion

ffmpeg2theora is the program you want. Not sure if it's in the repos. Picked it off these forums sometime ago :)#

Edit: Damn, Zalbor got ahead of me :P

---

### Post by ABCC on 2007-06-28
> **Zalbor said:**
> I've tried the script from there, and while I can play the resulting file in ubuntu, I can't play it in windows. Windows has the latest divx codec, and I do choose divx for the script.

What media player are you using in windows? It probably means you're missing a codec in your windows install. Try the windows version of VLC, available at [http://www.videolan.org]("http://www.videolan.org") Avi is supported out of the box with that player, so no need to wade into the woeful world of windows media codec packs. (isn't alliteration great?)

---

### Post by Catsworth on 2007-07-20
Still can't get this to work.  ffmpeg2theora seems to convert the files, but it complains about an 'unsupported video codec' and then the file just won't play.

Any more thoughts?

---

### Post by xkendrax on 2007-07-31
I can play flv files on vlc player, o thought i got to install some plugin but not.

---

### Post by punong_bisyonaryo on 2007-07-31
While it may be practical to some to convert every flv file they download, sometimes we just want to play it, so if no one minds I'm gonna re-ask how to make it work.

My multimedia codecs are all set and running, I can even play WMV players on xine (I installed mplayer's codecs into the /usr/lib/win32 where xine checks). I also have libxine-extracodecs installed.

But my flvs just don't play sound! How come?

PS. I think it's a clue that my video codecs are working fine, but my audio codecs have something amiss. What sound codec do I need to fix this?

---

### Post by punong_bisyonaryo on 2007-08-14
I created a new thread in the Multimedia section

[Downloaded FLVs have no sound]("http://ubuntuforums.org/showthread.php?p=3187016")

Basically, FLV sound works in VLC and MPlayer, but seems Miro uses Xine as its engine. Need help on this, please.

---

