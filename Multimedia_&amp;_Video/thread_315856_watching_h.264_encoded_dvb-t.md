---
title: "watching h.264 encoded dvb-t"
date: 2006-12-09
forum: Multimedia &amp; Video
---

### Post by edgyUser on 2006-12-09
Hi,

I was able to set up kaffeine to watch dvb channels using the leadtek dtv2000h card. Currently there is a trial HDTV transmission in my area. The HDTV material is H.264 encoded. Is it possible to set up kaffeine to watch the HDTV? I was able to watch it on my Windows setup using the Powerdvd decoder. Any help is appreciated.

BTW, I was able to hear the sound, but no video. It looks like the audio portion of the TS stream is decoded.

---

### Post by Nelson-Ray on 2006-12-09
Hey I'm no expert on the topic...but I am thinking the reason why you heard sound and no video is that your computer couldn't keep up with cpu requirements. H264 is pretty new and is just starting to get optimized in Linux. I have read some places that vlc and mplayer are getting optimized for H264 in the next releases. 

I actually downloaded some .TS HDTV files encoded in H264 format and my computer (AMD X2 4400/2 gigs ram/Nvidia 6600 GT) could play the video for like a second and then it would just blur up into unrecognizeable pixels :). I would bet in a few months you can view that with Kaffeine when theres more optimzation for H264, but at the moment I don't think its possible. I could be wrong though!

---

### Post by Nelson-Ray on 2006-12-10
Just letting you know MPlayer 1.0rc1 which was released Oct. 22 has noticeable improvements for H264. Their website says "Vorbis decoding has seen a big speedup, as has H.264. The optimizations to H.264 are still ongoing, but the difference should already be noticeable."


I couldnt find a build for Edgy, but I did see one for Fedora, so I rebooted into Fedora and checked it out. 1.0rc1 definitely has been improved for H264 and I can actually watch HD movies encoded in H264! 

Perhaps if you were able to just record the stream, then you could play the file in mplayer 1.0rc1? Then again you have to compile 1.0rc1 yourself or find a build for edgy. But anyways looks promising.

---

### Post by edgyUser on 2006-12-10
Thanks for your response. I have an Intel dual 2 core E6300 running. So it has a lot of CPU horsepower to decode H.264. The fact that it is working well in Windows proves that cpu is not an issue.

I am able to view H.264 encoded material with no problem. I believe the issue is how to get kaffeine to recognize the h.264 encoded ts stream and use the appropriate decoder to decode it.

---

### Post by jcmiguel on 2007-06-21
Would you mind to share how did you manage to make dvt2000h work? I am trying to get away from my Vista x64 HTPC with a Ubuntu x64 and I just cannot make it work. I regret so much have bouth Vista but I am stuck with it. Can you help?

---

### Post by mrscript on 2008-01-03
YES. It's possible. 
You'll need external ffmpeg (newest from SVN).

There are two ways to watch h.264 TV on ubuntu.

**1. kafeine:**
First completely remove kaffeine, xine-lib, libxine, ffmpeg, etc.

```

svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg
cd ffmpeg; ./configure --enable-pp --enable-gpl
make; sudo make install

```
Download xine-lib-1.1.8, then extract it and:```
./configure --with-external-ffmpeg
make; make install

```
Now download and compile newest kaffeine:
```

svn co svn://anonsvn.kde.org/home/kde/branches/extragear/kde3/multimedia
make -f Makefile.cvs
./configure
make
cd kaffeine
sudo make install

```
Thats all. Now you could watch h.264 encodet TV. 
BUT i must warn you, performance will be very poor (I don't know why... if someone find answer i'll be glad to hear it)

**2. VLC**
Download newest VLC.
Then
```

sudo apt-get build-dep vlc
sudo apt-get install subversion automake1.9 libtool cvs libgcrypt-dev libfaac-dev liblame-dev libfaad2-dev libtwolame-dev  libjack-dev

```
Extract VLC and enter that directory. Then
```

svn co svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg
cd ffmpeg
./configure --enable-gpl --enable-pp --enable-pthreads
make

```
Now you need to compile VLC with external ffmpeg.
```

# mkdir build; cd build;
#../configure --prefix=/usr --enable-debug --enable-shared-libvlc--with-ffmpeg-tree=PATH_TO_DOWNLOADED_AND_COMPILED_ffmpeg --enable-v4l --enable-dvb –enable-vcdx 
#make
# ./vlc --program= -v dvb-t:frequency=770000000:bandwidth=8:
```

with VLC performance very good ;)

---

