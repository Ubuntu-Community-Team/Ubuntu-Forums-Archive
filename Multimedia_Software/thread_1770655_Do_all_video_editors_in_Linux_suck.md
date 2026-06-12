---
title: "Do all video editors in Linux suck?"
date: 2011-05-29
forum: Multimedia Software
---

### Post by brad1138 on 2011-05-29
I have been trying to do some fairly basic video editing and basically every different editor I try either does not work, or crashes. I have tried Open video editor, Kino, Kdelive, Pitivi, Blender, and a few others I have deleted and cant remember.

Blender crashes when I click on open file. Pitivi, Kdelive, (and a few others) crash when you are in the middle of your project. Open Video editor won't let you see what you are doing, make some edits and click play to see how they look and it doesn't do anything. Kino had problems, but I can't remember what now.

My machine is stable, I do everything else (non-video editing) w/o any problems. This is really frustrating, I could boot into Windows XP and do it from there, but I like Ubuntu, and hate to feel like I *need* to go to XP/Windows.

---

### Post by BlouBlou on 2011-05-29
There is a good video editor called "Cinelerra ( [http://cinelerra.org/](http://cinelerra.org/) )" which works fine, and has very advanced stuffs.

---

### Post by sanderd17 on 2011-05-29
All those crashes, that sounds like you don't have enough memory or that the driver of your graphical card is poor. I never had problems with pitivi or KDElive, in any case not crashes, I didn't try others.

---

### Post by Simian Man on 2011-05-29
I've had Kdenlive crash before, but not nearly every time I use it or anything.  Is it always when you try to do the same thing or just randomly?

---

### Post by ghostborg on 2011-05-29
Openshot

---

### Post by cotcot on 2011-05-29
Seems to be something else than the editors themselve. (as mentioned by a previous post).
Do you have the required codecs installed (see info [[COLOR="Red"]here[/COLOR]]("https://help.ubuntu.com/community/RestrictedFormats"))?
I work for years with blender. It is OK.

---

### Post by brad1138 on 2011-05-29
I don't think the computer is the problem. Athlon 64 3200+ w/2 GB memory. That isn't real fast, but should be fast enough. I have a Nvidia 7600GS videocard w/256 MB mem and the proper drivers.

---

### Post by brad1138 on 2011-05-30
> **BlouBlou said:**
> There is a good video editor called "Cinelerra ( [http://cinelerra.org/](http://cinelerra.org/) )" which works fine, and has very advanced stuffs.

I tried that, look at this screen capt. Why is my preview (upper right) narrow like that, it is a 4x3 video. Also there is no sound when playing the preview window.

[IMG]http://i544.photobucket.com/albums/hh359/brad3d/Screenshot-3.png[/IMG]

---

### Post by brad1138 on 2011-05-30
AARGH!

[IMG]http://i544.photobucket.com/albums/hh359/brad3d/Screenshot-1-1.png[/IMG]

I tried Avidemux and it did the same thing. The screen shot shows it being played and looking normal on the left and then being shown in the editor about 1/2 as wide as it should be.

This is %#^@'n ridiculous.

Brad

---

### Post by inobe on 2011-05-30
where are you importing from, what is the file format and original aspect ratio?

---

### Post by Regele IONESCU on 2011-05-30
> **brad1138 said:**
> I tried that, look at this screen capt. Why is my preview (upper right) narrow like that, it is a 4x3 video. Also there is no sound when playing the preview window.

[IMG]http://i544.photobucket.com/albums/hh359/brad3d/Screenshot-3.png[/IMG]

Perhaps you are using HDV footage(1440*1080) or a wide format(either PAL or NTSC). The solution is to go to project settings and choose the correct pixel aspect ratio or change the image aspect ratio.

Good luck!
Christian.

P.S: blender is a very good video editor but you need at least basic editing knowledge.

---

### Post by brad1138 on 2011-05-30
> **inobe said:**
> where are you importing from, what is the file format and original aspect ratio?


This is a 640x480 mpg that my father created of old 8mms. I opened it in "Open Movie Editor" again and it displays it properly. I did notice that Avidemux listed it as a "352x480" video. Don't know where it is getting that, but apparently cinelerra is getting that also.

---

### Post by someitalian123 on 2011-05-30
DVDs can be encoded with a 352x480 resolution, when you play them on a normal dvd player or a computer the displayed aspect ration is 4:3. People use this for analogue to digital transfers since the actual resolution of vhs is about 300x480 interlaced.

---

### Post by configt on 2011-06-05
Where is the "delete post" option?

---

### Post by configt on 2011-06-05
Sorry to say this, but yes.  All Linux GUI video editors do suck so, so badly.

What is your source format, do you have the right codecs, enough memory, blah blah blah.

