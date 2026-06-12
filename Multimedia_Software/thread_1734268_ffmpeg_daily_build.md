---
title: "ffmpeg daily build"
date: 2011-04-20
forum: Multimedia Software
---

### Post by beew on 2011-04-20
Hi,

I installed the MOTU ffmpeg and libav ppa in Natty beta, the installation went through ok and media players all work. But I am having problems converting MP4 to MP3 (extracting audio) with the error message that libmp3lame unknown encoder. I checked that lame and libmp3lame0 are both installed. I wonder what might have been the missing piece.

Thanks.

---

### Post by andrew.46 on 2011-04-20
Hmmm... do both of these PPAs deliberately strip the mp3 encoder from their packages? Mind you if the audio stream in your mp4 is already mp3 a simple *-acodec copy* would suffice.

---

### Post by beew on 2011-04-20
> **andrew.46 said:**
> Hmmm... do both of these PPAs deliberately strip the mp3 encoder from their packages? Mind you if the audio stream in your mp4 is already mp3 a simple *-acodec copy* would suffice.

Actually I tried  converting the same mp4 file before I installed from the PPA and it went ok. I installed because I want to build bino from source and it requires ffmpeg 0.69 or higher.
[URL="http://bino.nongnu.org/download.html"]http://bino.nongnu.org/download.html
[/URL]

---

### Post by beew on 2011-04-20
Maybe this would shed some light. The package libavfilter1 does not update, Synaptic shows the following error message.
> libavfilter1:
 Depends: libavcodec52 but it is not going to be installed or
     libavcodec-extra-52 (>=4:0.7~daily~28195+201104180948~natty1) but 4:0.6.2-1ubuntu2+medibuntu1 is to be installed
 Depends: libavformat52 but it is not going to be installed or
     libavformat-extra-52 (>=4:0.7~daily~28195+201104180948~natty1) but 4:0.6.2-1ubuntu2+medibuntu1 is to be installed
 Depends: libavutil50 but it is not going to be installed or
     libavutil-extra-50 (>=4:0.7~daily~28195+201104180948~natty1) but 4:0.6.2-1ubuntu2+medibuntu1 is to be installed
 Depends: libswscale0 but it is not going to be installed or
     libswscale-extra-0 (>=4:0.7~daily~28195+201104180948~natty1) but 4:0.6.2-1ubuntu2+medibuntu1 is to be installed



---

### Post by FakeOutdoorsman on 2011-04-20
Let's compile [**bino**](http://bino.nongnu.org/download.html) on Ubuntu Maverick Meerkat 10.10:

0. Remove libav from the MOTU PPA.
```
sudo apt-get remove libav
```

1. Install FFmpeg:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

2. Get some bino dependencies [size=1](you may be able to prune some of these since I only tested this once)[/size]:
```
sudo apt-get install autoconf build-essential freeglut3-dev libass-dev libalut-dev libglew-dev libtool qt4-dev-tools
```

3. Get bino source code, compile, and install:
```
cd
wget http://download.savannah.gnu.org/releases/bino/bino-0.9.3.tar.xz
tar Jxvf bino-0.9.3.tar.xz
cd bino-0.9.3
autoreconf -i
./configure
make
sudo checkinstall --pkgname=bino --pkgversion="0.9.3" --backup=no --deldoc=yes --fstrans=no --default
```

---

### Post by beew on 2011-04-20
> **FakeOutdoorsman said:**
> Let's compile [**bino**]("http://bino.nongnu.org/download.html") on Ubuntu Maverick Meerkat 10.10:

0. Remove libav from the MOTU PPA.
```
sudo apt-get remove libav
```1. Install FFmpeg:

[HOWTO: Install and use the latest FFmpeg and x264]("http://ubuntuforums.org/showthread.php?t=786095")

