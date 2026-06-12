---
title: "Screencasting with ffmpeg gives washed out colors"
date: 2013-03-11
forum: Multimedia Software
---

### Post by Pithikos on 2013-03-11
I use ffmpeg to record the whole screen with lossless quality. I run this command:
```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1920x1080 -i :0.0 -acodec pcm_s16le -vcodec libx264 -preset ultrafast -qp 0 -threads 0 output.mkv
```

The screen shows this:
[IMG]http://i.stack.imgur.com/UmH36.png[/IMG]

And this is what I get:
[IMG]http://i.stack.imgur.com/lr5Nt.png[/IMG]

Why are the colors washed out? I have spent the whole day trying to fix this but I have no clue why the quality sucks so bad ](*,) I just want to record the screen exactly how it looks!

---

### Post by FakeOutdoorsman on 2013-03-11
The issue is from converting from BGRA color space to YUV color space, chroma subsampled 4:2:0. Even if you did not limit it to 4:2:0, then your player may convert it to 4:2:0 upon playback...assuming your player is capable, and crappy players like QuickTime will probably just show nothing or distorted output for non-4:2:0. I don't know what to recommend. Perhaps asking on the [ffmpeg-user mailing list](http://ffmpeg.org/mailman/admindb/ffmpeg-user) for a recommendation on how to avoid or improve the conversion will provide some clues.

Providing text console output instead of images allows it to be quoted easier.

---

### Post by Pithikos on 2013-03-11
> **FakeOutdoorsman said:**
> The issue is from converting from BGRA color space to YUV color space, chroma subsampled 4:2:0. Even if you did not limit it to 4:2:0, then your player may convert it to 4:2:0 upon playback...assuming your player is capable, and crappy players like QuickTime will probably just show nothing or distorted output for non-4:2:0. I don't know what to recommend. Perhaps asking on the [ffmpeg-user mailing list]("http://ffmpeg.org/mailman/admindb/ffmpeg-user") for a recommendation on how to avoid or improve the conversion will provide some clues.

Providing text console output instead of images allows it to be quoted easier.

The images were merely taken to show the quality of the videos(I try to screencast the terminal), not to look at the content.

I managed to get around by using a lossless codec instead of x264. I use:

```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 15 -s 1024x720 -i :0.0+0,25 -acodec flac -vcodec huffyuv -preset slow -qp 0 -threads 4 output.mkv
```

However this is a workaround as the file size becomes huge.

Direct audio output to PCM format is not possible as you get an error when you use it with HUFYUV+MATROTSKA. That's why I use FLAC for audio on this command.

---

### Post by mc4man on 2013-03-12
Just to note - see the same with the various gui sceen cap tools
 
So if you find anything useful post back...
A slight workaround here is to raise the saturation a bit & maybe adjust the gamma slightly. (darken
(haven't tried both at once, the sat does make it a bit better

May be other ways, have used (i think s= goes from 1.0 to 2.0
-filter:v hue=h=0:s=1.2

---

