---
title: "ffmpeg / avconv behaviour change 10.04 -&gt; 12.04"
date: 2012-06-07
forum: Multimedia Software
---

### Post by at both ends on 2012-06-07
Converted recently from 10.04LTS (ubuntu) to 12.04LTS(xubuntu).

I run a cron job to invoke icecream to record a 64 kb/s shoutcast radio show once a week and, when I have time, clip off the front and back minutes which are mostly ads. Under 10.04, I used ffmpeg, which is gone under 12.04 and replaced by avconv. (I reinstalled ffmpeg under 12.04 just to see if it behaves as avconv does, and it does, so the ffmpeg/avconv fork is irrelevant here.) The show usually runs two hours but, due to unannounced schedule change, ran only 90 minutes this week. My clipping was going to cut off about 1/4 of the file.

I was surprised to see that the output file (avconv or ffmpeg, didn't matter which) was bigger than the input. So I looked carefully at the logs and found that, by default, a 64 kb/s input stream was detected as such but the output defaulted to 160 kb/s. If I forced -ab 64k, I saw a resonable reduction in file size.

Since this happens with both avconv and ffmpeg, I assume it's a change in an underlying library (most likely libmp3lame) sometime between 10.04 and 12.04. Fair enough. Lots of things have changed. Can't stop progress and all that.

My question is a simple one: Why would any software encode audio at a higher bit rate in output than is available in the input? This makes no sense to me, as it has to involve pure invention of data.

---

### Post by FakeOutdoorsman on 2012-06-08
> **at both ends said:**
> I run a cron job to invoke icecream to record a 64 kb/s shoutcast radio show once a week and, when I have time, clip off the front and back minutes which are mostly ads.

You may already know this, but the *-ss* and *-t* commands can used in conjunction with *-acodec copy* (or *-c:a copy* or *-c copy* depending your ffmpeg version and input[s]) to trim your file without re-encoding. This preserves the quality, but maybe you require a different audio format which would require re-encoding. This example will skip the first 120 seconds and then create an output that is 2 minutes and 30 seconds long:

```
ffmpeg -i input.mp3 -ss 120 -t 00:02:30 -acodec copy output.mp3
```

> **at both ends said:**
> My question is a simple one: Why would any software encode audio at a higher bit rate in output than is available in the input? This makes no sense to me, as it has to involve pure invention of data.

The default for audio encoding, when *-ab*/*-b:a* or *-aq*/*-q:a* (syntax differences between versions) are not declared was previously set to *-ab 64k*, but was changed to *-ab 128k*.

FFmpeg can't predict what rate people want or what is "best" concerning the bitrate of the input. Copying the input bitrate isn't always a good idea anyway. An alternative method is to use *-aq*. This will only use as much bitrate as needed to reach a certain quality level and will result in a VBR output. External encoders, such as libmp3lame, all use different values for *-aq*, and for libmp3lame this option is mapped to the *-V* option in lame. See [LAME - Recommended encoder settings](http://wiki.hydrogenaudio.org/index.php?title=LAME#Recommended_encoder_settings) at Hydrogenaudio to get a good idea of what *-aq* value to use.

For even more control you can pipe from ffmpeg to lame:
```
ffmpeg -i input -ss 14 -t 320 -f wav - | lame --abr 56 -mm - output.mp3
```

---