2. Get some bino dependencies [SIZE=1](you may be able to prune some of these since I only tested this once)[/SIZE]:
```
sudo apt-get install autoconf build-essential freeglut3-dev libass-dev libalut-dev libglew-dev libtool qt4-dev-tools
```3. Get bino source code, compile, and install:
```
cd
wget http://download.savannah.gnu.org/releases/bino/bino-0.9.3.tar.xz
tar Jxvf bino-0.9.3.tar.xz
cd bino-0.9.3
autoreconf -i
./configure
make
sudo checkinstall --pkgname=bino --pkgversion="0.9.3" --backup=no --deldoc=yes --fstrans=no --default
```

I have question about step 0, why do you need to remove libav from MOTU?

Actually I am trying to build bino in Natty.  I installed bino through a ppa in Maverick.

But why can't you just do (as instructed on bino's site)

```
$ git clone [git://git.savannah.nongnu.org/bino.git](git://git.savannah.nongnu.org/bino.git)
$ cd bino
$ autoreconf -i
$ ./configure; make; make install
 
```and making sure all the dependencies are installed?

Also I would want to know why doesn't the MOTU ppa work (in terms of libmp3lame, see OP) as it would be a good way to get updated ffmeg automatically if it does.

I actually have many questions about ffmpeg, libav but I should start another thread when I get those questions sorted out.

---

### Post by beew on 2011-04-20
I read that ffmpeg-mt has been merged to the main library, so which version of ffmpeg would have multi-threading feature? Does it mean VLC will support multi-threading? If so which version do I need?

Thanks.

---

### Post by FakeOutdoorsman on 2011-04-20
> **beew said:**
> I have question about step 0, why do you need to remove libav from MOTU?
It is a precautionary measure to make sure it does not interfere with FFmpeg because the libav package from the MOTU PPA installs some of the same files as FFmpeg.

> **beew said:**
> Actually I am trying to build bino in Natty.
My instructions will probably work fine in Natty.

> **beew said:**
> But why can't you just do (as instructed on bino's site)

```
$ git clone [git://git.savannah.nongnu.org/bino.git](git://git.savannah.nongnu.org/bino.git)
$ cd bino
$ autoreconf -i
$ ./configure; make; make install
 
```and making sure all the dependencies are installed?
Nothing is stopping you. You can install bino from git too. Just add git-core as a dependency.

> **beew said:**
> Also I would want to know why doesn't the MOTU ppa work (in terms of libmp3lame, see OP) as it would be a good way to get updated ffmeg automatically if it does.
I don't know--ask the maintainer. I don't use PPAs. Perhaps the libav package wasn't compiled with libmp3lame support. Also note that the PPA mentions:
> This PPA contains daily builds of Libav that are built from the git master branch. They are intended for test rebuilds and testing of dependent packages. Do not enable this PPA on production systems!

> **beew said:**
> I read that ffmpeg-mt has been merged to the main library, so which version of ffmpeg would have multi-threading feature?
ffmpeg-mt code is continually merged into FFmpeg. If you compile FFmpeg using the link I provided then the ffmpeg-mt code will be included.

> **beew said:**
> Does it mean VLC will support multi-threading? If so which version do I need?
andrew.46 would be better to answer that, but you would have to compile VLC to take advantage of that I think:

