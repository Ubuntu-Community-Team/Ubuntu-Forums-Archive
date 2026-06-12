---
title: "Ripping MP3's From CD's?"
date: 2007-10-10
forum: Multimedia &amp; Video
---

### Post by CarlosinFL on 2007-10-10
OK - I have Sound Juicer installed and am able to extract CD's as OGG but now I need MP3 and I see that when I "edit profiles", there is already a MP3 profile enabled and has the correct settings to use LAME and everything. I made sure my 7.10 Beta has LAME installed however it is not an option to extract from for some strange reason and I don't understand why...? i did make sure the enabled box was checked and I made sure the extension is MP3 and all that stuff.

Here is when I installed LAME.

```
cwilliams@tunafish:~$ sudo apt-get install gstreamer0.10-plugins-bad-multiverse
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libavcodec1d libavutil1d libfaac0 libfaad2-0 libgsm1 libmjpegtools0c2a libmp4v2-0 libquicktime1 libx264-54 libxvidcore4
The following NEW packages will be installed:
  gstreamer0.10-plugins-bad-multiverse libavcodec1d libavutil1d libfaac0 libfaad2-0 libgsm1 libmjpegtools0c2a libmp4v2-0 libquicktime1 libx264-54 libxvidcore4
0 upgraded, 11 newly installed, 0 to remove and 7 not upgraded.
Need to get 3334kB of archives.
After unpacking 9253kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com gutsy/multiverse libmp4v2-0 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu5 [233kB]
Get:2 http://us.archive.ubuntu.com gutsy/multiverse libfaac0 1.24clean-0ubuntu4 [55.2kB]
Get:3 http://us.archive.ubuntu.com gutsy/multiverse libfaad2-0 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu5 [202kB]
Get:4 http://us.archive.ubuntu.com gutsy/main libavutil1d 3:0.cvs20070307-5ubuntu4 [39.5kB]
Get:5 http://us.archive.ubuntu.com gutsy/main libgsm1 1.0.10-13build1 [30.1kB]
Get:6 http://us.archive.ubuntu.com gutsy/main libavcodec1d 3:0.cvs20070307-5ubuntu4 [1611kB]
Get:7 http://us.archive.ubuntu.com gutsy/universe libquicktime1 2:1.0.0+debian-4ubuntu1 [430kB]
Get:8 http://us.archive.ubuntu.com gutsy/multiverse libmjpegtools0c2a 1:1.8.0-0.2ubuntu5 [219kB]
Get:9 http://us.archive.ubuntu.com gutsy/multiverse libx264-54 1:0.svn20070309-4ubuntu1 [211kB]                                                                     
Get:10 http://us.archive.ubuntu.com gutsy/multiverse libxvidcore4 2:1.1.2-0.1ubuntu2 [210kB]                                                                        
Get:11 http://us.archive.ubuntu.com gutsy/multiverse gstreamer0.10-plugins-bad-multiverse 0.10.5-1 [94.0kB]                                                         
Fetched 3334kB in 7s (424kB/s)                                                                                                                                      
Selecting previously deselected package libmp4v2-0.
(Reading database ... 88909 files and directories currently installed.)
Unpacking libmp4v2-0 (from .../libmp4v2-0_2.0.0+cvs20040908+mp4v2+bmp-0ubuntu5_i386.deb) ...
Selecting previously deselected package libfaac0.
Unpacking libfaac0 (from .../libfaac0_1.24clean-0ubuntu4_i386.deb) ...
Selecting previously deselected package libfaad2-0.
Unpacking libfaad2-0 (from .../libfaad2-0_2.0.0+cvs20040908+mp4v2+bmp-0ubuntu5_i386.deb) ...
Selecting previously deselected package libavutil1d.
Unpacking libavutil1d (from .../libavutil1d_3%3a0.cvs20070307-5ubuntu4_i386.deb) ...
Selecting previously deselected package libgsm1.
Unpacking libgsm1 (from .../libgsm1_1.0.10-13build1_i386.deb) ...
Selecting previously deselected package libavcodec1d.
Unpacking libavcodec1d (from .../libavcodec1d_3%3a0.cvs20070307-5ubuntu4_i386.deb) ...
Selecting previously deselected package libquicktime1.
Unpacking libquicktime1 (from .../libquicktime1_2%3a1.0.0+debian-4ubuntu1_i386.deb) ...
Selecting previously deselected package libmjpegtools0c2a.
Unpacking libmjpegtools0c2a (from .../libmjpegtools0c2a_1%3a1.8.0-0.2ubuntu5_i386.deb) ...
Selecting previously deselected package libx264-54.
Unpacking libx264-54 (from .../libx264-54_1%3a0.svn20070309-4ubuntu1_i386.deb) ...
Selecting previously deselected package libxvidcore4.
Unpacking libxvidcore4 (from .../libxvidcore4_2%3a1.1.2-0.1ubuntu2_i386.deb) ...
Selecting previously deselected package gstreamer0.10-plugins-bad-multiverse.
Unpacking gstreamer0.10-plugins-bad-multiverse (from .../gstreamer0.10-plugins-bad-multiverse_0.10.5-1_i386.deb) ...
Setting up libmp4v2-0 (2.0.0+cvs20040908+mp4v2+bmp-0ubuntu5) ...

Setting up libfaac0 (1.24clean-0ubuntu4) ...

Setting up libfaad2-0 (2.0.0+cvs20040908+mp4v2+bmp-0ubuntu5) ...

Setting up libavutil1d (3:0.cvs20070307-5ubuntu4) ...

Setting up libgsm1 (1.0.10-13build1) ...

Setting up libavcodec1d (3:0.cvs20070307-5ubuntu4) ...

Setting up libquicktime1 (2:1.0.0+debian-4ubuntu1) ...

Setting up libmjpegtools0c2a (1:1.8.0-0.2ubuntu5) ...

Setting up libx264-54 (1:0.svn20070309-4ubuntu1) ...

Setting up libxvidcore4 (2:1.1.2-0.1ubuntu2) ...

Setting up gstreamer0.10-plugins-bad-multiverse (0.10.5-1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```

---

### Post by nzadLithium on 2007-10-10
do 

sudo apt-get install gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-tools libglib2.0-0 liblame0

i'm pretty sure its one of those packages but i cant remember which. two of them are probably already installed but i can't remeber which ones they are.

after you done that you should be able to extract to mp3

---