I am running an extremely beefy system upon which Ubuntu is doing everything I need, such as, for example, running multiple web sites, 12 zoneminder camera's, VPN hosting for multiple clients, VPN client, and much, much more, 24x7x365 with no problem at all.

HOWEVER, when it comes to the most absolute BASIC of video editing, compilation, etc., it absolutely fails on every frontier.  I have 7 video editor packages installed on my system and NONE of them can do anything useful at all when it comes to multiple video and audio sources.  

Prove me wrong.

---

### Post by rosenkavalier on 2011-06-05
I agree with all the rants above. The best video editor, cinerella, doesn't seem to support x264 videos. And AFAIK only cinerella and LiVES have the audio recording feature... (LiVES failed to build on kernel 2.6.38)

I guess a voiceover studio has to rely on Windows for a while...

---

### Post by kelvin spratt on 2011-06-05
I use all the editors + cinerella with no problems at all i,m processing as I write this.
1st thing ram is not your problem unless you are using vbox, graphics card does that's what does all the work when processing video, I do nothing but edit music and video on Linux 250mb of ram on a graphics card is pathetic for video editing 500mb is just adequate 1gb is preferable. with cinelerra you may need to use avidemux to convert the sound 1st then use cinelerra, a good build of cinelerra works a treat they use it to edit for films, I don't use Ubuntu any more and when i did I spent a long time getting it to work  use arch and the version in the repro works a treat. if its simple sticking vids together with no editing you can use devede, set up your preferences use video preview to get the size you can then make a dvd or divx write to file or iso.

---

### Post by andrew.46 on 2011-06-07
> **configt said:**
> Prove me wrong.

Well I don't actually have the proof, more of a question :). Has aybody tried the newish video editor from the Videolan people:

