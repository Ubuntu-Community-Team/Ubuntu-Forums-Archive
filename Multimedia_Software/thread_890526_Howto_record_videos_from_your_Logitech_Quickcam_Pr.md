---
title: "Howto record videos from your Logitech Quickcam Pro 9000"
date: 2008-08-15
forum: Multimedia Software
---

### Post by nbkr on 2008-08-15
Hi,

I recently bought a Logitech Quickcam Pro 9000 (this [one]("http://www.amazon.com/gp/product/B000U1IX76/ref=s9sims_c1_at1-rfc_g1?pf_rd_m=A3JWKAKR8XB7XF&pf_rd_s=center-1&pf_rd_r=01M7113JDCE275PRK280&pf_rd_t=101&pf_rd_p=162597691&pf_rd_i=301128"))

and wanted to be able to record myself for a videolog. 

I tried cheese, but it doesn't really work well. For example after recording cheese doesn't show the video without restarting cheese.

VLC doesn't support the necessary video4linux2 driver.

mencoder doesn't record sound.

ffmpeg did fine, but doesn't show the video while recording. Anyway I could solve this.

So this is how I did it:

```

ffmpeg -f audio_device -i /dev/dsp1  -f video4linux2 -s 640x480 -i /dev/video0 -f avi - | tee `date -I`.avi | mplayer -

```

Hope this is useful for anyone else.

Regards
nbkr

---

### Post by lovinglinux on 2008-09-11
Thank you. Finally a script that works. Unfortunately, the voices sounds like a duck, because of high pitch. Do you know why?

---

### Post by nbkr on 2008-09-11
I'm sorry, I didn't have that problem. The sound was quite fine, regardless if it was recorded by the Webcam's microphone or through my headset.

---

### Post by lovinglinux on 2008-09-11
Thanks. I'm recording audio from line and video from tv card. Looks like everyone on my recordings have inhaled Helium gas. :)

---

### Post by boussetta on 2008-10-09
Hi guys;
I have the same webcam but still strugling with its installation, my pc is not recognizing it and I am a newbie to linux 
my system is am amd64, ubuntu 2.6.24-19-generic

Your support is very welcome

Thanks

---

### Post by nbkr on 2008-10-09
If you plug it in, what does "lsusb" on the console tell you?

---

### Post by boussetta on 2008-10-10
Hi ;

with lsusb I am getting:
Bus 002 Device 003: ID 046d:0990 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 04fc:0538 Sunplus Technology Co., Ltd 
Bus 001 Device 001: ID 0000:0000  


and 
with  lsmod | grep videodev
I am getting: 
videodev               30720  2 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            21888  3 uvcvideo,compat_ioctl32,videodev

I tried many things from this forum but still cannot see my webcam working
when I launch Camorama I get an error message: could not connect to video device (/dev/video0) Please check connection.

your suggestions are highly appreciated

---

### Post by nbkr on 2008-10-10
Your camera is recognized by the system (if you don't habe a logitec mouse). You just need an application that can show you, what the camera sees. As said, ffmpeg works well, camorama didn't. I've gotten the same errormessage.

---

### Post by boussetta on 2008-10-10
I tried skype, cheese and camorama that didn t work, in Ekiga it says :'Could not open the chosen channel'
I installed ffmpeg from the synaptic manager: /usr/bin/ffmpeg

but I don't know how to run it it, when I write ffmpeg in the cmd line a lots of options appear and nothing else, more over I am intrested mostly in using it with skype or Ekiga :(

Thanks for your support

---

### Post by balaji.ramasubramanian on 2008-11-15
I get the following if I try your command:

> ffmpeg -f audio_device -i /dev/dsp1  -f video4linux2 -s 640x480 -i /dev/video0 -f avi - | tee `date -I`.avi | mplayer -

FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
Unknown input or output format: audio_device
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing -.
Reading from stdin...
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll


Exiting... (End of file)

Can you please help me with this? I don't have avisynth.dll in the directory it is looking for. I also searched online and found this link where I could download w32codecs [http://forums.fedoraforum.org/showthread.php?t=168420](http://forums.fedoraforum.org/showthread.php?t=168420)

I followed the instructions there, but even that does not contain the avisynth.dll. At [www.avisynth.org](www.avisynth.org) I find the GPLed source, but I don't know how I should use it in Linux. How should I get this avisynth.dll?

---

