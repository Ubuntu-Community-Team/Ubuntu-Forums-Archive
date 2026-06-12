---
title: "Kdenlive Crashes when importing any clip"
date: 2010-11-28
forum: Multimedia Software
---

### Post by mardukvmbc on 2010-11-28
I'm on kubuntu 10.10 and kdenlive 0.7.8 and since the upgrade to 10.10 Kdenlive crashes whenever I import a clip with a segfault. 
Here's the dump from console:

File given:  true 
Color mode changed to  0 
File given:  true 
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
[dv @ 0x3219fa0]Estimating duration from bitrate, this may be inaccurate
[dv @ 0x31564d0]Estimating duration from bitrate, this may be inaccurate   
[dv @ 0x3204600]Estimating duration from bitrate, this may be inaccurate   
[dv @ 0x3219fa0]Estimating duration from bitrate, this may be inaccurate   
[dv @ 0x31564d0]Estimating duration from bitrate, this may be inaccurate   
[dv @ 0x3204600]Estimating duration from bitrate, this may be inaccurate   
Diverting av_*_packet function calls to libavcodec. Recompile to improve performance                                                                  
    Last message repeated 1 times                                          
swScaler: pal8 is not supported as output pixel format
KCrash: Application 'kdenlive' crashing...                                 
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
sock_file=/home/jason/.kde/socket-denpc/kdeinit4__0
QSocketNotifier: Invalid socket 11 and type 'Read', disabling...

[1]+  Stopped                 kdenlive

Any ideas?
Thanks!

---

### Post by Yellow Pasque on 2010-11-28
If you have PPA's that provide updated ffmpeg, this issue will occur. [http://kdenlive.org/forum/importing-video-file-kdelive-crash](http://kdenlive.org/forum/importing-video-file-kdelive-crash)

---

### Post by mardukvmbc on 2010-11-28
> **Temüjin said:**
> If you have PPA's that provide updated ffmpeg, this issue will occur. [http://kdenlive.org/forum/importing-video-file-kdelive-crash](http://kdenlive.org/forum/importing-video-file-kdelive-crash)

That was it, you rock!
I googled the heck out of this and didn't find it. I owe you a beer.

---

