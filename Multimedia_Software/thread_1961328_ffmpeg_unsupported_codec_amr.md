---
title: "ffmpeg unsupported codec amr"
date: 2012-04-19
forum: Multimedia Software
---

### Post by doru001 on 2012-04-19
On Lucid, I get unsupported codec for amr format from ffmpeg. amr is listed as supported format in ```
ffmpeg -formats
``` amr does not appear in "configuration:" among "--enable-*" options. 
The following packages are installed: 

```
libopencore-amrnb0
libopencore-amrwb0
libavcodec-extra-52
libavutil-extra-49
```
All of them seem to be provided by Ubuntu, not Medibuntu. 

```
ffmpeg -i in.amr out.wav
``` 
says unsupported codec for input stream, 
```
ffmpeg -i in.amr -acodec copy out.wav
```
works. 

Compilation from source excluded, I have a few questions: 
- Is "ffmpeg -i in.amr out.wav" supposed to work? 
- Is medibuntu required for amr?
- Why is "ffmpeg -i in.amr -acodec copy out.wav" working while "ffmpeg -i in.amr out.wav" is not? 
- What is the meaning of "configuration:" and why does it contradict the "-formats" listing? 

Please help me out of the haze.

---

### Post by shantiq on 2012-04-19
in ffmpeg it shows under ```
ffmpeg -codecs
```

>  
D A    amrnb           Adaptive Multi-Rate NarrowBand
D A    amrwb           Adaptive Multi-Rate WideBand



**But** would not convert for me   so caNNOT help you with ffmpeg **but**


i tried SoX   and it seems happy 


so

```
sox file.amr file.wav 
```     works there



will also convert to amr



>  sox input.wav -C 7  ouput.amr-nb    compression 1 to 7  extension has to be amr-nb   can be renamed amr after

---

### Post by doru001 on 2012-04-19
Thanks for the tip about sox. 

```
ffmpeg -codecs
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1.3, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1.3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Dec 21 2011 18:37:21, gcc: 4.4.3
ffmpeg: missing argument for option '-codecs'

```Different ffmpeg version?

---

### Post by shantiq on 2012-04-19
yes well it might help in the meantime there must be a way with ffmpeg but i cannot see it



:KS> ffmpeg
ffmpeg version 0.7.3-4:0.7.3-0ubuntu0.11.10.1, Copyright (c) 2000-2011 the Libav developers
  built on Jan  4 2012 16:08:51 with gcc 4.6.1


Personally happy that this newer version adds this  :::]]]]

>  DEA    alac            ALAC (Apple Lossless Audio Codec)


---

### Post by doru001 on 2012-04-19
```
sox FAIL formats: no handler for detected file type `amr-nb'
```

Do you have some special library installed for that?

---

### Post by shantiq on 2012-04-19
i guess you might need the extras [do not know for sure but try it maybe]



```
sudo apt-get install sox libsox-fmt-all

```

---

### Post by doru001 on 2012-04-19
> **shantiq said:**
> i guess you might need the extras [do not know for sure but try it maybe]



```
sudo apt-get install sox libsox-fmt-all

```
Thank you for your time, but I got the same result.

---

### Post by ron999 on 2012-04-19
> **doru001 said:**
> ... but I got the same result.
Hi
Try using mPlayer like this:-
```
mplayer in.amr -vc null -vo null -ao pcm:fast:file=out.wav
```

---

### Post by shantiq on 2012-04-19
shoot !!!  :KS


ok when you run just the word

```
sox
```   in your terminal do you get [scrolling down a bit]


> AUDIO FILE FORMATS: 8svx aif aifc aiff aiffc al amb **[COLOR="DarkRed"]amr-nb amr-wb [/COLOR]**anb au avi avr awb cdda cdr cvs cvsd cvu dat dvms f32 f4 f64 f8 ffmpeg flac fssd gsm gsrt hcom htk ima ircam la lpc lpc10 lu m4a m4b maud mp2 mp3 mp4 mpg nist ogg prc raw s1 s16 s2 s24 s3 s32 s4 s8 sb sds sf sl smp snd sndfile sndr sndt sou sox sph sw txw u1 u16 u2 u24 u3 u32 u4 u8 ub ul uw vms voc vorbis vox wav wavpcm wmv wv wve xa
PLAYLIST FORMATS: m3u pls
AUDIO DEVICE DRIVERS: alsa



or are they not present?

---

### Post by doru001 on 2012-04-19
mplayer did not like something: 
```
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Sound clip(05).amr.
libavformat file format detected.
[lavf] Audio stream found, -aid 0
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
Cannot find codec 'libamr_nb' in libavcodec...
ADecoder init failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x726D6173.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Video: no video


