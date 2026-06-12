---
title: "libxine1-ffmpeg isn't installed right"
date: 2008-12-29
forum: Multimedia Software
---

### Post by ostracize on 2008-12-29
```

[will@exile ~]$ dpkg -l *xine*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                   Version                                Description
+++-======================================-======================================-============================================================================================
pn  amarok-engine-xine                     <none>                                 (no description available)
pn  amarok-xine                            <none>                                 (no description available)
un  gxine                                  <none>                                 (no description available)
pn  kaffeine-xine                          <none>                                 (no description available)
rc  libarts1-xine                          4:3.5.10-0ubuntu1~hardy1               aRts plugin enabling xine support
un  libxine-doc                            <none>                                 (no description available)
pn  libxine-extracodecs                    <none>                                 (no description available)
ii  libxine1                               1.1.15-0ubuntu3                        the xine video/media player library, meta-package
ii  libxine1-bin                           1.1.15-0ubuntu3                        the xine video/media player library, binary files
ii  libxine1-console                       1.1.15-0ubuntu3                        libaa/libcaca/framebuffer/directfb related plugins for libxine1
un  libxine1-doc                           <none>                                 (no description available)
ii  libxine1-ffmpeg                        1.1.15-0ubuntu3                        MPEG-related plugins for libxine1
un  libxine1-gnome                         <none>                                 (no description available)
ii  libxine1-misc-plugins                  1.1.15-0ubuntu3                        Input, audio output and post plugins for libxine1
pn  libxine1-plugins                       <none>                                 (no description available)
ii  libxine1-x                             1.1.15-0ubuntu3                        X desktop video output plugins for libxine1
ii  libxinerama1                           2:1.0.3-2                              X11 Xinerama extension library
ii  phonon-backend-xine                    4:4.1.3-0ubuntu1~intrepid1             Phonon Xine 1.1.x backend
rc  xine-ui                                0.99.4+dfsg+cvs20061111-2ubuntu2       the xine video player, user interface

```
MP3s play fine in MPlayer but not at all in Kaffeine and Amarok. libxine1-ffmpeg is installed so I don't know what else I can do to get these mp3s to play. I removed libxine1-ffmpeg and allowed Kaffeine to install libxine1-ffmpeg itself automatically. This didn't help because immediately after it thought libxine1-ffmpeg was installed, it complained that the proper codec was not installed and so tried to install it all over again. Then it would say codec already installed. libxine1-ffmpeg is seriously screwed up. How can I get mp3s to play in these applications? Also, shouldn't the output of xine-list-1.1 show some kind of audio/mpeg or mp3?
```

[will@exile ~]$ xine-list-1.1 | sed 's/;/\n/g' | sort                                                                                                             
application/annodex                                                                                                                                               
application/ogg                                                                                                                                                   
application/vnd.ms-asf                                                                                                                                            
application/vnd.rn-realmedia                                                                                                                                      
application/x-annodex                                                                                                                                             
application/x-flash-video                                                                                                                                         
application/x-mplayer2                                                                                                                                            
application/x-ogg                                                                                                                                                 
application/x-ogm                                                                                                                                                 
application/x-ogm-audio                                                                                                                                           
application/x-ogm-video                                                                                                                                           
application/x-quicktimeplayer                                                                                                                                     
audio/168sv                                                                                                                                                       
audio/8svx                                                                                                                                                        
audio/aiff                                                                                                                                                        
audio/annodex                                                                                                                                                     
audio/basic                                                                                                                                                       
audio/flac                                                                                                                                                        
audio/flac                                                                                                                                                        
audio/mp4                                                                                                                                                         
audio/ogg                                                                                                                                                         
audio/x-16sv                                                                                                                                                      
audio/x-8svx                                                                                                                                                      
audio/x-aiff                                                                                                                                                      
audio/x-annodex                                                                                                                                                   
audio/x-basic                                                                                                                                                     
audio/x-flac
audio/x-flac
audio/x-m4a
audio/x-ms-wma
audio/x-ogg
audio/x-pn-aiff
audio/x-pn-au
audio/x-pn-realaudio
audio/x-pn-realaudio-plugin
audio/x-realaudio
audio/x-real-audio
image/ilbm
image/png
image/x-ilbm
image/x-png
video/anim
video/annodex
video/flv
video/mkv
video/mng
video/mp4
video/mpeg
video/msvideo
video/ogg
video/quicktime
video/x-anim
video/x-annodex
video/x-flic
video/x-flv



video/x-matroska
video/x-mng
video/x-mpeg
video/x-ms-asf
video/x-ms-asf-plugin
video/x-msvideo
video/x-ms-wax
video/x-ms-wmv
video/x-ms-wvx
video/x-ogg
video/x-quicktime

```

