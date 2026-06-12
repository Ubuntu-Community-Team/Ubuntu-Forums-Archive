---
title: "Installing mplayer2 || Natty"
date: 2011-06-29
forum: Multimedia Software
---

### Post by linuxyogi on 2011-06-29
Hi, 

Lately I am facing some issues playing some videos on mplayer.

[http://dl.dropbox.com/u/30630174/mplayer%20error.txt]("http://dl.dropbox.com/u/30630174/mplayer%20error.txt")

I want to try mplayer2 & see if that solves the issue.

I have downloaded mplayer2-build-2.0.tar.bz2 from [http://www.mplayer2.org/](http://www.mplayer2.org/)

Need your help in installing it.

---

### Post by beew on 2011-06-29
Hi,

You can get mplayer2  using this ppa

[https://launchpad.net/~ripps818/+archive/coreavc]("https://launchpad.net/%7Eripps818/+archive/coreavc")

It says mplayer but it is actually mplayer2, also you don't need to worry about coreavc, if you don't want it, just don't install dishowserver, the mplayer2 has nothing to do with it.

Alternatively, you can build it yourself.

```

$ sudo apt-get install libdvdread4 libdvdnav-dev libdvdread-dev && \ sudo /usr/share/doc/libdvdread4/install-css.sh
$ sudo apt-get build-dep mplayer 
$ sudo apt-get install build-essential subversion git-core yasm autoconf libtool  
$ git clone git://git.mplayer2.org/mplayer2-build.git  
$ cd mplayer2-build && ./enable-mt && ./init  
$ echo --prefix=$HOME >> ./mplayer_options  
$ make -j4  
$ make install  
$ mv $HOME/bin/mplayer $HOME/bin/mplayer2
```This will create a mplayer2 executable in the bin folder in your home directory. This way you can keep both mplayer and mplayer2 (in Smplayer there is an option to choose the mplayer backend) 

I am using this method because mplayer2 while in general better than mplayer it has problem streaming videos online (divx in particular it seems) because there is a conflict between how gnome-mplayer and mplayer2 handle pausing and restarting. So I use mplayer with gecko-mediaplayer (gnome-mplayer) for streaming but mplayer2 for watching local material and dvds (the first line of code basically adds the dvd playing function back to mplayer2, which the dev has removed)

I have been getting a lot of useful advice from andrew.46 on this thread.
[http://ubuntuforums.org/showthread.php?t=1542240&page=27](http://ubuntuforums.org/showthread.php?t=1542240&page=27)

---

### Post by linuxyogi on 2011-06-29
@beew

I read at openSUSE forum that just copying the binaries ([this]("http://ftp.mplayer2.org/pub/release/mplayer2-2.0-linux-x86-glibc27.tar.bz2")) to /usr/local/bin will do it so I 

downloaded  the file from [here ]("http://ftp.mplayer2.org/pub/release/mplayer2-2.0-linux-x86-glibc27.tar.bz2")& extracted it to my home folder, made it executable then

tried playing the same file which mplayer failed to play. Just to test it mplayer2 is really 

capable to playing the file. But unfortunately, same result. Those same errors. So, in that 

case do you think installing mplayer2 will be the solution in my case ?

---

### Post by linuxyogi on 2011-06-29
[B]Copied the downloaded file to /usr/bin (replaced mplayer).

Done !!![/B] 

Its working now.

```
$ mplayer --version
Unknown option on the command line: --version
Error parsing option on the command line: --version
MPlayer2 2.0 (C) 2000-2011 MPlayer Team
```

---

### Post by beew on 2011-06-29
> **linuxyogi said:**
> Copied the downloaded file to /usr/bin (replaced mplayer).

Done !!!

Its working now.

I read from the mplayer2 website that the binary for Linux has only basic functions comparing to the Windows and Mac versions though it doesn't say  what is missing.

If you are copying it into /usr/bin you are using it to replace mplayer (rather than having both like what I do with a compiled version of mplayer2) In that case I think you are better off with the ppa because you get regular updates and it has extra functions like being able to play DVD.

---

### Post by linuxyogi on 2011-06-29
> **beew said:**
> I read from the mplayer2 website that the binary for Linux has only basic functions comparing to the Windows and Mac versions though it doesn't say  what is missing.

If you are copying it into /usr/bin you are using it to replace mplayer (rather than having both like what I do with a compiled version of mplayer2) In that case I think you are better off with the ppa because you get regular updates and it has extra functions like being able to play DVD.

All I do with mplayer is play HD videos of different containers & codecs. I almost never 

play DVDs anymore. vdpau is working fine with mplayer2. So that's all I need ATM.

About the ppa, is this an official mplayer ppa ? If yes, I will install it right now. 

But I am really critical about stuff like these. Please understand. 

I really wish that mplayer2 gets included in the Ubuntu repos soon. Its already there at 

the openSUSE repos (I read) I don't know about other distros .

---

### Post by beew on 2011-06-29
> **linuxyogi said:**
> All I do with mplayer is play HD videos of different containers & codecs. I almost never 

play DVDs anymore. vdpau is working fine with mplayer2. So that's all I need ATM.

About the ppa, is this an official mplayer ppa ? If yes, I will install it right now. 

But I am really critical about stuff like these. Please understand. 

I really wish that mplayer2 gets included in the Ubuntu repos soon. Its already there at 

the openSUSE repos (I read) I don't know about other distros .

No, it is not "official" but I have been using it for the longest time and have nothing but good experience with it (like I said coreavc has nothing to do with it, I just installed the player) the reason I am not using it at the moment is that I need to keep ordinary mplayer for streaming, so I will need to have mplayer2 and mplayer installed side by side.

I never install mediaplayers from the "official repo" because they are always outdated (repo freezes for the entire life span of the release, that is 1.5 year for normal releases, 3 years for LTS, a lot can happen in between  for open source softwares, which are always in a  state of flux and even more true for multi-media stuffs) , almost always crippled (new features are missing even if they are important)  and sometimes permanently broken (bugs won't get fixed because Ubuntu's idea of "stablility" is that if you fix old bugs you may introduce new ones so they only fix security related bugs, so better live with lower expectations rather than taking a chance) 

As an example you have minitube 1.3 in Natty's repo, which is broken as in doesn't work and that was fixed upstream many months ago and the new version has been in ppas for Maverick for months before Natty was even released. But you will be stuck to it  til next year October if you use minitube and stick to official repos, so who cares if it is "stable" if things don't work?!

So even if mplayer2 is in the official repo I wouldl still rather use ppa or compile it myself.

---

### Post by linuxyogi on 2011-06-29
> **beew said:**
> No, it is not "official" but I have been using it for the longest time and have nothing but good experience with it (like I said coreavc has nothing to do with it, I just installed the player) the reason I am not using it at the moment is that I need to keep ordinary mplayer for streaming, so I will need to have mplayer2 and mplayer installed side by side.

I never install mediaplayers from the "official repo" because they are always outdated (repo freezes for the entire life span of the release, that is 1.5 year for normal release, 3 year for LTS, a lot can happen in between especially for open source software, which is always in state of flux and even more true for multi-media stuffs) , almost always crippled (new features are missing even if they are important)  and sometimes permanently broken (bugs won't get fixed because Ubuntu's idea of "stablility" is that if you fix old bugs you may introduce new ones so they only fix security related bugs, so better live with lower expectations rather than taking a chance) 

As an example you have minitube 1.3 in Natty's repo, which is broken as in doesn't work and that was fixed upstream many months ago and the new version has been in ppas for Maverick for months before Natty was even released. But you will be stuck to it  til next year October if you use minitube and stick to official repos, so who cares if it is "stable" if things don't work?!

So even if mplayer2 is in the official repo I wouldl still rather use ppa or compile it myself.

Point taken. I don't really have a problem using PPAs. I am using the wine ppa. For I need 

the latest version of wine to play games.  But the no one but guys at wine are maintaining 

that repo.  

Don't you think that mplayer project must  maintain a ppa of their own ? 

You must have done some searching regarding the subject. 

What did you find ?

---

### Post by beew on 2011-06-29
> **linuxyogi said:**
> 
Don't you think that mplayer project must  maintain a ppa of their own ? 

You must have done some searching regarding the subject. 

What did you find ?

There are two mplayer ppas which are maintained by mplayer developers as far as I know.
[https://launchpad.net/~longinus00/+archive/mplayer-mt]("https://launchpad.net/%7Elonginus00/+archive/mplayer-mt")
[https://launchpad.net/~motumedia/+archive/mplayer-daily]("https://launchpad.net/%7Emotumedia/+archive/mplayer-daily")

I don't have very good experience with the MOTU one even though many people recommend it. It apparently doesn't use VDPAU. It chokes on hd contents.

The mt one uses VDPAU and is quite good in playing hd content (with or without VDPAU) but still not as good as mplayer2 in my experience. I have been using ripps' ppa for mplayer and couldn't understand why it performed so much better than the others, then I found out it was actually mplayer2.

---

### Post by linuxyogi on 2011-06-29
> repo freezes for the entire life span of the release, that is 1.5 year for normal release, 3 year for LTS

That sucks :confused:

About the LTS, that's understandable. But for regular releases I wonder why Ubuntu has 

taken such a conservative policy. Isn't Ubuntu based on Sid which is known to be a 

bleeding edge distro ?


> There are two mplayer ppas which are maintained by mplayer developers as far as I know.
[https://launchpad.net/~longinus00/+archive/mplayer-mt]("https://launchpad.net/%7Elonginus00/+archive/mplayer-mt")
[https://launchpad.net/~motumedia/+archive/mplayer-daily]("https://launchpad.net/%7Emotumedia/+archive/mplayer-daily")

The mt one uses VDPAU and is quite good in playing hd content (with or  without VDPAU) but still not as good as mplayer2 in my experience.

That indicates the fact that an official mplayer2 ppa will be available soon (I hope) . :guitar:

---

### Post by beew on 2011-06-29
> **linuxyogi said:**
> 
taken such a conservative policy. Isn't Ubuntu based on Sid which is known to be a 

bleeding edge distro ?

A snapshot of Sid which is taken before Ubuntu's official release and frozen for the whole lifespan of the release. :)




> That indicates the fact that an official mplayer2 ppa will be available soon (I hope) . :guitar:It is actually not difficult to compile it. I am a total newbie in compiling stuffs, if I can do it anyone can. :)

---

### Post by jsevi83 on 2011-07-01
You can also install mplayer2 from here:

[https://launchpad.net/~ed10vi86/+archive/tst](https://launchpad.net/~ed10vi86/+archive/tst)

---

### Post by linuxyogi on 2011-07-27
> **beew said:**
> 

```

$ sudo apt-get install libdvdread4 libdvdnav-dev libdvdread-dev && \ sudo /usr/share/doc/libdvdread4/install-css.sh
$ sudo apt-get build-dep mplayer 
$ sudo apt-get install build-essential subversion git-core yasm autoconf libtool  
$ git clone git://git.mplayer2.org/mplayer2-build.git  
$ cd mplayer2-build && ./enable-mt && ./init  
$ echo --prefix=$HOME >> ./mplayer_options  
$ make -j4  
$ make install  
$ mv $HOME/bin/mplayer $HOME/bin/mplayer2
```This will create a mplayer2 executable in the bin folder in your home directory. This way you can keep both mplayer and mplayer2 (in Smplayer there is an option to choose the mplayer backend) 



Just used this method. Installation completed without any errors.

But seems like /home/username/bin/mplayer2 has no vdpau support

```

tux@tux:~/.bin$ ./mplayer2 -vo vdpau /home/tux/Videos/*
MPlayer2 2.0-276-gd6890a7 (C) 2000-2011 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/tux/Videos/9N_yEVjx7as.mp4.
Detected file format: QuickTime/MPEG-4/Motion JPEG 2000 format (libavformat)
[lavf] stream 0: audio (aac), -aid 0, -alang und
[lavf] stream 1: video (h264), -vid 0
VIDEO:  [H264]  1280x544  24bpp  29.970 fps  1786.0 kbps (218.0 kbyte/s)
Clip info:
 major_brand: mp42
 minor_version: 0
 compatible_brands: isomavc1mp42
 creation_time: 2010-01-27 13:11:41
Load subtitles in /home/tux/Videos/
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 125.5 kbit/8.89% (ratio: 15690->176400)
Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   9.5 (09.5) of 301.0 (05:01.0)  0.2% 


MPlayer interrupted by signal 2 in module: unknown


```I am running Lucid now.

---

### Post by mc4man on 2011-07-27
Do/did you have libvdpau-dev installed? (otherwise no vdpau support

---

### Post by linuxyogi on 2011-07-27
> **mc4man said:**
> Do/did you have libvdpau-dev installed? (otherwise no vdpau support

Yes lbvdpau-dev is installed.

```
$ aptitude search libvdpau-dev
i   libvdpau-dev                    - Video Decode and Presentation API for Unix

```

---

### Post by linuxyogi on 2011-07-27
Seems like no vdpau 

```
./mplayer2 -vo help
MPlayer2 2.0-276-gd6890a7 (C) 2000-2011 MPlayer Team
Available video output drivers:
    xv    X11/Xv
    gl_nosw    OpenGL no software rendering
    x11    X11 ( XImage/Shm )
    xover    General X11 driver for overlay capable video output drivers
    sdl    SDL YUV/RGB/BGR renderer (SDL v1.1.7+ only!)
    gl    OpenGL
    gl2    X11 (OpenGL) - multiple textures version
    dga    DGA ( Direct Graphic Access V2.0 )
    ggi    General Graphics Interface (GGI) output
    fbdev    Framebuffer Device
    fbdev2    Framebuffer Device
    svga    SVGAlib
    matrixview    MatrixView (OpenGL)
    aa    AAlib
    caca    libcaca
    v4l2    V4L2 MPEG Video Decoder Output
    dfbmga    DirectFB / Matrox G200/G400/G450/G550
    null    Null video output
    directfb    Direct Framebuffer Device
    mpegpes    MPEG-PES to DVB card
    yuv4mpeg    yuv4mpeg output for mjpegtools
    png    PNG file
    jpeg    JPEG file
    gif89a    animated GIF output
    tga    Targa output
    pnm    PPM/PGM/PGMYUV file
    md5sum    md5sum of each frame

```

---

### Post by beew on 2011-08-01
Don't know why, vdpau works flawlessly for me. Sorry can't help you other than bumping the thread.

---