VLMC
[http://www.videolan.org/vlmc/](http://www.videolan.org/vlmc/)

Not sure where they are up to with actual release versions...

---

### Post by blackbird34 on 2011-06-07
TRY OPENSHOT. Someone suggested this already. Its developing fast, got lots of good reviews in the Software Center. I had one look at it and worked out how i could do really easy video. I think. There are'nt very many others that seem to have nasty  surprises, they just haven't heard of it.

---

### Post by DrPotoroo on 2011-06-07
> **configt said:**
> Sorry to say this, but yes.  All Linux GUI video editors do suck so, so badly.

Actually, cinelerra is really very good. Quite buggy, but very good. If you don't know what you're doing you'll be frustrated with it. And it does take some mucking around to handle some file types. But if you take some time to learn some details about video editing you can do far better with cinelerra than most of your free or OEM windows options. Just make sure to change nearest neighbour scaling to bicubic/bilinear in the options. It's there as a playback option, but actually impacts on final render quality.

---

### Post by UncleAlan on 2011-08-31
I installed kdenlive 0.8 on  10.04 & 11.04 pcs.  It works on 11.04  and did on 10.04 for a day then crashed. Now it opens up the sections full screen width and crashes if I try to resize.  It really is totally unusable on this pc now. I have tried uninstalling and doing a cold reboot and reinstalling and it was still a mess.  This is a TOTAL disaster on this pc which is a shame as it showed such promise. It is SO disappointing and I nearly went back to Windows Movie Maker - that works but I want to use Ubuntu......maybe I need to see a specialist!!!

Unk.

---

### Post by PayPaul on 2011-10-06
I've been trying VLMC, VideoLan Movie Creator. I can't seem to make the clipping work on this .mov file. If the filetype was wrong for this program why isn't there any documentation on that fact? It also doesn't have any visible way to see the project preview. VLMC has an effects menue but there's also no apparent method for using those effects. What sucks most of all is the lack of documentation on this and some other open source programs like Pitivi, which is pitiful. See screenshot below of VLMC.

---

### Post by PayPaul on 2011-10-06
> **BlouBlou said:**
> There is a good video editor called "Cinelerra ( [http://cinelerra.org/](http://cinelerra.org/) )" which works fine, and has very advanced stuffs.

I do love it how this is only available through source code. Oh, and they say it may need some "tweaking". Here's what they admit about it:

[COLOR=Red]"[/COLOR][FONT=HELVETICA][FONT=HELVETICA][FONT=HELVETICA][FONT=HELVETICA][COLOR=Red]Downloads have no support or warranty and are not community approved.  Linux derivatives have become so unstable, don't be surprised if your compiler is incompatible & the source code requires some tweeks."[/COLOR]

[/FONT][/FONT][/FONT][/FONT]Yuck!

I haven't had much luck with building from source code. My experience has been with programs that are either old, buggy or always have some dependencies that need to be searched for. Can someone provide me with a step by step instruction on installing this. I see also that it is a non-supported program so I anticipate some error message about it being harmful.

Update: Went through the instructions both provided by the README file and in the terminal. This is what occured:

```
paulw@ubuntu:~/Cinerella Video Editor/cinelerra-4.3$ ./cinelerra
bash: ./cinelerra: Is a directory
paulw@ubuntu:~/Cinerella Video Editor/cinelerra-4.3$ r ./cinelerra
The program 'r' is currently not installed.  You can install it by typing:
sudo apt-get install littler
paulw@ubuntu:~/Cinerella Video Editor/cinelerra-4.3$ sudo apt-get install littler[sudo] password for paulw: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libkresources4 libkldap4 kipi-plugins libksane0 kipi-plugins-common libkipi8
  libmarblewidget11 libakonadi-kmime4 libgps19 libakonadiprotocolinternals1 libkexiv2-9
  mysql-server-core-5.1 digikam-data marble-plugins libqjson0 akonadi-server libmicroblog4
  libkabc4 mysql-client-core-5.1 kdegraphics-libs-data libkcal4 libkimap4
  libmailtransport4 libkmime4 kdepimlibs-kio-plugins libakonadi-kabc4 libkpimutils4
  marble-data kdepim-runtime libakonadi-kcal4 libkdcraw9 libakonadi-kde4
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dpatch gfortran gfortran-4.5 libblas-dev libbz2-dev libjpeg62-dev liblapack-dev
  libncurses5-dev libpcre3-dev libpcrecpp0 libpng12-dev libreadline-dev libreadline6-dev
  patchutils r-base-core r-base-dev r-cran-boot r-cran-class r-cran-cluster
  r-cran-codetools r-cran-foreign r-cran-kernsmooth r-cran-lattice r-cran-mass
  r-cran-matrix r-cran-mgcv r-cran-nlme r-cran-nnet r-cran-rpart r-cran-spatial
  r-cran-survival r-doc-html r-recommended
Suggested packages:
  curl gfortran-multilib gfortran-doc gfortran-4.5-multilib gfortran-4.5-doc
  libgfortran3-dbg ncurses-doc r-cran-getopt ess r-doc-info r-doc-pdf r-mathlib
  r-base-html cdbs debhelper
The following NEW packages will be installed:
  dpatch gfortran gfortran-4.5 libblas-dev libbz2-dev libjpeg62-dev liblapack-dev
  libncurses5-dev libpcre3-dev libpcrecpp0 libpng12-dev libreadline-dev libreadline6-dev
  littler patchutils r-base-core r-base-dev r-cran-boot r-cran-class r-cran-cluster
  r-cran-codetools r-cran-foreign r-cran-kernsmooth r-cran-lattice r-cran-mass
  r-cran-matrix r-cran-mgcv r-cran-nlme r-cran-nnet r-cran-rpart r-cran-spatial
  r-cran-survival r-doc-html r-recommended
0 upgraded, 34 newly installed, 0 to remove and 26 not upgraded.
Need to get 37.7 MB of archives.
After this operation, 84.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ natty/main libpcrecpp0 amd64 8.12-3ubuntu2 [37.7 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ natty/main dpatch all 2.0.31 [88.4 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ natty/main gfortran-4.5 amd64 4.5.2-8ubuntu4 [5,271 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ natty/main gfortran amd64 4:4.5.2-1ubuntu3 [1,206 B]
Get:5 http://us.archive.ubuntu.com/ubuntu/ natty/main libblas-dev amd64 1.2-8 [263 kB]     
Get:6 http://us.archive.ubuntu.com/ubuntu/ natty/main libbz2-dev amd64 1.0.5-6ubuntu1 [33.4 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ natty/main libjpeg62-dev amd64 6b1-1ubuntu1 [195 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ natty/main liblapack-dev amd64 3.3.0-3 [4,953 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ natty/main libncurses5-dev amd64 5.7+20101128-1 [330 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ natty/main libpcre3-dev amd64 8.12-3ubuntu2 [233 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ natty-updates/main libpng12-dev amd64 1.2.44-1ubuntu3.1 [220 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ natty/main libreadline6-dev amd64 6.2-0ubuntu1 [264 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ natty/main libreadline-dev amd64 6.2-0ubuntu1 [908 B]
Get:14 http://us.archive.ubuntu.com/ubuntu/ natty/universe r-base-core amd64 2.12.1-1 [14.1 MB]
Get:15 http://us.archive.ubuntu.com/ubuntu/ natty/universe littler amd64 0.1.3-1 [32.9 kB] 
Get:16 http://us.archive.ubuntu.com/ubuntu/ natty/main patchutils amd64 0.3.1-2build1 [108 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu/ natty/universe r-base-dev all 2.12.1-1 [3,544 B]
Get:18 http://us.archive.ubuntu.com/ubuntu/ natty/universe r-cran-boot all 1.2.43-1 [442 kB]
Get:19 http://us.archive.ubuntu.com/ubuntu/ natty/universe r-cran-mass amd64 7.3-9-1 [799 kB]
Get:20 http://us.archive.ubuntu.com/ubuntu/ natty/universe r-cran-class amd64 7.3-3-1 [66.1 kB]
Get:21 http://us.archive.ubuntu.com/ubuntu/ natty/universe r-cran-cluster amd64 1.13.2-1 [343 kB]
Get:22 http://us.archive.ubuntu.com/ubuntu/ natty/universe r-cran-codetools all 0.2-6-1 [42.7 kB]
Get:23 http://us.archive.ubuntu.com/ubuntu/ natty/universe r-cran-foreign amd64 0.8.41-1 [156 kB]
Get:24 http://us.archive.ubuntu.com/ubuntu/ natty/universe r-cran-kernsmooth amd64 2.23-4-1 [60.0 kB]
Get:25 http://us.archive.ubuntu.com/ubuntu/ natty/universe r-cran-lattice amd64 0.19-13-1 [687 kB]
Get:26 http://us.archive.ubuntu.com/ubuntu/ natty/universe r-cran-matrix amd64 0.999375-46-1 [3,069 kB]
Get:27 http://us.archive.ubuntu.com/ubuntu/ natty/universe r-cran-nlme amd64 3.1.97-1 [1,604 kB]
Get:28 http://us.archive.ubuntu.com/ubuntu/ natty/universe r-cran-mgcv amd64 1.7-2-1 [815 kB]
Get:29 http://us.archive.ubuntu.com/ubuntu/ natty/universe r-cran-nnet amd64 7.3-1-1 [62.2 kB]
Get:30 http://us.archive.ubuntu.com/ubuntu/ natty/universe r-cran-survival amd64 2.36-2-1 [2,582 kB]
Get:31 http://us.archive.ubuntu.com/ubuntu/ natty/universe r-cran-rpart amd64 3.1.48-1 [163 kB]
Get:32 http://us.archive.ubuntu.com/ubuntu/ natty/universe r-cran-spatial amd64 7.3-2-1 [103 kB]
Get:33 http://us.archive.ubuntu.com/ubuntu/ natty/universe r-doc-html all 2.12.1-1 [571 kB]
Get:34 http://us.archive.ubuntu.com/ubuntu/ natty/universe r-recommended all 2.12.1-1 [2,712 B]
Fetched 37.7 MB in 40s (937 kB/s)                                                          
Extracting templates from packages: 100%
Selecting previously deselected package libpcrecpp0.
(Reading database ... 194068 files and directories currently installed.)
Unpacking libpcrecpp0 (from .../libpcrecpp0_8.12-3ubuntu2_amd64.deb) ...
Selecting previously deselected package dpatch.
Unpacking dpatch (from .../archives/dpatch_2.0.31_all.deb) ...
Selecting previously deselected package gfortran-4.5.
Unpacking gfortran-4.5 (from .../gfortran-4.5_4.5.2-8ubuntu4_amd64.deb) ...
Selecting previously deselected package gfortran.
Unpacking gfortran (from .../gfortran_4%3a4.5.2-1ubuntu3_amd64.deb) ...
Selecting previously deselected package libblas-dev.
Unpacking libblas-dev (from .../libblas-dev_1.2-8_amd64.deb) ...
Selecting previously deselected package libbz2-dev.
Unpacking libbz2-dev (from .../libbz2-dev_1.0.5-6ubuntu1_amd64.deb) ...
Selecting previously deselected package libjpeg62-dev.
Unpacking libjpeg62-dev (from .../libjpeg62-dev_6b1-1ubuntu1_amd64.deb) ...
Selecting previously deselected package liblapack-dev.
Unpacking liblapack-dev (from .../liblapack-dev_3.3.0-3_amd64.deb) ...
Selecting previously deselected package libncurses5-dev.
Unpacking libncurses5-dev (from .../libncurses5-dev_5.7+20101128-1_amd64.deb) ...
Selecting previously deselected package libpcre3-dev.
Unpacking libpcre3-dev (from .../libpcre3-dev_8.12-3ubuntu2_amd64.deb) ...
Selecting previously deselected package libpng12-dev.
Unpacking libpng12-dev (from .../libpng12-dev_1.2.44-1ubuntu3.1_amd64.deb) ...
Selecting previously deselected package libreadline6-dev.
Unpacking libreadline6-dev (from .../libreadline6-dev_6.2-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libreadline-dev.
Unpacking libreadline-dev (from .../libreadline-dev_6.2-0ubuntu1_amd64.deb) ...
Selecting previously deselected package r-base-core.
Unpacking r-base-core (from .../r-base-core_2.12.1-1_amd64.deb) ...
Selecting previously deselected package littler.
Unpacking littler (from .../littler_0.1.3-1_amd64.deb) ...
Selecting previously deselected package patchutils.
Unpacking patchutils (from .../patchutils_0.3.1-2build1_amd64.deb) ...
Selecting previously deselected package r-base-dev.
Unpacking r-base-dev (from .../r-base-dev_2.12.1-1_all.deb) ...
Selecting previously deselected package r-cran-boot.
Unpacking r-cran-boot (from .../r-cran-boot_1.2.43-1_all.deb) ...
Selecting previously deselected package r-cran-mass.
Unpacking r-cran-mass (from .../r-cran-mass_7.3-9-1_amd64.deb) ...
Selecting previously deselected package r-cran-class.
Unpacking r-cran-class (from .../r-cran-class_7.3-3-1_amd64.deb) ...
Selecting previously deselected package r-cran-cluster.
Unpacking r-cran-cluster (from .../r-cran-cluster_1.13.2-1_amd64.deb) ...
Selecting previously deselected package r-cran-codetools.
Unpacking r-cran-codetools (from .../r-cran-codetools_0.2-6-1_all.deb) ...
Selecting previously deselected package r-cran-foreign.
Unpacking r-cran-foreign (from .../r-cran-foreign_0.8.41-1_amd64.deb) ...
Selecting previously deselected package r-cran-kernsmooth.
Unpacking r-cran-kernsmooth (from .../r-cran-kernsmooth_2.23-4-1_amd64.deb) ...
Selecting previously deselected package r-cran-lattice.
Unpacking r-cran-lattice (from .../r-cran-lattice_0.19-13-1_amd64.deb) ...
Selecting previously deselected package r-cran-matrix.
Unpacking r-cran-matrix (from .../r-cran-matrix_0.999375-46-1_amd64.deb) ...
Selecting previously deselected package r-cran-nlme.
Unpacking r-cran-nlme (from .../r-cran-nlme_3.1.97-1_amd64.deb) ...
Selecting previously deselected package r-cran-mgcv.
Unpacking r-cran-mgcv (from .../r-cran-mgcv_1.7-2-1_amd64.deb) ...
Selecting previously deselected package r-cran-nnet.
Unpacking r-cran-nnet (from .../r-cran-nnet_7.3-1-1_amd64.deb) ...
Selecting previously deselected package r-cran-survival.
Unpacking r-cran-survival (from .../r-cran-survival_2.36-2-1_amd64.deb) ...
Selecting previously deselected package r-cran-rpart.
Unpacking r-cran-rpart (from .../r-cran-rpart_3.1.48-1_amd64.deb) ...
Selecting previously deselected package r-cran-spatial.
Unpacking r-cran-spatial (from .../r-cran-spatial_7.3-2-1_amd64.deb) ...
Selecting previously deselected package r-doc-html.
Unpacking r-doc-html (from .../r-doc-html_2.12.1-1_all.deb) ...
Selecting previously deselected package r-recommended.
Unpacking r-recommended (from .../r-recommended_2.12.1-1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for doc-base ...
Processing 7 added doc-base file(s)...
Registering documents with scrollkeeper...
Setting up libpcrecpp0 (8.12-3ubuntu2) ...
Setting up dpatch (2.0.31) ...
Setting up gfortran-4.5 (4.5.2-8ubuntu4) ...
Setting up gfortran (4:4.5.2-1ubuntu3) ...
update-alternatives: using /usr/bin/gfortran to provide /usr/bin/f95 (f95) in auto mode.
Setting up libblas-dev (1.2-8) ...
update-alternatives: using /usr/lib/libblas/libblas.so to provide /usr/lib/libblas.so (libblas.so) in auto mode.
Setting up libbz2-dev (1.0.5-6ubuntu1) ...
Setting up libjpeg62-dev (6b1-1ubuntu1) ...
Setting up liblapack-dev (3.3.0-3) ...
update-alternatives: using /usr/lib/lapack/liblapack.so to provide /usr/lib/liblapack.so (liblapack.so) in auto mode.
Setting up libncurses5-dev (5.7+20101128-1) ...
Setting up libpcre3-dev (8.12-3ubuntu2) ...
Setting up libpng12-dev (1.2.44-1ubuntu3.1) ...
Setting up libreadline6-dev (6.2-0ubuntu1) ...
Setting up libreadline-dev (6.2-0ubuntu1) ...
Setting up r-base-core (2.12.1-1) ...
Setting R_PAPERSIZE_USER default to 'letter'

Creating config file /etc/R/Renviron with new version
Setting up littler (0.1.3-1) ...
Setting up patchutils (0.3.1-2build1) ...
Setting up r-base-dev (2.12.1-1) ...
Setting up r-cran-boot (1.2.43-1) ...
Setting up r-cran-mass (7.3-9-1) ...
Setting up r-cran-class (7.3-3-1) ...
Setting up r-cran-cluster (1.13.2-1) ...
Setting up r-cran-codetools (0.2-6-1) ...
Setting up r-cran-foreign (0.8.41-1) ...
Setting up r-cran-kernsmooth (2.23-4-1) ...
Setting up r-cran-lattice (0.19-13-1) ...
Setting up r-cran-matrix (0.999375-46-1) ...
Setting up r-cran-nlme (3.1.97-1) ...
Setting up r-cran-mgcv (1.7-2-1) ...
Setting up r-cran-nnet (7.3-1-1) ...
Setting up r-cran-survival (2.36-2-1) ...
Setting up r-cran-rpart (3.1.48-1) ...
Setting up r-cran-spatial (7.3-2-1) ...
Setting up r-doc-html (2.12.1-1) ...
Setting up r-recommended (2.12.1-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
paulw@ubuntu:~/Cinerella Video Editor/cinelerra-4.3$ 

```

So far I don't see the program in Applications. I have no idea what it means when it says? "ldconfig deferred processing now taking place"

Maybe it will show up later today?

---

### Post by WasMeHere on 2011-10-06
> **blackbird34 said:**
> TRY OPENSHOT. Someone suggested this already. Its developing fast, got lots of good reviews in the Software Center. I had one look at it and worked out how i could do really easy video. I think. There are'nt very many others that seem to have nasty  surprises, they just haven't heard of it.
+1

For an amateur like me *OpenShot* can do what I need: editing and file conversion. I have no problems with it. And it is in the repos.

Have fun
Olle

---

### Post by chriswere9 on 2011-11-28
The short answer is yes. I've found every video in Ubuntu to be really buggy. Basically video editing is a very advanced piece of software. Incidentally I have a very fast computer and all proprietary codecs installed and they're all really buggy.

It would be nice if you could buy video editing software for linux, but I don't think you can. And if you could the encoding codecs for Ubuntu are buggy themselves.

Unfortunately as much as I love Ubuntu, when it comes to video editing I spend more time working out bugs than I do video editing. Windows and MacOS trump Ubuntu on this one.

---

### Post by gppixelworks on 2011-12-18
> **brad1138 said:**
> I have been trying to do some fairly basic video editing and basically every different editor I try either does not work, or crashes. I have tried Open video editor, Kino, Kdelive, Pitivi, Blender, and a few others I have deleted and cant remember.

I had to chuckle upon reading the subject to this thread.  I've asked myself the same for the last 3+ years.

Yes, there are some ***consumer*** style video editors available.  I've been brought up using Avid Media Composer along with FCP and Vegas.  Needless to say after cutting on several professional NLE packages, the (public) offerings in Linux don't cut it. (pun intended) ](*,)

