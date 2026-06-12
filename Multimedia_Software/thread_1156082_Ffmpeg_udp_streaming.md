---
title: "Ffmpeg udp streaming"
date: 2009-05-11
forum: Multimedia Software
---

### Post by xzero1 on 2009-05-11
Using ffmpeg's udp, one can transcode and stream video and audio to a networked computer in a manner similar to vlc streaming. The video quality is can be quite good though there may be some av glitches from time to time. 

Why not just use vlc? This method can use the latest ffmpeg including ffmpeg-mt. Ffmpeg overall seems more flexible.

As an example, on a AMD x2 4400+ system, I can transcode in realtime a 720p h.264 video file and stream it in mpeg4 format to a 630Mhz eepc at 720x432 with ffmpeg-mt using this command:

```
ffmpeg -i filename -f mpegts -vcodec mpeg4 -acodec mp2 -ac 2 -ab 128k -s 720x432 -r 30 -re -b 2000k -threads 2 udp://192.168.0.104:1234
```where 192.168.0.104 is the client's computer nat address

...or do real-time viewing directly from a hd-pvr (720p) using:
```
cat /dev/video0 | buffer -s 500k -b 20 -m 20m  | ffmpeg -i - -f mpegts -vcodec mpeg4 -acodec mp2 -ac 2 -ab 128k -s 720x432 -r 30 -re -b 2000k -threads 2 udp://192.168.0.104:1234

```Depending on your cpu speed, various parameters may be adjusted for higher and lower quality as desired. It is critical that the server can keep up with the framerate of the video set by the -r parameter. If transcoding is not required, relatively little cpu is needed.

I use smplayer on the client, opening the file as udp://192.168.0.104:1234. A healthy cache size works best on the client.

Since this is udp, there is no control from the client machine, though one can pause and resume the video until the cache overflows. Ffmpeg also seems to support rtp streaming but I haven't gotten that working.

---

