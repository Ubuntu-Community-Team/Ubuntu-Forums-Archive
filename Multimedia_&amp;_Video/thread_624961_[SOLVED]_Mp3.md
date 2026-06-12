---
title: "[SOLVED] Mp3"
date: 2007-11-27
forum: Multimedia &amp; Video
---

### Post by diwas on 2007-11-27
Can anyone please help me how can i play .mp3 files in Ubuntu 7.10? 
My computer is permanently offline in Ubuntu. 
Please give me something or the other..please...im dyin...
thank you.

---

### Post by Yellow Pasque on 2007-11-27
You need the ubuntu-restricted-extras package.
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by diwas on 2007-11-28
Well thank you for the reply...but i cannot run the internet in my ubuntu...will it work without the internet?

---

### Post by mattroy89 on 2007-11-28
I also need help playing mp3's. But I do have an internet connection.

---

### Post by diwas on 2007-11-28
dude...wats the problem wid u man? just search for codecs in the internet and u have the mp3 buzzin in ur system.

---

### Post by Yellow Pasque on 2007-11-28
You can download the package ([http://packages.ubuntu.com](http://packages.ubuntu.com)) on another computer that does have internet access and transfer it over.

You can probably also get it off the CD, so make sure your CD-ROM is enabled in Software Sources, put the CD in, and then look in Synaptic Package Manager.

---

### Post by Lord DarkPat on 2007-11-28
I think u can do it directly in ur Media PLayer. I use Kubuntu, and Amarok(the media player) installs it automatically. It asks u first though. I dunno abt GNOME. Sorry if I wasn't of any help. It might be on the CD.

---

### Post by diwas on 2007-11-29
Hey there...i checked out the package's site for the restricted extras...but soon found out that i has too many dependencies...when i wanted to download the dependency files i found out that there are dependency files for that file...
do i have to manually download all the files?? damn this is freakin me out.
plz help guys.

---

### Post by Yellow Pasque on 2007-11-29
> **diwas said:**
> Hey there...i checked out the package's site for the restricted extras...but soon found out that i has too many dependencies...when i wanted to download the dependency files i found out that there are dependency files for that file...
do i have to manually download all the files?? damn this is freakin me out.
plz help guys.

If they're not currently installed (use synaptic to see this), then yes, you do need to download the packages listed as dependencies. Did you try getting them off the install CD as I suggested?

You could also try Linux Mint, which is a lot like Ubuntu, but without the idealistic haughtiness and aversion to proprietary formats/software.

---

### Post by koleoptero on 2007-11-29
You can download just the gstreamer plugins.

gstreamer 0.10 plugins bad
gstreamer 0.10 plugins ugly
gstreamer 0.10 plugins ffmpeg

with these you'll be able to play any file.

---

### Post by aysiu on 2007-11-29
Honestly, if you want proprietary format support and have no internet connection, you're better off installing Linux Mint.

Otherwise, once you get MP3 sorted out, you'll then have to download individual .deb packages for Java and for DVD playback... etc.

---

### Post by diwas on 2007-11-29
Yes i tried the cd but it isnt workin...i installed all the remaining files but it still cannot play mp3 files.
Where can i find these gstreamer files?? Will these files dont have any dependency problems?

---

### Post by aysiu on 2007-11-29
> **diwas said:**
> Yes i tried the cd but it isnt workin...i installed all the remaining files but it still cannot play mp3 files.
Where can i find these gstreamer files?? Will these files dont have any dependency problems?
No, they'll all have dependency problems, which is why you should install Linux Mint instead of Ubuntu.

---

### Post by diwas on 2007-11-29
[http://gstreamer.freedesktop.org/src/gst-plugins-bad/](http://gstreamer.freedesktop.org/src/gst-plugins-bad/) 
look at this link...there are so many files around here...do i have to dwnld all of them?

---

### Post by diwas on 2007-11-29
hey aysiu...cant i get a complete package which has no dependency problem?? or can anyone make package like dat?? 
plzzzz tell me............

---

### Post by aysiu on 2007-11-29
> **diwas said:**
> hey aysiu...cant i get a complete package which has no dependency problem?? or can anyone make package like dat?? 
plzzzz tell me............
No.

Ubuntu is designed to work with an internet connection for software installation.

If I were a programmer, I'd make a Windows version of *apt-get* to fetch dependencies, but I'm not a programmer.

If you have an internet connection *somewhere* (obviously not in Ubuntu), please take the time to download Linux Mint. It'll save you a lot of headaches down the road.

---

### Post by koleoptero on 2007-11-29
Indeed trying to manually install all the packages with their dependencies is a waste of time for you. If linux mint has all the codecs by default then install it. It will save you much time and effort.

---

### Post by ruibernardo on 2007-11-29
diwas, if you don't want to make a new install, I'll post here the links of the dependencies and the packages files you need. 

To do that, send me a PM with the file "/var/lib/dpkg/status". I'll post here the links of the dependencies and packages to install "ubuntu-restricted-extras", "gstreamer0.10-plugins-bad", "gstreamer0.10-plugins-ugly", "gstreamer0.10-plugins-ffmpeg" and any other packages you want.

---

### Post by aysiu on 2007-11-29
You can find all the dependencies here:
[http://packages.ubuntu.com](http://packages.ubuntu.com)

It's just annoying to follow the dependency tree and download each and every one to transfer over.

---

### Post by SnuffThePunk on 2007-11-29
Is it that you can't get your network working in Ubutnu? Try System > Administration > Networking.

---

### Post by diwas on 2007-11-30
Okay...i cannot download Linux Mint coz im usin a very very slow internet connection of 28.8kbps...so in that speed its impossible to download the while operating system, isnt it?
And since iam usin dial up modem i dont know why...it cannot be configured in my ubuntu system...its the only problem iam facing with ubuntu. Oh yeah i have searched all the how to's about dial up modem...i even have my own thread abt my problem but it doesnt seem like ubuntu is ever detect and run the modem...ok this is too out of topic...

Yesterday...i was completely in mood to download all the dependecies and all the required program files....but...the dependecies had their own dependencies and it had their own......so damn frustratin...

What i have in my ubuntu system is all that which comes with the cd distributed by canonical company free of cost. But i will pm u with the file you specified. Your help will really help me..hehe i think you got what i mean.

---

### Post by ruibernardo on 2007-12-01
From your status file and the details you gave me, here are the packages and dependencies you don't have and you need to install the following packages: **gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-ffmpeg jackd w32codecs**.

The links to the packages and the dependencies you don't have:

[http://packages.medibuntu.org/pool/free/f/ffmpeg/libavutil1d_0.cvs20070307-5ubuntu4+medibuntu2_i386.deb ]("http://packages.medibuntu.org/pool/free/f/ffmpeg/libavutil1d_0.cvs20070307-5ubuntu4+medibuntu2_i386.deb")[http://packages.medibuntu.org/pool/free/f/ffmpeg/libavcodec1d_0.cvs20070307-5ubuntu4+medibuntu2_i386.deb ]("http://packages.medibuntu.org/pool/free/f/ffmpeg/libavcodec1d_0.cvs20070307-5ubuntu4+medibuntu2_i386.deb")[http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu1_i386.deb ]("http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu1_i386.deb")[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.3/gcc-3.3-base_3.3.6-15ubuntu2_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.3/gcc-3.3-base_3.3.6-15ubuntu2_i386.deb")[http://archive.ubuntu.com/ubuntu/pool/universe/g/gstreamer0.10-ffmpeg/gstreamer0.10-ffmpeg_0.10.2-2ubuntu1_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/universe/g/gstreamer0.10-ffmpeg/gstreamer0.10-ffmpeg_0.10.2-2ubuntu1_i386.deb")[http://archive.ubuntu.com/ubuntu/pool/universe/libc/libcdaudio/libcdaudio1_0.99.12p2-3_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/universe/libc/libcdaudio/libcdaudio1_0.99.12p2-3_i386.deb")[http://archive.ubuntu.com/ubuntu/pool/main/libg/libgsm/libgsm1_1.0.10-13build1_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/main/libg/libgsm/libgsm1_1.0.10-13build1_i386.deb")[http://archive.ubuntu.com/ubuntu/pool/universe/libf/libfreebob/libfreebob0_1.0.3+svn443-2_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/universe/libf/libfreebob/libfreebob0_1.0.3+svn443-2_i386.deb")[http://archive.ubuntu.com/ubuntu/pool/universe/j/jack-audio-connection-kit/libjack0_0.103.0-6ubuntu1_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/universe/j/jack-audio-connection-kit/libjack0_0.103.0-6ubuntu1_i386.deb")[http://archive.ubuntu.com/ubuntu/pool/universe/libm/libmms/libmms0_0.3-5ubuntu2_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/universe/libm/libmms/libmms0_0.3-5ubuntu2_i386.deb")[http://archive.ubuntu.com/ubuntu/pool/main/libm/libmpcdec/libmpcdec3_1.2.2-1build1_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/main/libm/libmpcdec/libmpcdec3_1.2.2-1build1_i386.deb")[http://archive.ubuntu.com/ubuntu/pool/universe/libo/libopenspc/libopenspc0_0.3.99a-2_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/universe/libo/libopenspc/libopenspc0_0.3.99a-2_i386.deb")[http://archive.ubuntu.com/ubuntu/pool/universe/s/soundtouch/libsoundtouch1c2_1.3.0-2.1_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/universe/s/soundtouch/libsoundtouch1c2_1.3.0-2.1_i386.deb")[http://archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-bad0.10/gstreamer0.10-plugins-bad_0.10.5-4ubuntu1_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-bad0.10/gstreamer0.10-plugins-bad_0.10.5-4ubuntu1_i386.deb")[http://archive.ubuntu.com/ubuntu/pool/multiverse/f/faad2/libmp4v2-0_2.0.0+cvs20040908+mp4v2+bmp-0ubuntu5_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/multiverse/f/faad2/libmp4v2-0_2.0.0+cvs20040908+mp4v2+bmp-0ubuntu5_i386.deb")[http://archive.ubuntu.com/ubuntu/pool/multiverse/f/faac/libfaac0_1.24clean-0ubuntu4_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/multiverse/f/faac/libfaac0_1.24clean-0ubuntu4_i386.deb")[http://archive.ubuntu.com/ubuntu/pool/multiverse/f/faad2/libfaad2-0_2.0.0+cvs20040908+mp4v2+bmp-0ubuntu5_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/multiverse/f/faad2/libfaad2-0_2.0.0+cvs20040908+mp4v2+bmp-0ubuntu5_i386.deb")[http://archive.ubuntu.com/ubuntu/pool/multiverse/l/lame/liblame0_3.97-0.0_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/multiverse/l/lame/liblame0_3.97-0.0_i386.deb")[http://archive.ubuntu.com/ubuntu/pool/multiverse/x/x264/libx264-54_0.svn20070309-4ubuntu1_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/multiverse/x/x264/libx264-54_0.svn20070309-4ubuntu1_i386.deb")[http://archive.ubuntu.com/ubuntu/pool/multiverse/x/xvidcore/libxvidcore4_1.1.2-0.1ubuntu2_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/multiverse/x/xvidcore/libxvidcore4_1.1.2-0.1ubuntu2_i386.deb")[http://archive.ubuntu.com/ubuntu/pool/universe/libq/libquicktime/libquicktime1_1.0.0+debian-4ubuntu1_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/universe/libq/libquicktime/libquicktime1_1.0.0+debian-4ubuntu1_i386.deb")[http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mjpegtools/libmjpegtools0c2a_1.8.0-0.2ubuntu5_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/multiverse/m/mjpegtools/libmjpegtools0c2a_1.8.0-0.2ubuntu5_i386.deb")[http://archive.ubuntu.com/ubuntu/pool/multiverse/g/gst-plugins-bad-multiverse0.10/gstreamer0.10-plugins-bad-multiverse_0.10.5-1_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/multiverse/g/gst-plugins-bad-multiverse0.10/gstreamer0.10-plugins-bad-multiverse_0.10.5-1_i386.deb")[http://archive.ubuntu.com/ubuntu/pool/universe/a/a52dec/liba52-0.7.4_0.7.4-11_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/universe/a/a52dec/liba52-0.7.4_0.7.4-11_i386.deb")[http://archive.ubuntu.com/ubuntu/pool/universe/libd/libdvdread/libdvdread3_0.9.7-3ubuntu1_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/universe/libd/libdvdread/libdvdread3_0.9.7-3ubuntu1_i386.deb")[http://archive.ubuntu.com/ubuntu/pool/main/libi/libid3tag/libid3tag0_0.15.1b-10_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/main/libi/libid3tag/libid3tag0_0.15.1b-10_i386.deb")[http://archive.ubuntu.com/ubuntu/pool/main/libm/libmad/libmad0_0.15.1b-2.1ubuntu1_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/main/libm/libmad/libmad0_0.15.1b-2.1ubuntu1_i386.deb")[http://archive.ubuntu.com/ubuntu/pool/universe/m/mpeg2dec/libmpeg2-4_0.4.1-1_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/universe/m/mpeg2dec/libmpeg2-4_0.4.1-1_i386.deb")[http://archive.ubuntu.com/ubuntu/pool/universe/libs/libsidplay/libsidplay1_1.36.59-4_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/universe/libs/libsidplay/libsidplay1_1.36.59-4_i386.deb")[http://archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-ugly0.10/gstreamer0.10-plugins-ugly_0.10.6-0ubuntu2_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-ugly0.10/gstreamer0.10-plugins-ugly_0.10.6-0ubuntu2_i386.deb")[http://archive.ubuntu.com/ubuntu/pool/multiverse/g/gst-plugins-ugly-multiverse0.10/gstreamer0.10-plugins-ugly-multiverse_0.10.6-0ubuntu1_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/multiverse/g/gst-plugins-ugly-multiverse0.10/gstreamer0.10-plugins-ugly-multiverse_0.10.6-0ubuntu1_i386.deb")[http://archive.ubuntu.com/ubuntu/pool/universe/j/jack-audio-connection-kit/jackd_0.103.0-6ubuntu1_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/universe/j/jack-audio-connection-kit/jackd_0.103.0-6ubuntu1_i386.deb")[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.3/libstdc++5_3.3.6-15ubuntu2_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.3/libstdc++5_3.3.6-15ubuntu2_i386.deb")

Save them on a directory in the offline computer and type on a terminal:

```
sudo dpkg -i *
sudo apt-get install -f

```I would have included "ubuntu-restriced-extras", but that package installs java6 also, but when it does it makes another download from Suns website. To have java, I advise you to download directly from their website.

To read DVDs you need to install libdvdread3:

[http://archive.ubuntu.com/ubuntu/pool/universe/libd/libdvdread/libdvdread3_0.9.7-3ubuntu1_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/universe/libd/libdvdread/libdvdread3_0.9.7-3ubuntu1_i386.deb")

I'm not sure if this package doesn't do another download as java6, so try it and then say if it worked.

Please reply if you had any problem.

---

