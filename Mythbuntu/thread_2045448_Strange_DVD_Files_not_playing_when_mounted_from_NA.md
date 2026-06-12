---
title: "Strange: DVD Files not playing when mounted from NAS"
date: 2012-08-21
forum: Mythbuntu
---

### Post by matthias.rieber on 2012-08-21
Hi all,
 
I have a combined FE/BE running Mythbuntu 12.04 and Myth 0.25 - latest fixes.
First I mounted my nas to FE/BE via smbnetfs - most run fine, but some DVD's don't.
I figured out, that this was a problem of rights, so I changed to cifs-mount in fstab with full rights to mythtv-user:
> 
myth@myth-desktop:~/Videos/DVD/Harry_Potter/Harry Potter 2 - und die Kammer des Schreckens/VIDEO_TS$ ls -al
total 7203968
drwxrwxrwx 1 mythtv myth 0 Aug 21 01:14 .
drwxrwxrwx 1 mythtv myth 0 Aug 21 01:14 ..
-rwxrwxrwx 1 mythtv myth 12288 Jun 19 2010 video_ts.bup
-rwxrwxrwx 1 mythtv myth 12288 Jun 19 2010 video_ts.ifo
-rwxrwxrwx 1 mythtv myth 2768896 Jun 19 2010 video_ts.vob
-rwxrwxrwx 1 mythtv myth 98304 Jun 19 2010 vts_01_0.bup
-rwxrwxrwx 1 mythtv myth 98304 Jun 19 2010 vts_01_0.ifo
-rwxrwxrwx 1 mythtv myth 149448704 Jun 19 2010 vts_01_0.vob
-rwxrwxrwx 1 mythtv myth 1073739776 Jun 19 2010 vts_01_1.vob
-rwxrwxrwx 1 mythtv myth 1073739776 Jun 19 2010 vts_01_2.vob
-rwxrwxrwx 1 mythtv myth 1073739776 Jun 19 2010 vts_01_3.vob
-rwxrwxrwx 1 mythtv myth 1073739776 Jun 19 2010 vts_01_4.vob
-rwxrwxrwx 1 mythtv myth 1073739776 Jun 19 2010 vts_01_5.vob
-rwxrwxrwx 1 mythtv myth 1073739776 Jun 19 2010 vts_01_6.vob
-rwxrwxrwx 1 mythtv myth 782206976 Jun 19 2010 vts_01_7.vob

 
If I copy the files to al local directory on FE/BE, then I can play the DVD in mythtv fine.....
 
Using mythffplayer works fine (independet of the VIDEO_TS directory is local or on nas)
> 
myth@myth-desktop:~/Videos/DVD/Harry_Potter/Harry Potter 2 - und die Kammer des Schreckens/VIDEO_TS$ mythffplay video_ts.vob
FFplay version UNKNOWN, Copyright (c) 2003-2011 the FFmpeg developers
built on Aug 9 2012 18:17:37 with gcc 4.6.3
configuration: --compile-type=profile --prefix=/usr --runprefix=/usr --enable-crystalhd --enable-lirc --enable-audio-alsa --enable-audio-oss --enable-dvb --enable-ivtv --enable-firewire --enable-joystick-menu --with-bindings=perl --enable-ffmpeg-pthreads --enable-pic --enable-vaapi --perl-config-opts='INSTALLDIRS=vendor' --enable-libvpx --enable-libx264 --enable-libmp3lame --enable-libfaac --enable-libxvid --enable-nonfree --enable-opengl-video --enable-vdpau
libavutil 50. 39. 0 / 50. 39. 0
libavcodec 52.113. 1 / 52.113. 1
libavformat 52.101. 0 / 52.101. 0
libavdevice 52. 2. 3 / 52. 2. 3
libavfilter 1. 76. 0 / 1. 76. 0
libswscale 0. 12. 0 / 0. 12. 0
libpostproc 51. 2. 0 / 51. 2. 0
Input #0, mpeg, from 'video_ts.vob':
Duration: 00:00:12.00, start: 0.128389, bitrate: 1845 kb/s
Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x576 [PAR 16:15 DAR 4:3], 9800 kb/s, 25 fps, 2.08 tbr, 90k tbn, 50 tbc
^C37.83 A-V: 0.000 s:0.0 aq= 0KB vq= 0KB sq= 0B f=0/0 0/0 

 
Using mplayer works, too (alternative player) - but without menues (so, no "waf").
Using a seperate FE (lubuntu 12.04, myth 0.25 latest fixes) playing the DVD works, too (mounted via cifs) - but not on the main htpc....
 
