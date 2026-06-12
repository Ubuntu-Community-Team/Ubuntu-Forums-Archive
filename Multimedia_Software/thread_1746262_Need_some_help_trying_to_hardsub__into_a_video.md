---
title: "Need some help trying to hardsub *** into a video"
date: 2011-05-01
forum: Multimedia Software
---

### Post by blenderfox on 2011-05-01
Hi,

I'm trying to use mencoder to convert an MKV into a hardsub AVI. The MKV has and *** track, and I've extracted that.

I'm trying to overlay that onto the video by using mencoder and using the following:

```
mencoder -ovc xvid -xvidencopts pass=1 -oac pcm -sub '/home/yukinom/Desktop/Subs/mysubs.***' -o 'myvid.avi' -fps 23.976215 '/home/yukinom/Desktop/Source/sourcevid.mkv'
```

Now, I chose the specific FPS because I was getting loads of duplicate frame errors. Now, if I use this, I get the overlay, but I lose all styles contained within the ***, and I the same text format is used through the video (which is not what is shown in the sub file.) I try using the -*** and the -vf ***,pp switches as shown below, but I still get no subtitles, and I lose sync between audio and video.

```
mencoder -ovc xvid -xvidencopts pass=1 -oac pcm -*** -vf ***,pp -sub '/home/yukinom/Desktop/Subs/mysubs.***' -o 'myvid.avi' -fps 23.976215 '/home/yukinom/Desktop/Source/sourcevid.mkv'
```

Is there an easier way to do this? All I want to do is overlay (burn) the subtitles onto the video, and preserve the text styles contained within the ***. Surely someone else must have wanted to do this, but all I can find are examples of encode switches and people using different format sub files.

EDIT: The "***" are the a s s (**A**dvanced **S**ub**S**tation) abbreviation. Looks like the auto-censoring took it out :P

---

### Post by darzki on 2011-05-01
Mencoder doesn't support 'a s s' subtitle format. You can use mplayer to export all frames with subtitles on to jpg/png but it take huge amount of space. Even so, if you have more than 500GB free on hard disk (for avi quality probably less than that) then be my guest.

About sync problems, try using different variants of:
```
-mc 100
```

---

### Post by blenderfox on 2011-05-02
If mencoder doesn't support 'a s s', then why are there switches that deal with it within it's syntax? Then I use the "-a s s" switch, I see something like this in the output:

```
[***] auto-open
[***] Init
[***] Updating font cache
[***] Added subtitle file: 'mysubs.***' (17 styles, 372 events)

```

So it is doing something with the a s s  file.

> **darzki said:**
> Mencoder doesn't support 'a s s' subtitle format. You can use mplayer to export all frames with subtitles on to jpg/png but it take huge amount of space. Even so, if you have more than 500GB free on hard disk (for avi quality probably less than that) then be my guest.

About sync problems, try using different variants of:
```
-mc 100
```

---

### Post by darzki on 2011-05-02
Maybe some sort of preparation for this, I can't tell. I searched mplayer mailing lists and the latest question about this is from January:
```

http://lists.mplayerhq.hu/pipermail/mencoder-users/2011-January/012502.html

```

As you can see it't still unanswered.

So apparently mencoder doesn't yet support '-a s s' subtitles - I'm waiting for this too.

---

### Post by blenderfox on 2011-05-02
> **darzki said:**
> Maybe some sort of preparation for this, I can't tell. I searched mplayer mailing lists and the latest question about this is from January:
```

http://lists.mplayerhq.hu/pipermail/mencoder-users/2011-January/012502.html

```

As you can see it't still unanswered.

So apparently mencoder doesn't yet support '-a s s' subtitles - I'm waiting for this too.

The only way Ive been able to get around this is to convert my MKV into an subless AVI, then load that into avidemux and apply the a s s subs via filter.

---

### Post by darzki on 2011-05-02
This filter works now? Last time (about year ago) I couldn't force it work as I wanted to.

---

### Post by blenderfox on 2011-05-02
> **darzki said:**
> This filter works now? Last time (about year ago) I couldn't force it work as I wanted to.

the avidemux filter? Yes, but it's very temperamental. Sometimes, avidemux will crash or hang.

---

### Post by darzki on 2011-05-02
Handbrake supports 'a s s' subtitle format. Without any fancy stuff, but still it's always something.

