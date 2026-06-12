---
title: "Transcode error PS3 Media Server &amp; Samsung AllShare Play"
date: 2012-11-04
forum: Multimedia Software
---

### Post by mashedbear on 2012-11-04
Hello
I am using ubuntu 12.04, PS 3 Media Server 1.7, and Samsung AllShare Play on a 2012 Samsung TV and am trying to play home videos' from my ubuntu PC on the Samsung TV. All devices are on a wired ethernet LAN.

I am get a transcode error in PS 3 Media server - traces below - and the video does not play (infact Allshare play force quits with a "please check your network connection" dialog). Pictures (.jpg) and MP3's both stream fine from the PC to the TV.

> INFO  2012-11-04 16:15:42.028 [New I/O server worker #10-3] Starting transcode/remux of 00020.MTS
ERROR 2012-11-04 16:15:52.656 [New I/O server worker #10-3] There is no inputstream to return for 00020.MTS [tsMuxeR]
INFO  2012-11-04 16:15:57.894 [New I/O server worker #10-4] Starting transcode/remux of 00021.MTS
WARN  2012-11-04 16:16:02.659 [Process Destroyer] Sending kill -14 to the Unix process: 12067
WARN  2012-11-04 16:16:02.683 [Process Destroyer] Sending kill -14 to the Unix process: 12084
INFO  2012-11-04 16:16:03.501 [StartPlaying Event] renderer: 192.168.1.90, file: /home/paul/Videos/114NelsonRd-Mar2012/00021.MTS
INFO  2012-11-04 16:16:07.524 [StopPlaying Event] renderer: 192.168.1.90, file: /home/paul/Videos/114NelsonRd-Mar2012/00021.MTS

The video file is an AVCHD ( .MTS file extension), codec is H.264 MPEG-4 AVC, resolution 1440 x 1080, frame rate is 50. 

I have gone through a trial and error with the common transcoding settings in the PS 3 Media server. To no effect.  
Currently the settings are:
> Transcode buffer: 400
Number of cores: 2
MPEG-2 Options: keyint=25:vqmax=7:vqmin=2  /* Medium quality for HD Wifi transcoding */
On the general configuration tab I have set the Default Renderer to Samsung AllShare

Any ideas on how to solve this or of a DNLA media server that works with AVCHD files and Samsung TVs greatly appreciated.

---

### Post by nothingspecial on 2012-11-05
*Thread moved to **Multimedia & Video**.*

---

### Post by mashedbear on 2012-11-10
Bump - any ideas anyone

---

### Post by evilsoup on 2012-11-10
These files play fine on your computer, right?

You can try using mencoder instead of TSmuxer (you'll have to make sure the transcode folders are visible on your renderer, or I think you can set mencoder to be your default transcoder).

If that doesn't work, you could try remuxing a file to MP4 with ffmpeg.
```
 sudo apt-get install ffmpeg
ffmpeg -i input.mts -a:c copy -v:c copy testoutput.mp4
```

This will be completely lossless, since all it's doing is transferring the video to a new container.

---

### Post by mashedbear on 2012-11-12
Thanks. The files play fine on the computer.

To use Mencoder would you somehow disable tsmuxer in the PS3 Media Server?

---