Here a part of FE-log of main htpc:
> 
Aug 21 00:03:52 myth-desktop mythfrontend[2047]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingDVD
Aug 21 00:03:59 myth-desktop mythfrontend[2047]: I CoreContext dvdringbuffer.cpp:338 (OpenFile) DVDRB: Opened DVD device at /home/myth/Videos/DVD/Harry_Potter/Harry Potter 2 - und die Kammer des Schreckens
Aug 21 00:03:59 myth-desktop mythfrontend[2047]: I CoreContext dvdringbuffer.cpp:364 (OpenFile) DVDRB: There are 4 titles on the disk
Aug 21 00:04:01 myth-desktop mythfrontend[2047]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
Aug 21 00:05:15 myth-desktop mythfrontend[2047]: E CoreContext mythplayer.cpp:937 (OpenFile) Player(2): Couldn't find an A/V decoder for: '/home/myth/Videos/DVD/Harry_Potter/Harry Potter 2 - und die Kammer des Schr$
Aug 21 00:05:15 myth-desktop mythfrontend[2047]: E CoreContext mythplayer.cpp:2663 (StartPlaying) Player(2): Unable to open video file.

 
So: how there can be an missing A/V decoder if the files can be played when residing local and why it can be played with mythffplay if A/V decoder is missing ?
 
I'm running out of ideas.... pls help !
 
thx

---

### Post by matthias.rieber on 2012-08-24
... no one no ideas ?
pls assist !

---

### Post by matthias.rieber on 2012-08-27
I figured out something like a solution.....
 
Mounting the fs via fstab like 
 
> 
//192.168.*.*/myvideos /Videos cifs password= 0 0

 
will NOT work for DVD directories
 
mounting the fs with:
 
> 
mount.cifs -o password= //192.168.*.*/myvideos /Videos 

 
WILL work.... It makes no sense, but it works (tried several times with different options)
 
So I added the line above in autostart - and can watch DVD's now....

---

### Post by Rotak on 2012-08-29
Hmm. Maybe the *password=* is interpreted wrongly in FSTAB. As you don't seem to use a password... can't you just omit that option and use "defaults"?

---

### Post by nickrout on 2012-08-29
> **matthias.rieber said:**
> I figured out something like a solution.....
 
Mounting the fs via fstab like 
 

 
will NOT work for DVD directories
 
mounting the fs with:
 

 
WILL work.... It makes no sense, but it works (tried several times with different options)
 
So I added the line above in autostart - and can watch DVD's now....

I am not sure if you are using a blank pasword, or just omitting it so we don't learn it. However it is bad practice to use password= in fstab anyway. Any user can read fstab. You are better to use credentials=filename and make filename only readable by root. I use credentials=/root/cifscredentials. see man mount.cifs for details.

Having said that I am not sure why you are having that sort of problem, the lines seem functionally equivalnet, although in neither have you specified a username so maybe you are ruuning the commandline as a different user to the user (root) that mounts via fstab.

Still at least you have a solution, you could add your mount command to /etc/rc.local

---

### Post by matthias.rieber on 2012-09-03
Hi,
 
thanks for the replys.
 
@rotak: I tried with "defaults" first - it would not work :-( 
even with account "guest" - would not work, too....
 
@nickrout: Maybe you're right.... I never tried to use credentials (I hve no pwd for that section on my nas in my intranet - there are only Videos in there).... I'll read a little bit about credentials and give you a feedback....
 
@both: Thanks for your help
 
Matthias

---

### Post by matthias.rieber on 2012-09-14
Now I tried with .smbcredentials....
I created the file, put in my username an password, added the option to fstab, unmounted the cifs-mounts, remounted them with option credentials=....

Error in frontend.log: "missing A/V Decoder..."

so still the same:
mounting with
mount.cifs ... in autostart works - all the rest (fusesmb, smbnetfs, fstab) doesn't .....

I do not understand that.....

Matthias

---

