---
title: "gstreamer dependency issues"
date: 2012-06-29
forum: Multimedia Software
---

### Post by hueyfree on 2012-06-29
I'm running Ubuntu 11.04 I first noticed I had a problem when I got an error in sound converter.  When I went to play a video on movie player I had to install the necessary plugins.  I then got this problem

                                  gstreamer0.10-ffmpeg: Depends: libavcodec-extra-52 (>= 4:0.6-1~) but 6:0.7.13.0ubuntu0jon1 is to be installed  
                       Depends: libavformat-extra-52 (>= 4:0.6-1~) but 6:0.7.13.0ubuntu0jon1 is to be installed  
                       Depends: libavutil-extra-50 (>= 4:0.6-1~) but 6:0.7.13.0ubuntu0jon1 is to be installed  
                       Depends: libc6 (>= 2.7) but 2.13-0ubuntu13.1 is to be installed  
                       Depends: libglib2.0-0 (>= 2.24.0) but 2.28.6-0ubuntu1 is to be installed  
                       Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.22) but 0.10.32-1ubuntu5 is to be installed  
                       Depends: libgstreamer0.10-0 (>= 0.10.26) but 0.10.32-3ubuntu3.1 is to be installed  
                       Depends: liborc-0.4-0 (>= 1:0.4.10) but 1:0.4.11-2 is to be installed  
                       Depends: libpostproc-extra-51 (>= 4:0.6-1~) but 6:0.7.13.0ubuntu0jon1 is to be installed  
                       Depends: libswscale-extra-0 (>= 4:0.6-1~) but 6:0.7.13.0ubuntu0jon1 is to be installed  
  
Tried uninstalling and reinstalling good, bad and ugly with no luck. Made sure repository was updated and found no broken packages in package manager.  Any suggestions?

---

### Post by BicyclerBoy on 2012-06-29
I would guess you are using Jon Serverisson's FFmpeg ppa..
This seems to be incompatible with gstreamer0.10-ffmpeg..
Could be packaging problem or could be real incompatibility from the ffmpeg-libav/avconv fork.

I noticed this the other day when trying to play an old wma audio file.

---

### Post by mc4man on 2012-06-29
It looks like he tried to avoid breakage with the oldabi* packages but that's apparently not working with  gstreamer-ffmpeg

You could drop him a note, maybe he'll build a replacement package

Overall though still don't really get the need for newer shared FFmpeg libs installed in /usr/ 

Here on 12.04 I do use the current FFmpeg built static & also have 2 apps that benefit from the latest FFmpeg. (but they need a rebuild to take advantage

In one case - vlc, I statically link, in the other, audacious/audacious plugins, it is better on 64 bit to use shared. So for audacious I just simply build FFmpeg as shared to /opt & link at runtime

---

### Post by hueyfree on 2012-06-30
Thanks for your input.  I've gone through my applications  and it looks like it's not a major issue at this point.  Been using vlc. Just wondering what issues I might have when I upgrade.

---

