---
title: "Videos Missing - No Files Found"
date: 2008-07-10
forum: Mythbuntu
---

### Post by Chewiesw on 2008-07-10
Hi

Myth has lost all my videos. I could browse/play/see all my videos on the weekend and then they just disappeared. I get “Video root -no file found” message. I can't see videos in mythweb either .

(If I browse to /var/lib/mythtv/videos outside myth I do see the videos and I can play them.)

I run a complete front/backend and I have checked the video path and it is correct. (/var/lib/mythtv/videos).

I have manually re-applied the link in case it was wrong. Created a new directory and applied that.

I have also upgraded my system from 7.10 to 8.04 still nothing.

I have also tried uninstalled/re-installed mythvideo via synantic.

Pleeease help,

---

### Post by st2000 on 2008-07-11
> **Chewiesw said:**
> Hi

Myth has lost all my videos. I could browse/play/see all my videos on the weekend and then they just disappeared. I get “Video root -no file found” message. I can't see videos in mythweb either .

(If I browse to /var/lib/mythtv/videos outside myth I do see the videos and I can play them.)

I run a complete front/backend and I have checked the video path and it is correct. (/var/lib/mythtv/videos).

I have manually re-applied the link in case it was wrong. Created a new directory and applied that.

I have also upgraded my system from 7.10 to 8.04 still nothing.

I have also tried uninstalled/re-installed mythvideo via synantic.

Pleeease help,

Had the same happen.
I'm running a Debian system kernel: 2.6.25-2
MythTV Version   : export&#65533;&#65533;
MythTV Branch    : branches/release-0-21-fixes
Library API      : 0.21.20080304-1
Network Protocol : 40
Options compiled in:
 linux profile using_oss using_alsa using_arts using_jack using_backend using_dbox2 using_dvb using_firewire using_frontend using_hdhomerun using_iptv using_ivtv using_joystick_menu using_libfftw3 using_lirc using_opengl_vsync using_v4l using_x11 using_xrandr using_xv using_xvmc using_xvmcw using_xvmc_vld using_bindings_perl using_bindings_python using_opengl using_ffmpeg_threads using_libavc_5_3 using_live

Funny thing, the back end running on another Debian computer has a front end which can see and play the video files just fine!

Can anyone offer suggestions?

---

### Post by ironicirony on 2010-01-31
First off, it's nice to be able to help as opposed to asking for help ;)  If you are having the same issue I was - not being able to scan for new videos from the 'video manager' like was possible in every other version of mythtv I've used, as long as your paths are correct, try this.  Open 'Video Manager' and press the 'm' key.  It brings up a menu that shows all sorts of options - one being 'Scan for Changes.'  All of the sudden, all my videos from local sources, smb shares and nfs mounts showed up!  MAGIC!  Why it's like this - I'm not sure.  I'm going to try and see how I can get this to automate when 'Video Manager' is opened.  I'll post back if I find it.

Best 'o Luck.

II

---

### Post by tonycollinet on 2010-02-03
Thanks - that solved my problem as well.

---

### Post by slevinfcross on 2012-01-07
> **ironicirony said:**
> First off, it's nice to be able to help as opposed to asking for help ;)  If you are having the same issue I was - not being able to scan for new videos from the 'video manager' like was possible in every other version of mythtv I've used, as long as your paths are correct, try this.  Open 'Video Manager' and press the 'm' key.  It brings up a menu that shows all sorts of options - one being 'Scan for Changes.'  All of the sudden, all my videos from local sources, smb shares and nfs mounts showed up!  MAGIC!  Why it's like this - I'm not sure.  I'm going to try and see how I can get this to automate when 'Video Manager' is opened.  I'll post back if I find it.

Best 'o Luck.

II

Thank you very much! ;)

---

