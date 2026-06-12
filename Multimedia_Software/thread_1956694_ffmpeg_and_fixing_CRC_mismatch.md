---
title: "ffmpeg and fixing CRC mismatch"
date: 2012-04-11
forum: Multimedia Software
---

### Post by sbbaxter on 2012-04-11
Hi

I have a number of .ts TV recordings I'm trying to encode to .avi (using mpeg4 or libx264).  I'm using ProjectX to demux the raw files from VDR, then using ffmpeg as follows:
ffmpeg -i 00001.m2v -i 00001.ac3 -acodec libmp3lame -ab 128k -ac 2 -vcodec libx264 -preset fast -crf 24 -vf scale='640:-1' -threads 0 /srv/video/Current/Torrents/Fringe-2012-03-30.avi

For about 1/2 my recordings, this works perfectly.  The other half seem to have CRC errors or sync errors in the original .ts recording, and the resulting .avi file has errors in the header.  mplayer reports:

Playing /srv/video/Current/Torrents/Fringe-2012-03-30a.avi.
AVI file format detected.
ID_VIDEO_ID=0
[aviheader] Video stream found, -vid 0
ID_AUDIO_ID=1
[aviheader] Audio stream found, -aid 1
[B]** empty list?!
Could not determine number of frames (for absolute seek).
[/B]VIDEO:  [H264]  640x360  24bpp  59.940 fps  -17179870.0 kbps (-2097152.0 kbyte/s)

If I force the demuxer to lavf, it plays fine:
mplayer -demuxer lavf /srv/video/Current/Torrents/Fringe-2012-03-30a.avi

But vlc or MediaPlayer under Windows won't render or play the file.

The problem appears to be caused by errors in the original .ts file.

Any ideas on how to fix this?  Using ffmpeg?  Anything else?

---

### Post by andrew.46 on 2012-04-11
h.264 in an avi container can be problematical, try *Fringe-2012-03-30.**[COLOR="Red"]mp4[/COLOR]*** and see if the error vanishes.

---

### Post by sbbaxter on 2012-04-12
Perfect!

Thanks - switch to .mp4 container fixes the problem:

ffmpeg -i 00001.m2v -i 00001.ac3 -acodec libmp3lame -ab 128k -ac 2 -vcodec libx264 -preset fast -crf 24 -vf scale='640:-1' -threads 0 /srv/video/Current/Torrents/Fringe-2012-03-30.mp4

---

### Post by andrew.46 on 2012-04-12
Great news :).

---

