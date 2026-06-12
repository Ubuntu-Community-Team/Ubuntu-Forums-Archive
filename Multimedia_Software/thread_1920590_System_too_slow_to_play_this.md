---
title: "System too slow to play this?"
date: 2012-02-05
forum: Multimedia Software
---

### Post by userub on 2012-02-05
Hello,

I'm having some trouble with a video camera. It's a Kodak Zi6 model, which saves files in .MOV format.

I have one of the videos saved on a USB drive, and when I plugged it into this computer, it slowed down drastically. It would barely even open the USB folder. I used the Terminal to play the file and it succeeded, but the playback was slow and choppy.

Here is the output of the Terminal:

MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Zi6_0016.mov.
libavformat file format detected.
[lavf] stream 0: video (h264), -vid 0
[lavf] stream 1: audio (aac), -aid 0, -alang eng
VIDEO:  [H264]  1280x720  24bpp  29.970 fps  9314.2 kbps (1137.0 kbyte/s)
Clip info:
 major_brand: qt  
 minor_version: 0
 compatible_brands: qt  
 comment: KODAK Zi6 Pocket Video Camera
 comment-eng: KODAK Zi6 Pocket Video Camera
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] This driver only supports the 3Dfx Banshee, Voodoo3 and Voodoo 5.
[VO_3DFX] Unable to open /dev/3dfx.
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 15999->192000)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1280x720 => 1280x720 Planar YV12 
A:   6.2 V:   1.6 A-V:  4.590 ct:  0.028   0/  0 335% 51% 24.6% 50 0 

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

A:  12.1 V:   3.2 A-V:  8.913 ct:  0.037   0/  0 323% 47% 25.1% 97 0 
Exiting... (Quit)



Could anyone suggest what to do?

Thank you.

---

### Post by sudodus on 2012-02-05
Please post information about your computer hardware and operating system!

- brand and type
- motherboard, cpu, ram
- graphics chip or card

Flavour [KLX]ubuntu? Version 10.04 LTS, 11.04, 11.10 ?

And if there is something special ...

It helps us help to know ...

What happens if you copy the video file to your internal hard disk drive? Will it work faster?

VIDEO:  [H264]  1280x720  24bpp  29.970 fps  9314.2 kbps (1137.0 kbyte/s): This kind of video needs some horsepower to play well.

---

### Post by userub on 2012-02-05
> **sudodus said:**
> Please post information about your computer hardware and operating system!

- brand and type
- motherboard, cpu, ram
- graphics chip or card

Flavour [KLX]ubuntu? Version 10.04 LTS, 11.04, 11.10 ?

Could you tell me how to find those specs?

I'm also not sure which version of Ubuntu I'm using.

> 
What happens if you copy the video file to your internal hard disk drive? Will it work faster?I don't know how to do that through the Terminal, which is the only way I can access the drive when the file is on it.

> VIDEO:  [H264]  1280x720  24bpp  29.970 fps  9314.2 kbps (1137.0 kbyte/s): This kind of video needs some horsepower to play well.

Which part of it takes up the most power? I have some videos, downloaded from Youtube, that are 1280x720 and they play smoothly.

Although, I do have some that are ?/1080 and the playback is rough on those.

---

