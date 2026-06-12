---
title: "FFMPEG blocking after 12.04 Precise upgrade"
date: 2012-05-13
forum: Multimedia Software
---

### Post by ZeroFossilFuel on 2012-05-13
When playing a HD .MTS Canon video with VLC or trying to convert with WinFF, I am getting a LOT of interlaced video blocking or tiling at the edges of moving objects. See attached. Videos play fine in Xine and MPlayer which use MEncoder to render. I've searched the forum threads and find nothing on this topic. Can't believe I'm the only one.

Primary machine is Intel i5 760, Intel DQ57TM MoBo, Nvidia 9600GT, 8GB ram, 1.6TB storage.

It was working fine in 11.10. I've tried all the codec upgrades and hacks I could find including the Jon Severinsson Precise PPA. I have the same problem on 3 different machines with video adapters from ATI and Nvidia. Running out of ideas and I've got videos backing up that I want to produce!

Z

---

### Post by ZeroFossilFuel on 2012-05-20
Anyone?

---

### Post by Jose Catre-Vandis on 2012-05-22
Have you got ffmpeg compiled or just the repo install?

Do the artifacts appear after encoding or with the raw video? Can you explain exactly your workflow: e.g. Copy raw video to PC, encode raw video to ?? format, playback in VLC shows artifacts, etc

---

### Post by ZeroFossilFuel on 2012-05-22
> **Jose Catre-Vandis said:**
> Have you got ffmpeg compiled or just the repo install?

Do the artifacts appear after encoding or with the raw video? Can you explain exactly your workflow: e.g. Copy raw video to PC, encode raw video to ?? format, playback in VLC shows artifacts, etc

Thanks for your reply. I am using compiled versions of ffmpeg from the repo.

In Kdenlive I usually render to 720p. Camera shoots at 1080p. To keep KL from complaining about source and project settings mismatch, I transcode my clips first using WinFF, then bring them in to KL. (I was using Xvid Widescreen but that's not working anymore either, even though I have libxvidcore4 loaded. Nor is AC3 even though I have libavcodec-extra-53 loaded. That's a separate problem for another thread.)

I noticed the artifacts when checking the transcoded clips the first time after the 12.04 upgrade using VLC. So I tried viewing the raw clips using VLC and the same artifacts persist. When viewing the raw clips using Xine or mplayer, the video is perfectly clean, no artifacts.

I also tried rendering the raw clips to 720p using KL. The output files are still not perfect but they are much cleaner. And at the end of each rendering job I get a crash error message even though the output files seem to be okay, I presume also related to the ffmpeg bug.

As nauseating as the thought is, I'm actually considering rendering my latest projects in WMM. Yuk.

Hope someone can save me from this a fate.

---

### Post by thatguruguy on 2012-05-22
That's really weird.

Have you tried converting to an .mp4, following the instructions [here]("http://pvdm.xs4all.nl/wiki/index.php5/Convert_an_AVCHD_/_MTS_file_to_MP4_using_ffmpeg")?  You can also size it while converting, by using the following flag:
```
-s 1280x720
```

---

### Post by rreese6 on 2012-05-23
Try to use the GIT repository and compile from there.
[http://ffmpeg.org/]("http://ffmpeg.org/")
I always found the repro packages and their sources to be missing features I needed.

use your package manager to install GIT

Best Regards,

---

### Post by ZeroFossilFuel on 2012-05-25
> **thatguruguy said:**
> That's really weird.

Have you tried converting to an .mp4, following the instructions [here]("http://pvdm.xs4all.nl/wiki/index.php5/Convert_an_AVCHD_/_MTS_file_to_MP4_using_ffmpeg")?  You can also size it while converting, by using the following flag:
```
-s 1280x720
```
I had not tried that but you are correct. I tried it on one clip and that did work. I can play back the converted clips in any player fine. This is a band-aid for for the underlying problem but at least maybe I can get some work done while other bugs are being worked out. Thank you for that.

Stupid me for upgrading to 12.04 before allowing the dust to settle.

---

### Post by ZeroFossilFuel on 2012-08-10
Bump.

Several kernel upgrades, VLC and ffmpeg updates later and I still have all these same problems. I can convert via the command line method fine and I can even import directly to kdenlive now. But VLC still produces the block effect and WinFF still cannot convert the files with ffmpeg without the block effect.

FWIW, I give generously to Ubuntu and 3rd party app development efforts and encourage others to do the same. But sometimes I wonder............

---

