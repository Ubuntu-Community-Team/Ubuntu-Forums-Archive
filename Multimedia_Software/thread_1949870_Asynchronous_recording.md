---
title: "Asynchronous recording?"
date: 2012-03-31
forum: Multimedia Software
---

### Post by Halbblutplins on 2012-03-31
I was recording my desktop with ffmpeg yesterday and today I wanted to convert it to an other format and than I've recorgnized that the audio track is to long so it is asynchronous.

[U][U]I hope someone of you will be able to help me!!!
[/U][/U]

---

### Post by BicyclerBoy on 2012-03-31
I don't understand..

Is the video & audio out of sync ?
Does the A/V sync get progressively worse from start to end ?

What codec/container did you choose for your recording?

---

### Post by Halbblutplins on 2012-04-02
The audio track gets shorter while recording so after stopping recording the audio track is shorter than the video??????


My scrpit:

```
ffmpeg -f alsa -ac 2 -i pulse -s 1366x768 -f x11grab -i :0.0 -r 30 -qscale 1 -acodec aac -strict experimental -vcodec mpeg4 /home/peter/screencast.mp4
```
Hope you have a solution.......


Peter

---

### Post by BicyclerBoy on 2012-04-03
Could be that your PC is not fast enough to display/capture/encode mjpeg to mpeg4 (xvid?) at 30fps.

Do you really want xvid & AAC together?

So could try 15fps and/or encode the video to mpeg2 or leave as mjpeg & then post-transcode mjpeg (all I frames) to mpeg4/10 (h264) or mpeg4/2 (ASP-xvid).

There are other sync options we could try if above fails.

---

### Post by Halbblutplins on 2012-04-04
My pc is fast enough for this thing, it has even worked 1 month ago.

I tried to record only one audio source and this has helped &#8594; everything perfect but if I record 2 audio sources, with pulse and this script:

```
pactl load-module module-null-sink sink_name=mix
pactl load-module module-loopback sink=mix
pactl load-module module-loopback sink=mix
```

it isn't synchron anymore! ???


Peter

---