```

https://trac.handbrake.fr/wiki/Subtitles

```

I didn't test it, ever, so I can't say anything about quality etc.

---

### Post by blenderfox on 2011-05-03
> **darzki said:**
> Handbrake supports 'a s s' subtitle format. Without any fancy stuff, but still it's always something.

```

https://trac.handbrake.fr/wiki/Subtitles

```

I didn't test it, ever, so I can't say anything about quality etc.

I'll give it a try, but I need to preserve the styles contained within the a s s subfile, so if handbrake doesn't do that, it's probably out of the question.

---

### Post by JohnAStebbins on 2011-05-03
> **momokoyukino said:**
> I'll give it a try, but I need to preserve the styles contained within the a s s subfile, so if handbrake doesn't do that, it's probably out of the question.

HandBrake can hardsub ssa subs, which are not exactly the same as a s s, but usually close enough to work.  It will keep the font and style information.  But the ssa subtitle must already be muxed into your source video.  HandBrake doesn't support importing it from an external file.

Also, you should use the nightly builds of HandBrake since there were significant bugs with ssa subs in the release.  Nightly builds can be found here:
[https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)

---

### Post by blenderfox on 2011-05-03
Well, two of the four videos I'm trying to process are muxed with a s s subs. The last two are separate, but I can easily mux them with mkvmerge, I guess.

---

### Post by blenderfox on 2011-05-03
handbrake did the job. I'm marking this thread as solved now. Thanks for the help :)

---

### Post by blenderfox on 2011-05-04
> **darzki said:**
> Handbrake supports 'a s s' subtitle format. Without any fancy stuff, but still it's always something.

```

https://trac.handbrake.fr/wiki/Subtitles

```

I didn't test it, ever, so I can't say anything about quality etc.

I can tell you now the quality of encoding from handbrake varies depending on the codec you use. I used ffmpeg and got quite a lossy picture, but when I used H.264, I got a far better picture at the cost of turning the encode time from 20 minutes to 90 minutes.

---

### Post by JohnAStebbins on 2011-05-04
> **momokoyukino said:**
> I can tell you now the quality of encoding from handbrake varies depending on the codec you use. I used ffmpeg and got quite a lossy picture, but when I used H.264, I got a far better picture at the cost of turning the encode time from 20 minutes to 90 minutes.

HandBrake's default settings for the ffmpeg mpeg-4 encoder are tuned for speed, so will not generate the best quality to filesize trade-off. In the HandBrake snapshots, we have added an entry box for advanced ffmpeg encoder settings on the advanced tab.  If you know the ffmpeg encoder option strings, you can enter them here.  But mpeg-4 is never going to equal h.264 in quality at the same bitrate.  It's just an older relatively inferior format.

Were you using average bitrate or constant quality mode for your ffmpeg encoding?  If you used constant quality mode, did you set an appropriate value in the quality slider?  A value of 3 produces acceptable quality and 2 is pretty much indistinguishable from the source.  Of coarse, higher quality means larger files.  The ffpmeg quality scale is different than the x264 quality scale.  For x264, a value of 21 is probably roughly the same as a value of 3 for ffmpeg.

---

### Post by blenderfox on 2011-05-04
> **JohnAStebbins said:**
> HandBrake's default settings for the ffmpeg mpeg-4 encoder are tuned for speed, so will not generate the best quality to filesize trade-off. In the HandBrake snapshots, we have added an entry box for advanced ffmpeg encoder settings on the advanced tab.  If you know the ffmpeg encoder option strings, you can enter them here.  But mpeg-4 is never going to equal h.264 in quality at the same bitrate.  It's just an older relatively inferior format.

Were you using average bitrate or constant quality mode for your ffmpeg encoding?  If you used constant quality mode, did you set an appropriate value in the quality slider?  A value of 3 produces acceptable quality and 2 is pretty much indistinguishable from the source.  Of coarse, higher quality means larger files.  The ffpmeg quality scale is different than the x264 quality scale.  For x264, a value of 21 is probably roughly the same as a value of 3 for ffmpeg.

Well, I was accepting defaults mainly to see how fast and how good the quality is. the source is in x264, so I'm keeping it like that. But now I've had a play, I'm going to try tinkering with the settings. Point is, it works. :)

---

