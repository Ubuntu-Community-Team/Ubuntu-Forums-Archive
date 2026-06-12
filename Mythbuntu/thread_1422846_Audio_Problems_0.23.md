---
title: "Audio Problems 0.23"
date: 2010-03-05
forum: Mythbuntu
---

### Post by jimmyoo0 on 2010-03-05
I have no sound in my dvb-t recordings :(
This is what i think the problem is , from mythfrontend log when playing the file:

2010-03-06 14:57:22.839 AFD: Opened codec 0x94504d0, id(H264) type(Video)
2010-03-06 14:57:22.839 AFD: codec AAC/LATM has 0 channels
2010-03-06 14:57:22.839 AFD Error: Could not find decoder for codec (AAC/LATM), ignoring.
2010-03-06 14:57:22.839 AFD Error: Could not find decoder for codec (DVB_TELETEXT), ignoring.
2010-03-06 14:57:22.839 AFD: Opened codec 0x93cfd30, id(DVB_SUBTITLE) type(Subtitle)
2010-03-06 14:57:22.839 NVP(2): Disabling Audio, params(-1,-1,-1)
2010-03-06 14:57:22.952 VDPAU: Created 2 output surfaces.
2010-03-06 14:57:22.952 VDPAU: Created VDPAU render device 1024x768
2010-03-06 14:57:23.064 NVP(2): Forcing decode extra audio option on (Video method requires it).
2010-03-06 14:57:23.064 FilterManager: Failed to load filter 'colorspace', no such filter exists
2010-03-06 14:57:23.065 OSD Theme Dimensions W: 1280 H: 720
2010-03-06 14:57:23.202 Video timing method: USleep with busy wait
2010-03-06 14:57:23.202 SendReceiveStringList(MESSAGE,COMMFLAG_REQUEST 1010 2010-02-15T20:30:00) called from UI thread
2010-03-06 14:57:23.202 TV: Changing from None to Watching WatchingPreRecorded
2010-03-06 14:57:23.210 Realtime priority would require SUID as root.

I have had a bit of a search and have not come up with any solutions.

I have Win32codecs and libfaad0 installed.

Any help greatly appreciated.

---

### Post by jimmyoo0 on 2010-03-05
just to add, the audio works when playing the same file in vlc.

---

### Post by jimmyoo0 on 2010-03-05
[SIZE=1]After a bit of hunting it looks as if mythbuntu repository is not compiled with [/SIZE][FONT=Verdana,Arial,Helvetica][SIZE=1][COLOR=black][FONT=Verdana,Arial,Helvetica][COLOR=black]--enable-libfaad 

Can this be enabled by the package manager or not? is this a big deal?

Looks like i might just have to compile this myself  :( oh well the joys of trunk i suppose


[/COLOR][/FONT][/COLOR][/SIZE][/FONT] [SIZE=1]mythfrontend --version
Please include all output in bug reports.
MythTV Version   : 23667
MythTV Branch    : trunk
Network Protocol : 56
Library API      : 0.23.20100302-1
QT Version       : 4.5.2
Options compiled in:
 linux debug using_oss using_alsa using_pulse using_jack using_pulseoutput using_backend using_dvb using_firewire using_frontend using_glx_proc_addr_arb using_hdhomerun using_hdpvr using_iptv using_ivtv using_joystick_menu using_lirc using_mheg using_opengl_video using_opengl_vsync using_qtdbus using_qtwebkit using_v4l using_x11 using_xrandr using_xv using_xvmc using_xvmc_vld using_xvmcw using_bindings_perl using_bindings_python using_opengl using_vdpau using_ffmpeg_threads using_libavc_5_3 using_live using_mheg

[/SIZE]

---

### Post by jimmyoo0 on 2010-03-06
just to let you all know compiling  with --enable[FONT=Verdana,Arial,Helvetica][SIZE=1][COLOR=black][FONT=Verdana,Arial,Helvetica][COLOR=black]-libfaad[/COLOR][/FONT][/COLOR][/SIZE][/FONT] fixed the problem, now i just have to fix a segfault problem

---

### Post by superm1 on 2010-03-06
> **jimmyoo0 said:**
> [SIZE=1]After a bit of hunting it looks as if mythbuntu repository is not compiled with [/SIZE][FONT=Verdana,Arial,Helvetica][SIZE=1][COLOR=black][FONT=Verdana,Arial,Helvetica][COLOR=black]--enable-libfaad 

Can this be enabled by the package manager or not? is this a big deal?

Looks like i might just have to compile this myself  :( oh well the joys of trunk i suppose


[/COLOR][/FONT][/COLOR][/SIZE][/FONT] [SIZE=1]mythfrontend --version
Please include all output in bug reports.
MythTV Version   : 23667
MythTV Branch    : trunk
Network Protocol : 56
Library API      : 0.23.20100302-1
QT Version       : 4.5.2
Options compiled in:
 linux debug using_oss using_alsa using_pulse using_jack using_pulseoutput using_backend using_dvb using_firewire using_frontend using_glx_proc_addr_arb using_hdhomerun using_hdpvr using_iptv using_ivtv using_joystick_menu using_lirc using_mheg using_opengl_video using_opengl_vsync using_qtdbus using_qtwebkit using_v4l using_x11 using_xrandr using_xv using_xvmc using_xvmc_vld using_xvmcw using_bindings_perl using_bindings_python using_opengl using_vdpau using_ffmpeg_threads using_libavc_5_3 using_live using_mheg

[/SIZE]

Your best bet is to apt-get source the builds and add the libfaad flag to the package and rebuild (debuild).  If that works, please file a bug and we can get the flag added to the build.

---

### Post by jimmyoo0 on 2010-03-06
I have tried to build from source with the [SIZE=1] [/SIZE][FONT=Verdana,Arial,Helvetica][SIZE=1][COLOR=black][FONT=Verdana,Arial,Helvetica][COLOR=black]--enable-libfaad flag,[/COLOR][/FONT][/COLOR][/SIZE][/FONT] but am getting a segfault when trying to play files with AAC audio play back is working fine on files with MP3 audio.

I cant seem to see what is wrong in the log's, I have attached log if someone could have a look and see what i have missed that would be great.

---

### Post by superm1 on 2010-03-06
> **jimmyoo0 said:**
> I have tried to build from source with the [SIZE=1] [/SIZE][FONT=Verdana,Arial,Helvetica][SIZE=1][COLOR=black][FONT=Verdana,Arial,Helvetica][COLOR=black]--enable-libfaad flag,[/COLOR][/FONT][/COLOR][/SIZE][/FONT] but am getting a segfault when trying to play files with AAC audio play back is working fine on files with MP3 audio.

I cant seem to see what is wrong in the log's, I have attached log if someone could have a look and see what i have missed that would be great.

Do you have the backtrace from the segfault?  That's the thing most likely to help in this failure.

---

### Post by jimmyoo0 on 2010-03-25
I have updated to the current 0.23-fixes branch and compiled from svn with all of the flags used in mythbuntu and the --enable-libfaad flag and can confirm that AAC audio worked and i have not found any segfaults or problems.

I think the segfaults i was seeing was related to ticket #8143 MHEG not working.

So we could add this flag to the mythbuntu daily builds? I think it would help quite a few people as i have seen a few posts lately from people trying to find out what was wrong when they have had this problem, also this codec is being used more and more as standard around the world.

---

### Post by nickrout on 2010-03-28
> **jimmyoo0 said:**
> I have updated to the current 0.23-fixes branch and compiled from svn with all of the flags used in mythbuntu and the --enable-libfaad flag and can confirm that AAC audio worked and i have not found any segfaults or problems.

I think the segfaults i was seeing was related to ticket #8143 MHEG not working.

So we could add this flag to the mythbuntu daily builds? I think it would help quite a few people as i have seen a few posts lately from people trying to find out what was wrong when they have had this problem, also this codec is being used more and more as standard around the world.

why on earth would mythbuntu be compiled without faad support?

---

### Post by jimmyoo0 on 2010-03-28
I have just added a comment to a bug report where faad support has just been added to the 10.04 build asking for it to be added to the 9.10 build of 0.23-fixes.

[https://bugs.launchpad.net/mythbuntu/+bug/546552](https://bugs.launchpad.net/mythbuntu/+bug/546552)

Not sure if this was the right way to do it or if i should have opened a new bug?

---

### Post by jimmyoo0 on 2010-03-29
Just an update, i updated to today's daily build 0.23-fixes23825 on karmic and the -libfaad flag has been enabled in the build.

I just want to say a big thanks to all the people that put in so much hard work to make mythtv and mythbuntu the great softare that it is.

---