### Post by mcduck on 2012-02-05
h.264 is a video format that requires some power to work well (at least if you don't have a graphics card that supports hardware decoding for this format). And the bandwidth of course has a huge impact as well (the kbit/s value, basically describing the quality of the video, how much data is used to store every second of the video).

(Just to make this more clear, .mov is not a video format. It's a container file, able to include video and audio in many different formats. So you are now dealing with a h.264 video format, and AAC audio format).

Anyway, you said you are playing the file from the USB drive? Does it work better if you move the file to your computer first, and then play it from there? Perhaps the USB drive is too slow and it's read/transfer speed is not enough for the video in question. And since you also said that the whole computer slowed down when you plugged in the drive, it really sounds like that there's a problem with that drive, so you might want to look into that instead of the video file...

---

### Post by userub on 2012-02-05
Okay, I tried a different USB drive and the system didn't slow down. I think you're right; the other drive must have a problem.

I copied the video to the computer, and it does play faster. However, it's still somewhat choppy and the quality isn't good. Terminal's output:

> MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Zi6_0016.MOV.
libavformat file format detected.
[lavf] stream 0: video (h264), -vid 0
[lavf] stream 1: audio (aac), -aid 0, -alang eng
VIDEO:  [H264]  1280x720  24bpp  29.970 fps  9314.2 kbps (1137.0 kbyte/s)
Clip info:
 major_brand: qt  
 minor_version: 0
 compatible_brands: qt  
 comment: KODAK Zi6 Pocket Video Camera
 comment-eng: KODAK Zi6 Pocket Video Camera
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] This driver only supports the 3Dfx Banshee, Voodoo3 and Voodoo 5.
[VO_3DFX] Unable to open /dev/3dfx.
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 15999->192000)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1280x720 => 1280x720 Planar YV12 
A:   2.9 V:   2.2 A-V:  0.715 ct:  0.024   0/  0 99% 16%  2.7% 50 0 

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

A:  22.6 V:  22.3 A-V:  0.303 ct:  0.024   0/  0 85% 12%  1.6% 603 0 
Exiting... (Quit)

I don't know how to find the details of the computer's hardware.

Assuming the specs are too low, what options do I have? Could I convert the file to decrease the quality so it can then play smoothly?

---

### Post by sudodus on 2012-02-05
> **userub said:**
> Okay, I tried a different USB drive and the system didn't slow down. I think you're right; the other drive must have a problem.

I copied the video to the computer, and it does play faster. However, it's still somewhat choppy and the quality isn't good. Terminal's output 1:
A: 12.1 V: 3.2 [COLOR="Red"]A-V: 8.913[/COLOR] ct: 0.037 0/ 0 323% 47% 25.1% 97 0

2: (with the file on the internal drive)
A: 22.6 V: 22.3 [COLOR="red"]A-V: 0.303[/COLOR] ct: 0.024 0/ 0 85% 12% 1.6% 603 0 

The red text show how much the video is lagging after the audio, and, yes, it is much better now, but it is still lagging.
> 
I don't know how to find the details of the computer's hardware.

Assuming the specs are too low, what options do I have? Could I convert the file to decrease the quality so it can then play smoothly? Yes, you can, for example using ffmpeg. Look at the following links