I've been using VirtualBox to run 'proper' editing software. Had been able to run an earlier version of Avid Media Composer OK on VirtualBox but after a year or so started having problems which I think may have been due to changes in Virtualbox (I never upgraded Avid during that time).

After that I've used Sony's Vegas which runs well under VirtualBox. Currently using v10.  Don't know about v11 as I will not be upgrading due to the very soon to be released ***Lightworks***. \\:D/

The Linux (and Mac) version of [Lightworks]("http://www.lightworksbeta.com/") will be free.  Lightworks is a true professional NLE system which has been around for a couple decades.  Until the last year or so it's only been available with specific hardware.

Lightworks has had a many feature films cut with it.  'The Kings Speech' is one that I recall off hand.

In any event, I highly recommend Lightworks and it's well worth the wait until the Linux beta version is released.  Check out [the Lightworks website]("http://www.lightworksbeta.com/") for more information on a true professional NLE for Linux.  It's currently in alpha for Windows platforms (I didn't get it to run in VirtualBox).

Enjoy!

---

### Post by RedRat on 2011-12-19
I found this thread interesting and agree that virtually all the Linux editors suck big time. However, these are buggy because of the nature of people writing open source (OS) programs. Face the fact, big companies like Adobe and their video editors that are proprietary, have big programming staffs who are paid to write code. In order to sell their editors, those programs have to be very good for the average or intended user. If they ain't good, they don't sell and the company goes out of business. 

Unfortunately, too many OS programs are first conceived and then written by maybe one or a handful of programmers who do it to solve an immediate problem. Then pass it along (bugs and all) out to the open source market where it is usually given away free. When bug reports do make it back to the authors, they try to fix them as best they can but they are operating on their own time, they ain't getting paid to resolve the bug. They do it as their time and interest provides. 

Don't get me wrong, there are a lot of great OS programs out there in the Linux world. However, I have not seen too many video editing programs that are that easy to use. I ran into this when I wanted to edit some HD video I shot of my grandson. Same travails as reported here by most responders. Good Luck on finding a good program.

---

### Post by tgerbert on 2011-12-23
I'm surprised only one person thus far has made any mention of Lightworks...I'm gonna throw in my recommendation for Lightworks too.

I've played around with it a bit under Windows and am extremely impressed, and found it to be incredibly stable, though lacking support for more than a handful of codecs (some kind of legal issues there particular to the Windows alpha).

At any rate, I'm eagerly awaiting the arrival of Lightworks on the Linux platform.

---

### Post by sgtGarcia on 2011-12-25
Most of the time I use KDEnLive ( Quite good for non-pro user like Me ) & Cinelerra/Cinecutie ( mostly for testing ).  

As for Lightworks:

> **tgerbert said:**
> I'm surprised only one person thus far has made any mention of Lightworks...I'm gonna throw in my recommendation for Lightworks too.

As You see for yourself:

> **tgerbert said:**
> 
At any rate, I'm eagerly awaiting the arrival of Lightworks on the Linux platform.

Lightworks  IS NOT YET AVAILABLE for Linux. So to be precise it isn't Video Editor For Linux YET :P

> **tgerbert said:**
> 
At any rate, I'm eagerly awaiting the arrival of Lightworks on the Linux platform. 

Well, I'm waiting for it too & We are not the only one :D

---

### Post by SirWeazel on 2011-12-25
I'm surprised it took 3 pages before the mention of lightworks, but sadly it's not released yet. I was/am hoping to read a post by some lucky person who has had the chance to preview the alpha/beta build that is still not publicly released yet :(

Anyways, I'll be watching this thread because I have a talented young brother inlaw at video editing, but who is also talented at getting the latest windows virus,malware,toolbar,ect. (despite all education and preeching on what to/not do)

---

### Post by tgerbert on 2011-12-25
...just for clarification's sake, it has been released, just not for Linux. I did try running it with Wine, no luck as of yet (I haven't put too much effort into making it work, but I expect it won't work too well if at all); I haven't bothered to try a VirtualBox yet, but I'm not too sure I see much point in that (at least for me, since I've still got a Windows partition I can boot to).

> **SirWeazel said:**
> I'm surprised it took 3 pages before the mention of lightworks, but sadly it's not released yet. I was/am hoping to read a post by some lucky person who has had the chance to preview the alpha/beta build that is still not publicly released yet :(

---

### Post by aeronutt on 2011-12-25
I've been playing with Openshot, Avidemux, and Cinellera over the past few days. None of them do the basic things I need in a way I can use them. 

Cinellera: complicated, hard for me to use, and on first attempt saved a video and it was in 2 or 3 colors, orange and red.
Avidemux: windows frequently have their borders 'off' my screen. A real PIA.
Openshot: When I rotated a video, it cropped it also. Can't figure out how to not make that happen.

---

### Post by tgerbert on 2011-12-25
> **tgerbert said:**
> ...just for clarification's sake, it has been released, just not for Linux. I did try running it with Wine, no luck as of yet (I haven't put too much effort into making it work, but I expect it won't work too well if at all); I haven't bothered to try a VirtualBox yet, but I'm not too sure I see much point in that (at least for me, since I've still got a Windows partition I can boot to).

Oops...I posted to the wrong thread, disregard my above comments.

---

### Post by stuartcnz on 2012-01-01
No! **Not** all video editors in Linux Suck. You need to ask yourself two questions. First what level of video editing do I require, then secondly, what is my skill base for editing video.

If you don't have a background in video editing, you are best using a consumer grade software, such as Kino or Openshot editor. They won't do anything really flash, or even allow you that much flexibility, but they do what they do well, and are both quick and easy to learn.

If you want more scope and flexibility, then the current choices really boil down to either kdenlive or Cinelerra. My personal choice is the community version or Cinelerra, which is extremely flexible and will allow you to do some very advanced stuff, if you take the time to learn about it, but is not for beginners, as they will become frustrated with it, through lack of understanding.

Lightworks has been mentioned, though as has already been pointed out, is not yet available for Linux. Further, it looks like the open source version that will be released will be somewhat stripped down, and to get the full benefits, will require the use of numerous plugins, which will **not** be free.

So to summerize, at this stage I would recommend either Kino or Openshot for the home user. Kdenlive or Cinelerra for the more advanced user (Community version of Cinelerra being my choice). And star gazing into the future I think by far the best option for Linux will be Lumiera, though that will be quite some time away.

---

### Post by amauk on 2012-01-01
Maybe slightly off-topic, but I recently listened to a fantastic podcast about video editing on linux

[http://gnuworldorder.info/audiophile/gnuWorldOrder_7x05.ogg](http://gnuworldorder.info/audiophile/gnuWorldOrder_7x05.ogg)

---

### Post by kodec on 2012-01-17
In my opinion as an editor coming from using Avid, Premiere and Final Cut(rarely) and Vegas Pro for almost 10 years, yes they all suck (Linux progs that is). Cinelerra seems to be the most decent in terms of being able to keyframe all of the built-in effects (just no standard plugin architecture can be used). Kdenlive, OpenShot and other dedicated video editors still suck at standard features that all pro editing software has. I just got into a minor debate on the Lightworks forum about my reasoning for why the Linux and Mac OS port has been delayed. The moderator's reason of DOS code having to be ported made me laugh. Cinelerra for pro work or even Blender are the best bet. Blender and Nuke for compositing/vfx.

The perfect editing system would have.

Timeline based editor with timecode support.
Source/Project Monitor with scopes support.
Plugin system using frei0r and OpenFX API with fully "keyframeable" parameters.
Scale, Rotate, Translate and Crop, all "keyframeable".
Basic Composite math functions.
Basic color correction system (Color vectors for HMS, gamma, gain, curves).
Basic audio mixing functions.

Simple isn't it? 

I'm really tempted to get my programming and math skills up and make my own. Too many projects developed by individuals that truly don't understand the art of editing. The professional ports care too much about making bread with open source software.

My Lightworks debate:
[http://www.lightworksbeta.com/index.php?option=com_kunena&func=view&catid=21&id=17909&limit=6&limitstart=30&Itemid=269]("http://www.lightworksbeta.com/index.php?option=com_kunena&func=view&catid=21&id=17909&limit=6&limitstart=30&Itemid=269")

---

### Post by bcarlowise on 2012-01-17
> **aeronutt said:**
> I've been playing with Openshot, Avidemux, and Cinellera over the past few days. None of them do the basic things I need in a way I can use them. 

Cinellera: complicated, hard for me to use, and on first attempt saved a video and it was in 2 or 3 colors, orange and red.
Avidemux: windows frequently have their borders 'off' my screen. A real PIA.
Openshot: When I rotated a video, it cropped it also. Can't figure out how to not make that happen.

I've been using Openshot as my video editor which I find to be very easy to use and quite stable...with ONE big caveat....it crashes when exporting a video if you move the mouse (using Ubuntu 11.04 or 11.10 and Gnome3 with an ATI video card). It runs perfectly fine (no crashing) if using Unity. I also noticed the issue when rotating a video....it does not rotate the entire video including the orientation but instead only rotates the video while maintaining the landscape orientation thereby resulting in a vertical clipping (cropping) of the video. My solution was to use mencoder to rotate any videos that required rotation. I recently discovered though that AviDemux rotates videos effectively so I can start using that for my video rotation as well.

---

### Post by kjkrum on 2012-08-14
Glad to see I'm not the only one sitting here swearing at the computer.  Sorry to see it's been years and the problem remains unresolved.

Cinelerra: Interprets MP4 video recorded on a Sony Bloggie as empty sound files.

Kino: No audio playback in any format.  Tried padsp wrapper without success.

OpenShot: Playback is choppy, can't keep video and audio synced.  User interface is diabolically counter-intuitive.

LiVES: Takes several minutes just to *open* a small clip (< 1 MB).  UI sucks massively.

I'm not even looking for the "perfect" editor.  I just want one that works!

---

### Post by RedRat on 2012-08-15
> **kjkrum said:**
> Glad to see I'm not the only one sitting here swearing at the computer.  Sorry to see it's been years and the problem remains unresolved.

Cinelerra: Interprets MP4 video recorded on a Sony Bloggie as empty sound files.

Kino: No audio playback in any format.  Tried padsp wrapper without success.

OpenShot: Playback is choppy, can't keep video and audio synced.  User interface is diabolically counter-intuitive.

LiVES: Takes several minutes just to *open* a small clip (< 1 MB).  UI sucks massively.

I'm not even looking for the "perfect" editor.  I just want one that works!

My guess is that much depends on which version of Ubuntu you are using. I tried these same editors in my older 8.04LTS 32bit and had only 2Gb of memory. I agree that they all sucked big time. I have now moved on the 12.04LTS 64bit with much more memory (6Gb). I plan to try these video editors out on my new system. 

Part of the problem with this kind of software is that the technology is moving faster than the software developers (all volunteers) can update the software. A few years back, it was difficult, if not impossible,  to get HDVideo into an Ubuntu machines, now I suppose it is much better--I don't whether there is support even for BluRay. To get volunteer developers, who are not working for a salary, to improve/update/create new video software, takes some magical goal for them. Perhaps to make a name for themselves or to solve an immediate problem they might be having, some even for the curiosity or intellectual challenge to create something new. 

Keep in mind that video software developed for Windows and Mac are created by big companies for which this is a core business. They pay their developers, some rather handsomely, to make the software better. They also can afford to run test labs, e.g., Microsoft, to get an idea how users at different skill levels use existing software.

---

