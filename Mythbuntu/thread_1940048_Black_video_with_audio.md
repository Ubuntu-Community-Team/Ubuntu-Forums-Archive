---
title: "Black video with audio"
date: 2012-03-12
forum: Mythbuntu
---

### Post by davidstoll on 2012-03-12
This started yesterday.  When I try to watch live TV or recorded TV, I get audio, but black/blank video.

I did the normal updates with a reboot, but nothing other than that (i.e. no config changes).

This is a frontend (10.10) that has the black video problem, but the backend/frontend (10.10) plays video just fine.

Youtube plays back ok and so does VLC.

Could someone help me troubleshoot this?

---

### Post by nickrout on 2012-03-12
> **davidstoll said:**
> This started yesterday.  When I try to watch live TV or recorded TV, I get audio, but black/blank video.

I did the normal updates with a reboot, but nothing other than that (i.e. no config changes).

This is a frontend (10.10) that has the black video problem, but the backend/frontend (10.10) plays video just fine.

Youtube plays back ok and so does VLC.

Could someone help me troubleshoot this?

logs? (why do I have to say this so often??)

what did you update and what are the respective versions of key software (what was it before, what is it now?)

what video card and driver? is the driver working properly since the update?

none of us have access to yuor machine, and we are not mind readers.

---

### Post by davidstoll on 2012-03-13
It's a nettop, so it has an NVidia ION.

The "Additional Drivers" gui says it is "the current version", but I don't think that got upgraded.  I only did the normal package updates...chrome, myth related stuff, etc.

My partial log is attached.

---

### Post by BicyclerBoy on 2012-03-13
You have a heap of audio errors in the log..
You should re-scan the audio devices (mythfrontend setup menu) & make sure your selection is one on the list & check your video playback profiles..

---

### Post by davidstoll on 2012-03-13
> **BicyclerBoy said:**
> You have a heap of audio errors in the log..
You should re-scan the audio devices (mythfrontend setup menu) & make sure your selection is one on the list & check your video playback profiles..

I re-scanned and picked about 6 different devices, one at a time and re-checked.  Some gave me sound, but none gave me video.

---

### Post by davidstoll on 2012-03-13
> **davidstoll said:**
> I re-scanned and picked about 6 different devices, one at a time and re-checked.  Some gave me sound, but none gave me video.

I also tried NULL, but it didn't help.

I think it is related to VDPAU.  I just changed the rendering profile from VDPAU Slim to Normal and video played...well HD not very well, but it did play.

I also tried  other VDPAU profiles, but no luck.
Only works with non-VDPAU profiles.

---

### Post by nickrout on 2012-03-14
What version of mythtv are you running?

There are some changes in 0.25.

---

### Post by nickrout on 2012-03-14
also a log with -v playback may help.

---

### Post by davidstoll on 2012-03-14
> **nickrout said:**
> What version of mythtv are you running?

There are some changes in 0.25.

Forgot about that.... 0.24

---

### Post by davidstoll on 2012-03-14
Also, I can't vnc into the machine.  It asks for a password and then I get an I/O error.  Now that I think about it, that's probably related.

Maybe it was that darn solar flare...  ;)

---

### Post by davidstoll on 2012-03-14
> **nickrout said:**
> also a log with -v playback may help.

