---
title: "Security Cameras"
date: 2014-02-21
forum: Multimedia Software
---

### Post by pendulous on 2014-02-21
Setting up UBUNTO for my home security system. I've already setup the hardware, connections, downloaded guvcview and it's dependencies. 

I launch guvcview as root ~/.local/share/applications:
```

[Desktop Entry]
Name=guvcview
Comment=Open guvcview as root
Exec=gksudo -k -u root guvcview
Icon=camera-web
Terminal=false
Type=Application
Categories=Application;System;
Name[en_US]=guvcview

```

But am unable to change any settings, sliders do not modify anything, buttons (-/+) do not move or change.

---

### Post by TheFu on 2014-02-21
Running most GUI programs as root is a mistake. If access to a specific device doesn't work without root, then fix the permissions, don't just run as root. Let me know if you need help for that.

I've used guvcview with a normal webcam and didn't see the issue. However, I won't run it as root.

You;ll want to wipe any config files, since they will be owned by root, not the real userid.  On the version installed here, settings are stored in .gpfl files and I just needed to add my userid to the "video" group.

---

### Post by pendulous on 2014-02-21
When I installed the GUI it hadn't responded to anything; though, I moved the pan slider a bit and it just reset the camera, but unable to do anything now. The sliders both display 36000 as a value, if I slide bar it does nothing, if I click the (-/+) it does nothing, if I attempt to manually adjust the number values it does nothhing. Brightness, Contrast, Saturation, White balance, Grain, Sharpness, Exposure all seem to work, but not Pan / Tilt. I also do not see a "zoom" option. The reason I set it to root is that the main guvcview site claims you need to run it as root at first, so I setup the script to run, since I'm having problems just getting it to work normally.

Where are these .gpfl files located? The only files I located were .guvcviewrc and deleted them both from root and usr directory.

---

### Post by TheFu on 2014-02-21
You installed from source, the Ubuntu repo or some PPA?
Also, the camera involved will matter, since not all drivers for all camera will be 100% supported. Mine are not.

I'm running  .... 
```
$ dpkg -l |grep guvcv
ii  guvcview                               1.5.3-0ubuntu1                                GTK+ base UVC Viewer
```

I've found that many developers, usually for website tools, find it easier to tell people the easy answer, not the correct answer. Understanding file permissions is all that is needed for access control of devices.

```
ls -l /dev/vid*
crw-rw----+  1 root video    81,   0 Feb 16 16:41 video0
```
group rw for "video" members. Simple.

---

### Post by pendulous on 2014-02-21
I installed via synaptic. 10x C920 hidden throughout the grounds with wireless access. They work fine on the previous windows machine that crashed, I just want to try out ubuntu and see how they run.... it'll cost me nothing vs the alternative.
```


$ dpkg -l |grep guvcv
ii  guvcview                                   1.5.3-0ubuntu1                      GTK+ base UVC Viewer
```
```

~$ ls -l /dev/vid*
crw-rw----+ 1 root video 81, 0 Feb 21 03:28 /dev/video0
```

---

### Post by pendulous on 2014-02-24
So is there a solution to get these cameras to work with the software properly?

GUVCVIEW: 
Unable to move Pan/Tilt... both register at 36000. Slider moves, but unable to change values as previously noted.