[Howto: Build the development version of vlc under Ubuntu](http://ubuntuforums.org/showthread.php?t=1398119)

---

### Post by beew on 2011-04-20
Thanks for the answers. I am sure I will come up with more question, your tutorial is a great resource.

---

### Post by mc4man on 2011-04-20
While you're free do do as you want that ppa is not really for general use and is far from a 'daily'. More used as a testing ppa
If this is what you've used
[https://launchpad.net/~motumedia/+archive/ffmpeg-daily](https://launchpad.net/~motumedia/+archive/ffmpeg-daily)

---

### Post by andrew.46 on 2011-04-20
> **beew said:**
> I read that ffmpeg-mt has been merged to the main library, so which version of ffmpeg would have multi-threading feature? Does it mean VLC will support multi-threading? If so which version do I need?

FFmpeg-mt was merged with FFmpeg (videolan) in late March so your best bet is to get a copy of vlc compiled against FFmpeg from April onwards. This would obviously include the quirkily named 'FFmpeg 0.6.90-rc0 "Love and Peace"' release. I am not sure about benefits for vlc of FFmpeg-mt except for my deep suspicion that in general for the *average* user FFmpeg-mt will not change all that much. Others will disagree :).

---

### Post by beew on 2011-04-20
> **mc4man said:**
> While you're free do do as you want that ppa is not really for general use and is far from a 'daily'. More used as a testing ppa
If this is what you've used
[https://launchpad.net/~motumedia/+archive/ffmpeg-daily]("https://launchpad.net/%7Emotumedia/+archive/ffmpeg-daily")

Yes, it is. So is there other way to get up to date ffmpeg via ppa? I will try FakeOutdoorsman's tutorial but it will take sometimes and probably lots of trial and error.

I install Natty in an external drive so I don't mind taking risks and experimenting. The point is to figure out what works best and then reproduce it in the regular install.

---

### Post by beew on 2011-04-20
> **andrew.46 said:**
> FFmpeg-mt was merged with FFmpeg (videolan) in late March so your best bet is to get a copy of vlc compiled against FFmpeg from April onwards. This would obviously include the quirkily named 'FFmpeg 0.6.90-rc0 "Love and Peace"' release. I am not sure about benefits for vlc of FFmpeg-mt except for my deep suspicion that in general for the *average* user FFmpeg-mt will not change all that much. Others will disagree :).

Thanks for the info. I use an mplayer build with ffmpeg-mt ([https://launchpad.net/~ripps818/+archive/coreavc  ]("https://launchpad.net/%7Eripps818/+archive/coreavc")I don't use coreavc, just the player) and find it working better than VLC for hd video playback on dual core machines even with open source drivers (so no VDPAU) 

From the top command I see cpu usage is much more even between two cores for mplayer whereas VLC behaves differently for different videos and different machines. Sometimes the cpu usage is kind of even but most time it is rather one sided and in some cases (usually clips involving fast actions) VlC just chokes on one cpu while mplayer still manages rather smooth playback. 

I would think that building VLC with ffmpeg-mt will improve performance in these cases (I like mplayer, but it is good also to have a good second video player and I notice that VLC performs better than mplayer when cpu usage is not an issue, like for videos that can be played with one core easily)

EDITED: I also tried using mplayer from the MOTU ppa and it is not performing that well in Natty and probably worse than VLC on single core machines. Don't know why but ripps' version of  mplayer works flawlessly on all machines I have tested(it is built from svn and statically linked to its own ffmpeg libraries apparently)

---

### Post by flyingAnt on 2011-04-25
[COLOR=#000000][FONT=Times New Roman][COLOR=#333333][FONT=Lucida Grande]   Serious addiction from this site lol, a lot of your writes have definitely helped me out. Looking forward to your posts!:popcorn:
[/FONT][/COLOR][/FONT][/COLOR]

---

### Post by andrew.46 on 2011-04-25
> **beew said:**
> From the top command I see cpu usage is much more even between two cores for mplayer whereas VLC behaves differently for different videos and different machines. Sometimes the cpu usage is kind of even but most time it is rather one sided and in some cases (usually clips involving fast actions) VlC just chokes on one cpu while mplayer still manages rather smooth playback.

I have finally had my curiosity tickled with the whole mt thing but I will have to admit to being not entirely sure how to test this effectively with top. Can I ask how you have watched your own cpu performance and interpreted the result? I have been ruuning MPlayer with and without *-lavdopts threads=4* and watching my dual cores with top but there must be a better way....

---

### Post by mc4man on 2011-04-25
> but there must be a better way.... 

Maybe take a look at sysstat package ,  man mpstat could prove useful to get some idea

---

