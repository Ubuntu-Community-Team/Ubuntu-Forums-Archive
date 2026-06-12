---
title: "Program to split long .flv files into multiple .flv files"
date: 2009-11-17
forum: Multimedia Software
---

### Post by toupeiro on 2009-11-17
Hi,

I have a handfull of almost 2 hour flv files that I want to split off into multiple individual flv files, or find some way to marker them so that if I were to burn them to a DVD that these could be TOC pointers.  I'm more inclined to split them off because then its easier to make them DVD chapters.

Any suggestions on which program may do this the best for linux?

EDIT:  major correction.  I am actually trying to split **.mkv** files.  Oversight on my part, I apologise.  If a moderator happens to see this, if they could make the changes to the subject line, that would be very appreciated!

---

### Post by KeLa on 2009-11-17
Have you try to google it?
This is what i found from google:
[http://www.bunkus.org/videotools/mkvtoolnix/](http://www.bunkus.org/videotools/mkvtoolnix/)

---

### Post by toupeiro on 2009-11-17
> **KeLa said:**
> Have you try to google it?
This is what i found from google:
[http://www.bunkus.org/videotools/mkvtoolnix/](http://www.bunkus.org/videotools/mkvtoolnix/)

I did google it.  And, I did install mkvtoolnix.  Its a good way to edit mkv files and turn other source into mkv, but it doesn't seem to have any way to get them to DVD unfortunately.. :(

I also tried using devede but apparently this is very broken in ubuntu karmic right now..

> sudo apt-get install devede
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dvdauthor imagemagick libavcodec-extra-52 libavformat-extra-52 libavutil-extra-49 libiso9660-5 libopenjpeg2
  libpostproc-extra-51 libsvga1 libswscale-extra-0 libvcdinfo0 mencoder mplayer-nogui vcdimager
Suggested packages:
  transfig imagemagick-doc mplayer-doc netselect fping
The following NEW packages will be installed:
  devede dvdauthor imagemagick libavcodec-extra-52 libavformat-extra-52 libavutil-extra-49 libiso9660-5 libopenjpeg2
  libpostproc-extra-51 libsvga1 libswscale-extra-0 libvcdinfo0 mencoder mplayer-nogui vcdimager
0 upgraded, 15 newly installed, 0 to remove and 0 not upgraded.
Need to get 9,610kB of archives.
After this operation, 22.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse libavutil-extra-49 4:0.5+svn20090706-2ubuntu3 [68.9kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe libopenjpeg2 1.3+dfsg-4 [81.2kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse libavcodec-extra-52 4:0.5+svn20090706-2ubuntu3 [2,202kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse libavformat-extra-52 4:0.5+svn20090706-2ubuntu3 [367kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse libpostproc-extra-51 4:0.5+svn20090706-2ubuntu3 [57.2kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe libsvga1 1:1.4.3-27ubuntu1 [306kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse libswscale-extra-0 4:0.5+svn20090706-2ubuntu3 [118kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse mplayer-nogui 2:1.0~rc3+svn20090426-1ubuntu10 [2,115kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse mencoder 2:1.0~rc3+svn20090426-1ubuntu10 [1,639kB]                 
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe dvdauthor 0.6.14-3ubuntu4 [200kB]                                   
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe libiso9660-5 0.78.2+dfsg1-3 [113kB]                                 
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe libvcdinfo0 0.7.23-4ubuntu1 [133kB]                                 
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe vcdimager 0.7.23-4ubuntu1 [559kB]                                   
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main imagemagick 7:6.5.1.0-1.1ubuntu3 [95.7kB]                               
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse devede 3.14.0-0ubuntu5 [1,555kB]                                  
Fetched 9,610kB in 9s (1,002kB/s)                                                                                       
Selecting previously deselected package libavutil-extra-49.
(Reading database ... 319109 files and directories currently installed.)
Unpacking libavutil-extra-49 (from .../libavutil-extra-49_4%3a0.5+svn20090706-2ubuntu3_amd64.deb) ...
Selecting previously deselected package libopenjpeg2.
Unpacking libopenjpeg2 (from .../libopenjpeg2_1.3+dfsg-4_amd64.deb) ...
Selecting previously deselected package libavcodec-extra-52.
Unpacking libavcodec-extra-52 (from .../libavcodec-extra-52_4%3a0.5+svn20090706-2ubuntu3_amd64.deb) ...
Selecting previously deselected package libavformat-extra-52.
Unpacking libavformat-extra-52 (from .../libavformat-extra-52_4%3a0.5+svn20090706-2ubuntu3_amd64.deb) ...
Selecting previously deselected package libpostproc-extra-51.
Unpacking libpostproc-extra-51 (from .../libpostproc-extra-51_4%3a0.5+svn20090706-2ubuntu3_amd64.deb) ...
Selecting previously deselected package libsvga1.
Unpacking libsvga1 (from .../libsvga1_1%3a1.4.3-27ubuntu1_amd64.deb) ...
Selecting previously deselected package libswscale-extra-0.
Unpacking libswscale-extra-0 (from .../libswscale-extra-0_4%3a0.5+svn20090706-2ubuntu3_amd64.deb) ...
Selecting previously deselected package mplayer-nogui.
Unpacking mplayer-nogui (from .../mplayer-nogui_2%3a1.0~rc3+svn20090426-1ubuntu10_amd64.deb) ...
Selecting previously deselected package mencoder.
Unpacking mencoder (from .../mencoder_2%3a1.0~rc3+svn20090426-1ubuntu10_amd64.deb) ...
Selecting previously deselected package dvdauthor.
Unpacking dvdauthor (from .../dvdauthor_0.6.14-3ubuntu4_amd64.deb) ...
Selecting previously deselected package libiso9660-5.
Unpacking libiso9660-5 (from .../libiso9660-5_0.78.2+dfsg1-3_amd64.deb) ...
Selecting previously deselected package libvcdinfo0.
Unpacking libvcdinfo0 (from .../libvcdinfo0_0.7.23-4ubuntu1_amd64.deb) ...
Selecting previously deselected package vcdimager.
Unpacking vcdimager (from .../vcdimager_0.7.23-4ubuntu1_amd64.deb) ...
Selecting previously deselected package imagemagick.
Unpacking imagemagick (from .../imagemagick_7%3a6.5.1.0-1.1ubuntu3_amd64.deb) ...
Selecting previously deselected package devede.
Unpacking devede (from .../devede_3.14.0-0ubuntu5_all.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
install-info: warning: no info dir entry in `/usr/share/info/menu.info.gz'
Processing triggers for menu ...
Processing triggers for desktop-file-utils ...
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Setting up libavutil-extra-49 (4:0.5+svn20090706-2ubuntu3) ...

Setting up libopenjpeg2 (1.3+dfsg-4) ...

Setting up libavcodec-extra-52 (4:0.5+svn20090706-2ubuntu3) ...

Setting up libavformat-extra-52 (4:0.5+svn20090706-2ubuntu3) ...

Setting up libpostproc-extra-51 (4:0.5+svn20090706-2ubuntu3) ...

Setting up libsvga1 (1:1.4.3-27ubuntu1) ...

Setting up libswscale-extra-0 (4:0.5+svn20090706-2ubuntu3) ...

Setting up mplayer-nogui (2:1.0~rc3+svn20090426-1ubuntu10) ...

Setting up mencoder (2:1.0~rc3+svn20090426-1ubuntu10) ...
Setting up dvdauthor (0.6.14-3ubuntu4) ...
Setting up libiso9660-5 (0.78.2+dfsg1-3) ...

Setting up libvcdinfo0 (0.7.23-4ubuntu1) ...

Setting up vcdimager (0.7.23-4ubuntu1) ...
Ignoring install-info called from maintainer script
The package vcdimager should be rebuild with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package vcdimager should be rebuild with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package vcdimager should be rebuild with new debhelper to get trigger support

Setting up imagemagick (7:6.5.1.0-1.1ubuntu3) ...

Setting up devede (3.14.0-0ubuntu5) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
toupeiro@mobius:/usr/local$ devede
DeVeDe 3.14.0
Locale: en_US.UTF-8
Using package-installed files
/home/toupeiro/
Entro en fonts
Salgo de fonts
/home/toupeiro/
Temp Directory is:  /var/tmp
home load:  /home/toupeiro/.devede
linea:  video_format:pal

linea:  temp_folder:/var/tmp/

linea:  multicore:1


Basically, devede comes up and it cannot find mencoder or mplayer, although they were just installed from official repos.  They are there in fact, but I get the following errors:

> mencoder: symbol lookup error: mencoder: undefined symbol: codec_wav_tags
mplayer: symbol lookup error: mplayer: undefined symbol: codec_wav_tags



So, anything using mencoder to do the dirty work is going to be broke I think until its fixed.  Further googling has traces of this problem, but they were all from other repos.  I am able to reproduce it from the official ones though.  Might follow up on the bug reports with that info.

---

### Post by andrew.46 on 2009-11-17
Hi toupeiro,

I am not sure if this is what you are after but mvkvmerge gui has the ability to split output files with several different options. I attach a screenshot to demonstrate the option.

All the best,

Andrew

---

### Post by toupeiro on 2009-11-17
> **andrew.46 said:**
> Hi toupeiro,

I am not sure if this is what you are after but mvkvmerge gui has the ability to split output files with several different options. I attach a screenshot to demonstrate the option.

All the best,

Andrew

Ah.. ok I see. hmmmm  So One thing I noticed after getting the tool is that my co-worker that made the mkv file already setup chapters exactly where I would want to put them. Is there a way to split on the chaptering thats already encoded in the file or do I need to figure out how to string the time codes in?  I guess that would get them split, I tried k3b, but so far I haven't found anything that will accept this format to burn to dvd.  any ideas?

Thanks Andrew!

---

### Post by andrew.46 on 2009-11-17
Hi toupeiro,

> **toupeiro said:**
> Ah.. ok I see. hmmmm  So One thing I noticed after getting the tool is that my co-worker that made the mkv file already setup chapters exactly where I would want to put them. Is there a way to split on the chaptering thats already encoded in the file or do I need to figure out how to string the time codes in? 

Looks like to the right of the 'Global' tab there is a 'Chapter Editor' where I guess you could add and subtract chapters from your input file to produce several output files. I confess I have never used this feature so you may have to experiment a little :).

Andrew

---

### Post by toupeiro on 2009-11-17
> **andrew.46 said:**
> Hi toupeiro,



Looks like to the right of the 'Global' tab there is a 'Chapter Editor' where I guess you could add and subtract chapters from your input file to produce several output files. I confess I have never used this feature so you may have to experiment a little :).

Andrew

This worked like a champion!  Thanks Andrew.

As far as the burning issue, I was able to get things working by pulling doing a subversion pull for mplayer/mencoder and installing devede from source.  This is going to let me do the chapters I wanted to do with the split mkv files!

I appreciate the help!

---

### Post by andrew.46 on 2009-11-17
Hi toupeiro,

> **toupeiro said:**
> I appreciate the help!

Well I owe you some thanks for making me look at a feature of this fine program I have really not investigated before :).

Andrew

---

