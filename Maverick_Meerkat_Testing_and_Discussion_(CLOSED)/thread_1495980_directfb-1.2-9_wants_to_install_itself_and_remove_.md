---
title: "directfb-1.2-9 wants to install itself and remove numerous packages like mplayer."
date: 2010-05-28
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Starks on 2010-05-28
anyone else seeing this?

---

### Post by vikrant82 on 2010-05-28
At first, I didnt upgrade this. But I tried to act smart, and did some partial upgrades on some video codec related packages like libavcodec, libavformat, libavfilter etc .. 

And then mplayer was broken, crying something related to libavformat 

If that mess wasn't enough, I went ahead with directfb upgrade as well, which shut the doors on mplayer completely. Removed a bunch of packages like gstreamer-bad as well.

Now to downgrade it wants to remove entire kde. :(

Its a mess right now. Will wait and watch!!!

One thing is sure, mplayer is broken for sure, [COLOR="Red"]dont upgrade libav* packages if you love your mplayer[/COLOR]

---

### Post by vikrant82 on 2010-05-28
directfb-1.2-9 got added as dependency for libxine1-x, libxine1-console and libsdl1.2debian-alsa, 

May be --force-conflict(ing) all of these packages might let me eventually install mplayer, but even that is broken from a different angle. I would rather wait for mess to sort itself. 

No more partial upgrades! grr!

---

### Post by Vanishing on 2010-05-29
> **vikrant82 said:**
> At first, I didnt upgrade this. But I tried to act smart, and did some partial upgrades on some video codec related packages like libavcodec, libavformat, libavfilter etc .. 

And then mplayer was broken, crying something related to libavformat 

If that mess wasn't enough, I went ahead with directfb upgrade as well, which shut the doors on mplayer completely. Removed a bunch of packages like gstreamer-bad as well.

Now to downgrade it wants to remove entire kde. :(

Its a mess right now. Will wait and watch!!!

One thing is sure, mplayer is broken for sure, [COLOR="Red"]dont upgrade libav* packages if you love your mplayer[/COLOR]

This is what you are getting right?> mplayer: error while loading shared libraries: libavutil.so.49: cannot open shared object file: No such file or directory

---

### Post by vikrant82 on 2010-05-29
Actually, If you see carefully there are two packages related to these - libav*-extra and libav*

Looks like, the library files, are no longer there in *-extra packages. So yo can go ahead and corresponding package without the 'extra'. For e.g. libavutil49 for libavutil-extra-49 etc..

After replacing all such packages, you'll get rid of all all missing shared library error messages, but then you'll run into some error related to libavformat52.

Something on these lines - 

```
"/usr/bin/mplayer: relocation error: /usr/bin/mplayer: symbol codec_wav_tags, version LIBAVFORMAT_52 not defined in file libavformat.so.52 with link time reference"]
```

---

### Post by tghe-retford on 2010-05-29
Bug report already in place and someone is already aware of:

[https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/587163](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/587163)

---

### Post by vikrant82 on 2010-05-29
Yes, this covers directfb issue. 

What about, mplayer being broken as well, even if you get it installed somehow ? Can anyone else confirm, that mplayer is broken after upgrading libav* packages ?

---

### Post by plun on 2010-05-29
Well this is the situation now....

```
The following packages will be REMOVED:
  boxee gnome-mplayer gstreamer0.10-plugins-bad libdirectfb-1.2-0 mencoder
  mplayer mplayer-nogui smplayer smplayer-themes smplayer-translations
The following NEW packages will be installed:
  dockmanager libdirectfb-1.2-9 python-dockmanager python-mutagen zeitgeist
  zeitgeist-core zeitgeist-datahub
The following packages have been kept back:
  docky
The following packages will be upgraded:
  cpp-4.4 g++-4.4 gcc-4.4 gcc-4.4-base libdirectfb-dev libdirectfb-extra
  libnih-dbus1 libnih1 libsdl1.2-dev libsdl1.2debian
  libsdl1.2debian-pulseaudio libstdc++6-4.4-dev libxine1 libxine1-bin
  libxine1-console libxine1-ffmpeg libxine1-misc-plugins libxine1-x
18 upgraded, 7 newly installed, 10 to remove and 1 not upgraded.

```

Going to check mplayer after removal....

```
plun@plun-laptop:~$ sudo aptitude install mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  libdirectfb-1.2-9 
The following NEW packages will be installed:
  libdirectfb-1.2-0{a} mplayer 
0 packages upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 4,221kB of archives. After unpacking 8,471kB will be used.
The following packages have unmet dependencies:
  libdirectfb-1.2-9: Conflicts: libdirectfb-1.2-0 but 1.2.8-5ubuntu2 is to be installed.
The following actions will resolve these dependencies:

Remove the following packages:
chromium
chromium-bsu
ffmpeg
gimp
gstreamer0.10-plugins-bad-multiverse
libdirectfb-1.2-9
libdirectfb-dev
libdirectfb-extra
libgegl-0.0-0
libmjpegtools-1.9
libsdl-image1.2
libsdl1.2-dev
libsdl1.2debian
libsdl1.2debian-pulseaudio
libxine1
libxine1-console
libxine1-x
phonon-backend-xine
ubuntu-desktop
virtualbox-3.2
vlc

Keep the following packages at their current version:
mplayer [Not Installed]

Leave the following dependencies unresolved:
gimp-data recommends gimp
libgimp2.0 recommends gimp
ubuntu-restricted-extras recommends gstreamer0.10-plugins-bad-multiverse
Score is -12268

Accept this solution? [Y/n/q/?] 

```

---

### Post by plun on 2010-05-29
More breakage.....):P

```
The following packages will be REMOVED:
  aqualung ffmpeg gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad-multiverse
  libavcodec-dev libavdevice52 libavfilter0 libavformat-dev libavformat52
  libavutil-dev libmjpegtools-1.9 libpostproc51 libquicktime1 libswscale0
  libxine1-ffmpeg vlc vlc-nox vlc-plugin-pulse
The following packages have been kept back:
  docky
The following packages will be upgraded:
  libavcodec-extra-52 libavutil-extra-49 xserver-xorg-video-intel
3 upgraded, 0 newly installed, 18 to remove and 1 not upgraded.
Need to get 679kB of archives.
After this operation, 35.7MB disk space will be freed.
Do you want to continue [Y/n]? 

```

---

### Post by mc4man on 2010-05-29
Well you'll just need to wait for an mplayer rebuild (and probably anything else that dep's on the shared ffmpeg libs) or build yourself, most all of the build-deps are available. (everything here but vdpau which I don't use

On a positive note they finally brought ffmpeg forward from 0.5(.1) that was used in jaunty thru lucid. - using atm r23019, a considerable improvement


The issue atm with the ffmpeg extra packages is they're being built with no *.so's inc. (/usr/lib),   so they'll need to be rebuilt also.
(some small changes to rules fixed a test rebuild here

---

### Post by zika on 2010-05-30
I do not use mplayer. But, as of today, I cannot play .wmv in Totem.
libavutil50 (4.0.6)
libavutil-extra49 (4.0.6)
libavcodex-extra52 (4.0.6)
libavformat-extra52 (4.0.6)
It searches for suitable plugin and...

---

### Post by taavikko on 2010-05-30
> **zika said:**
> I do not use mplayer. But, as of today, I cannot play .wmv in Totem.
libavutil50 (4.0.6)
libavutil-extra49 (4.0.6)
libavcodex-extra52 (4.0.6)
libavformat-extra52 (4.0.6)
It searches for suitable plugin and...

[http://ubuntuforums.org/showthread.php?t=1497079](http://ubuntuforums.org/showthread.php?t=1497079)

---

### Post by zika on 2010-05-30
> **taavikko said:**
> [http://ubuntuforums.org/showthread.php?t=1497079](http://ubuntuforums.org/showthread.php?t=1497079)Thank You. I've moved my question there... :)

---

### Post by Vanishing on 2010-05-31
Not fixed yet...three days already without movies..:(

---

### Post by vikrant82 on 2010-06-03
Just got the updates. All good and shiny like before :)

---

### Post by Starks on 2010-06-03
btw. electric sheep is affected.

---

### Post by zika on 2010-06-03
> **vikrant82 said:**
> Just got the updates. All good and shiny like before :)Do You have **"plain"** or **"-extra"** libav* installed?
I have following (reinstalled them in anticipation):
```
libavutil-extra-49 (new is 50, I guess)
libavcodec-extra-52
libavdevice-extra-52
libavfilter-extra-1
libpostproc-extra-51
libavformat-extra-52
libswscale-extra-0
```and, still no luck in Totem. I see that ffmpeg-extra, containing these files is in queue...

---

### Post by ranch hand on 2010-06-03
> **Starks said:**
> btw. electric sheep is affected.
???

Say what?  I grew up around sheep, there is a lot of sheep around here.  Never saw an electric sheep.

This isn't some kind of thing for "strange" geeks is it, kind of along the lines of inflatable sheep?  I sure hope not.

---

### Post by cariboo on 2010-06-03
Have a look [here]("http://electricsheep.org/") to learn more about electric sheep. It's in the repositories. BTW the web page is horrible.

---

### Post by ranch hand on 2010-06-03
> **cariboo907 said:**
> Have a look [here]("http://electricsheep.org/") to learn more about electric sheep. It's in the repositories. BTW the web page is horrible.
Boy that is a relief.

That page is pretty bad.  Doesn't quite work right.

---

### Post by zika on 2010-06-03
> **Starks said:**
> btw. electric sheep is affected.It works OK on my machine... Nice...

---

### Post by Starks on 2010-06-03
what i meant is that synaptic wants to uninstall it.

---

### Post by vikrant82 on 2010-06-03
> **zika said:**
> Do You have **"plain"** or **"-extra"** libav* installed?
I have following (reinstalled them in anticipation):
```
libavutil-extra-49 (new is 50, I guess)
libavcodec-extra-52
libavdevice-extra-52
libavfilter-extra-1
libpostproc-extra-51
libavformat-extra-52
libswscale-extra-0
```and, still no luck in Totem. I see that ffmpeg-extra, containing these files is in queue...

```
ii  chromium-codecs-ffmpeg-extra                             0.5+svn20100602r48686+47943+48655-0ubuntu1~ucd1   Extra ffmpeg codecs for the Chromium Browser
ii  chromium-codecs-ffmpeg-nonfree                           0.5+svn20100602r48686+47943+48655-0ubuntu1~ucd1   dummy upgrade package
ii  ffmpeg                                                   4:0.6~svn20100505-1ubuntu2                        multimedia player, server and encoder
ii  gstreamer0.10-ffmpeg                                     0.10.10-1                                         FFmpeg plugin for GStreamer
ii  libavcodec52                                             4:0.6~svn20100505-1ubuntu2                        ffmpeg codec library
ii  libavdevice52                                            4:0.6~svn20100505-1ubuntu2                        ffmpeg device handling library
ii  libavfilter1                                             4:0.6~svn20100505-1ubuntu2                        ffmpeg video filtering library
ii  libavformat52                                            4:0.6~svn20100505-1ubuntu2                        ffmpeg file format library
ii  libavutil49                                              4:0.5.1-1ubuntu1                                  ffmpeg utility library
ii  libavutil50                                              4:0.6~svn20100505-1ubuntu2                        ffmpeg utility library
ii  libpostproc51                                            4:0.6~svn20100505-1ubuntu2                        ffmpeg video postprocessing library
ii  libswscale0                                              4:0.6~svn20100505-1ubuntu2                        ffmpeg video scaling library
ii  libxine1-ffmpeg                                          1.1.17-1ubuntu4                                   MPEG-related plugins for libxine1
ii  mplayer                                                  2:1.0~rc3++final-0ubuntu2                         movie player for Unix-like systems

```

```
ii  gstreamer0.10-alsa                                       0.10.29-4                                         GStreamer plugin for ALSA
ii  gstreamer0.10-ffmpeg                                     0.10.10-1                                         FFmpeg plugin for GStreamer
ii  gstreamer0.10-fluendo-mp3                                0.10.14.debian-1                                  Fluendo mp3 decoder GStreamer plugin
ii  gstreamer0.10-nice                                       0.0.12-1                                          ICE library (GStreamer plugin)
ii  gstreamer0.10-pitfdll                                    0.9.1.1+cvs20080215-1ubuntu2                      GStreamer plugin for using MS Windows binary
rc  gstreamer0.10-plugins-bad                                0.10.18-1ubuntu1                                  GStreamer plugins from the "bad" set
ii  gstreamer0.10-plugins-bad-multiverse                     0.10.18-0ubuntu1                                  GStreamer plugins from the "bad" set (Multiv
ii  gstreamer0.10-plugins-base                               0.10.29-4                                         GStreamer plugins from the "base" set
ii  gstreamer0.10-plugins-base-apps                          0.10.29-4                                         GStreamer helper programs from the "base" se
ii  gstreamer0.10-plugins-good                               0.10.23-1ubuntu1                                  GStreamer plugins from the "good" set
ii  gstreamer0.10-plugins-ugly                               0.10.14.3-1                                       GStreamer plugins from the "ugly" set
ii  gstreamer0.10-plugins-ugly-multiverse                    0.10.14-0ubuntu1                                  GStreamer plugins from the "ugly" set (Multi
ii  gstreamer0.10-pulseaudio                                 0.10.23-1ubuntu1                                  GStreamer plugin for PulseAudio
ii  gstreamer0.10-tools                                      0.10.29-1                                         Tools for use with GStreamer
ii  gstreamer0.10-x                                          0.10.29-4                                         GStreamer plugins for X11 and Pango
ii  libgstreamer-plugins-base0.10-0                          0.10.29-4                                         GStreamer libraries from the "base" set
ii  libgstreamer0.10-0                                       0.10.29-1                                         Core GStreamer libraries and elements
```

---

### Post by Vanishing on 2010-06-03
Confirm on mplayer fixed. Confirm on totem still broken. However electric sheep installs fine.:P I'm happy.

---

### Post by Starks on 2010-06-03
Is gstreamer0.10-plugins-bad still broken?

---

### Post by plun on 2010-06-03
> **Starks said:**
> Is gstreamer0.10-plugins-bad still broken?

Yep... its broken.

Also tested this package from Debian Sids repo and it seems to be a mess now with the good package fighting the bad.....Sids package can be forced to install but codecs doesn't work.

---

### Post by eris23 on 2010-06-03
With mplayer 2:1.0~rc3++final-0ubuntu2 electricsheep built from svn works, so it's not a directfb problem.

---

### Post by zika on 2010-06-06
Totem is, still, broken even though gst-{bad,good} came trhrough. It still needs H.264 decoder...

---

### Post by eris23 on 2010-06-06
Totem working after:
rm ~/.gstreamer-0.10/*
followed by
gst-inspect

---

### Post by taavikko on 2010-06-06
> **eris23 said:**
> Totem working after:
rm ~/.gstreamer-0.10/*
followed by
gst-inspect

[http://ubuntuforums.org/showpost.php?p=9419012&postcount=25](http://ubuntuforums.org/showpost.php?p=9419012&postcount=25)

---

### Post by zika on 2010-06-06
> **eris23 said:**
> Totem working after:
rm ~/.gstreamer-0.10/*
followed by
gst-inspectThis does not help in my case... I still get only sound and no image, and it asks for h.264 decoder...

Bingo! With "ordinary" libav* ([http://ubuntuforums.org/showpost.php?p=9419111&postcount=26](http://ubuntuforums.org/showpost.php?p=9419111&postcount=26)) installed and with refreshed registry it works, finally. Thank You!...

---

### Post by null_pointer_us on 2010-06-06
*chuckle*

The extra packages break h264 playback.
The ordinary packages break mp3 playback.

My media files have h264 for video and mp3 for audio, so it's still broken either way.

Ah, well, testing. VLC works for me until the updated packages are available. :popcorn:

---

### Post by zika on 2010-06-06
> **null_pointer_us said:**
> *chuckle*

The extra packages break h264 playback.
The ordinary packages break mp3 playback.

My media files have h264 for video and mp3 for audio, so it's still broken either way.

Ah, well, testing. VLC works for me until the updated packages are available. :popcorn:I've, just, tried. Both h.264 and mp3 works...
Did You try with refreshing registry file (see above)...?

---

### Post by null_pointer_us on 2010-06-06
Yes, I tried [COLOR="DarkOrange"]**rm ~/.gstreamer-0.10/registry.x86_64.bin**[/COLOR], which is the only file in that folder.

Then I ran [COLOR="DarkOrange"]**gst-inspect**[/COLOR] to regenerate the registry file above. It found 137 plugins and 976 features.

```
$ aptitude search libavcodec libavdevice libavfilter libavformat libavutil libswscale libpostproc
p   libavcodec-dev                                                                       - development files for libavcodec                                                               
i   libavcodec-extra-52                                                                  - ffmpeg codec library                                                                           
p   libavcodec-unstripped-52                                                             - ffmpeg utility library - transitional package                                                  
c   libavcodec52                                                                         - ffmpeg codec library                                                                           
p   libavdevice-dev                                                                      - development files for libavdevice                                                              
p   libavdevice-extra-52                                                                 - ffmpeg device handling library                                                                 
p   libavdevice-unstripped-52                                                            - ffmpeg utility library - transitional package                                                  
p   libavdevice52                                                                        - ffmpeg device handling library                                                                 
p   libavfilter-dev                                                                      - development files for libavfilter                                                              
p   libavfilter-extra-0                                                                  - ffmpeg video filtering library                                                                 
p   libavfilter-extra-1                                                                  - ffmpeg video filtering library                                                                 
p   libavfilter0                                                                         - ffmpeg video filtering library                                                                 
p   libavfilter1                                                                         - ffmpeg video filtering library                                                                 
p   libavformat-dev                                                                      - development files for libavformat                                                              
i   libavformat-extra-52                                                                 - ffmpeg file format library                                                                     
p   libavformat-unstripped-52                                                            - ffmpeg utility library - transitional package                                                  
c   libavformat52                                                                        - ffmpeg file format library                                                                     
p   libavutil-dev                                                                        - development files for libavutil                                                                
p   libavutil-extra-49                                                                   - ffmpeg utility library                                                                         
i   libavutil-extra-50                                                                   - ffmpeg utility library                                                                         
p   libavutil-unstripped-50                                                              - ffmpeg utility library - transitional package                                                  
i A libavutil49                                                                          - ffmpeg utility library                                                                         
c   libavutil50                                                                          - ffmpeg utility library                                                                         
p   libpostproc-dev                                                                      - development files for libpostproc                                                              
i   libpostproc-extra-51                                                                 - ffmpeg video postprocessing library                                                            
p   libpostproc-unstripped-51                                                            - ffmpeg utility library - transitional package                                                  
c   libpostproc51                                                                        - ffmpeg video postprocessing library                                                            
p   libswscale-dev                                                                       - development files for libswscale                                                               
i   libswscale-extra-0                                                                   - ffmpeg video scaling library                                                                   
p   libswscale-unstripped-0                                                              - ffmpeg utility library - transitional package                                                  
c   libswscale0                                                                          - ffmpeg video scaling library
```

It looks like libavutil49 ordinary stuck around somehow. I'll try replacing that with the corresponding extra package. EDIT: Yep, this gets me back to where taavikko was when he reported those warnings about totem failing to load some gstreamer plugins. I'll try replacing all extra packages with the ordinary packages again. Yep, it's working now. I must've missed a package earlier.

---

### Post by eris23 on 2010-06-06
On my Maverick system:
Total count: 221 plugins, 1528 features

I do have gstreamer0.10-plugins-bad and gstreamer0.10-plugins-bad-multiverse installed.

---

### Post by plun on 2010-06-06
The bad package is fixed today....

[https://lists.ubuntu.com/archives/maverick-changes/2010-June/001259.html](https://lists.ubuntu.com/archives/maverick-changes/2010-June/001259.html)

--

---

### Post by null_pointer_us on 2010-06-06
Installing gstreamer0.10-plugins-bad broke Totem for me.

This caused NO removals/conflicts/broken packages, as you can see below:

```
$ sudo aptitude install gstreamer0.10-plugins-bad
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  freepats{a} gstreamer0.10-plugins-bad libcdaudio1{a} libcelt0-0{a} libdc1394-22{a} libdirac-encoder0{a} libfftw3-3{a} libflite1{a} libgme0{a} libiptcdata0{a} libkate1{a} 
  libmimic0{a} libmms0{a} libofa0{a} liborc-0.4-0{a} libsoundtouch1c2{a} libwildmidi0{a} 
0 packages upgraded, 17 newly installed, 0 to remove and 0 not upgraded.
Need to get 30.5MB/47.9MB of archives. After unpacking 70.1MB will be used.
Do you want to continue? [Y/n/?] 
Writing extended state information... Done
Get:1 http://us.archive.ubuntu.com/ubuntu/ maverick/universe freepats 20060219-1 [29.0MB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ maverick/universe gstreamer0.10-plugins-bad 0.10.18.3-1ubuntu2 [1,538kB]                                                                       
Fetched 30.5MB in 45s (666kB/s)                                                                                                                                                           
Selecting previously deselected package freepats.
(Reading database ... 197364 files and directories currently installed.)
Unpacking freepats (from .../freepats_20060219-1_all.deb) ...
Selecting previously deselected package libcdaudio1.
Unpacking libcdaudio1 (from .../libcdaudio1_0.99.12p2-9_amd64.deb) ...
Selecting previously deselected package libcelt0-0.
Unpacking libcelt0-0 (from .../libcelt0-0_0.7.1-1_amd64.deb) ...
Selecting previously deselected package libdc1394-22.
Unpacking libdc1394-22 (from .../libdc1394-22_2.1.2-2_amd64.deb) ...
Selecting previously deselected package libdirac-encoder0.
Unpacking libdirac-encoder0 (from .../libdirac-encoder0_1.0.2-3_amd64.deb) ...
Selecting previously deselected package libflite1.
Unpacking libflite1 (from .../libflite1_1.4-release-2_amd64.deb) ...
Selecting previously deselected package libgme0.
Unpacking libgme0 (from .../libgme0_0.5.5-2_amd64.deb) ...
Selecting previously deselected package libiptcdata0.
Unpacking libiptcdata0 (from .../libiptcdata0_1.0.3-1ubuntu1_amd64.deb) ...
Selecting previously deselected package libkate1.
Unpacking libkate1 (from .../libkate1_0.3.7-3_amd64.deb) ...
Selecting previously deselected package libmimic0.
Unpacking libmimic0 (from .../libmimic0_1.0.4-2build1_amd64.deb) ...
Selecting previously deselected package libmms0.
Unpacking libmms0 (from .../libmms0_0.4-2_amd64.deb) ...
Selecting previously deselected package libfftw3-3.
Unpacking libfftw3-3 (from .../libfftw3-3_3.2.2-1_amd64.deb) ...
Selecting previously deselected package libofa0.
Unpacking libofa0 (from .../libofa0_0.9.3-3.1_amd64.deb) ...
Selecting previously deselected package liborc-0.4-0.
Unpacking liborc-0.4-0 (from .../liborc-0.4-0_0.4.4-2_amd64.deb) ...
Selecting previously deselected package libsoundtouch1c2.
Unpacking libsoundtouch1c2 (from .../libsoundtouch1c2_1.3.1-2_amd64.deb) ...
Selecting previously deselected package libwildmidi0.
Unpacking libwildmidi0 (from .../libwildmidi0_0.2.2-3_amd64.deb) ...
Selecting previously deselected package gstreamer0.10-plugins-bad.
Unpacking gstreamer0.10-plugins-bad (from .../gstreamer0.10-plugins-bad_0.10.18.3-1ubuntu2_amd64.deb) ...
Setting up freepats (20060219-1) ...
Setting up libcdaudio1 (0.99.12p2-9) ...
Setting up libcelt0-0 (0.7.1-1) ...
Setting up libdc1394-22 (2.1.2-2) ...
Setting up libdirac-encoder0 (1.0.2-3) ...
Setting up libflite1 (1.4-release-2) ...
Setting up libgme0 (0.5.5-2) ...
Setting up libiptcdata0 (1.0.3-1ubuntu1) ...
Setting up libkate1 (0.3.7-3) ...
Setting up libmimic0 (1.0.4-2build1) ...
Setting up libmms0 (0.4-2) ...
Setting up libfftw3-3 (3.2.2-1) ...
Setting up libofa0 (0.9.3-3.1) ...
Setting up liborc-0.4-0 (0.4.4-2) ...
Setting up libsoundtouch1c2 (1.3.1-2) ...
Setting up libwildmidi0 (0.2.2-3) ...
Setting up gstreamer0.10-plugins-bad (0.10.18.3-1ubuntu2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
```

MPlayer and VLC seem to work OK.

---

### Post by mc4man on 2010-06-06
Just to re-state something
The ffmpeg extra versions only add encoding support - the same for the multiverse gstreamer plugins.

Neither add decoding support

libavutil49 is being kept atm for some apps (vlc is one) and a plugin - gstreamer0.10-ffmpeg.

**the libavutil49-extra version should not be used **

Once vlc is rebuilt it will use libavutil50

If the gstreamer plugins in maverick are updated to current versions (maybe they will, maybe not), and done properly then the gstreamer0.10-ffmpeg plugin will not depend on any of the ffmpeg libs

---