[[COLOR="red"]_http://ubuntuforums.org/showthread.php?t=786095_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=786095")

[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1920371_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1920371")

But first you should let us know about your computer and operating system. (See my next post.)

---

### Post by SeijiSensei on 2012-02-05
> **userub said:**
> I don't know how to find the details of the computer's hardware.

```

sudo apt-get install hwinfo
sudo hwinfo > /root/hwinfo.txt
sudo more /root/hwinfo.txt

```

This will tell you more than you could possibly ever want to know about your hardware.

There are some other methods as well.  What really matters for video decoding is the speed of your CPU and whether your video card supports hardware decoding of H.264-encoded material.  To see information about the CPU, run the command "cat /proc/cpuinfo".  The entry for "model name" gives the processor's name and speed. 

As for the video card, only NVIDIA cards have good support for hardware-decoding of H.264 in Linux.  Apparently you don't have an NVIDIA card because mplayer reports 

> Failed to open VDPAU backend libvdpau_nvidia.so

"VDPAU" is NVIDIA's interface for *nix machines to access the graphics decoder.  If you have an NVIDIA card, you have to install the proprietary drivers to get VDPAU to work.  Navigate to System > Additional Drivers to run the application that will look at the video hardware and install the appropriate drivers if available.  If you have an ATI or NVIDIA card, the application will install the correct drivers.  If it doesn't find either, you most likely have Intel graphics without any hardware decoding.

If you have a laptop, you don't have many options available to improve its performance.  If it's a desktop machine, you can spend less than $50 and add an NVIDIA card.  Any of [these]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709%20600030348&IsNodeId=1") will work, though be sure you choose the correct interface (PCI, PCI Express, AGP) before ordering.

---

### Post by sudodus on 2012-02-05
> **userub said:**
> Could you tell me how to find those specs?
Hardware:
```
gksudo lshw | less
``` or the GUI program ***hardinfo*** installed by ```
sudo apt-get install hardinfo
```
> 

I'm also not sure which version of Ubuntu I'm using.

***sysinfo*** installed by ```
sudo apt-get install sysinfo
``` or ***System monitor*** 
> 
I don't know how to do that through the Terminal, which is the only way I can access the drive when the file is on it.

Obviously you have solved that problem now :-)
> 
Which part of it takes up the most power? I have some videos, downloaded from Youtube, that are 1280x720 and they play smoothly.

Although, I do have some that are ?/1080 and the playback is rough on those.
The video decoding, as stated by mcduck, and sending video signals to the screen, and it depends how much motion there is in the video (if the whole picture changes, or only one person moves and the background remains the same ...)

Your hardware might or might not be used more efficiently (depending of what it is and how you run it now)

---

### Post by userub on 2012-02-05
> **SeijiSensei said:**
> ```

sudo apt-get install hwinfo
sudo hwinfo > /root/hwinfo.txt
sudo more /root/hwinfo.txt

```This will tell you more than you could possibly ever want to know about your hardware.

[quote=sudodus]

gksudo lshw | less

or the GUI program ***hardinfo*** installed by [/quote]

I've tried all three, but I don't know which section of the output is relevant.

I'm using Ubuntu 11.04, though.

> There are some other methods as well.  What really matters for video decoding is the speed of your CPU and whether your video card supports hardware decoding of H.264-encoded material.  To see information about the CPU, run the command "cat /proc/cpuinfo".  The entry for "model name" gives the processor's name and speed. This is the entry:

model name    : Intel(R) Celeron(R) M CPU        520  @ 1.60GHz

I'm not sure what it means.

> As for the video card, only NVIDIA cards have good support for hardware-decoding of H.264 in Linux.  Apparently you don't have an NVIDIA card because mplayer reports 



"VDPAU" is NVIDIA's interface for *nix machines to access the graphics decoder.  If you have an NVIDIA card, you have to install the proprietary drivers to get VDPAU to work.  Navigate to System > Additional Drivers to run the application that will look at the video hardware and install the appropriate drivers if available.  If you have an ATI or NVIDIA card, the application will install the correct drivers.  If it doesn't find either, you most likely have Intel graphics without any hardware decoding.

If you have a laptop, you don't have many options available to improve its performance.  If it's a desktop machine, you can spend less than $50 and add an NVIDIA card.  Any of [these]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709%20600030348&IsNodeId=1") will work, though be sure you choose the correct interface (PCI, PCI Express, AGP) before ordering.Additional Drivers didn't turn up anything for video cards. This computer is a laptop, so it seems my only option on this machine is to convert the video.

There are other computers here but they don't have Ubuntu installed. The video won't play properly on any of them, and the desktops don't have the right codec to either convert or play the video.

Is there a codec I can use for those desktops? What are the minimum resources needed to play the video? And will I need to just buy a new video card for them?

Thanks in advance.

---

### Post by sudodus on 2012-02-06
> **userub said:**
> I've tried all three, but I don't know which section of the output is relevant.

I'm using Ubuntu 11.04, though.

This is the entry:

model name    : Intel(R) Celeron(R) M CPU        520  @ 1.60GHz

It means that it is not very powerful.
> 
I'm not sure what it means.

Additional Drivers didn't turn up anything for video cards. This computer is a laptop, so it seems my only option on this machine is to convert the video.
 Yes, to play in that computer > 
There are other computers here but they don't have Ubuntu installed. The video won't play properly on any of them, and the desktops don't have the right codec to either convert or play the video.

Is there a codec I can use for those desktops? What are the minimum resources needed to play the video? And will I need to just buy a new video card for them?

Thanks in advance.

I suggest that you boot those computers from your boot CD or USB drive (the install drive for Ubuntu 11.04) and run
```
gksudo lshw > lshw1.txt
```
```
gksudo lshw > lshw2.txt
```
```
...
```
and attach those files to a reply post. Then we can see which computer would be the best candidate to run video, and where to add a new video card.

But an option if you run Windows is to download VLC for windows and try it. It will bring its own codecs and is able to run a lot of video file types.

---