```
/# guvcview
guvcview 1.5.3

** (guvcview:16613): WARNING **: The connection is closed
ALSA lib pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.SB-XFi.pcm.hdmi.0:CARD=0,AES0=4,AES1=130,AES2=0,AES3=2'
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4720:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM hdmi
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.SB-XFi.pcm.hdmi.0:CARD=0,AES0=4,AES1=130,AES2=0,AES3=2'
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4720:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM hdmi
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.SB-XFi.pcm.modem.0:CARD=0'
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4720:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline:CARD=0,DEV=0
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.SB-XFi.pcm.modem.0:CARD=0'
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4720:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline:CARD=0,DEV=0
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.SB-XFi.pcm.modem.0:CARD=0'
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4720:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM phoneline
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.SB-XFi.pcm.modem.0:CARD=0'
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4720:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM phoneline
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
video device: /dev/video0 
Init. HD Pro Webcam C920 (location: usb-0000:00:0b.1-4)
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 160, height = 90 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 180 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 432, height = 240 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 640, height = 360 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 800, height = 448 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 800, height = 600 }
    Time interval between frame: 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 864, height = 480 }
    Time interval between frame: 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 960, height = 720 }
    Time interval between frame: 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1024, height = 576 }
    Time interval between frame: 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1280, height = 720 }
    Time interval between frame: 1/10, 2/15, 1/5, 
{ discrete: width = 1600, height = 896 }
    Time interval between frame: 2/15, 1/5, 
{ discrete: width = 1920, height = 1080 }
    Time interval between frame: 1/5, 
{ discrete: width = 2304, height = 1296 }
    Time interval between frame: 1/2, 
{ discrete: width = 2304, height = 1536 }
    Time interval between frame: 1/2, 
{ pixelformat = 'H264', description = 'H.264' }
   { not supported - request format(875967048) support at http://guvcview.sourceforge.net }
{ pixelformat = 'MJPG', description = 'MJPEG' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 160, height = 90 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 180 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 432, height = 240 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 640, height = 360 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 800, height = 448 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 800, height = 600 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 864, height = 480 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 960, height = 720 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1024, height = 576 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1280, height = 720 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1600, height = 896 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1920, height = 1080 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ pixelformat = 'RGB3', description = 'RGB3' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 160, height = 90 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 180 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 432, height = 240 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 640, height = 360 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 800, height = 448 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 800, height = 600 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 864, height = 480 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 960, height = 720 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1024, height = 576 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1280, height = 720 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1600, height = 896 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1920, height = 1080 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 2304, height = 1296 }
    Time interval between frame: 1/2, 
{ discrete: width = 2304, height = 1536 }
    Time interval between frame: 1/2, 
{ pixelformat = 'BGR3', description = 'BGR3' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 160, height = 90 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 180 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 432, height = 240 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 640, height = 360 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 800, height = 448 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 800, height = 600 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 864, height = 480 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 960, height = 720 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1024, height = 576 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1280, height = 720 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1600, height = 896 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1920, height = 1080 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 2304, height = 1296 }
    Time interval between frame: 1/2, 
{ discrete: width = 2304, height = 1536 }
    Time interval between frame: 1/2, 
{ pixelformat = 'YU12', description = 'YU12' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 160, height = 90 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 180 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 432, height = 240 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 640, height = 360 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 800, height = 448 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 800, height = 600 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 864, height = 480 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 960, height = 720 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1024, height = 576 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1280, height = 720 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1600, height = 896 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1920, height = 1080 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 2304, height = 1296 }
    Time interval between frame: 1/2, 
{ discrete: width = 2304, height = 1536 }
    Time interval between frame: 1/2, 
{ pixelformat = 'YV12', description = 'YV12' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 160, height = 90 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 180 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 432, height = 240 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 640, height = 360 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 800, height = 448 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 800, height = 600 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 864, height = 480 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 960, height = 720 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1024, height = 576 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1280, height = 720 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1600, height = 896 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1920, height = 1080 }
    Time interval between frame: 1/30, 1/24, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 2304, height = 1296 }
    Time interval between frame: 1/2, 
{ discrete: width = 2304, height = 1536 }
    Time interval between frame: 1/2, 
vid:046d 
pid:082d 
driver:uvcvideo
Adding control for Pan (relative)
UVCIOC_CTRL_ADD - Error: Inappropriate ioctl for device
checking format: 1196444237
VIDIOC_G_COMP:: Inappropriate ioctl for device
fps is set to 1/24
drawing controls


** (guvcview:16613): WARNING **: Unable to create Ubuntu Menu Proxy: The connection is closed
Checking video mode 640x480@32bpp : OK 
^Cwrite /root/.guvcviewrc OK
free controls
cleaned allocations - 100%
Closing portaudio ...OK
Closing GTK... OK
```


V4L2UCP:
Reacts the same as GUVCVIEW; though, sliders do not move, unable to modify (36000) values.

```
/# v4l2ucp

(process:16876): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(process:16876): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(process:16876): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
QGtkStyle was unable to detect the current GTK+ theme.
Qt: Session management error: None of the authentication protocols specified are supported

(process:16876): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```

Not a hardware issue, all 10 of these cameras were working under a Windows environment using a licensed software to manage them. I'm trying to do away with the paid license with ubuntu, so far doesn't seem it's possible.

---