---

### Post by ostracize on 2008-12-31
Could someone who can play mp3s at the very least please post the output of libxine1-ffmpeg for me?

---

### Post by Ng Oon-Ee on 2008-12-31
Ah, may as well help you out =).

```
application/annodex
application/ogg
application/vnd.ms-asf
application/vnd.rn-realmedia
application/x-annodex
application/x-flash-video
application/x-mplayer2
application/x-ogg
application/x-ogm
application/x-ogm-audio
application/x-ogm-video
application/x-quicktimeplayer
audio/168sv
audio/8svx
audio/aiff
audio/annodex
audio/basic
audio/flac
audio/mp3
audio/mp4
audio/mpeg
audio/mpeg2
audio/mpeg3
audio/mpegurl
audio/musepack
audio/ogg
audio/wav
audio/x-16sv
audio/x-8svx
audio/x-aiff
audio/x-annodex
audio/x-basic
audio/x-flac
audio/x-flac
audio/x-m4a
audio/x-mp3
audio/x-mpeg
audio/x-mpeg2
audio/x-mpeg3
audio/x-mpegurl
audio/x-ms-wma
audio/x-musepack
audio/x-ogg
audio/x-pn-aiff
audio/x-pn-au
audio/x-pn-realaudio
audio/x-pn-realaudio-plugin
audio/x-pn-wav
audio/x-pn-windows-acm
audio/x-realaudio
audio/x-real-audio
audio/x-wav
audio/x-wavpack
image/ilbm
image/png
image/x-ilbm
image/x-png
video/anim
video/annodex
video/flv
video/mkv
video/mng
video/mp4
video/mpeg
video/msvideo
video/ogg
video/quicktime
video/x-anim
video/x-annodex
video/x-flic
video/x-flv
video/x-matroska
video/x-mng
video/x-mpeg
video/x-ms-asf
video/x-ms-asf-plugin
video/x-msvideo
video/x-ms-wax
video/x-ms-wmv
video/x-ms-wvx
video/x-ogg
video/x-quicktime
```

---

### Post by Ng Oon-Ee on 2008-12-31
Just to mention, I have amarok-engine-xine installed, as well as libxin1-bin, libxine1-ffmpeg, libxine1-gnome, libxin1-misc-plugins, among others. Hope it helps. But I use AmaroK exclusively, never tried Kaffeine before (keeps you awake, I heard).

---

### Post by ostracize on 2009-01-02
> **Ng Oon-Ee said:**
> Just to mention, I have amarok-engine-xine installed, as well as libxin1-bin, libxine1-ffmpeg, libxine1-gnome, libxin1-misc-plugins, among others. Hope it helps. But I use AmaroK exclusively, never tried Kaffeine before (keeps you awake, I heard).

