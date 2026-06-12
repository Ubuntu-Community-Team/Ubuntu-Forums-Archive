---
title: "mpeg-4 video editor"
date: 2007-09-10
forum: Multimedia Production
---

### Post by Boldor on 2007-09-10
I use a Sanyo Xacti DMX HD1A digital video camera. (aka VCP HD1A)

It allows a certain amount of editing on the camera, but I'd like to be able to edit the footage when it is on the computer (delete scenes, join scenes together, add music)

Data on the camera is stored on an SD card as mpeg-4. Most of what I record is at 720i.

Is there any editing software that has been developed for this?

Thanks,

Paul

---

### Post by UbuWu on 2007-09-10
[Kdenlive]("http://kdenlive.org/") can probably do all of that. You have to install it manually though, or upgrade to gutsy which has it in the repositories.

---

### Post by Amazona aestiva on 2007-09-10
For Feisty version see the first link in my signature.
I like Kdenlive.;)

---

### Post by Boldor on 2007-09-11
Thanks for pointing me towards KDEnlive. I added it and the list of other suggested bits and pieces.

It is great to be able to start to work with my footage on the computer again. However, when I add the clips to a project, the sound doesn't seem to come with them. The files play fine in VLC.

Is there some kind of setting of a plug-in I needed to set up?

Thanks.

---

### Post by Boldor on 2007-09-11
Hang on!

This is what I did before install KDEnlive:


[COLOR="Red"]Note:
It is recommended to install ffmpeg, mencoder, libxvidcore4, Xine and GStreamer because these are used by many programs!(players and encoders)
Easy way to install these: Last updated/checked:02-09-2007
Code:

sudo apt-get install gstreamer0.8-a52dec gstreamer0.8-aa gstreamer0.8-audiofile gstreamer0.8-cdio gstreamer0.8-dv gstreamer0.8-dvd gstreamer0.8-faac gstreamer0.8-faad gstreamer0.8-misc gstreamer0.10-alsa gstreamer0.10-doc gstreamer0.10-esd gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-gl gstreamer0.10-gnomevfs gstreamer0.10-gnonlin gstreamer0.10-gnonlin-dev gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-dbg gstreamer0.10-plugins-bad-doc gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-bad-multiverse-dbg gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-base-dbg gstreamer0.10-plugins-base-doc gstreamer0.10-plugins-farsight gstreamer0.10-plugins-good gstreamer0.10-plugins-good-dbg gstreamer0.10-plugins-good-doc gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-dbg gstreamer0.10-plugins-ugly-doc gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-ugly-multiverse-dbg gstreamer0.10-sdl gstreamer0.10-tools gstreamer0.10-x gstreamer-tools irb1.8 liba52-0.7.4 libbreakpoint-ruby1.8 libcdaudio1 libcmdparse2-ruby1.8 libdaemonize-ruby1.8 libdvdnav4 libdvdread3 libdvdplay0 libfaac0 libfaad2-0 libfreebob0 libgems-ruby1.8 libglib2-ruby libgsm1 libgstreamer0.8-0 libgstreamer0.8-ruby libgstreamer0.10-0 libgstreamer0.10-0-dbg libgstreamer0.10-ruby1.8 libgstreamer-gconf0.8-0 libgstreamer-perl libgstreamer-plugins0.8-0 libgstreamer-plugins-base0.10-0 libgstreamer-plugins-pulse0.10-0 libid3tag0 libjack0.100.0-0 libjinglebase0.3-0 libjinglep2p0.3-0 libjinglexmllite0.3-0 libjinglexmpp0.3-0 liblame0 liblog4r-ruby1.8 libmad0 libmjpegtools0c2a libmms0 libmp4v2-0 libmpcdec3 libmpeg2-4 libncurses-ruby1.8 libopenssl-ruby1.8 libpulse0 libquicktime0 libreadline-ruby1.8 libruby1.8 libruby1.8-dbg libruby1.8-extras libsidplay1 libsoundtouch1c2 libswfdec0.3 libwavpack1 libxvidcore4 libxvidcore4-dev rdoc1.8 ruby1.8 ruby ffmpeg mencoder mplayer xvid4conf libxine-extracodecs libxine1-ffmpeg libxine1

and install libdvdcss2:
libdvdcss2 1.2.9 - i386
libdvdcss2 1.2.9 - amd64

And You might have to turn off the desktop effects. It can cause plenty of visual errors![/COLOR]




I also have VLC and mplayer installed from before.

Now I have lost the audio on mp4 and avi files. Have I installed something that is conflicting?

---

### Post by UbuWu on 2007-09-11
Wow! Who told you to do that? You probably don't even need halve of that. The things I would recommend installing is the gstreamer good bad and ugly packages (0.10, not 0.8 ) and libdvdcss.

---

### Post by stmiller on 2007-09-11
Yeah you definitely do not want both gstreamer0.8 AND gstreamer0.10 packages.

---

### Post by Boldor on 2007-09-15
Thank you for your help so far.

In response to the advice that I didn't need everything, I uninstalled what I had previously installed. This ended up almost stripping all the software from my system. Without knowing what else had also disappeared I opted for a clean install of Feisty.

I now have the KDE installed too.

Same problem though. When adding a clip, the audio isn't recognised. If I look at the clip properties, this is what I get:

Type: Mute video clip
Video codec: mpeg4
Audio code: 
Fps: 0
Audio: None
Size: 1280x720


The clips play fine in VLC. Is there some other codec that I need to install for kdenlive?

---

### Post by vinutux on 2007-09-18
use vlc to convert u r video to other common formats (ie mpeg1 mpeg2 avi xvid ogg-theora) and use it with video editor...


it is possible converting videoes in vlc Files->Wizad->........



try it:)

---

### Post by Cresho on 2008-07-20
I have a working work flow that works for sanyo xacti mp4 files.  I am using virtualdub, mp4cam2avi, xvid softwares under wine.  There are bugs but it mainly is towards adjusting the 

1.render to opengl
2. not minimizing video nor switching windows workspace under ubuntu
3.resizing your view perspective under virtualdub to small frames. (just click on each window and hit 33 percent on both.)  for some reason, if opengl isnt looking at the frames, it stops the process.

I'll post a tutorial later on for future reference for people who use the sanyo xacti hd1000.  If you can't wait, ill give you my current info if you pm me.

---

