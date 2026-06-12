---
title: "Stuttering ogg-files with ffmpeg2theora ?"
date: 2012-01-09
forum: Multimedia Software
---

### Post by HolgerB on 2012-01-09
Hi all,

I have been experimenting a bit with the ogg codec familiy lately (Vorbis audio and Theora video). For this I used ffmpeg2theora (latest version from [http://v2v.cc/~j/ffmpeg2theora/](http://v2v.cc/~j/ffmpeg2theora/)). In order to get a better feeling for the performance of Theora I tried various sources: DVB-T streams with 25 FPS, 720p HD from satellite and a copy of a PAL DVD. While the resulting video was nice in terms of quality, all those generated ogg files were extremely changing the playback speed. A few frames look like in slow-motion and then the movie seems to speed up to fast-forward speed. I tried to set the output FPS as well as using different player (VLC, Mplayer). I even tried to play back the files on different PCs but the ogg files produces by ffmpeg2theora stuttered everywhere. It seems to be an issue of the encoded files itself since even the remuxed theora video (via Matroska Mux GUI) stutters. The oggz-tools (namely oggz-validate) do not report any corruption to the files itself.

Has anyone of you experience similar issues with ffmpeg2theora ? Or should I completely away from ffmpeg2theora and use plain ffmpeg ?

TIA,
Holger

---

### Post by andrew.46 on 2012-01-09
> **HolgerB said:**
> Has anyone of you experience similar issues with ffmpeg2theora ? Or should I completely away from ffmpeg2theora and use plain ffmpeg ?

Perhaps at least run a few input files with FFmpeg, Fakeoutdoorsman show the way:

[http://ubuntuforums.org/showpost.php?p=11412993&postcount=3](http://ubuntuforums.org/showpost.php?p=11412993&postcount=3)

---

### Post by HolgerB on 2012-01-09
> **andrew.46 said:**
> Perhaps at least run a few input files with FFmpeg, Fakeoutdoorsman show the way:

[http://ubuntuforums.org/showpost.php?p=11412993&postcount=3](http://ubuntuforums.org/showpost.php?p=11412993&postcount=3)

Man, thanks...one can be stupid :)

I used -v (= Quality-setting) and -V (=bitrate setting) at the same time. This seems to have caused the stuttering. I first tried ffmpeg with the commandline from the link you provided and it worked.

---

### Post by andrew.46 on 2012-01-09
Great news :)

---

### Post by HolgerB on 2012-01-10
> **andrew.46 said:**
> Great news :)
Indeed !

We simple had PEBCAK again !  ](*,)](*,)](*,)

---