Thank you for your help. I have a major issue then:
```

[will@exile ~]$ sudo apt-get remove libxine1-ffmpeg
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED
  libxine1-ffmpeg
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 881kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 106669 files and directories currently installed.)
Removing libxine1-ffmpeg ...
[will@exile ~]$ xine-list-1.1 | sed 's/;/\n/g' | sort >> /tmp/before
[will@exile ~]$ sudo apt-get install libxine1-ffmpeg
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed
  libxine1-ffmpeg
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/393kB of archives.
After this operation, 881kB of additional disk space will be used.
Selecting previously deselected package libxine1-ffmpeg.
(Reading database ... 106657 files and directories currently installed.)
Unpacking libxine1-ffmpeg (from .../libxine1-ffmpeg_1.1.15-0ubuntu3_i386.deb) ...
Setting up libxine1-ffmpeg (1.1.15-0ubuntu3) ...

[will@exile ~]$ xine-list-1.1 | sed 's/;/\n/g' | sort >> /tmp/after
[will@exile ~]$ diff /tmp/before /tmp/after
47a48
> video/mpeg
56a58
> video/x-mpeg

```
```

[will@exile ~]$ dpkg -L libxine1-ffmpeg
/.
/usr
/usr/lib
/usr/lib/xine
/usr/lib/xine/plugins
/usr/lib/xine/plugins/1.24
/usr/lib/xine/plugins/1.24/xineplug_decode_ff.so
/usr/lib/xine/plugins/1.24/xineplug_decode_faad.so
/usr/lib/xine/plugins/1.24/xineplug_decode_mad.so
/usr/lib/xine/plugins/1.24/xineplug_decode_mpeg2.so
/usr/lib/xine/plugins/1.24/xineplug_decode_a52.so
/usr/lib/xine/plugins/1.24/xineplug_decode_dts.so
/usr/lib/xine/plugins/1.24/xineplug_dmx_mpeg.so
/usr/lib/xine/plugins/1.24/xineplug_dmx_mpeg_block.so
/usr/lib/xine/plugins/1.24/xineplug_dmx_mpeg_elem.so
/usr/lib/xine/plugins/1.24/xineplug_dmx_mpeg_pes.so
/usr/lib/xine/plugins/1.24/xineplug_dmx_mpeg_ts.so
/usr/lib/xine/plugins/1.24/post
/usr/lib/xine/plugins/1.24/post/xineplug_post_planar.so
/usr/share
/usr/share/doc
/usr/share/doc/libxine1-ffmpeg

```
Why isn't audio/mpeg3 getting installed on my machine?!

---