Exiting... (End of file)
```

---

### Post by doru001 on 2012-04-19
> **shantiq said:**
> shoot !!!  :KS


ok when you run just the word

```
sox
```   in your terminal do you get [scrolling down a bit]





or are they not present?

They are missing from the list, and anb also is missing.

---

### Post by shantiq on 2012-04-19
i am going to ask a dumb question here:KS   but you have got your restricted extras on your system?   You probably do already


```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by doru001 on 2012-04-19
> **shantiq said:**
> i am going to ask a dumb question here:KS   but you have got your restricted extras on your system?   You probably do already


```
sudo apt-get install ubuntu-restricted-extras
```
I have them: 
```
dpkg -l | grep ubuntu-restricted-extras
ii  ubuntu-restricted-extras                   39                                              Commonly used restricted packages for Ubuntu

```

---

### Post by ron999 on 2012-04-19
> **doru001 said:**
> mplayer did not like something: 
```
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Sound clip(05).amr.
libavformat file format detected.
[lavf] Audio stream found, -aid 0
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
[COLOR="Red"]Cannot find codec 'libamr_nb' in libavcodec[/COLOR]...

```
Hi
Maybe you need Option B or Option C here ---> [http://ubuntuforums.org/showthread.php?t=1117283&highlight=ffmpeg+codecs]("http://ubuntuforums.org/showthread.php?t=1117283&highlight=ffmpeg+codecs")

---

### Post by doru001 on 2012-04-19
> **ron999 said:**
> Hi
Maybe you need Option B or Option C here ---> [http://ubuntuforums.org/showthread.php?t=1117283&highlight=ffmpeg+codecs](http://ubuntuforums.org/showthread.php?t=1117283&highlight=ffmpeg+codecs)
Thanks, I've been on that page many times. Packages are installed, compilation does not work (the instructions are obsolete?), and Medibuntu does not show any amr libraries.

---

### Post by flurospar on 2012-04-19
Try
```

sudo apt-get install libopencore-amr

```

---

### Post by doru001 on 2012-04-19
> **flurospar said:**
> Try
```

sudo apt-get install libopencore-amr

```
That is not available. There are two dev and dbg packages, one for each amrnb and amrwb package. I did not install them.

---

### Post by ron999 on 2012-04-19
> **doru001 said:**
> ...compilation does not work (the instructions are obsolete?)
If you intend to compile FFmpeg the Lucid HOWTO is here ---> [http://ubuntuforums.org/showpost.php?p=9868359&postcount=1289]("http://ubuntuforums.org/showpost.php?p=9868359&postcount=1289")

---

### Post by doru001 on 2012-04-19
> **ron999 said:**
> If you intend to compile FFmpeg the Lucid HOWTO is here ---> [http://ubuntuforums.org/showpost.php?p=9868359&postcount=1289](http://ubuntuforums.org/showpost.php?p=9868359&postcount=1289)
Thanks, I will try it tomorrow. What makes you think that this would solve my problem? I see that they install by hand every codec they need, and amr is not among them.

---

### Post by mc4man on 2012-04-19
> **doru001 said:**
> Thanks, I will try it tomorrow. What makes you think that this would solve my problem? I see that they install by hand every codec they need, and amr is not among them.
haven't used lucid in a long time but re-read step 2 - 

sudo apt-get install ..... libopencore-[COLOR="Blue"]amrnb[/COLOR]-dev, libopencore-[COLOR="Blue"]amrwb[/COLOR]-dev

---

### Post by doru001 on 2012-04-19
> **mc4man said:**
> haven't used lucid in a long time but re-read step 2 - 

sudo apt-get install ..... libopencore-[COLOR=Blue]amrnb[/COLOR]-dev, libopencore-[COLOR=Blue]amrwb[/COLOR]-dev
Good enough, thank you, I will post the results tomorrow.

---

### Post by FakeOutdoorsman on 2012-04-19
> **doru001 said:**
> Is "ffmpeg -i in.amr out.wav" supposed to work?
Yes, but only if you follow option A or C from [HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283).

> **doru001 said:**
> Is medibuntu required for amr?
Yes, if you use ffmpeg from the repository.
No, if you compile ffmpeg.

> **doru001 said:**
> Why is "ffmpeg -i in.amr -acodec copy out.wav" working while "ffmpeg -i in.amr out.wav" is not?
In the first command ffmpeg is blindly copying the audio from the input and dumping it into the output. You could probably do this with a variety of output formats despite them being not a valid or supported combination. The second command is attempting to re-encode, but it fails because you do not have an AMR decoder.

To get AMR decoding working you have two main options: you can compile ffmpeg (see option A in above link), or, if you want to use repository ffmpeg, use the **libavcodec-extra-52** package from Medibuntu (see option C in above link). Then in *ffmpeg -formats*, under the Codecs section (I'm talking about repo version here), you should see:
```
DEA    libopencore_amrnb OpenCORE Adaptive Multi-Rate (AMR) Narrow-Band
D A    libopencore_amrwb OpenCORE Adaptive Multi-Rate (AMR) Wide-Band
```

---

### Post by doru001 on 2012-04-20
> **FakeOutdoorsman said:**
> Yes, but only if you follow option A or C from [HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283).


Yes, if you use ffmpeg from the repository.
No, if you compile ffmpeg.


In the first command ffmpeg is blindly copying the audio from the input and dumping it into the output. You could probably do this with a variety of output formats despite them being not a valid or supported combination. The second command is attempting to re-encode, but it fails because you do not have an AMR decoder.

To get AMR decoding working you have two main options: you can compile ffmpeg (see option A in above link), or, if you want to use repository ffmpeg, use the **libavcodec-extra-52** package from Medibuntu (see option C in above link). Then in *ffmpeg -formats*, under the Codecs section (I'm talking about repo version here), you should see:
```
DEA    libopencore_amrnb OpenCORE Adaptive Multi-Rate (AMR) Narrow-Band
D A    libopencore_amrwb OpenCORE Adaptive Multi-Rate (AMR) Wide-Band
```
Thank you for your answer. Now I understand that my ffmpeg is not compiled with the amr codec. How can I find out the archive from which a package originated? My packages have all "Origin: Ubuntu" and medibuntu has been added to sources.list.d but I removed it some time ago.

---

### Post by for.i.am.root on 2012-04-20
I originally wrote this for Lucid. It will auto download the source for just about any codec and compile it. Let a few community members read through it before you run it.

```

#! /bin/bash
# As of 19-APR-2012 this script works to download and install just about every codec needed for video as well as a bunch of extra stuff I use.
# This script was written for lucid (10.04), however, as long as the package names/versions didn't change it will work for newer systems.
# For troubleshooting tips / issues drop me a line.
#
# for.i.am.root
#
# Install lsb to get rid of the stupid no modules error
sudo apt-get -y update && sudo apt-get -y install lsb
# Backup sources.list
sudo mv /etc/apt/sources.list /etc/apt/sources.list.backup
# Get the codename of the current version
varcode=`lsb_release -a | grep Codename | sed 's/Codename://' | sed -e 's/^[ \t]*//'`
# Add medibuntu / multivers / universe / restricted / virtualbox
sudo cat << EOF >> /etc/apt/sources.list
# Comment below to disable restricted
deb http://us.archive.ubuntu.com/ubuntu/ $varcode main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ $varcode main restricted
deb http://us.archive.ubuntu.com/ubuntu/ $varcode-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ $varcode-updates main restricted
# Comment below to disable univrese
deb http://us.archive.ubuntu.com/ubuntu/ $varcode universe
deb-src http://us.archive.ubuntu.com/ubuntu/ $varcode universe
deb http://us.archive.ubuntu.com/ubuntu/ $varcode-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ $varcode-updates universe
# Comment below to disable multiverse
deb http://us.archive.ubuntu.com/ubuntu/ $varcode multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ $varcode multiverse
deb http://us.archive.ubuntu.com/ubuntu/ $varcode-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ $varcode-updates multiverse
# medibuntu is needed for this script
deb http://packages.medibuntu.org/ $varcode free non-free
deb-src http://packages.medibuntu.org/ $varcode free non-free
# Comment below to disable Virtualbox repo
deb http://download.virtualbox.org/virtualbox/debian $varcode contrib non-free
EOF
# Add PS3MediaServer
sudo add-apt-repository ppa:happy-neko/ps3mediaserver
# Add Virtualbox
cd && wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
# This line merges the two sources files
# You will end up with a bunch doubles in source.list
# After the second run of update it will fix itself
# But you will still have doubles in your /etc/apt/sources.list
# They will just be ignored
sudo cat /etc/apt/sources.list.backup >> /etc/apt/sources.list
# Update and install keyring
sudo apt-get -y update
sudo apt-get -y update
sudo apt-get -y --allow-unauthenticated install medibuntu-keyring
sudo apt-get -y update
sudo apt-get -y install libx11-dev libogg-dev libfaac-dev libvdpau-dev libsdl1.2-dev libvorbis-dev libxfixes-dev libtheora-dev libvorbis-dev libxvidcore-dev libjack0 libopencore-amrnb-dev libopencore-amrwb-dev libxvidcore4 build-essential checkinstall doxygen git-core lynx nasm subversion texi2html wget zlib1g-dev libgtk2.0-dev
# Depending on your system one of these will work. The other will fail
sudo apt-get -y install w64codecs
sudo apt-get -y install w32codecs
# Get ready for the new stuff
sudo apt-get -y remove ffmpeg x264 libx264-dev libmp3lame-dev libvpx-dev
# Install yasm ubuntu 10.04 uses 0.8 need >1.0
cd && wget http://www.tortall.net/projects/yasm/releases/yasm-1.2.0.tar.gz && tar -zxvf ./yasm-1.2.0.tar.gz && cd ./yasm-1.2.0 && ./configure && make && checkinstall --pkgname=yasm --pkgversion=1.2.0 --backup=no --deldoc=yes --fstrans=no --default && cd
# Make sure the installation was successful
if [ $? -ne 0 ]
then
echo "error yasm"
exit 1
else
sudo rm -frv ./yasm-1.2.0
fi
# Install x264
cd && git clone git://git.videolan.org/x264 && cd x264 && ./configure --enable-static && make && sudo checkinstall --pkgname=x264 --pkgversion="3:$(./#version.sh | awk -F'[" "]' '/POINT/{print $4"+git"$5}')" --backup=no --deldoc=yes --fstrans=no --default && cd
# Make sure the installation was successful
if [ $? -ne 0 ]
then
echo "error x264"
exit 1
fi
# Install lame
cd && wget http://downloads.sourceforge.net/project/lame/lame/3.99/lame-3.99.5.tar.gz && tar xzvf lame-3.99.5.tar.gz && cd ./lame-3.99.5 && sudo ./configure --enable-nasm --disable-shared && sudo make && sudo checkinstall --pkgname=lame-ffmpeg --pkgversion="3.99.5" --backup=no --deldoc=yes --install=yes --fstrans=no --default && cd
# Make sure the installation was successful
if [ $? -ne 0 ]
then
echo "error lame-ffmpeg"
exit 1
else
sudo rm -frv ./lame-3.99.5
fi
# Install opencore amr
cd && wget http://downloads.sourceforge.net/project/opencore-amr/opencore-amr/opencore-amr-0.1.3.tar.gz && tar -zxvf opencore-amr-0.1.3.tar.gz && cd ./opencore-amr-0.1.3 && sudo ./configure --disable-shared && sudo make && sudo checkinstall --pkgname="libopencore-amr" --pkgversion="0.1.3" --backup=no --fstrans=no --install=yes --default && cd
# Make sure the installation was successful
if [ $? -ne 0 ]
then
echo "error opencore"
exit 1
else
sudo rm -frv ./opencore-amr-0.1.3
fi
# Install theora
cd && wget http://downloads.xiph.org/releases/theora/libtheora-1.1.1.tar.gz && tar xzvf libtheora-1.1.1.tar.gz && cd ./libtheora-1.1.1 && sudo ./configure --disable-shared && sudo make && sudo checkinstall --pkgname=libtheora --pkgversion "1.1.1" --backup=no --fstrans=no --install=yes --default && cd
# Make sure the installation was successful
if [ $? -ne 0 ]
then
echo "error theora"
exit 1
else
sudo rm -frv ./libtheora-1.1.1
fi
# Install libvpx-dev
cd && git clone http://git.chromium.org/webm/libvpx.git && cd ./libvpx && ./configure && make && sudo checkinstall --pkgname=libvpx --pkgversion="1:$(date +%Y%m%d%H%M)-git" --backup=no --deldoc=yes --fstrans=no --default && cd
# Make sure the installation was successful
if [ $? -ne 0 ]
then
echo "error libvpx"
exit 1
else
sudo rm -frv ./libvpx
fi
# Install ffmpeg
cd && git clone --depth 1 git://source.ffmpeg.org/ffmpeg && cd ffmpeg && ./configure --enable-libvpx --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-nonfree --enable-version3 --enable-x11grab --enable-version3 --enable-postproc --enable-libxvid && make && sudo checkinstall --pkgname=ffmpeg --pkgversion="5:$(date +%Y%m%d%H%M)-git" --backup=no --deldoc=yes --fstrans=no --default && cd
# Make sure the installation was successful
if [ $? -ne 0 ]
then
echo "error ffmpeg"
exit 1
fi
# Install qt-faststart
cd ~/ffmpeg && make tools/qt-faststart && sudo checkinstall --pkgname=qt-faststart --pkgversion="$(date +%Y%m%d%H%M)-git" --backup=no --deldoc=yes --fstrans=no --default install -Dm755 tools/qt-faststart /usr/local/bin/qt-faststart && cd
# Make sure the installation was successful
if [ $? -ne 0 ]
then
echo "error faststart"
exit 1
fi
# re-install x264
cd ~/x264 && make distclean && ./configure --enable-static && make && sudo checkinstall --pkgname=x264 --pkgversion="3:$(./version.sh | awk -F'[" "]' '/POINT/{print $4"+git"$5}')" --backup=no --deldoc=yes --fstrans=no --default && cd
# Make sure the installation was successful
if [ $? -ne 0 ]
then
echo "error x264"
exit 1
else
sudo rm -frv ./x264
sudo rm -frv ./ffmpeg
fi
# Make sure nothing gets replaced
hash x264 ffmpeg ffplay
echo "ffmpeg hold" | sudo dpkg --set-selections
echo "x264 hold" | sudo dpkg --set-selections
echo "lame-ffmpeg hold" | sudo dpkg --set-selections
echo "libopencore-amr hold" | sudo dpkg --set-selections
echo "libtheora hold" | sudo dpkg --set-selections
# Update and install the good stuff
# This is all the stuff that I use on my rigs and that I like having enabled
# A lot to dig through, but you should only install what you need / use
sudo apt-get -y install ubuntu-restricted-extras mencoder mplayer vlc arista avidemux gettext debian-keyring konqueror-nsplugins msttcorefonts ttf-xfree86-nonfree xfs g++-multilib g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg git-doc git-arch git-cvs git-svn git-email git-daemon-run git-gui gitk gitweb equivs libasound2-doc nas debhelper fakeroot libfftw3-dev libggi-target-emu libggi-target-monotext libggimisc2 jackd liblrdf0-dev libqt4-dev sidplay-base xsidplay libstdc++6-4.3-doc lynx-cur-wrapper mplayer-doc ladspa-sdk diff-doc subversion-tools db4.6-util latex2html libmyodbc odbc-postgresql mozilla-plugin-vlc videolan-doc cryptsetup k3b gparted devede linux-generic linux-headers-generic linux-image-generic compiz compiz-plugins compiz-gnome compiz-core emerald compiz-fusion-plugins-main compiz-fusion-plugins-extra fusion-icon compizconfig-settings-manager msttcorefonts reiser4progs libdvdcss2 openssh-server ssh wine vsftpd unixodbc debconf java-common locales gsfonts-x11 flashplugin-nonfree dkms ps3mediaserver libwxbase2.8-dev libcurl4-gnutls-dev liblua5.1-curl-dev ubufox transmission-cli libcurl3 libcurl3-gnutls lm-sensors stress pi rcconf computertemp sensors-applet tightvncserver acpidump gimp
# Install sun-java6-jre
cd && wget http://mirror.pnl.gov/ubuntu//pool/multiverse/s/sun-java6/sun-java6-bin_6.24-1build0.8.04.1_amd64.deb && dpkg -i ./sun-java6-bin_6.24-1build0.8.04.1_amd64.deb
# Make sure the installation was successful
if [ $? -ne 0 ]
then
echo "error sun-java6-bin"
exit 1
else
sudo rm ./sun-java6-bin_6.24-1build0.8.04.1_amd64.deb
fi
cd && wget http://mirror.pnl.gov/ubuntu//pool/multiverse/s/sun-java6/sun-java6-jre_6.24-1build0.8.04.1_all.deb && dpkg -i sun-java6-jre_6.24-1build0.8.04.1_all.deb
# Make sure the installation was successful
if [ $? -ne 0 ]
then
echo "error sun-java6-jre"
exit 1
else
sudo rm ./sun-java6-jre_6.24-1build0.8.04.1_all.deb
fi
# Install VirtualBox
sudo apt-get -y install virtualbox-4.1
cd && wget http://download.virtualbox.org/virtualbox/4.1.12/Oracle_VM_VirtualBox_Extension_Pack-4.1.12-77245.vbox-extpack
# Final update and clean up
sudo apt-get -y update && sudo apt-get -y upgrade && sudo apt-get -y clean && sudo apt-get -y autoremove
# Update boot files/images
sudo update-initramfs -u ALL && sudo update-grub

```

---

### Post by doru001 on 2012-04-20
**FakeOutdoorsman: ** On this page [http://ubuntuforums.org/showpost.php?p=9868359&postcount=1289](http://ubuntuforums.org/showpost.php?p=9868359&postcount=1289) you use a "hash" command which I can not find in any package. Please tell me what to do about it.

---

### Post by doru001 on 2012-04-21
I followed the instructions on this page: [http://ubuntuforums.org/showpost.php?p=9868359&postcount=1289](http://ubuntuforums.org/showpost.php?p=9868359&postcount=1289) and now ffmpeg can use the amr codec:```
ffmpeg -i file.amr file.wav
```works. In the new version, use: 
```

ffmpeg -codecs
and not 
ffmpeg -formats
```
to display available codecs. 

I wish to thank everybody who posted here and especially **FakeOutdoorsman** who helped me understand basic usage of ffmpeg. I also thank **ron999** and **mc4man** who encouraged me to compile ffmpeg from source. Compilation took over 3 hours on my slow unicore computer.

---

### Post by FakeOutdoorsman on 2012-04-21
> **doru001 said:**
> **FakeOutdoorsman: ** On this page [http://ubuntuforums.org/showpost.php?p=9868359&postcount=1289](http://ubuntuforums.org/showpost.php?p=9868359&postcount=1289) you use a "hash" command which I can not find in any package. Please tell me what to do about it.

*hash* is included in Ubuntu by default

---

### Post by doru001 on 2012-04-21
> **FakeOutdoorsman said:**
> *hash* is included in Ubuntu by default

It is a builtin! That's why I did not find it. What does it mean that the command is remembered? Now this is a transparent command. 

Is Lucid missing from this [list]("http://ubuntuforums.org/showthread.php?t=1117283") under [SIZE="3"]**[COLOR="Brown"]C. Medibuntu[/COLOR]**[/SIZE] with a reason? I mean, could I use Medibuntu? After I uninstall packages I could reinstall them by issuing the checkinstall command only, without compiling again, I suspect. 

So there is no simple way to find out the origin repository of a package from apt-cache show, for example.

---

### Post by FakeOutdoorsman on 2012-04-21
> **doru001 said:**
> It is a builtin! That's why I did not find it. What does it mean that the command is remembered? Now this is a transparent command.
The hash command is only needed when the repository version of ffmpeg is used and then removed, and then the compiled version of ffmpeg is compiled, installed, and used all within the same session. Otherwise you may receive an error that the new ffmpeg can't be found. I added it to the guide as a preventative measure.

> **doru001 said:**
> Is Lucid missing from this [list]("http://ubuntuforums.org/showthread.php?t=1117283") under [SIZE="3"]**[COLOR="Brown"]C. Medibuntu[/COLOR]**[/SIZE] with a reason?
Perhaps I don't understand the question. Lucid is listed under option **C. Medibuntu**.

> **doru001 said:**
> So there is no simple way to find out the origin repository of a package from apt-cache show, for example.

```
dpkg -s libavcodec-extra-53
```

---

### Post by doru001 on 2012-04-22
> **FakeOutdoorsman said:**
> The hash command is only needed when the repository version of ffmpeg is used and then removed, and then the compiled version of ffmpeg is compiled, installed, and used all within the same session. Otherwise you may receive an error that the new ffmpeg can't be found. I added it to the guide as a preventative measure.

Right, it should be a bash optimization. 

> **FakeOutdoorsman said:**
> Perhaps I don't understand the question. Lucid is listed under option **C. Medibuntu**.

I apologize. Again, my fault, I did not see it at the end of the line. 
 
So this should make ffmpeg work for amr even though amr is not listed among codecs (and also it is not listed among compile options, if I remember correctly) for the Lucid Ubuntu repository version of ffmpeg. If this is correct, and if you tell me that I won't have to recompile the compiled version of ffmpeg (I still have all files resulted from installation) in order to reinstall it with checkinstall if the medibuntu version fails, then I will give it a try and install from medibuntu. This method may have advantages, like simplicity and speed. 

> **FakeOutdoorsman said:**
> ```
dpkg -s libavcodec-extra-53
```

On my system: 
```

**$ dpkg -s libavcodec-extra-52**
Package: libavcodec-extra-52
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 10916
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: ffmpeg-extra
Version: 4:0.5.1-1ubuntu1.3
Replaces: ffmpeg (<< 4:0.5.1-1), libavcodec-unstripped-52 (<< 4:0.5.1-1ubuntu1.3), libavcodec52
Depends: libavutil-extra-49 (>= 4:0.5.1), libavutil-extra-49 (<< 4:0.5.1-99), libc6 (>= 2.7), libdirac-encoder0, libfaad2, libgsm1 (>= 1.0.13), libmp3lame0, libopenjpeg2, libschroedinger-1.0-0 (>= 1.0.0), libspeex1 (>= 1.2~beta3-1), libtheora0 (>= 0.0.0.alpha7.dfsg), libvorbis0a (>= 1.1.2), libvorbisenc2 (>= 1.1.2), libx264-85, libxvidcore4 (>= 1.2.2), zlib1g (>= 1:1.1.4)
Suggests: libfaad0
Conflicts: libavcodec-unstripped-52 (<< 4:0.5.1-1ubuntu1.3), libavcodec52
Description: ffmpeg codec library
 This is the codec library from the ffmpeg project. It supports most existing
 encoding formats (MPEG, DivX, MPEG4, AC3, DV...).
 .
 This package contains a unrestricted version of the libavcodec shared
 object that should only be used by Debian packages.
Homepage: http://ffmpeg.org/
Original-Maintainer: Debian multimedia packages maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>
**$ dpkg -s libavcodec-extra-52 | grep -i medibuntu**
**$ dpkg -l | grep libavcodec-extra-52**
ii  libavcodec-extra-52                        4:0.5.1-1ubuntu1.3                              ffmpeg codec library

```Probably I installed it during the period when the medibuntu repository was added to my sources.list.d directory. However, medibuntu is not mentioned by dpkg -s output.

---

### Post by FakeOutdoorsman on 2012-04-22
> **doru001 said:**
> So this should make ffmpeg work for amr even though amr is not listed among codecs
If you install libavcodec-extra-52 from Medibuntu then AMR will be listed under the Codecs section of *ffmpeg -formats*. If you install libavcodec-extra-52 or libavcodec52 from the Ubuntu repository then AMR will not be listed under the Codecs section of *ffmpeg -formats*.

Using libavcodec-extra-52 from Ubuntu repo:
```
$ ffmpeg -formats 2>&1 | grep -i amr
 DE amr             3GPP AMR file format
```
 
Using libavcodec-extra-52 from Medibuntu repo:
```
 $ ffmpeg -formats 2>&1 | grep -i amr
 DE amr             3GPP AMR file format
 DEA    libopencore_amrnb OpenCORE Adaptive Multi-Rate (AMR) Narrow-Band
 D A    libopencore_amrwb OpenCORE Adaptive Multi-Rate (AMR) Wide-Band
```
Ignore the "3GPP AMR file format" line as it is referring to the format, not the decoder.

So, once again, either install libavcodec-extra-52 from Medibuntu or compile FFmpeg to gain AMR decoding support.

> **doru001 said:**
> I won't have to recompile the compiled version of ffmpeg (I still have all files resulted from installation)
Reinstalling your compiled ffmpeg is easy:
```
cd ~/ffmpeg
dpkg -i ffmpeg_5:N-37676-gdd7198b-1_amd64.deb
```
Of course your ffmpeg_5:N-37676-gdd7198b-1_amd64.deb will have a different version and Git hash (those numbers and letters that you can ignore).

> **doru001 said:**
> On my system: 
```

**$ dpkg -s libavcodec-extra-52**
Package: libavcodec-extra-52
...
Version: 4:0.5.1-1ubuntu1.3

```
You appear to be using libavcodec-extra-52 from the Ubuntu repository that does not support AMR decoding. The Medibuntu version output look like:
```
$ dpkg -s libavcodec-extra-52
Package: libavcodec-extra-52
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 5624
Maintainer: Medibuntu Packaging Team <medibuntu-maintainers@lists.launchpad.net>
Architecture: amd64
Source: ffmpeg-extra
Version: 4:0.5.1-1ubuntu1.3+medibuntu1
...
```

---

### Post by doru001 on 2012-04-23
> **FakeOutdoorsman said:**
> Reinstalling your compiled ffmpeg is easy:
```
cd ~/ffmpeg
dpkg -i ffmpeg_5:N-37676-gdd7198b-1_amd64.deb
```
So I can let checkinstall packages other than ffmpeg installed. 
> **FakeOutdoorsman said:**
> You appear to be using libavcodec-extra-52 from the Ubuntu repository that does not support AMR decoding.
So after I add medibuntu in my sources.list.d I should run: 
```
sudo apt-get remove ffmpeg
sudo apt-get install ffmpeg libavcodec-extra-52=4:0.5.1-1ubuntu1.3+medibuntu1
```
to get the right packages? 

Please tell me whether the compilation and the medibuntu instructions from Lucid apply to Precise. 

Thank you for your good info on these complicated issues.

---

### Post by doru001 on 2012-04-24
To sum up: 

There are two versions of ffmpeg available for every Ubuntu release. 

  **I.** One is from Ubuntu repositories. This one is incomplete, it does not know of many formats because of copyright issues. You can complete it if you [add Medibuntu]("https://help.ubuntu.com/community/Medibuntu#Adding_the_Repository") among your repositories and then [install required packages]("http://ubuntuforums.org/showthread.php?t=1117283") from there (see [COLOR="Sienna"][COLOR="DarkOrange"]**C. Medibuntu**[/COLOR][/COLOR]). Complete packages in Medibuntu have identical names with incomplete packages in Ubuntu. However, complete packages in Medibuntu take precedence over packages in Ubuntu, such that ```
sudo apt-get update
sudo apt-get upgrade
```should provide you with the complete packages if you have the incomplete packages installed already. The origin of the package is listed in the Version and Maintainer records of the package information: ```
$dpkg -s libavcodec-extra-52
Package: libavcodec-extra-52
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 10924
Maintainer: Medibuntu Packaging Team <medibuntu-maintainers@lists.launchpad.net>
Architecture: i386
Source: ffmpeg-extra
Version: 4:0.5.1-1ubuntu1.3+medibuntu1
``` **Lucid** included, ```
ffmpeg -formats
``` lists available codecs under **Codec** heading. Later versions may switch to ```
ffmpeg -codecs
```, which is less confusing for newcomers. There are no instructions for **Precise**, but packages with similar names are available in the Medibuntu repository, and instructions for **Oneiric** may apply for **Precise**, too. 

  **II.** Another is [compiled]("http://ubuntuforums.org/showthread.php?t=786095") from source on your machine. Compilation takes a long time and it is not clear yet that the guide works for **Precise**. Compilation offers you the very last update of ffmpeg. The compiled version of ffmpeg does not require additional codec packages from Ubuntu or Medibuntu. Use ```
ffmpeg -codecs
``` to list available codecs.

---

