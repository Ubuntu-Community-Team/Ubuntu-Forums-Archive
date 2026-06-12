---
title: "rm to avi"
date: 2008-08-11
forum: Multimedia Software
---

### Post by bobotoes on 2008-08-11
How can I convert rm (real player) video to avi without loss of quality?

---

### Post by tuxxy on 2008-08-11
> MEncoder

A decent media player is one of the prerequisites of a good desktop. Sometimes you may want more than that. For example, you may have backed up the hard-to-watch Robotech series to the .rm format, but now you would like to watch it on your vcd player. MPlayer also has a solution for this: it can crosscode nearly all media files. If you have compiled the MPlayer package, MEncoder is also present. 

The syntax is very simple. This command line encodes the basket.rm file with the libav codec (the best divx codec for both performance and quality) and the soundtrack with mp3lame. 

```
mencoder -ovc lavc basket.rm -oac mp3lame -o basket.avi
```

Remember the avi file with the broken index? Instead of always using the workaround, you can permanently fix it with MEncoder. The following command rebuilds the index and copies the whole audio and video stream as they are to the output file. 

```
mencoder -idx input.avi -ovc copy -oac copy -o output.avi
```

Perhaps you'd like to catenate multiple avi files into one single file. Provided they use the same codec and have the same bitrate, this is also easy. It's back to Unix roots:

```
cat 1.avi 2.avi | mencoder -noidx -ovc copy -oac copy -o output.avi -
```

I'll not go into much detail here, because MPlayer and MEncoder have more options than I can describe in this article. Enjoy these rich programs and experiment with the settings.

[http://www.linuxdevcenter.com/pub/a/linux/2003/04/06/mplayer.html](http://www.linuxdevcenter.com/pub/a/linux/2003/04/06/mplayer.html)

---

### Post by bobotoes on 2008-08-11
That worked pretty well. Thanks. The video and audio are not in sync though. Is there a way to correct this?

---

### Post by tuxxy on 2008-08-11
[This thread]("http://www.meizume.com/video-imaging/106-mencoder-video-converter-info.html") may be of use

---

### Post by bobotoes on 2008-08-12
As far as A/V sync and original quality goes, I am achieving best results with the following: ```
$ mencoder rtsp://path/to/file.rm -ovc lavc -oac pcm -o file.avi
```There is one problem though. file.avi is 4 times as large as file.rm. file.rm is available for complete download or as a stream, so I am basing its size on the downloaded version. Is there some compression flag to include that will maintain high quality?

---