I'm so sorry, I don't know what that is.  :(

---

### Post by nickrout on 2012-03-14
> **davidstoll said:**
> I'm so sorry, I don't know what that is.  :(

try ```
mythfrontend --help 
```for details.

---

### Post by davidstoll on 2012-03-14
> **nickrout said:**
> try ```
mythfrontend --help 
```for details.

attached

---

### Post by nickrout on 2012-03-14
what options did you give? -v playback, or something more extensive?

---

### Post by davidstoll on 2012-03-15
> **nickrout said:**
> what options did you give? -v playback, or something more extensive?

That one was -v all.

I apologize, I thought playback was just a term used for more verbose output, so I chose all.

This one is -v playback.

---

### Post by davidstoll on 2012-03-17
Is there anything else I can round up to assist in the troubleshooting?

---

### Post by matt06 on 2012-03-17
I would dig deeper in the playback profiles, check the card setup in the backend, and check timezones/clocks both on the backend and frontend machines.

---

### Post by nickrout on 2012-03-17
> **matt06 said:**
> I would dig deeper in the playback profiles, check the card setup in the backend, and check timezones/clocks both on the backend and frontend machines.


Yes try a different playback profile.

Do you get the same result with recordings that wrere successfully made before the problem arose?

---

### Post by davidstoll on 2012-03-17
> **nickrout said:**
> Yes try a different playback profile.

Do you get the same result with recordings that wrere successfully made before the problem arose?

As I mentioned in post #6, I did try other playback profiles.  Specifically, "normal", but basically anything VDPAU has stopped working.

My backend/frontend doesn't have any VDPAU playback issues, nor does my other frontend.  This one was fine, but all of a sudden had this issue.

---

### Post by matt06 on 2012-03-17
You mentioned that this started after doing an update.  Can you post the contents of /var/log/apt/term.log or history.log ??

---

### Post by davidstoll on 2012-03-17
> **matt06 said:**
> You mentioned that this started after doing an update.  Can you post the contents of /var/log/apt/term.log or history.log ??

No problem, thanks for helping.

---

### Post by matt06 on 2012-03-18
It appears that both MythTV and the NVidia driver were updated.  I would try rolling back to your previous display driver.

Also, your not being able to vnc into the machine leads me to believe there are some other things going on here, i.e., the problem lies somewhere other than Myth itself.

---

### Post by davidstoll on 2012-03-18
> **matt06 said:**
> It appears that both MythTV and the NVidia driver were updated.  I would try rolling back to your previous display driver.

Also, your not being able to vnc into the machine leads me to believe there are some other things going on here, i.e., the problem lies somewhere other than Myth itself.

should I apt-get purge nvidia-current?
and then re-install nvidia-current or something else?

---

### Post by matt06 on 2012-03-18
I'm not sure.  If it was my box I wouldn't be afraid to try it, but I don't want to give bad advice either.  I'd search the forums on how to do it...I don't run 10.10 so I'd just be guessing.

---

### Post by davidstoll on 2012-03-18
> **matt06 said:**
> I'm not sure.  If it was my box I wouldn't be afraid to try it, but I don't want to give bad advice either.  I'd search the forums on how to do it...I don't run 10.10 so I'd just be guessing.

I purged the nvidia-current, rebooted and re-installed...no luck.

I also downloaded the lates Nvidia driver/script from the Nvidia web site and installed that...still no luck.

:(

---

### Post by BicyclerBoy on 2012-03-18
The driver sourced direct from nVidia needs to be installed in a console login session with X server stopped.
This method has build dependencies like kernel headers etc.
It is not for the novice or faint-hearted** but** it is extremely well documented..Study the nVidia readme/docs..

The main problem with this method is that your driver install is broken with every kernel update.

There are a few 3rd party ppa with later versions of nVidia graphics drivers.

Check your glx install:
glxinfo | grep OpenGL
check vdpau:
qvdpautest
vdpauinfo

The last 2 may need to be complied..

---

### Post by davidstoll on 2012-03-18
> **BicyclerBoy said:**
> The driver sourced direct from nVidia needs to be installed in a console login session with X server stopped.
This method has build dependencies like kernel headers etc.
It is not for the novice or faint-hearted** but** it is extremely well documented..Study the nVidia readme/docs..

The main problem with this method is that your driver install is broken with every kernel update.

There are a few 3rd party ppa with later versions of nVidia graphics drivers.

Check your glx install:
glxinfo | grep OpenGL
check vdpau:
qvdpautest
vdpauinfo

The last 2 may need to be complied..

Yes, I did a ctrl+alt+F1, stopped GDM and installed the driver/script from the Nvidia website, but it didn't help, so I removed it.

```
$ glxinfo | grep OpenGL
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: ION/PCI/SSE2
OpenGL version string: 3.3.0 NVIDIA 260.19.06
OpenGL shading language version string: 3.30 NVIDIA via Cg compiler
OpenGL extensions:
```

```
$ qvdpautest
qvdpautest: command not found
$ sudo apt-get install qvdpautest
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package qvdpautest
```

```
$ vdpauinfo
vdpauinfo: command not found
$ sudo apt-get install vdpauinfo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package vdpauinfo
```

---

### Post by BicyclerBoy on 2012-03-18
I think vdpauinfo is available in a ppa.

Does the OpenGL version string match the driver version installed as reported by nvidia-settings ?
Does it match with info in /var/log/Xorg.0.log ?

You can always pick the previous kernel at grub..
AFAIK The package managed nVidia driver installer inserts the nVidia kernel module into all the available kernel images..

Can you change your mythtv video playback profile to non-vdpau & test?
Do you have any additional parameters for VDPAU (i.e vdpaubuffers=nn)?

---

### Post by davidstoll on 2012-03-18
> **BicyclerBoy said:**
> I think vdpauinfo is available in a ppa.

Does the OpenGL version string match the driver version installed as reported by nvidia-settings ?
Does it match with info in /var/log/Xorg.0.log ?

You can always pick the previous kernel at grub..
AFAIK The package managed nVidia driver installer inserts the nVidia kernel module into all the available kernel images..

Can you change your mythtv video playback profile to non-vdpau & test?
Do you have any additional parameters for VDPAU (i.e vdpaubuffers=nn)?


I tried to boot to a previous kernel, but xwin didn't come up, I just got the black screen login.  I tried the last 2 listed in the grub menu.

vdpauinfo output attached.

I don't think I see wht you are looking for to match in Xorg.0.log and nvidia-settings.  Xorg.0.log attached.

As I mentioned a couple of times, if I change to a non-vdpau playback profile, it plays just fine, it's just that the CPU and fan go nuts.

I don't run anything special as far as extra parameters for VDPAU.

---

### Post by matt06 on 2012-03-20
I have an ION system running 10.04 and Myth 0.23 so I'll post what settings I have for my VDPAU playback profile (unsure of the NVIDIA driver version).  It may not be until tonight/tomorrow that I have time to check though.

---

### Post by davidstoll on 2012-03-20
> **matt06 said:**
> I have an ION system running 10.04 and Myth 0.23 so I'll post what settings I have for my VDPAU playback profile (unsure of the NVIDIA driver version).  It may not be until tonight/tomorrow that I have time to check though.

Thanks, but I have always just used one of the default profile options...Vdpau slim, normal or high.  Although, high never worked for me.

I never changed them.

---

### Post by matt06 on 2012-03-20
> **davidstoll said:**
> Thanks, but I have always just used one of the default profile options...Vdpau slim, normal or high.  Although, high never worked for me.

I never changed them.

Ok, understood.  FWIW, here's some stuff from mine.

```
mythuser@revo:/var/log/mythtv$ glxinfo | grep -i opengl
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: ION/PCI/SSE2
OpenGL version string: 3.3.0 NVIDIA 280.13
OpenGL shading language version string: 3.30 NVIDIA via Cg compiler
OpenGL extensions:
```
xorg.conf:

```
Section "Screen"
	Identifier	"Default Screen"
	Option	"AddARGBGLXVisuals"	"True"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```
and my frontend logged with -v playback (a few possibly relevant portions bolded and italicized, I have a bunch of lines following "TV: StartPlayer" that are not in yours, but maybe that's code changes between 0.23 and 0.24):

```
2012-03-20 18:02:24.733 mythfrontend version: branches/release-0-23-fixes [26863] www.mythtv.org
2012-03-20 18:02:24.734 Using runtime prefix = /usr
2012-03-20 18:02:24.735 Using configuration directory = /home/mythuser/.mythtv
2012-03-20 18:02:25.443 Empty LocalHostName.
2012-03-20 18:02:25.443 Using localhost value of revo
2012-03-20 18:02:25.444 Testing network connectivity to '192.168.0.107'
2012-03-20 18:02:25.597 New DB connection, total: 1
2012-03-20 18:02:25.615 Connected to database 'mythconverg' at host: 192.168.0.107
2012-03-20 18:02:25.616 Closing DB connection named 'DBManager0'
2012-03-20 18:02:25.648 ScreenSaverX11Private: Gnome screen saver support enabled
2012-03-20 18:02:25.650 DPMS is active.
2012-03-20 18:02:25.676 Primary screen: 0.
2012-03-20 18:02:25.692 Connected to database 'mythconverg' at host: 192.168.0.107
2012-03-20 18:02:25.695 Using screen 0, 1600x900 at 0,0
2012-03-20 18:02:25.793 Desktop video mode: 1600x900 59.9808 Hz
2012-03-20 18:02:25.843 max_width: 1600 max_height: 900
2012-03-20 18:02:25.846 MythUI Image Cache size set to 20971520 bytes
2012-03-20 18:02:25.904 AudioPulseUtil: Suspend Success
2012-03-20 18:02:25.905 user: 1000 effective user: 1000 before privileged thread
2012-03-20 18:02:25.905 user: 1000 effective user: 1000 after privileged thread
2012-03-20 18:02:25.905 user: 1000 effective user: 1000 run_priv_thread
2012-03-20 18:02:25.906 Enabled verbose msgs:  important general playback
2012-03-20 18:02:25.954 Primary screen: 0.
2012-03-20 18:02:25.956 Using screen 0, 1600x900 at 0,0
2012-03-20 18:02:25.976 Using theme base resolution of 1280x720
2012-03-20 18:02:26.035 LIRC: Successfully initialized '/dev/lircd' using '/home/mythuser/.mythtv/lircrc' config
2012-03-20 18:02:26.035 JoystickMenuThread Error: Joystick disabled - Failed to read /home/mythuser/.mythtv/joystickmenurc
2012-03-20 18:02:26.148 Using Frameless Window
2012-03-20 18:02:26.148 Using Full Screen Window
2012-03-20 18:02:26.982 Using the Qt painter
2012-03-20 18:02:27.685 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/MythCenter-wide/base.xml'
2012-03-20 18:02:27.712 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2012-03-20 18:02:27.839 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2012-03-20 18:02:27.857 Current MythTV Schema Version (DBSchemaVer): 1254
2012-03-20 18:02:27.877 VDP: decoder<->render support: ffmpeg      null xlib xshm xv-blit opengl vdpau
2012-03-20 18:02:27.877 VDP: decoder<->render support: libmpeg2    null xlib xshm xv-blit opengl vdpau
2012-03-20 18:02:27.878 VDP: decoder<->render support: xvmc        xvmc-blit
2012-03-20 18:02:27.878 VDP: decoder<->render support: xvmc-vld    xvmc-blit
2012-03-20 18:02:27.878 VDP: decoder<->render support: vdpau       vdpau
2012-03-20 18:02:27.888 VDP: Ignoring profile item 511 (OSD Renderer opengl is not supported w/renderer xvmc-blit (supported: chromakey,ia44blend))
2012-03-20 18:02:27.893 VDP: Ignoring profile item 509 (renderer quartz-blit is not supported w/decoder ffmpeg (supported: null,xlib,xshm,xv-blit,opengl,vdpau))
2012-03-20 18:02:27.902 VDP: Ignoring profile item 521 (renderer quartz-blit is not supported w/decoder ffmpeg (supported: null,xlib,xshm,xv-blit,opengl,vdpau))
2012-03-20 18:02:27.903 VDP: Ignoring profile item 522 (renderer quartz-blit is not supported w/decoder ffmpeg (supported: null,xlib,xshm,xv-blit,opengl,vdpau))
2012-03-20 18:02:27.907 VDP: Ignoring profile item 525 (renderer quartz-blit is not supported w/decoder ffmpeg (supported: null,xlib,xshm,xv-blit,opengl,vdpau))
2012-03-20 18:02:27.907 VDP: Ignoring profile item 526 (renderer quartz-blit is not supported w/decoder ffmpeg (supported: null,xlib,xshm,xv-blit,opengl,vdpau))
2012-03-20 18:02:27.911 VDP: Ignoring profile item 529 (renderer quartz-blit is not supported w/decoder ffmpeg (supported: null,xlib,xshm,xv-blit,opengl,vdpau))
2012-03-20 18:02:27.912 VDP: Ignoring profile item 530 (renderer quartz-blit is not supported w/decoder ffmpeg (supported: null,xlib,xshm,xv-blit,opengl,vdpau))
2012-03-20 18:02:29.431 Registering Internal as a media playback plugin.
2012-03-20 18:02:29.563 Cannot load language en_us for module mytharchive
2012-03-20 18:02:29.599 Cannot load language en_us for module mythbrowser
2012-03-20 18:02:29.609 Registering WebBrowser as a media playback plugin.
2012-03-20 18:02:29.609 Cannot load language en_us for module mythbrowser
2012-03-20 18:02:29.731 MonitorRegisterExtensions(0x100, gif,jpg,png)
2012-03-20 18:02:29.732 Cannot load language en_us for module mythgallery
2012-03-20 18:02:29.772 Cannot load language en_us for module mythmovies
2012-03-20 18:02:30.267 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2012-03-20 18:02:30.392 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2012-03-20 18:02:30.410 Cannot load language en_us for module mythmusic
2012-03-20 18:02:30.459 Cannot load language en_us for module mythnews
2012-03-20 18:02:30.558 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2012-03-20 18:02:30.644 Cannot load language en_us for module mythvideo
2012-03-20 18:02:30.703 Cannot load language en_us for module mythweather
2012-03-20 18:02:30.709 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/menu-ui.xml
2012-03-20 18:02:30.944 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2012-03-20 18:02:30.949 Found mainmenu.xml for theme 'MythCenter-wide'
2012-03-20 18:02:31.379 MythContext: Connecting to backend server: 192.168.0.107:6543 (try 1 of 1)
2012-03-20 18:02:31.381 Using protocol version 23056
2012-03-20 18:02:32.281 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2012-03-20 18:02:32.741 New DB connection, total: 2
2012-03-20 18:02:32.743 Connected to database 'mythconverg' at host: 192.168.0.107
2012-03-20 18:02:32.747 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/recordings-ui.xml
2012-03-20 18:02:35.727 TV: StartTV() -- begin
2012-03-20 18:02:35.753 TV: ctor -- begin
2012-03-20 18:02:35.777 TV: ctor -- end
2012-03-20 18:02:35.777 TV: Init -- begin
2012-03-20 18:02:35.779 TV: Init -- end channel groups
2012-03-20 18:02:35.826 TV: DrawUnusedRects() -- begin
2012-03-20 18:02:35.827 TV: DrawUnusedRects() -- end
2012-03-20 18:02:35.828 TV: DrawUnusedRects() -- begin
2012-03-20 18:02:35.828 TV: DrawUnusedRects() -- end
2012-03-20 18:02:35.905 TV: DrawUnusedRects() -- begin
2012-03-20 18:02:35.905 TV: DrawUnusedRects() -- end
2012-03-20 18:02:35.906 TV: Init -- end
2012-03-20 18:02:35.908 TV: tv->Playback() -- begin
2012-03-20 18:02:35.922 TV: tv->Playback() -- end
2012-03-20 18:02:35.922 TV: StartTV -- process events begin
2012-03-20 18:02:35.926 TV: HandleStateChange(0) -- begin
2012-03-20 18:02:35.927 TV: Attempting to change from None to WatchingPreRecorded
2012-03-20 18:02:35.943 RingBuf(myth://192.168.0.107:6543/2251_20100303020000.mpg): OpenFile(myth://192.168.0.107:6543/2251_20100303020000.mpg, 12)
2012-03-20 18:02:35.969 RingBuf(myth://192.168.0.107:6543/2251_20100303020000.mpg): CalcReadAheadThresh(0 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
[I][B]2012-03-20 18:02:36.026 TV: StartPlayer(0, WatchingPreRecorded, main) -- begin
2012-03-20 18:02:36.026 TV: Elapsed time since TV constructor was called: 273 ms
2012-03-20 18:02:36.643 [mpeg2video @ 0x228f960]mpeg_decode_postinit() failure
2012-03-20 18:02:36.644 [mpeg2video @ 0x228f960]mpeg_decode_postinit() failure
2012-03-20 18:02:36.644 [mpeg2video @ 0x228f960]mpeg_decode_postinit() failure
2012-03-20 18:02:36.645 [mpeg2video @ 0x228f960]mpeg_decode_postinit() failure
2012-03-20 18:02:36.645 [mpeg2video @ 0x228f960]mpeg_decode_postinit() failure
2012-03-20 18:02:36.645 [mpeg2video @ 0x228f960]mpeg_decode_postinit() failure
2012-03-20 18:02:36.646 [mpeg2video @ 0x228f960]mpeg_decode_postinit() failure
2012-03-20 18:02:36.646 [mpeg2video @ 0x228f960]mpeg_decode_postinit() failure
2012-03-20 18:02:36.646 [mpeg2video @ 0x228f960]mpeg_decode_postinit() failure
2012-03-20 18:02:36.647 [mpeg2video @ 0x228f960]mpeg_decode_postinit() failure
2012-03-20 18:02:36.647 [mpeg2video @ 0x228f960]mpeg_decode_postinit() failure
2012-03-20 18:02:36.648 [mpeg2video @ 0x228f960]mpeg_decode_postinit() failure
2012-03-20 18:02:36.648 [mpeg2video @ 0x228f960]mpeg_decode_postinit() failure
2012-03-20 18:02:36.651 [mpeg2video @ 0x228f960]mpeg_decode_postinit() failure
2012-03-20 18:02:37.487 AFD: Stream #0, has id 0x31 codec id MPEG2VIDEO, type Video, bitrate 10897600 at 0xab1e9500
2012-03-20 18:02:37.496 VDP: Accepting: cmp(>= 0 720) dec(vdpau) cpus(2) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpaubasicdoublerate,vdpaubasic) filt(vdpaucolorspace=auto)
2012-03-20 18:02:37.496 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(2) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpauadvanced) filt(vdpaucolorspace=auto)
2012-03-20 18:02:37.498 VDP: LoadBestPreferences(2048x2048, 0)
2012-03-20 18:02:37.498 VDP: LoadBestPreferences(2048x2048, 60)
2012-03-20 18:02:37.498 VDP: LoadBestPreferences(1920x1080, 60)
2012-03-20 18:02:37.506 VDP: Accepting: cmp(>= 0 720) dec(vdpau) cpus(2) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpaubasicdoublerate,vdpaubasic) filt(vdpaucolorspace=auto)
2012-03-20 18:02:37.506 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(2) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpauadvanced) filt(vdpaucolorspace=auto)
2012-03-20 18:02:37.506 VDP: LoadBestPreferences(2048x2048, 0)
2012-03-20 18:02:37.508 VDP: LoadBestPreferences(2048x2048, 60)
2012-03-20 18:02:37.508 VDP: LoadBestPreferences(1920x1080, 60)
2012-03-20 18:02:37.517 VDP: Accepting: cmp(>= 0 720) dec(vdpau) cpus(2) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpaubasicdoublerate,vdpaubasic) filt(vdpaucolorspace=auto)
2012-03-20 18:02:37.517 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(2) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpauadvanced) filt(vdpaucolorspace=auto)
2012-03-20 18:02:37.517 VDP: LoadBestPreferences(2048x2048, 0)
2012-03-20 18:02:37.517 VDP: LoadBestPreferences(2048x2048, 60)
2012-03-20 18:02:37.517 VDP: LoadBestPreferences(1920x1080, 60)
2012-03-20 18:02:37.522 Using 1 CPUs for decoding
2012-03-20 18:02:37.522 AFD: InitVideoCodec() 0xaa67c6d0 id(MPEG2VIDEO) type (Video).
2012-03-20 18:02:37.522 detectInterlace(Detect Scan, Interlaced Scan, 29.97, 1080) ->Interlaced Scan
[/B][/I]2012-03-20 18:02:37.523 AFD: EIA-708 caption service #1 is in the English language.
2012-03-20 18:02:37.524 AFD: Using vdpau for video decoding
2012-03-20 18:02:37.524 AFD: Looking for decoder for MPEG2VIDEO
2012-03-20 18:02:37.524 AFD: Opened codec 0xaa67c6d0, id(MPEG2VIDEO) type(Video)
2012-03-20 18:02:37.524 AFD: Stream #1, has id 0x34 codec id AC3, type Audio, bitrate 192000 at 0xaa67cc80
2012-03-20 18:02:37.525 AFD: codec AC3 has 2 channels
2012-03-20 18:02:37.525 AFD: Looking for decoder for AC3
2012-03-20 18:02:37.526 AFD: Opened codec 0xab1ee290, id(AC3) type(Audio)
2012-03-20 18:02:37.526 AFD: Stream #2, has id 0x35 codec id AC3, type Audio, bitrate 192000 at 0xab1ee840
2012-03-20 18:02:37.526 AFD: codec AC3 has 2 channels
2012-03-20 18:02:37.526 AFD: Looking for decoder for AC3
2012-03-20 18:02:37.528 AFD: Opened codec 0xaa6b1390, id(AC3) type(Audio)
2012-03-20 18:02:37.528 AFD: Stream #3, has id 0x110 codec id DVB_VBI, type Data, bitrate 0 at 0xaa6b1940
2012-03-20 18:02:37.529 AFD: data codec (Data)
2012-03-20 18:02:37.529 RingBuf(myth://192.168.0.107:6543/2251_20100303020000.mpg): CalcReadAheadThresh(0 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2012-03-20 18:02:37.602 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2012-03-20 18:02:37.602 Opening ALSA audio device 'default'.
2012-03-20 18:02:37.627 mixer unable to find control Master 1
2012-03-20 18:02:37.629 Dec: Trying to select track (w/lang)
2012-03-20 18:02:37.630 Dec: Selecting first track
2012-03-20 18:02:37.630 Dec: Selected track #1 in the Unknown language(0)
2012-03-20 18:02:37.630 Dec: Selected track #1 in the English language(6647399)
2012-03-20 18:02:37.630 Dec: Resyncing position map. posmapStarted = 0 livetv(0) watchingRec(0)
2012-03-20 18:02:37.718 Position map filled from DB to: 108074
2012-03-20 18:02:37.720 Dec: SyncPositionMap prerecorded, from DB: 7205 entries
2012-03-20 18:02:37.720 Dec: SyncPositionMap, new totframes: 108074, new length: 3606, posMap size: 7205
2012-03-20 18:02:37.720 AFD: Position map found
2012-03-20 18:02:37.720 AFD: Successfully opened decoder for file: "myth://192.168.0.107:6543/2251_20100303020000.mpg". novideo(0)
2012-03-20 18:02:37.725 AO: Using time stretch 1.2
[I][B]2012-03-20 18:02:37.751 VideoOutput: Allowed renderers: vdpau
2012-03-20 18:02:37.751 VideoOutput: Allowed renderers (filt: vdpau): vdpau[/B][/I]
2012-03-20 18:02:37.756 VDP: Accepting: cmp(>= 0 720) dec(vdpau) cpus(2) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpaubasicdoublerate,vdpaubasic) filt(vdpaucolorspace=auto)
2012-03-20 18:02:37.756 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(2) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpauadvanced) filt(vdpaucolorspace=auto)
2012-03-20 18:02:37.757 VDP: LoadBestPreferences(2048x2048, 0)
2012-03-20 18:02:37.757 VDP: LoadBestPreferences(2048x2048, 60)
2012-03-20 18:02:37.757 VDP: LoadBestPreferences(1920x1080, 60)
2012-03-20 18:02:37.757 VideoOutput: Preferred renderer: vdpau
2012-03-20 18:02:37.757 VideoOutput: Trying video renderer: 'vdpau'
2012-03-20 18:02:37.779 VDP: Accepting: cmp(>= 0 720) dec(vdpau) cpus(2) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpaubasicdoublerate,vdpaubasic) filt(vdpaucolorspace=auto)
2012-03-20 18:02:37.780 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(2) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpauadvanced) filt(vdpaucolorspace=auto)
2012-03-20 18:02:37.780 VDP: LoadBestPreferences(2048x2048, 0)
2012-03-20 18:02:37.780 VDP: LoadBestPreferences(2048x2048, 60)
2012-03-20 18:02:37.791 VideoOutWindow::SetPIPState. pip_state: 0]
2012-03-20 18:02:37.792 Display Rect  left: 0, top: 112, width: 1600, height: 675, aspect: 1.33333
2012-03-20 18:02:37.792 Video Rect    left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
2012-03-20 18:02:37.792 VDP: LoadBestPreferences(1920x1088, 60)
2012-03-20 18:02:37.792 Display Rect  left: 0, top: 112, width: 1600, height: 675, aspect: 1.33333
2012-03-20 18:02:37.792 Video Rect    left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
2012-03-20 18:02:37.792 VDP: SetVideoRenderer(vdpau)
2012-03-20 18:02:37.792 VDP: SetVideoRender(vdpau) == GetVideoRenderer()
2012-03-20 18:02:37.794 VideoOutput: Pixel dimensions: Screen 1600x900, window 1600x900
2012-03-20 18:02:37.795 VideoOutput: Actual display dimensions: 442x251 mm  Aspect: 1.76096
2012-03-20 18:02:37.795 VideoOutput: Estimated window dimensions: 442x251 mm  Aspect: 1.76096
2012-03-20 18:02:38.557 VDPAU: Created 2 output surfaces.
2012-03-20 18:02:38.557 VDPAU: Set colorkey to 0x20202
2012-03-20 18:02:38.557 VDPAU: Version 1
[I][B]2012-03-20 18:02:38.557 VDPAU: Information NVIDIA VDPAU Driver Shared Library  280.13  Wed Jul 27 17:18:15 PDT 2011
2012-03-20 18:02:38.558 VDPAU: HQ scaling level 1 of 9 available.
2012-03-20 18:02:38.558 VDPAU: MPEG4 hardware acceleration supported.[/B][/I]
2012-03-20 18:02:38.558 VDPAU: Created VDPAU render device 1600x900
2012-03-20 18:02:38.568 VidOutVDPAU: Created VDPAU osd (1600x900)
2012-03-20 18:02:38.970 VidOutVDPAU: PictureAttributes: Brightness, Contrast, Colour, Hue
2012-03-20 18:02:38.987 VidOutVDPAU: Using ITU BT.709 colorspace
2012-03-20 18:02:38.987 Display Rect  left: 0, top: 0, width: 1600, height: 900, aspect: 1.77778
2012-03-20 18:02:38.987 Video Rect    left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
***2012-03-20 18:02:38.987 VidOutVDPAU: Created VDPAU context (GPU decode)***
2012-03-20 18:02:38.994 Over/underscan. V: 0, H: 0
2012-03-20 18:02:38.994 Display Rect  left: 0, top: 0, width: 1600, height: 900, aspect: 1.77778
2012-03-20 18:02:38.994 Video Rect    left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
2012-03-20 18:02:38.994 VDP: LoadBestPreferences(1920x1088, 29.97)
2012-03-20 18:02:38.994 NVP(0): Forcing decode extra audio option on (Video method requires it).
2012-03-20 18:02:38.997 FilterManager: GetFilterInfo(convert) returning: 0x0
2012-03-20 18:02:38.997 NVP(0): LoadFilters('vdpaucolorspace=auto'..) -> 0x0
2012-03-20 18:02:39.000 OSD Theme Dimensions W: 640 H: 480
2012-03-20 18:02:39.674 playCtx: StartDecoderThread(): took 1949 ms to start player.
2012-03-20 18:02:39.674 NVP(0): ClearAfterSeek(1)
2012-03-20 18:02:39.674 VidOutVDPAU: ClearAfterSeek()
2012-03-20 18:02:39.674 TV: StartPlayer(0, WatchingPreRecorded, main) -- end ok
2012-03-20 18:02:39.674 VidOutVDPAU: DiscardFrames(0)
2012-03-20 18:02:39.674 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAA
2012-03-20 18:02:39.675 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAA -- done
2012-03-20 18:02:39.675 VidOutVDPAU: DiscardFrames() 3: AAAAAAAAAAAAAAAAA -- done()
2012-03-20 18:02:39.676 TV: Changing from None to WatchingPreRecorded
2012-03-20 18:02:39.679 Realtime priority would require SUID as root.
2012-03-20 18:02:39.679 VDP: GetFilteredDeint() : vdpau -> 'vdpaubasicdoublerate'
2012-03-20 18:02:39.681 VidOutVDPAU: Enabled deinterlacing.
2012-03-20 18:02:39.682 TV: HandleStateChange(0) -- end
2012-03-20 18:02:39.686 DRMVideoSync: Could not open device /dev/dri/card0, No such file or directory
2012-03-20 18:02:39.686 RTCVideoSync: Could not open /dev/rtc, Permission denied.
2012-03-20 18:02:39.687 Set video sync frame interval to 33366
2012-03-20 18:02:39.696 Video timing method: USleep with busy wait
2012-03-20 18:02:39.696 Refresh rate: 16672, frame interval: 33366
2012-03-20 18:02:39.698 NVP(0): Waiting for prebuffer..  0 LAAAAAAAAAAAAAAAA
2012-03-20 18:02:39.718 VidOutVDPAU: Created VDPAU decoder (2 ref frames)
2012-03-20 18:02:39.719 Detect Letterbox: The source is not a supported frame format (was 11)
2012-03-20 18:02:39.728 Set video sync frame interval to 33366
2012-03-20 18:02:39.728 AFD: DoFastForward(3370 (1), do discard frames)
2012-03-20 18:02:39.733 Enabled deinterlacing
2012-03-20 18:02:39.733 Dec: DoFastForward(3370 (1), do discard frames)
2012-03-20 18:02:39.733 Dec: FindPosition(3370, search not adjusted) --> 
			[224:3360(90595132),225:3375(90895180)]
2012-03-20 18:02:39.734 AFD: SeekReset(3375, 0, do flush, do discard)
2012-03-20 18:02:39.735 AFD: SeekReset() flushing
2012-03-20 18:02:39.736 ScreenSaverX11Private: DPMS Deactivated 1
2012-03-20 18:02:39.737 ScreenSaverX11Private: ResetTimer -- begin
2012-03-20 18:02:39.737 ScreenSaverX11Private: StopTimer
2012-03-20 18:02:39.739 ScreenSaverX11Private: StartTimer
2012-03-20 18:02:39.739 ScreenSaverX11Private: ResetTimer -- end
2012-03-20 18:02:39.768 VidOutVDPAU: DiscardFrames(1)
2012-03-20 18:02:39.769 VideoBuffers::DiscardFrames(1): UAAAAAAAAAAAAAAAA
2012-03-20 18:02:39.769 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAA -- done()
2012-03-20 18:02:39.769 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAA -- done
2012-03-20 18:02:39.770 VidOutVDPAU: DiscardFrames() 3: AAAAAAAAAAAAAAAAA -- done()
2012-03-20 18:02:39.770 NVP(0): ClearAfterSeek(0)
2012-03-20 18:02:39.775 VDPAU: Added 2 output surfaces (total 4, max 4)
2012-03-20 18:02:39.781 NVP(0): Changing speed to 1.2
2012-03-20 18:02:39.782 RingBuf(myth://192.168.0.107:6543/2251_20100303020000.mpg): CalcReadAheadThresh(0 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2012-03-20 18:02:39.781 NVP(0): Waiting for prebuffer..  0 AAAAAAAAAAAAAAAAA
2012-03-20 18:02:39.782 NVP(0): DoPlay() -- begin
2012-03-20 18:02:39.782 NVP(0): DoPlay: rate: 29.97 speed: 1.2 skip: 1 => new interval 27805
2012-03-20 18:02:39.782 VDP: LoadBestPreferences(1920x1088, 35.964)
2012-03-20 18:02:39.784 VDP: GetFilteredDeint(vdpaubasic) : vdpau -> 'vdpaubasic'
2012-03-20 18:02:39.785 VidOutVDPAU: Enabled deinterlacing.
2012-03-20 18:02:39.786 Set video sync frame interval to 27805
2012-03-20 18:02:39.786 NVP(0): Stretch Factor 1.2, disable passthru 
2012-03-20 18:02:39.786 NVP(0): DoPlay() -- setting unpaused
2012-03-20 18:02:39.802 Enabled deinterlacing
2012-03-20 18:02:39.866 PlaybackBoxHelper: Requesting preview for 'myth://192.168.0.107:6543/2251_20100303020000.mpg.png'
2012-03-20 18:02:39.867 PlaybackBoxHelper: Requested preview for 'myth://192.168.0.107:6543/2251_20100303020000.mpg.png'
2012-03-20 18:02:39.922 MythContext: Connecting to backend server: 192.168.0.107:6543 (try 1 of 1)
2012-03-20 18:02:39.924 Using protocol version 23056
2012-03-20 18:02:40.350 Saved: '/home/mythuser/.mythtv/remotecache/2251_20100303020000.mpg.png'
2012-03-20 18:02:40.350 PlaybackBoxHelper: Preview for 'myth://192.168.0.107:6543/2251_20100303020000.mpg' ready
2012-03-20 18:02:40.351 PlaybackBoxHelper: Preview for 'myth://192.168.0.107:6543/2251_20100303020000.mpg.png' done
2012-03-20 18:02:40.356 Preview: previewThreadDone took 5ms
'video_output' mean = '28790.97', std. dev. = '6118.20', fps = '34.73'
2012-03-20 18:02:43.336 NVP(0): Video is 3.11012 frames behind audio (too slow), dropping frame to catch up.
2012-03-20 18:02:43.371 NVP(0): Video is 3.48344 frames behind audio (too slow), dropping frame to catch up.
2012-03-20 18:02:43.406 NVP(0): Video is 3.84434 frames behind audio (too slow), dropping frame to catch up.
2012-03-20 18:02:43.441 NVP(0): Video is 4.18698 frames behind audio (too slow), dropping frame to catch up.
2012-03-20 18:02:43.476 NVP(0): Video is 4.52487 frames behind audio (too slow), dropping frame to catch up.
2012-03-20 18:02:43.511 NVP(0): Video is 4.84122 frames behind audio (too slow), dropping frame to catch up.
2012-03-20 18:02:43.546 NVP(0): Video is 5.16839 frames behind audio (too slow), dropping frame to catch up.
2012-03-20 18:02:43.581 NVP(0): Video is 5.4947 frames behind audio (too slow), dropping frame to catch up.
2012-03-20 18:02:43.616 NVP(0): Video is 5.81136 frames behind audio (too slow), dropping frame to catch up.
2012-03-20 18:02:43.651 NVP(0): Video is 6.12976 frames behind audio (too slow), dropping frame to catch up.
2012-03-20 18:02:43.686 NVP(0): Video is 6.44949 frames behind audio (too slow), dropping frame to catch up.
2012-03-20 18:02:43.720 NVP(0): Video is 6.76123 frames behind audio (too slow), dropping frame to catch up.
2012-03-20 18:02:43.755 NVP(0): Video is 7.07596 frames behind audio (too slow), dropping frame to catch up.
2012-03-20 18:02:43.789 NVP(0): Video is 7.38392 frames behind audio (too slow), dropping frame to catch up.
2012-03-20 18:02:43.824 NVP(0): Video is 7.66884 frames behind audio (too slow), dropping frame to catch up.
2012-03-20 18:02:43.858 NVP(0): Video is 7.96346 frames behind audio (too slow), dropping frame to catch up.
2012-03-20 18:02:43.893 NVP(0): Video is 8.24737 frames behind audio (too slow), dropping frame to catch up.
2012-03-20 18:02:43.927 NVP(0): Video is 8.5412 frames behind audio (too slow), dropping frame to catch up.
2012-03-20 18:02:43.962 NVP(0): Video is 8.84251 frames behind audio (too slow), dropping frame to catch up.
2012-03-20 18:02:43.996 NVP(0): Video is 9.12242 frames behind audio (too slow), dropping frame to catch up.
2012-03-20 18:02:44.031 NVP(0): Video is 9.41327 frames behind audio (too slow), dropping frame to catch up.
2012-03-20 18:02:44.065 NVP(0): Video is 9.70336 frames behind audio (too slow), dropping frame to catch up.
2012-03-20 18:02:44.099 NVP(0): Video is 9.98385 frames behind audio (too slow), dropping frame to catch up.
2012-03-20 18:02:44.134 NVP(0): Video is 10.2751 frames behind audio (too slow), dropping frame to catch up.
2012-03-20 18:02:44.135 NVP(0): Video is 10.5566 frames behind audio (too slow), dropping frame to catch up.
2012-03-20 18:02:44.135 NVP(0): Video is 10.4799 frames behind audio (too slow), dropping frame to catch up.
2012-03-20 18:02:44.136 NVP(0): Video is 10.1347 frames behind audio (too slow), dropping frame to catch up.
2012-03-20 18:02:44.136 NVP(0): Video is 9.57004 frames behind audio (too slow), dropping frame to catch up.
2012-03-20 18:02:44.136 NVP(0): Video is 8.84988 frames behind audio (too slow), dropping frame to catch up.
2012-03-20 18:02:44.136 NVP(0): Video is 8.01305 frames behind audio (too slow), dropping frame to catch up.
2012-03-20 18:02:44.136 NVP(0): Video is 7.07973 frames behind audio (too slow), dropping frame to catch up.
2012-03-20 18:02:44.137 NVP(0): Video is 6.09203 frames behind audio (too slow), dropping frame to catch up.
2012-03-20 18:02:44.137 NVP(0): Video is 5.05452 frames behind audio (too slow), dropping frame to catch up.
2012-03-20 18:02:44.137 NVP(0): Video is 3.97069 frames behind audio (too slow), dropping frame to catch up.
'video_output' mean = '27801.85', std. dev. = '11233.51', fps = '35.97'
'video_output' mean = '27802.62', std. dev. = '48.71', fps = '35.97'
2012-03-20 18:02:50.891 NVP(0): 400 interlaced frames seen.
'video_output' mean = '27802.31', std. dev. = '49.38', fps = '35.97'
2012-03-20 18:02:52.668 TV: SetActive(0,w/o OSD) 0 -> 0 -- begin
2012-03-20 18:02:52.669 TV: SetActive(0,w/o OSD) 0 -> 0 -- end
2012-03-20 18:02:52.709 TV: HandleStateChange(0) -- begin
2012-03-20 18:02:52.709 TV: Attempting to change from WatchingPreRecorded to None
2012-03-20 18:02:52.710 TV: StopStuff() for player ctx 0 -- begin
2012-03-20 18:02:52.710 TV: SetActive(0,w/o OSD) 0 -> 0 -- begin
2012-03-20 18:02:52.710 TV: SetActive(0,w/o OSD) 0 -> 0 -- end
2012-03-20 18:02:52.710 TV: StopStuff(): stopping ring buffer
2012-03-20 18:02:52.710 NVP(0): Exited decoder loop.
2012-03-20 18:02:52.727 VidOutVDPAU: DiscardFrames(1)
2012-03-20 18:02:52.727 VideoBuffers::DiscardFrames(1): UuAUUuDULUDDUUUAU
2012-03-20 18:02:52.727 VideoBuffers::DiscardFrames(): AAAAAADAAADDAAAAA -- done()
2012-03-20 18:02:52.728 VideoBuffers::DiscardFrames(1): AAAAAADAAADDAAAAA -- done
2012-03-20 18:02:52.728 VidOutVDPAU: DiscardFrames() 3: AAAAAADAAADDAAAAA -- done()
2012-03-20 18:02:52.756 TV: StopStuff(): stopping player
2012-03-20 18:02:52.756 TV: StopStuff() -- end
2012-03-20 18:02:52.756 TV: Changing from WatchingPreRecorded to None
2012-03-20 18:02:52.757 TV: HandleStateChange(0) -- end
2012-03-20 18:02:52.757 TV: StartTV -- process events end
2012-03-20 18:02:52.757 TV: StartTV -- process events 2 begin
2012-03-20 18:02:52.757 ScreenSaverX11Private: DPMS Reactivated 1
2012-03-20 18:02:52.758 ScreenSaverX11Private: StopTimer
2012-03-20 18:02:52.769 TV: StartTV -- process events 2 end
2012-03-20 18:02:52.771 TV::~TV() -- begin
2012-03-20 18:02:52.771 PlaybackBoxHelper: Requesting preview for 'myth://192.168.0.107:6543/2251_20100303020000.mpg.png'
2012-03-20 18:02:52.772 PlaybackBoxHelper: Requested preview for 'myth://192.168.0.107:6543/2251_20100303020000.mpg.png'
2012-03-20 18:02:52.772 MythContext: Connecting to backend server: 192.168.0.107:6543 (try 1 of 1)
2012-03-20 18:02:52.774 Using protocol version 23056
2012-03-20 18:02:52.834 TV::~TV() -- lock
2012-03-20 18:02:52.940 TV::~TV() -- end
2012-03-20 18:02:52.943 TV: StartTV -- end
2012-03-20 18:02:53.011 PlaybackBoxHelper: Requesting preview for 'myth://192.168.0.107:6543/2251_20100303020000.mpg.png'
2012-03-20 18:02:53.011 PlaybackBoxHelper: Requested preview for 'myth://192.168.0.107:6543/2251_20100303020000.mpg.png'
2012-03-20 18:02:53.012 MythContext: Connecting to backend server: 192.168.0.107:6543 (try 1 of 1)
2012-03-20 18:02:53.014 Using protocol version 23056
2012-03-20 18:02:53.035 PlaybackBoxHelper: Requesting preview for 'myth://192.168.0.107:6543/2251_20100303020000.mpg.png'
2012-03-20 18:02:53.035 PlaybackBoxHelper: Requested preview for 'myth://192.168.0.107:6543/2251_20100303020000.mpg.png'
2012-03-20 18:02:53.036 MythContext: Connecting to backend server: 192.168.0.107:6543 (try 1 of 1)
2012-03-20 18:02:53.038 Using protocol version 23056
2012-03-20 18:02:53.158 Saved: '/home/mythuser/.mythtv/remotecache/2251_20100303020000.mpg.png'
2012-03-20 18:02:53.158 PlaybackBoxHelper: Preview for 'myth://192.168.0.107:6543/2251_20100303020000.mpg' ready
2012-03-20 18:02:53.160 PlaybackBoxHelper: Preview for 'myth://192.168.0.107:6543/2251_20100303020000.mpg.png' done
2012-03-20 18:02:53.165 Preview: previewThreadDone took 5ms
2012-03-20 18:02:53.440 Saved: '/home/mythuser/.mythtv/remotecache/2251_20100303020000.mpg.png'
2012-03-20 18:02:53.442 Saved: '/home/mythuser/.mythtv/remotecache/2251_20100303020000.mpg.png'
2012-03-20 18:02:55.764 AudioPulseUtil: Resume Success
2012-03-20 18:02:55.765 Deleting UPnP client...
```
And this stuff in your log jumps out at me...bolded lines in particular.

```
2012-03-15 07:31:29.371 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2012-03-15 07:31:29.372 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2012-03-15 07:31:29.379 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2012-03-15 07:31:29.379 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
...
2012-03-15 07:31:48.934 Warning! Time difference between the master backend and this system is 30 seconds.
...
[I][B]2012-03-15 07:32:03.196 VideoOutput: Allowed renderers: xv-blit,xshm,xlib,opengl,vdpau
2012-03-15 07:32:03.196 VideoOutput: Allowed renderers (filt: dummy): xlib,xshm,xv-blit,opengl,vdpau[/B][/I]
...
[I][B]2012-03-15 07:32:04.111 VDPAU: Information NVIDIA VDPAU Driver Shared Library  260.19.06  Mon Sep 13 07:05:35 PDT 2010
2012-03-15 07:32:04.111 VDPAU: HQ Scaling not supported.
2012-03-15 07:32:04.111 VDPAU: MPEG4 hardware acceleration not supported.[/B][/I]
...
***2012-03-15 07:32:04.260 VidOutVDPAU: Created VDPAU context (software decode)***
```
Seems that your driver may not be working properly??

---

### Post by davidstoll on 2012-03-20
Matt06, you have a Revo too?  Cool!  Good little machine for the price.

Anyway, what seems to stand out to me is that I have driver v260 and your's is 280.  I have nvidia-current, so how do I get that updated.  The "additional drivers" gui doesn't show anything else and I've do apt-get updates and upgrades quite often.

Can you help me update that and lets see what happens....?

---

### Post by nickrout on 2012-03-20
> **davidstoll said:**
> Matt06, you have a Revo too?  Cool!  Good little machine for the price.

Anyway, what seems to stand out to me is that I have driver v260 and your's is 280.  I have nvidia-current, so how do I get that updated.  The "additional drivers" gui doesn't show anything else and I've do apt-get updates and upgrades quite often.

Can you help me update that and lets see what happens....?

As has been said earlier in the thread, there is a ppa for more up to date nvidia drivers.

---

### Post by davidstoll on 2012-03-20
> **nickrout said:**
> As has been said earlier in the thread, there is a ppa for more up to date nvidia drivers.

Actually, there are several and a couple I tried didn't work.

So, I kept trying after the post above and I found this one:
[http://www.ubuntuupdates.org/ppa/ubuntu-x-swat](http://www.ubuntuupdates.org/ppa/ubuntu-x-swat)

And I'm up to driver 295, but I still have an issue.

---

### Post by matt06 on 2012-03-21
I would venture to guess that the driver module isn't getting loaded.

Can you bring up the NVidia-settings GUI at all?  What does dmesg look like?  I can look at my Revo again tomorrow, but I did check the packages earlier.  Ignore the karmic stuff, I believe it's just leftover from upgrading.  Now that I look at it, perhaps mine is in a broken state as well and just works by sheer luck ;)

dpkg -l | grep -i nvidia

```
ii  envyng-core                          2.0.1ubuntu3                                    install the ATI or the NVIDIA driver
ii  libvdpau1                            0.4-3~lucid~nvidiavdpauppa1                     Video Decode and Presentation API for Unix (
ii  nvidia-173-modaliases                173.14.22-0ubuntu11                             Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-185-modaliases                280.13-0ubuntu1~lucid~xup2                      Transitional package for nvidia-185-modalias
ii  nvidia-190-modaliases                190.53-0ubuntu1~karmic~nvidiavdpauppa14         Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-195-modaliases                195.36.15-0ubuntu1~karmic~nvidiavdpauppa2       Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-96-modaliases                 96.43.17-0ubuntu1.1                             Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-common                        0.2.23                                          Find obsolete NVIDIA drivers
ii  nvidia-current                       280.13-0ubuntu1~lucid~xup2                      NVIDIA binary Xorg driver, kernel module and
ii  nvidia-current-modaliases            280.13-0ubuntu1~lucid~xup2                      Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-settings                      195.36.08-0ubuntu2                              Tool of configuring the NVIDIA graphics driv

```

dpkg -l | grep -i vdpau

```
ii  libvdpau1                            0.4-3~lucid~nvidiavdpauppa1                     Video Decode and Presentation API for Unix (
ii  nvidia-190-modaliases                190.53-0ubuntu1~karmic~nvidiavdpauppa14         Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-195-modaliases                195.36.15-0ubuntu1~karmic~nvidiavdpauppa2       Modaliases for the NVIDIA binary X.Org drive

```

---

### Post by nickrout on 2012-03-21
lsmod will tel lyou whether the nvidia module is loaded.

/var/log/Xorg.0.org will also tell you what module is being used.

---

### Post by BicyclerBoy on 2012-03-21
As Nick suggests..
post the /var/log/Xorg.0.log again..because the driver has been changed.

Are you using 1.2x playback speed-up ?
Can you reset to 1x.

Are you using vdpau profile additional cmds?
I don't think your GPU supports HQ scaling & has other restrictions.
Or is this ION2?
Your 260 driver log states no HQ scaling.
Your 285 driver log states that HQ scale is avail level 1. 

There is a message in one of your -v playback logs about invalid picture format/size.

With recent graphics drivers/Xorg, you can remove the /etc/X11/xorg.conf.
You do not need Load "glx" etc.

---

### Post by matt06 on 2012-03-21
davidstoll's (OP) logs are a few pages back, I posted mine just for comparing.

---

### Post by BicyclerBoy on 2012-03-21
He's up to 295.xxx.xx and climbing...

---

### Post by davidstoll on 2012-03-24
I'm not using any extra Vdpau commands.  I only use the Vdpau playback profiles that are built-into mythtv.  Specifically "vdpau slim" has always been my playback profile on this and other machines, but I've tried "vdpau normal" and "vdpau high".  If I use the "CPU--" profile (for instance), video playback works, but it's clearly taxing the little machine's CPU, especially with HD.

My GPU is ION, not ION2.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16883103266](http://www.newegg.com/Product/Product.aspx?Item=N82E16883103266)

The new Xorg.0.log is attached.

Playback is 1x.  I don't ever change it because I don't see a reason to do so.  However, I did change it from 1x and back just to be sure.

lsmod output is attached.  It looks like there is an nvidia module loaded, but I'm not sure if that is the one I need or is even correct.

The nvidia-settings GUI does come up just fine and as far as I can tell all the settings are available and basically look like what I would expect.

```
$ dpkg -l | grep -i nvidia
ii  nvidia-173-modaliases                173.14.28-0ubuntu1                                 Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-185-modaliases                295.20-0ubuntu1~maverick~xup1                      Transitional package for nvidia-185-modaliases
ii  nvidia-96-modaliases                 96.43.19-0ubuntu1                                  Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-common                        0.2.24                                             Find obsolete NVIDIA drivers
ii  nvidia-current                       295.20-0ubuntu1~maverick~xup1                      NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-current-modaliases            295.20-0ubuntu1~maverick~xup1                      Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-settings                      295.20-0ubuntu1~maverick~xup1                      Tool of configuring the NVIDIA graphics driver
ii  vdpauinfo                            0.0.6-1~karmic~nvidiavdpauppa1                     
```

```
$ dpkg -l | grep -i vdpau
ii  libvdpau1                            0.4-5ubuntu1                                       Video Decode and Presentation API for Unix (libraries)
ii  nvidia-current                       295.20-0ubuntu1~maverick~xup1                      NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  vdpauinfo                            0.0.6-1~karmic~nvidiavdpauppa1                     
 of a VDPAU device.
```

---

### Post by nickrout on 2012-03-24
> **davidstoll said:**
> I'm not using any extra Vdpau commands.  I only use the Vdpau playback profiles that are built-into mythtv.  Specifically "vdpau slim" has always been my playback profile on this and other machines, but I've tried "vdpau normal" and "vdpau high".  If I use the "CPU--" profile (for instance), video playback works, but it's clearly taxing the little machine's CPU, especially with HD.

My GPU is ION, not ION2.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16883103266](http://www.newegg.com/Product/Product.aspx?Item=N82E16883103266)

The new Xorg.0.log is attached.

Playback is 1x.  I don't ever change it because I don't see a reason to do so.  However, I did change it from 1x and back just to be sure.

lsmod output is attached.  It looks like there is an nvidia module loaded, but I'm not sure if that is the one I need or is even correct.

The nvidia-settings GUI does come up just fine and as far as I can tell all the settings are available and basically look like what I would expect.

```
$ dpkg -l | grep -i nvidia
ii  nvidia-173-modaliases                173.14.28-0ubuntu1                                 Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-185-modaliases                295.20-0ubuntu1~maverick~xup1                      Transitional package for nvidia-185-modaliases
ii  nvidia-96-modaliases                 96.43.19-0ubuntu1                                  Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-common                        0.2.24                                             Find obsolete NVIDIA drivers
ii  nvidia-current                       295.20-0ubuntu1~maverick~xup1                      NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-current-modaliases            295.20-0ubuntu1~maverick~xup1                      Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-settings                      295.20-0ubuntu1~maverick~xup1                      Tool of configuring the NVIDIA graphics driver
ii  vdpauinfo                            0.0.6-1~karmic~nvidiavdpauppa1                     
```

```
$ dpkg -l | grep -i vdpau
ii  libvdpau1                            0.4-5ubuntu1                                       Video Decode and Presentation API for Unix (libraries)
ii  nvidia-current                       295.20-0ubuntu1~maverick~xup1                      NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  vdpauinfo                            0.0.6-1~karmic~nvidiavdpauppa1                     
 of a VDPAU device.
```

Well it seems clear from your Xorg log that the nvidia driver is in use.

Have you tried playing the files with mplayer using vdpau? This might eliminate vdpau from the picture.

Is it the same with ALL video and recoding files?

---

### Post by davidstoll on 2012-03-25
> **nickrout said:**
> Well it seems clear from your Xorg log that the nvidia driver is in use.

Have you tried playing the files with mplayer using vdpau? This might eliminate vdpau from the picture.

Is it the same with ALL video and recoding files?

As I mentioned in my first post, I can play videos in youtube and also videos with VLC (and yes, mplayer too).  In fact, I can play the exact same recordings (via a share) with VLC.

All recorded videos have the same issue (HD & SD, no matter which of my 3 recording devices recorded the content) when I playback in MythTV.

---

### Post by nickrout on 2012-03-25
does mplayer work with vdpau?

---

### Post by davidstoll on 2012-03-25
> **nickrout said:**
> does mplayer work with vdpau?

I apologize.  I'm not sure how to know if it does or not.  I've searched and it seems like you may have to "build" one that has the vdpau libraries...as in...custom.

Unless there is a command line switch, this is beyond my abilities.

---

### Post by nickrout on 2012-03-25
simply ask mplayer what video outputs it supports:

```
mplayer -vo help
```

If vdpau is listed you are good to go. If not use the medibuntu version of mplayer, which will have vdpau support.

then ```
mplayer -vo vdpau filename.mpg
```

---

### Post by davidstoll on 2012-03-25
> **nickrout said:**
> simply ask mplayer what video outputs it supports:

```
mplayer -vo help
```

If vdpau is listed you are good to go. If not use the medibuntu version of mplayer, which will have vdpau support.

then ```
mplayer -vo vdpau filename.mpg
```

Ok, cool.  My version supports vdpau.

```
$ mplayer -vo vdpau -fs testfile.mkv 
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team

Playing testfile.mkv.
libavformat file format detected.
[matroska @ 0x8d24310]Estimating duration from bitrate, this may be inaccurate
[lavf] stream 0: video (h264), -vid 0, testfile
[lavf] stream 1: audio (dca), -aid 0, -alang eng, DTS-CORE 1536K
VIDEO:  [H264]  1280x694  0bpp  24.000 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 doctype: matroska
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 1536.0 kbit/100.00% (ratio: 192000->192000)
Selected audio codec: [ffdca] afm: ffmpeg (FFmpeg DTS)
==========================================================================
AO: [pulse] Init failed: Connection refused
Failed to initialize audio driver 'pulse'
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
Movie-Aspect is 1.84:1 - prescaling to correct movie aspect.
VO: [vdpau] 1280x694 => 1280x694 Planar YV12  [fs]
A:   3.5 V:   3.0 A-V:  0.495 ct:  0.000   0/  0 96% 15%  6.7% 65 0 

           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.

A:  32.0 V:  28.2 A-V:  3.830 ct:  0.000   0/  0 85% 13% 14.5% 654 0 
Exiting... (Quit)
```

I have an HDPVR which records in x264.  I can set it to record in mp4, mkv, ts, mpg, whatever container I want.

The video does play back with mplayer, but at about 1/2 to 1/3 the rate of the audio, which plays back at normal rate (at least what my ears tell me)...SD, HD, x264, 720p, 1080i, mpeg, mpeg2, mpeg4, etc.

Also, XBMC plays all videos (everything I throw at it, SD, HD, x264, 720p, 1080i, mpeg, mpeg2, mpeg4, etc) as smooth as silk.

---

### Post by davidstoll on 2012-03-28
Any new thoughts based on the info I posted in the previous message?

---

### Post by nickrout on 2012-03-28
> **davidstoll said:**
> Any new thoughts based on the info I posted in the previous message?

Looks to me like your mplayer wasn't playing properly with vdpau either, becasue any player with vdpau should play back any video from an HDPVR without breaking sweat.

is your XBMC set up to output to vdpau? You can get playback info by pressing o (thats the letter o not zero) on your keyboard during playback.

I am pretty well stuck for ideas as to what is wrong with your mythtv. 

Is an interim solution to use XBMC with mythbox addon (you will need XBMC Eden (11.0))

---

### Post by BicyclerBoy on 2012-03-28
Your mythfrontend -v playback log has some odd ? things..
(nVidia 260).
VidOutVDPAU: Created VDPAU context (software decode)

When you generated that log output..were you 'livetv' channel grazing?

(software decode) is logged 3 times (GPU decode) is listed 4 times.

The ION has video frame size decoding limitations..
Your ION system likely can't do software decode..

I would wind back the kernel & go back to (slightly more) trusted nVidia drivers 260-280.
Completely remove libvdpau & then re-install it..
Boot a live DVD/CD of mythbuntu & check VDPAU works..

---

### Post by davidstoll on 2012-03-28
> **nickrout said:**
> Looks to me like your mplayer wasn't playing properly with vdpau either, becasue any player with vdpau should play back any video from an HDPVR without breaking sweat.

is your XBMC set up to output to vdpau? You can get playback info by pressing o (thats the letter o not zero) on your keyboard during playback.

I am pretty well stuck for ideas as to what is wrong with your mythtv. 

Is an interim solution to use XBMC with mythbox addon (you will need XBMC Eden (11.0))

Yes, it looks like XBMC is using vdpau to playback.
Thanks for the o tip.

---

### Post by davidstoll on 2012-03-28
> **BicyclerBoy said:**
> Your mythfrontend -v playback log has some odd ? things..
(nVidia 260).
VidOutVDPAU: Created VDPAU context (software decode)

When you generated that log output..were you 'livetv' channel grazing?

(software decode) is logged 3 times (GPU decode) is listed 4 times.

The ION has video frame size decoding limitations..
Your ION system likely can't do software decode..

I would wind back the kernel & go back to (slightly more) trusted nVidia drivers 260-280.
Completely remove libvdpau & then re-install it..
Boot a live DVD/CD of mythbuntu & check VDPAU works..

Booting to a different/previous kernel brings me to a black login screen...no gui.  This is the case for all listed kernels on the boot screen except the most recent.

I can roll back the nVidia drivers, but I had the problem with an earlier version too....so I'm not sure it's going to help.  Plus, I'm not specifically sure how to get 280 (for instance).  All I have is an updated PPA with nvidia-current which happens to be 295.

I'm not liking the looks of this...
```
$ sudo apt-get remove libvdpau1 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnotify-bin libfftw3-3 xbmc-skin-confluence xbmc-data libfaac0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libshairport1 libyajl1 xbmc xbmc-bin xbmc-data xbmc-skin-confluence
Recommended packages:
  libafpclient0 libcec libnfs0
The following packages will be REMOVED:
  libmyth-0.24-0 libvdpau1 mplayer mythbuntu-desktop mythgallery mythmovies mythmusic mythtv-common
  mythtv-frontend mythtv-theme-arclight mythtv-theme-blootube-osd mythtv-theme-blueosd mythtv-theme-childish
  mythtv-theme-graphite mythtv-theme-iulius-osd mythtv-theme-metallurgy mythtv-theme-mono-osd
  mythtv-theme-mythbuntu mythtv-theme-projectgrayhem-osd mythtv-theme-retro-osd mythtv-theme-titivillus-osd
  mythtv-themes mythtv-transcode-utils mythvideo mythweather vdpauinfo
The following NEW packages will be installed:
  libshairport1 libyajl1
The following packages will be upgraded:
  xbmc xbmc-bin xbmc-data xbmc-skin-confluence
4 upgraded, 2 newly installed, 26 to remove and 12 not upgraded.
Need to get 36.1MB of archives.
After this operation, 134MB disk space will be freed.
Do you want to continue [Y/n]?
```

It wants to remove mythtv-frontend...uh, I think there is something wrong.

---

### Post by BicyclerBoy on 2012-03-28
Better not do that then...
Would fix the mythtv problem tho'!
It only un-installs the packages, it does not delete them or their config stuff. Still seems risky.

apt-get purge libvdpau1
would get rid of libvdpau1 if the damage can be sustained..

myth has a dependency on libvdpau1..interestingly XBMC seems to handle this different.

You can use synaptic GUI tool to select an earlier version of the nVidia driver, the problems start when the earlier version is in a different ppa (std packages for example).

I thought (not sure why) that the nVidia driver package installers build the kernel module for all your kernel versions.
The DIY nVidia method only builds for the current kernel.
So why do your previous kernels cause X server to fail ?
You can <ctrl>+<alt>+<F1> login
cp /var/log/Xorg.0.log ~/Documents/Xorg.0.log01

---

### Post by BicyclerBoy on 2012-03-29
Back to your mplayer test:
you have to set the codec as well as the video overlay..

mplayer -vo vdpau &#8722;vc [ffmpeg12vdpau, ffwmv3vdpau, ffvc1vdpau, ffh264vdpau, 
ffodivxvdpau]

ION vdpau can not decode mpeg4-asp (divx xvid) so you would use -vc ffodivx.

So your error could have been caused by software decode being to slow..

Try:
export VDPAU_TRACE=1
export VDPAU_NVIDIA_DEBUG=3
mplayer blah...

vdpauinfo

---

### Post by davidstoll on 2012-03-29
> **BicyclerBoy said:**
> Back to your mplayer test:
you have to set the codec as well as the video overlay..

mplayer -vo vdpau &#8722;vc [ffmpeg12vdpau, ffwmv3vdpau, ffvc1vdpau, ffh264vdpau, 
ffodivxvdpau]

ION vdpau can not decode mpeg4-asp (divx xvid) so you would use -vc ffodivx.

So your error could have been caused by software decode being to slow..

Try:
export VDPAU_TRACE=1
export VDPAU_NVIDIA_DEBUG=3
mplayer blah...

vdpauinfo


```
$ vdpauinfo 
display: :0.0   screen: 0
API version: 1
Information string: NVIDIA VDPAU Driver Shared Library  295.33  Sat Mar 17 15:23:04 PDT 2012

Video surface:

name   width height types
-------------------------------------------
420     4096  4096  NV12 YV12 
422     4096  4096  UYVY YUYV 

Decoder capabilities:

name               level macbs width height
-------------------------------------------
MPEG1                 0  8192  2048  2048
MPEG2_SIMPLE          3  8192  2048  2048
MPEG2_MAIN            3  8192  2048  2048
H264_MAIN            41  8190  2032  2048
H264_HIGH            41  8190  2032  2048
VC1_SIMPLE            1  8190  2048  2048
VC1_MAIN              2  8190  2048  2048
VC1_ADVANCED          4  8190  2048  2048

Output surface:

name              width height nat types
----------------------------------------------------
B8G8R8A8          8192  8192    y  Y8U8V8A8 V8U8Y8A8 
R10G10B10A2       8192  8192    y  Y8U8V8A8 V8U8Y8A8 

Bitmap surface:

name              width height
------------------------------
B8G8R8A8          8192  8192
R8G8B8A8          8192  8192
R10G10B10A2       8192  8192
B10G10R10A2       8192  8192
A8                8192  8192

Video mixer:

feature name                    sup
------------------------------------
DEINTERLACE_TEMPORAL             y
DEINTERLACE_TEMPORAL_SPATIAL     y
INVERSE_TELECINE                 y
NOISE_REDUCTION                  y
SHARPNESS                        y
LUMA_KEY                         y
HIGH QUALITY SCALING - L1        -
HIGH QUALITY SCALING - L2        -
HIGH QUALITY SCALING - L3        -
HIGH QUALITY SCALING - L4        -
HIGH QUALITY SCALING - L5        -
HIGH QUALITY SCALING - L6        -
HIGH QUALITY SCALING - L7        -
HIGH QUALITY SCALING - L8        -
HIGH QUALITY SCALING - L9        -

parameter name                  sup      min      max
-----------------------------------------------------
VIDEO_SURFACE_WIDTH              y         1     4096
VIDEO_SURFACE_HEIGHT             y         1     4096
CHROMA_TYPE                      y  
LAYERS                           y         0        4

attribute name                  sup      min      max
-----------------------------------------------------
BACKGROUND_COLOR                 y  
CSC_MATRIX                       y  
NOISE_REDUCTION_LEVEL            y      0.00     1.00
SHARPNESS_LEVEL                  y     -1.00     1.00
LUMA_KEY_MIN_LUMA                y  
LUMA_KEY_MAX_LUMA                y 
```


With this, I heard audio, but no video came up.  I tried several files.
```
$ mplayer -vo vdpau -vc ff264vdpau sample.mkv 
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team

Playing sample.mkv.
libavformat file format detected.
[matroska @ 0xa090390]max_analyze_duration reached
[matroska @ 0xa090390]Estimating duration from bitrate, this may be inaccurate
[lavf] stream 0: video (h264), -vid 0
[lavf] stream 1: audio (aac), -aid 0, -alang eng
[lavf] stream 2: subtitle (unknown), -sid 0, -slang nld
VIDEO:  [H264]  864x486  0bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 doctype: matroska
 TITLE: 
 ARTIST: 
 COMPOSER: 
 SYNOPSIS: 
 DATE_RELEASED: 
 GENRE: 
==========================================================================
Forced video codec: ff264vdpau
Cannot find codec matching selected -vo and video format 0x34363248.
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [pulse] Init failed: Connection refused
Failed to initialize audio driver 'pulse'
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
```

---

### Post by BicyclerBoy on 2012-03-30
ION vdpau decode limits:
VDPAU Features Note 1

GPUs with this note may not support H.264 streams with the following widths: 49, 54, 59, 64, 113, 118, 123, 128 macroblocks (769-784, 849-864, 929-944, 1009-1024, 1793-1808, 1873-1888, 1953-1968, 2033-2048 pixels).

So your 864x486 may not be decode-able..

I'm not sure the ff264vdpau == ff**h264**vdpau !

mplayer did not like it..

---

### Post by nickrout on 2012-03-30
> **BicyclerBoy said:**
> ION vdpau decode limits:
VDPAU Features Note 1

GPUs with this note may not support H.264 streams with the following widths: 49, 54, 59, 64, 113, 118, 123, 128 macroblocks (769-784, 849-864, 929-944, 1009-1024, 1793-1808, 1873-1888, 1953-1968, 2033-2048 pixels).

So your 864x486 may not be decode-able..


Yeah it is kinda weird that my ION plays 720p better than 576p (576p is 1024 wide and falls foul of the above problem. One of the reasons I got an ION2 for my second frontend machine - it does not have this problem)

But this cannot be related surely to the original problem. The OP should be testing a myth recorded file with mplayer, or the test is not a valid comparison with myth's playback.

---

### Post by BicyclerBoy on 2012-03-30
You are right..about comparing playback with same file.

The OP never answered previous questions regarding h/w & s/w decoding messages in mythtv playback logs.

I was not very clear about mplayer...
mplayer did not like the cmd line options because of a typo..

The OPs mplayer cmd line was wrong, he specified a non-existent codec ff264vdpau..

---

### Post by nickrout on 2012-03-30
I am actually unclear whether mplayer still needs -vc as well as -vo vdpau. The lappie where I do my testing does not have nvidia.

---

### Post by davidstoll on 2012-03-30
> **BicyclerBoy said:**
> You are right..about comparing playback with same file.

The OP never answered previous questions regarding h/w & s/w decoding messages in mythtv playback logs.

I was not very clear about mplayer...
mplayer did not like the cmd line options because of a typo..

The OPs mplayer cmd line was wrong, he specified a non-existent codec ff264vdpau..

I re-tried with ffh264vdpau and it does play back much better, but pauses ever few seconds...just for half second.  But other than that, it's smooth.

I did try with several other files, including an originally recorded mythtv file...several actually.  1080i to SD/analog.

As far as the logs go, I tried to produce what was asked for.  I need help interpreting them.  For instance, there are some audio device errors, but I don't have any trouble with audio, so, I guess I can ignore that...I'm not really sure what I'm looking for.

I'm really sorry I'm not better able to get you what you need to help me...but I do appreciate everyone who is trying.

---

### Post by davidstoll on 2012-03-30
> **nickrout said:**
> I am actually unclear whether mplayer still needs -vc as well as -vo vdpau. The lappie where I do my testing does not have nvidia.

You are right about that I think.

MPG files recorded by myth playback with -vo vdpau, but not with -vc ffh264vdpau.

I just tested this on a working machine.

---

### Post by BicyclerBoy on 2012-03-31
Can you try this in a terminal, one cmd after another..

sudo apt-get install libvdpau-dev
* forget this line  -- {export VDPAU_TRACE=1}
export VDPAU_NVIDIA_DEBUG=3
mplayer -vo vdpau -vc ffh264vdpau sample.mkv

where sample.mkv is a file that does not decode..

* The trace library can't be found on my PC altho it is installed..

Can you post:
ls -al /usr/lib/vdpau*
ls -al /usr/lib/vdpau/*

---

### Post by davidstoll on 2012-03-31
> **BicyclerBoy said:**
> Can you try this in a terminal, one cmd after another..

sudo apt-get install libvdpau-dev
* forget this line  -- {export VDPAU_TRACE=1}
export VDPAU_NVIDIA_DEBUG=3
mplayer -vo vdpau -vc ffh264vdpau sample.mkv

where sample.mkv is a file that does not decode..

* The trace library can't be found on my PC altho it is installed..

Can you post:
ls -al /usr/lib/vdpau*
ls -al /usr/lib/vdpau/*

I did the apt-get, export and mplayer commands above and videos seemed to play fairly well.  Except for a periodic stutter every couple of seconds, it was pretty good.  I tried several different files and recordings and got video playback.

By the way, when I try to play the recordings within mythtv, it's almost like the TV picture gets shut off.  Even if you play a black video, you can still tell the TV is outputting energy.  What I'm seeing is almost like the PC is telling the TV to shut the picture off completely.

also...
```
$ ls -al /usr/lib/vdpau*
total 1912
drwxr-xr-x   2 root root    4096 2012-03-18 14:29 .
drwxr-xr-x 157 root root   61440 2012-03-31 17:08 ..
lrwxrwxrwx   1 root root      38 2012-03-18 14:29 libvdpau_nvidia.so.1 -> /etc/alternatives/libvdpau_nvidia.so.1
-rwxr-xr-x   1 root root 1809144 2012-03-18 14:22 libvdpau_nvidia.so.295.20
lrwxrwxrwx   1 root root      24 2012-03-18 14:22 libvdpau_trace.so.1 -> libvdpau_trace.so.295.20
-rwxr-xr-x   1 root root   65640 2012-03-18 14:22 libvdpau_trace.so.295.20

$ ls -al /usr/lib/vdpau/*
lrwxrwxrwx 1 root root      38 2012-03-18 14:29 /usr/lib/vdpau/libvdpau_nvidia.so.1 -> /etc/alternatives/libvdpau_nvidia.so.1
-rwxr-xr-x 1 root root 1809144 2012-03-18 14:22 /usr/lib/vdpau/libvdpau_nvidia.so.295.20
lrwxrwxrwx 1 root root      24 2012-03-18 14:22 /usr/lib/vdpau/libvdpau_trace.so.1 -> libvdpau_trace.so.295.20
-rwxr-xr-x 1 root root   65640 2012-03-18 14:22 /usr/lib/vdpau/libvdpau_trace.so.295.20
```

---

### Post by BicyclerBoy on 2012-03-31
That's a good observation..
Kind of suggests that myth is selecting a video mode that is out of range for the monitor/TV.

Do you have a different display setting to GUI size (mythfrontend TV settings playback?) ?

Does your TV have a mode /info display option (OSD) ?
Try changing video inputs to get info..

I think your vdpau lib paths/links look okay..

---

### Post by davidstoll on 2012-03-31
> **BicyclerBoy said:**
> That's a good observation..
Kind of suggests that myth is selecting a video mode that is out of range for the monitor/TV.

Do you have a different display setting to GUI size (mythfrontend TV settings playback?) ?

Does your TV have a mode /info display option (OSD) ?
Try changing video inputs to get info..

I think your vdpau lib paths/links look okay..

My TV says HDMI-1 1080p for the input.  Actually, it's called MythTV 1080p...I renamed it a while back so as to help others in my house know what is what.  I also just tried to move it to a different HDMI input...no luck.

I don't see a different playback resolution in the myth playback settings.  I know what you are talking about, but I'm not finding that specifically.  I roamed around other locations in the menu system in myth too.  I'm sorry I'm not finding it.

I do see where you can set a zoom and an aspect ratio override, and scaling and displacement options.  But all that stuff is default, 0, off or auto.

But my TV is definitely shutting the picture off...not black screen...OFF...although there is sound.  This is only when the playback profile is VDPAU (of some kind).  Other things like CPU-- are just fine except the CPU and fan go nuts.

---

### Post by davidstoll on 2012-04-03
Just a friendly bump.

Just let me know if there is some bit of information that I need to provide.

---

### Post by davidstoll on 2012-04-06
Am I going to have to blow this thing away... :/

---

### Post by jyavenard on 2012-04-07
> **nickrout said:**
> I am actually unclear whether mplayer still needs -vc as well as -vo vdpau. The lappie where I do my testing does not have nvidia.

They are two different thing.
One tells mplayer to use vdpau for the decoding, and the other to use vpdau for the rendering.

You do not have to use both at the same time; you can perfectly do software decoding, and vdpau (hardware) for the rendering: that includes deinterlacing, scaling and display

---

### Post by davidstoll on 2012-04-09
I don't suppose there is anything else to look at...?

Any other ideas?

---

### Post by BicyclerBoy on 2012-04-09
The release notes for 295.33 state that it is contains a bug fix for vdpau decode in low end products...

To clarify ..this played okay (except for stutter) ?
mplayer -vo vdpau -vc ffh264vdpau sample.mkv

Any warnings/errors reported?

Can you try the exact same recording/file in mythtv (from videos folder)..

mplayer cmd line:
The -vo cmd option sets the renderer. (vdpau, openGL Xvideo etc)
The -vc cmd option sets the decoder. (multiple h/w or s/w)

AFAIK You can not use (not yet) VDPAU decoder without VDPAU renderer.

---

### Post by davidstoll on 2012-04-09
> **BicyclerBoy said:**
> The release notes for 295.33 state that it is contains a bug fix for vdpau decode in low end products...

To clarify ..this played okay (except for stutter) ?
mplayer -vo vdpau -vc ffh264vdpau sample.mkv

Any warnings/errors reported?

Can you try the exact same recording/file in mythtv (from videos folder)..

mplayer cmd line:
The -vo cmd option sets the renderer. (vdpau, openGL Xvideo etc)
The -vc cmd option sets the decoder. (multiple h/w or s/w)

AFAIK You can not use (not yet) VDPAU decoder without VDPAU renderer.


I think I need to first get off 295.  I was at 260 (I think) and I was told that wasn't good.  All I did was add (x-swat I think) ppa and updated nvidia-current.  What ppa do you recommend so that nvidia-current is a good version (270 or 280?)?

---

### Post by nickrout on 2012-04-09
> **davidstoll said:**
> I think I need to first get off 295.  I was at 260 (I think) and I was told that wasn't good.  All I did was add (x-swat I think) ppa and updated nvidia-current.  What ppa do you recommend so that nvidia-current is a good version (270 or 280?)?

the x-swat drivers are at 295.33

---

### Post by davidstoll on 2012-04-09
> **nickrout said:**
> the x-swat drivers are at 295.33

right

I'm getting the sense that this is not ideal.
Rather than fighting with a "bug" in 295, I'm thinking I should get to 280 or 270 or whatever is considered stable/clean...

Keep in mind, I'm having the exact same issue with 295 that I had with my "old" 260 drivers.

---

### Post by nickrout on 2012-04-09
Well it doesn't seem to be a driver issue then does it...

---

### Post by davidstoll on 2012-04-09
> **nickrout said:**
> Well it doesn't seem to be a driver issue then does it...

I don't think so, but I'm not sure what else to look at.

---