### Post by mc4man on 2009-01-02
Gave this a quick try and saw the same thing, installing libxine1-ffmpeg doesn't enable mp3's in kubuntu 8.04. (though it must be installed

What you need to do is replace some or all of the libav* packages with the 'unstripped' versions.

Probably just libavcodec, I did all of them. (libavcodec, libavformat, libavutil, libavdevice (in doing so a few other packages will be installed, libfaad0, libfaac0, libmp3lame0, ect.

 After that **restart** amarok and you should be ok.

I found this much easier to do in synaptic than adept, your choice there.

---

### Post by xc3RnbFO8P on 2009-01-02
amarok-engine-xine
libxine1-all-plugins
libxine1-plugins
(libxine1-gnome)

---

### Post by ostracize on 2009-01-03
> **mc4man said:**
> Gave this a quick try and saw the same thing, installing libxine1-ffmpeg doesn't enable mp3's in kubuntu 8.04. (though it must be installed

What you need to do is replace some or all of the libav* packages with the 'unstripped' versions.

Probably just libavcodec, I did all of them. (libavcodec, libavformat, libavutil, libavdevice (in doing so a few other packages will be installed, libfaad0, libfaac0, libmp3lame0, ect.

 After that **restart** amarok and you should be ok.

I found this much easier to do in synaptic than adept, your choice there.
This doesn't seem to have helped. My results are still exactly the same:
```

[will@exile ~]$ sudo apt-cache search libav | grep unstripped | awk '{print $1}'
libavcodec-unstripped-51                                                        
libavdevice-unstripped-52                                                       
libavformat-unstripped-52                                                       
libavutil-unstripped-49                                                         
[will@exile ~]$ sudo apt-get install `sudo apt-cache search libav | grep unstripped | awk '{print $1}'`
Reading package lists... Done                                                                          
Building dependency tree                                                                               
Reading state information... Done                                                                      
libavcodec-unstripped-51 is already the newest version.                                                
The following packages will be REMOVED                                                                 
  libavdevice52 libavformat52 libavutil49                                                              
The following NEW packages will be installed                                                           
  libavdevice-unstripped-52 libavformat-unstripped-52 libavutil-unstripped-49                          
0 upgraded, 3 newly installed, 3 to remove and 0 not upgraded.                                         
Need to get 774kB of archives.                                                                         
After this operation, 16.4kB of additional disk space will be used.                                    
Do you want to continue [Y/n]? y                                                                       
Get: 1 http://ca.archive.ubuntu.com intrepid/multiverse libavutil-unstripped-49 3:0.svn20080206-12ubuntu3+unstripped5 [81.0kB]
Get: 2 http://ca.archive.ubuntu.com intrepid/multiverse libavformat-unstripped-52 3:0.svn20080206-12ubuntu3+unstripped5 [630kB]
Get: 3 http://ca.archive.ubuntu.com intrepid/multiverse libavdevice-unstripped-52 3:0.svn20080206-12ubuntu3+unstripped5 [62.7kB]                                                  
Fetched 774kB in 10s (72.3kB/s)                                                                                                                                                   
dpkg: libavformat52: dependency problems, but removing anyway as you request:                                                                                                     
 libk3b3-extracodecs depends on libavformat52 (>= 3:0.svn20080206-8) | libavformat-unstripped-52 (>= 3:0.svn20080206-8); however:                                                 
  Package libavformat52 is to be removed.                                                                                                                                         
  Package libavformat-unstripped-52 is not installed.                                                                                                                             
 libavdevice52 depends on libavformat52 (>= 3:0.svn20080206-8) | libavformat-unstripped-52 (>= 3:0.svn20080206-8); however:                                                       
  Package libavformat52 is to be removed.                                                                                                                                         
  Package libavformat-unstripped-52 is not installed.                                                                                                                             
 ffmpeg depends on libavformat52 (>= 3:0.svn20080206-8) | libavformat-unstripped-52 (>= 3:0.svn20080206-8); however:                                                              
  Package libavformat52 is to be removed.                                                                                                                                         
  Package libavformat-unstripped-52 is not installed.                                                                                                                             
(Reading database ... 106669 files and directories currently installed.)                                                                                                          
Removing libavformat52 ...                                                                                                                                                        
dpkg: libavutil49: dependency problems, but removing anyway as you request:                                                                                                       
 transcode depends on libavutil49 (>= 3:0.svn20080206-8) | libavutil-unstripped-49 (>= 3:0.svn20080206-8); however:                                                               
  Package libavutil49 is to be removed.                                                                                                                                           
  Package libavutil-unstripped-49 is not installed.                                                                                                                               
 libpostproc51 depends on libavutil49 (>= 3:0.svn20080206-8) | libavutil-unstripped-49 (>= 3:0.svn20080206-8); however:                                                           
  Package libavutil49 is to be removed.                                                                                                                                           
  Package libavutil-unstripped-49 is not installed.                                                                                                                               
 libavdevice52 depends on libavutil49 (>= 3:0.svn20080206-8) | libavutil-unstripped-49 (>= 3:0.svn20080206-8); however:                                                           
  Package libavutil49 is to be removed.                                                                                                                                           
  Package libavutil-unstripped-49 is not installed.                                                                                                                               
 libswscale0 depends on libavutil49 (>= 3:0.svn20080206-8) | libavutil-unstripped-49 (>= 3:0.svn20080206-8); however:                                                             
  Package libavutil49 is to be removed.                                                                                                                                           
  Package libavutil-unstripped-49 is not installed.                                                                                                                               
 ffmpeg depends on libavutil49 (>= 3:0.svn20080206-8) | libavutil-unstripped-49 (>= 3:0.svn20080206-8); however:                                                                  
  Package libavutil49 is to be removed.                                                                                                                                           
  Package libavutil-unstripped-49 is not installed.                                                                                                                               
 libavcodec-unstripped-51 depends on libavutil49 (>= 3:0.svn20080206-8) | libavutil-unstripped-49 (>= 3:0.svn20080206-8); however:                                                
  Package libavutil49 is to be removed.                                                                                                                                           
  Package libavutil-unstripped-49 is not installed.                                                                                                                               
 libquicktime1 depends on libavutil49 (>= 3:0.svn20080206-8) | libavutil-unstripped-49 (>= 3:0.svn20080206-8); however:                                                           
  Package libavutil49 is to be removed.                                                                                                                                           
  Package libavutil-unstripped-49 is not installed.                                                                                                                               
 libxine1-ffmpeg depends on libavutil49 (>= 3:0.svn20080206-8) | libavutil-unstripped-49 (>= 3:0.svn20080206-8); however:                                                         
  Package libavutil49 is to be removed.                                                                                                                                           
  Package libavutil-unstripped-49 is not installed.                                                                                                                               
Removing libavutil49 ...                                                                                                                                                          
dpkg: libavdevice52: dependency problems, but removing anyway as you request:                                                                                                     
 ffmpeg depends on libavdevice52 (>= 3:0.svn20080206-8) | libavdevice-unstripped-52 (>= 3:0.svn20080206-8); however:                                                              
  Package libavdevice52 is to be removed.                                                                                                                                         
  Package libavdevice-unstripped-52 is not installed.                                                                                                                             
Removing libavdevice52 ...                                                                                                                                                        
Processing triggers for libc6 ...                                                                                                                                                 
ldconfig deferred processing now taking place                                                                                                                                     
Selecting previously deselected package libavutil-unstripped-49.                                                                                                                  
(Reading database ... 106631 files and directories currently installed.)                                                                                                          
Unpacking libavutil-unstripped-49 (from .../libavutil-unstripped-49_3%3a0.svn20080206-12ubuntu3+unstripped5_i386.deb) ...                                                         
Selecting previously deselected package libavformat-unstripped-52.                                                                                                                
Unpacking libavformat-unstripped-52 (from .../libavformat-unstripped-52_3%3a0.svn20080206-12ubuntu3+unstripped5_i386.deb) ...                                                     
Selecting previously deselected package libavdevice-unstripped-52.                                                                                                                
Unpacking libavdevice-unstripped-52 (from .../libavdevice-unstripped-52_3%3a0.svn20080206-12ubuntu3+unstripped5_i386.deb) ...                                                     
Setting up libavutil-unstripped-49 (3:0.svn20080206-12ubuntu3+unstripped5) ...                                                                                                    

Setting up libavformat-unstripped-52 (3:0.svn20080206-12ubuntu3+unstripped5) ...

Setting up libavdevice-unstripped-52 (3:0.svn20080206-12ubuntu3+unstripped5) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

[will@exile ~]$ xine-list-1.1 | sed 's/;/\n/g' | grep mpeg                                                                                                                         
video/mpeg                                                                                                                                                                         
video/x-mpeg                                                                                                                                                                       
[will@exile ~]$ sudo apt-get remove libxine1-ffmpeg
Reading package lists... Done                      
Building dependency tree                           
Reading state information... Done                  
The following packages will be REMOVED             
  libxine1-ffmpeg                                  
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 881kB disk space will be freed.         
Do you want to continue [Y/n]? y                              
(Reading database ... 106670 files and directories currently installed.)
Removing libxine1-ffmpeg ...                                            
[will@exile ~]$ xine-list-1.1 | sed 's/;/\n/g' | grep mpeg              
[will@exile ~]$ sudo apt-get install libxine1-ffmpeg
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed
  libxine1-ffmpeg
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/393kB of archives.
After this operation, 881kB of additional disk space will be used.
Selecting previously deselected package libxine1-ffmpeg.
(Reading database ... 106658 files and directories currently installed.)
Unpacking libxine1-ffmpeg (from .../libxine1-ffmpeg_1.1.15-0ubuntu3_i386.deb) ...
Setting up libxine1-ffmpeg (1.1.15-0ubuntu3) ...

[will@exile ~]$ xine-list-1.1 | sed 's/;/\n/g' | grep mpeg
video/mpeg
video/x-mpeg
[will@exile ~]$ dpkg -L libxine1-ffmpeg
/.
/usr
/usr/lib
/usr/lib/xine
/usr/lib/xine/plugins
/usr/lib/xine/plugins/1.24
/usr/lib/xine/plugins/1.24/xineplug_decode_ff.so
/usr/lib/xine/plugins/1.24/xineplug_decode_faad.so
/usr/lib/xine/plugins/1.24/xineplug_decode_mad.so
/usr/lib/xine/plugins/1.24/xineplug_decode_mpeg2.so
/usr/lib/xine/plugins/1.24/xineplug_decode_a52.so
/usr/lib/xine/plugins/1.24/xineplug_decode_dts.so
/usr/lib/xine/plugins/1.24/xineplug_dmx_mpeg.so
/usr/lib/xine/plugins/1.24/xineplug_dmx_mpeg_block.so
/usr/lib/xine/plugins/1.24/xineplug_dmx_mpeg_elem.so
/usr/lib/xine/plugins/1.24/xineplug_dmx_mpeg_pes.so
/usr/lib/xine/plugins/1.24/xineplug_dmx_mpeg_ts.so
/usr/lib/xine/plugins/1.24/post
/usr/lib/xine/plugins/1.24/post/xineplug_post_planar.so
/usr/share
/usr/share/doc
/usr/share/doc/libxine1-ffmpeg


```

---

### Post by mc4man on 2009-01-03
Well you shouldn't have to do anything but install libxine1-ffmpeg.

Your dpkg -L libxine1-ffmpeg is exactly what I saw when mp3's were playable, there's nothing mentioned otherwise.

I was surprised when changing the libav's 'seemed' to help, probably just a coincidence.

I had tried to test this off of a live cd but it wouldn't work right so I did a real install. I was considering keeping kubuntu 8.10 on my extra machine, but in it's 3 hr lifespan adept broke totally, I got a sig whatever error on an update, trying to access a location (audiocd :/) proved impossible due to 'the application responsible...blah blah, icons kept disappearing, ect, So it's gone...

The only thing that did work right was ironically mp3 playback in amarok (though not at first.

I know you can't remove amarok in k 8.10, have you tried a re install?

---

### Post by ostracize on 2009-01-03
> **mc4man said:**
> 
I know you can't remove amarok in k 8.10, have you tried a re install?
A re-install of amarok? Or Kubuntu 8.10? I've tried to reinstall amarok 2 but that made no difference. I do not look forward to the prospect of reinstalling my OS.

---

### Post by mc4man on 2009-01-03
Amarok

---

### Post by ostracize on 2009-01-05
> **mc4man said:**
> Amarok

Like I said. I've tried it and that didn't help.

Furthermore, the problem must be related to libxine1-ffmpeg. I can install amarok as often as I want but xine-list-1.1 still will not show mpeg3

---

### Post by ostracize on 2009-01-06
*Bump*

This problem has rendered my entire MP3 collection useless. I need help please!

---

### Post by xc3RnbFO8P on 2009-01-06
> Could someone who can play mp3s at the very least please post the output of libxine1-ffmpeg for me?
```
rob@rob-desktop:~$ xine-list-1.1 | sed 's/;/\n/g' | sort
application/annodex
application/ogg
application/vnd.ms-asf
application/vnd.rn-realmedia
application/x-annodex
application/x-flash-video
application/x-mplayer2
application/x-ogg
application/x-ogm
application/x-ogm-audio
application/x-ogm-video
application/x-quicktimeplayer
audio/168sv
audio/8svx
audio/aiff
audio/annodex
audio/basic
audio/flac
audio/mp3
audio/mp4
audio/mpeg
audio/mpeg2
audio/mpeg3
audio/mpegurl
audio/musepack
audio/ogg
audio/wav
audio/x-16sv
audio/x-8svx
audio/x-aiff
audio/x-annodex
audio/x-basic
audio/x-flac
audio/x-flac
audio/x-m4a
audio/x-mp3
audio/x-mpeg
audio/x-mpeg2
audio/x-mpeg3
audio/x-mpegurl
audio/x-ms-wma
audio/x-musepack
audio/x-ogg
audio/x-pn-aiff
audio/x-pn-au
audio/x-pn-realaudio
audio/x-pn-realaudio-plugin
audio/x-pn-wav
audio/x-pn-windows-acm
audio/x-realaudio
audio/x-real-audio
audio/x-wav
audio/x-wavpack
image/ilbm
image/png
image/x-ilbm
image/x-png
video/anim
video/annodex
video/flv
video/mkv
video/mng
video/mp4
video/mpeg
video/msvideo
video/ogg
video/quicktime
video/x-anim
video/x-annodex
video/x-flic
video/x-flv
video/x-matroska
video/x-mng
video/x-mpeg
video/x-ms-asf
video/x-ms-asf-plugin
video/x-msvideo
video/x-ms-wax
video/x-ms-wmv
video/x-ms-wvx
video/x-ogg
video/x-quicktime

```

---

### Post by ostracize on 2009-01-07
Well, It's a permissions problem:
```

[will@exile ~]$ xine-list-1.1 | sed 's/;/\n/g' | grep mpeg
video/mpeg                                                
video/x-mpeg                                              
[will@exile ~]$ sudo -s                                   
[root@exile ~]# xine-list-1.1 | sed 's/;/\n/g' | grep mpeg
video/mpeg                                                
video/x-mpeg                                              
audio/mpeg2                                               
audio/x-mpeg2                                             
audio/mpeg3                                               
audio/x-mpeg3                                             
audio/mpeg                                                
audio/x-mpeg                                              
audio/x-mpegurl                                           
audio/mpegurl                         

```
I ran Amarok as root and mp3s played perfect. So what do I have to do to get this working as myself instead of root?

---

### Post by mc4man on 2009-01-08
I wasn't telling you to reinstall amarok again, just answering your previous question.

No longer have kubuntu 8.10 (actually threw out the live cd so I wouldn't be tempted

What I see in ubuntu though is in the home dir. -> .xine is a file called catalog.cache

Maybe try deleting it and let it get rebuilt (if it exists in kubuntu

---

### Post by ostracize on 2009-01-08
That did it!

I moved .xine to .xine-bak and the .xine directory was rebuilt with a proper catalog.cache.

```

[will@exile bin]$ xine-list-1.1 | sed 's/;/\n/g' | grep mpeg
video/mpeg
video/x-mpeg
audio/mpeg2
audio/x-mpeg2
audio/mpeg3
audio/x-mpeg3
audio/mpeg
audio/x-mpeg
audio/x-mpegurl
audio/mpegurl


```
Mp3s are working again.

Thank you so much for your help!

---

### Post by videomar on 2009-05-10
Hm.

Thank you for your help, had the same problem onn the lenovo S9e with easypeasy installed. I updated the system and suddenly amarok 2 didn't play about 90 % of the soundfiles on the system. Always said... "too many errors encountered on playlist" - but via the synaptic-packetmanagement i installed the "phonon-backend-xine" and everything is fine again...

Kind regards,
r.

---

### Post by PLIACHAS PASCHALIS on 2009-05-12
> **videomar said:**
> Hm.

Thank you for your help, had the same problem onn the lenovo S9e with easypeasy installed. I updated the system and suddenly amarok 2 didn't play about 90 % of the soundfiles on the system. Always said... "too many errors encountered on playlist" - but via the synaptic-packetmanagement i installed the "phonon-backend-xine" and everything is fine again...

Kind regards,
r.

i did the same think and now it's working.
Thanks

---

### Post by pseudo endeavor on 2010-02-10
.xine solution worked. Thank you.

---

