---
title: "Cinelerra Install error."
date: 2007-05-22
forum: Multimedia Production
---

### Post by cmmike1 on 2007-05-22
I'm trying to follow the official way to install cinelerra from their website but i keep coming across errors. I added the repo and did sudo apt-get update and it fetched some data. here is the outcome of my terminal.
```
mike@mike-desktop:~$ sudo apt-get install cinelerra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  vmware-player-kernel-modules-2.6.20-15 dia-libs libmagick++9c2a libkexif1
  vmware-player-kernel-modules-2.6.17-11 libburn2 libnspr4-0d
  vmware-player-kernel-modules dvdauthor libexo-0.3-0 libexif-dev
  libgphoto2-2-dev dia-gnome libmp4v2-dev libxul0d vamps kommander libntlm0
  libdbus-glib-1-dev libmozjs0d dia-common libpq4 libisofs2 libxul-common
  libnss3-0d eutils x-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libmpeg3hv libquicktimehv
The following NEW packages will be installed:
  cinelerra libmpeg3hv libquicktimehv
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/14.0MB of archives.
After unpacking 30.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libmpeg3hv libquicktimehv cinelerra
Install these packages without verification [y/N]? y
(Reading database ... 161385 files and directories currently installed.)
Unpacking libmpeg3hv (from .../libmpeg3hv_1%3a2.1.0-2svn2007424ubuntu3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libmpeg3hv_1%3a2.1.0-2svn2007424ubuntu3_i386.deb (--unpack):
 trying to overwrite `/usr/bin/mpeg3dump', which is also in package mpeg3-utils
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Selecting previously deselected package libquicktimehv.
Unpacking libquicktimehv (from .../libquicktimehv_1%3a2.1.0-2svn2007424ubuntu3_i386.deb) ...
Selecting previously deselected package cinelerra.
Unpacking cinelerra (from .../cinelerra_1%3a2.1.0-2svn2007424ubuntu3_i386.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libmpeg3hv_1%3a2.1.0-2svn2007424ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
If i answer no to the second question the installation stops right there. I can't seem to get it installed correctly and if anyone can help that would be awesome.

---

### Post by cmmike1 on 2007-05-23
no one knows of anything that could be going wrong?

---

### Post by drosky on 2007-05-23
> **cmmike1 said:**
> no one knows of anything that could be going wrong?

I don't know if this is the culprit, because I haven't experienced this problem, but I've seen a few other posts where people seem to have had trouble installing cinelerra with apt-get.  You might try using aptitude or synaptic.  I installed it with synaptic a few days ago and it went fine.  Again, I don't know if this is the problem, it's just something I've seen.

---

### Post by FRuMMaGe on 2007-05-23
> **cmmike1 said:**
> no one knows of anything that could be going wrong?

Synaptic usually installed perfectly.  I used to have lots of problems with libmpeg but now its fine.

---

### Post by cmmike1 on 2007-05-23
Now when i install it via synaptic i get this error at the end

```
E: /var/cache/apt/archives/libmpeg3hv_1%3a2.1.0-2svn2007424ubuntu3_i386.deb: trying to overwrite `/usr/bin/mpeg3dump', which is also in package mpeg3-utils
```

I have no idea what to do.

---

### Post by drosky on 2007-05-23
> **cmmike1 said:**
> Now when i install it via synaptic i get this error at the end

```
E: /var/cache/apt/archives/libmpeg3hv_1%3a2.1.0-2svn2007424ubuntu3_i386.deb: trying to overwrite `/usr/bin/mpeg3dump', which is also in package mpeg3-utils
```

I have no idea what to do.

It sounds like you have a conflict where there is a file or files that are in two different packages.  I don't have mpeg3-utils installed on my system.

The files in libmpeg3hv seem to be a superset of what is in mpeg3-utils.  You could try first un-installing mpeg3-utils and then installing libmpeg3hv (which is probably a dependency of cinelerra).  Of course, some other package may depend on mpeg3-utils, so you will have to see if that program runs properly with the versions of the same tools provided by libmpeg3hv.

---

### Post by cmmike1 on 2007-05-23
Alright, I have cinelerra working now but when i got to edit and view playback it is very slow. It seems as if it is going frame by frame. I'm using avi files by the way. Does this happen to anyone else?

---

### Post by drosky on 2007-05-23
> **cmmike1 said:**
> Alright, I have cinelerra working now but when i got to edit and view playback it is very slow. It seems as if it is going frame by frame. I'm using avi files by the way. Does this happen to anyone else?

It depends on several things, such as your machine, the type of encoding for the video you have in your AVI file, how many video tracks you have, and how many and what kind of effects are attached to the track (but I assume right now you have just one track and no effects).  Cinelerra seems to play some formats better/faster than others.  I've found that DV and mpeg2 seem to play back in cinelerra better than mpeg4, for example.

Cinelerra isn't really designed to be a video viewer, and once you start adding effects and multiple tracks, previewing will slow down even on fast hardware with DV or mpeg2.  There are a couple things you can do that can help.  One is to go into Settings->Preferences->Playback and uncheck "Play every frame" if it is checked.  This will allow Cinelerra to skip frames during playback so that your video plays at full speed but with a low frame rate.  Also, when placing effects on tracks, after you tweak the effect settings the way you want, you can temporarily disable the effect until you are ready to render the video.  This really helps speed up previewing for computationally intense effects (remember to turn them back on when you render).

Even doing all this, there will be times when the slow frame rate will make it hard to preview your film properly.  In this case, what I usually do is to render a portion of the film to a format that renders fairly quickly, such as motion JPEG, DV, or component video, and view the result in a movie player.

---

### Post by kayosiii on 2007-05-24
Some formats cause this sort of error. I know that Quicktime movies created with Final Cut or Quicktime do this when played back in Cinelerra. In that case AVI files saved from Quicktime don't have the same problem.

It would be helpful to know what codec the AVI files are using & what program they were created in...

---

### Post by cmmike1 on 2007-05-24
> **kayosiii said:**
> Some formats cause this sort of error. I know that Quicktime movies created with Final Cut or Quicktime do this when played back in Cinelerra. In that case AVI files saved from Quicktime don't have the same problem.

It would be helpful to know what codec the AVI files are using & what program they were created in...

I'm not exactly sure how to tell what codec they are using because i didn't import any of the clips. My friend imported them from his windows xp computer using adobe premiere pro and i wanted to try to do some editing with cinelerra. If there is a way i can find out what codec they use please tell me and i will tell you.

---

### Post by drosky on 2007-05-24
> **cmmike1 said:**
> I'm not exactly sure how to tell what codec they are using because i didn't import any of the clips. My friend imported them from his windows xp computer using adobe premiere pro and i wanted to try to do some editing with cinelerra. If there is a way i can find out what codec they use please tell me and i will tell you.

Install Transcode, it includes a command, "tcscan", which reports information on the video stream.  You could also play the file in mplayer (from the command line) and look at the information echoed to the terminal.

EDIT: Cinelerra may also be able to tell you if you look at the clip properties.

---

### Post by cmmike1 on 2007-05-25
> **drosky said:**
> Install Transcode, it includes a command, "tcscan", which reports information on the video stream.  You could also play the file in mplayer (from the command line) and look at the information echoed to the terminal.

EDIT: Cinelerra may also be able to tell you if you look at the clip properties.
I ran the clip in mplayer from the command line and this is the output.
```
mike@mike-desktop:~$ mplayer /media/MAXTOR\ 300_/Footage/mike/mike_morrisline.avi
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Celeron(R) CPU 2.80GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /media/MAXTOR 300_/Footage/mike/mike_morrisline.avi.
AVI file format detected.
VIDEO:  [dvsd]  720x480  24bpp  29.970 fps  28771.3 kbps (3512.1 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
Xv: could not grab port 325
Xv: could not grab port 326
Xv: could not grab port 327
Xv: could not grab port 328
Xv: could not grab port 329
Xv: could not grab port 330
==========================================================================
Opening video decoder: [dshow] DirectShow video codecs
Decoder supports the following YUV formats: YUY2 UYVY 
Decoder is capable of YUV output (flags 0x9)
VDec: vo config request - 720 x 480 (preferred colorspace: Packed YUY2)
[PP] Using codec's postprocessing, max q = 4.
VDec: using Packed YUY2 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 720x480 => 720x480 Packed YUY2 
Selected video codec: [qdv] vfm: dshow (Sony Digital Video (DV))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 1536.0 kbit/100.00% (ratio: 192000->192000)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
A:   4.9 V:   4.5 A-V:  0.469 ct:  0.013 135/135 46% 34% 28.0% 69 0 

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

A:  11.4 V:   9.3 A-V:  2.082 ct:  0.015 281/281 45% 41% 31.3% 211 0 
Badly interleaved AVI file detected - switching to -ni mode...
A:  20.8 V:  20.8 A-V:  0.033 ct:  0.427 623/623 43% 40% 19.3% 427 0 

Exiting... (End of file)

```
I think my computer is fast enough with 1 gig of ram to play the file and it plays fine. It says something about 29fps for the video clip.

---

### Post by drosky on 2007-05-25
> **cmmike1 said:**
> I ran the clip in mplayer from the command line and this is the output.
[
I think my computer is fast enough with 1 gig of ram to play the file and it plays fine. It says something about 29fps for the video clip.

It appears that mplayer is using a win32 codec (qdv.dll) to decode the Sony digital video format.  I'm not familiar with this but it appears to be just DV, perhaps in some Sony-proprietary format.  I don't know if Cinelerra can use win32 codecs, but if it can't, it is probably using another DV codec to decode and play the video.  For me, DV normally plays fairly smoothly in Cinelerra, but perhaps it has more trouble with this Sony variety of DV.

You could try using Mencoder or Transcode to convert the file to a normal DV1 or DV2 AVI.  There shouldn't be any loss of quality and the file might work better in Cinelerra.  Caveat:  A lot of this is just guessing since I have never worked with a Sony digital video file.

---

### Post by kayosiii on 2007-05-25
Transcoding might be a good idea... If it is anything like the Apple problem you will notice when you go frame by frame that the frames only update every six or so if that is the case it is probably worth sending a small example file to the guys at cvs.cinelerra.org...

---

### Post by cmmike1 on 2007-05-27
I will have to try and convert the video clip sometime tomorrow to DV and see if it makes a difference at all. If anyone is interested i would be willing to upload a portion of a clip to see how it reacts to other peoples set up. The whole file is over 100mb so if anyone is willing to test it out let me know.

---

