---
title: "dvgrab creates dv2 with slow audio"
date: 2012-01-30
forum: Multimedia Software
---

### Post by dave0109 on 2012-01-30
I am using dvgrab (from the command line) to extract video from my DV camera, over firewire.  If I use the dv1 or raw types, then everything is perfect, except that AVIdemux doesn't like those file types, so I can't convert to MPEG4 and shove the video onto my media centre.

AVIdemux is, however, happy with the dv2 format, but dvgrab seems to have a problem capturing the audio, which runs at about 50% speed.

Any ideas?

---

### Post by Jose Catre-Vandis on 2012-02-01
can you convert the dv1 using ffmpeg? Something like:

```
ffmpeg -i input.dv1 [options] output.mp4
```

Options you might want are when in the input file to start and to stop. Use "-ss 00:00:00" for your start point and "-t 000" (number of seconds) for length of the encode.

---

### Post by dave0109 on 2012-02-07
Thanks, I resorted to using Handbrake to do the conversion, although I'm having problems with field dominance, but that's another topic.

Would still like to get dvgrab fixed though.  Guess I'll have to find their forum and report it directly.

---

### Post by FakeOutdoorsman on 2012-02-09
What are your dvgrab commands so I can attempt to reproduce the behavior? Does dv2 play at 50% speed in Avidemux or some other player?

---

### Post by dave0109 on 2012-02-12
The command was just a basic:

```

dvgrab -a -f dv2 -t tape28-

```

The first time, I was capturing the whole tape, on which I had 3 complete edits. The first one is 12 mins, but when I played it in VLC, it showed 18 minutes.  The video was fine, but the audio was slow.  Actually given the times above, maybe the audio is at 66.67%.  Just to rule out VLC, I encoded the video with Avidemux and had the same, slow, audio.

Subsequent attempts, I used a '-d 12:30' parameter, to save me some time, and I switched between '-f dv1', '-f raw', and '-f dv2'.

---

### Post by mafeuser on 2012-10-16
Hallo People!
Are there any news on that problem?

Unfortunatelly I meet the same problem, ie. sometimes audio goes too fast and sometimes too slow:(

Have You got any idea how to synchronise audio back to video using ffmpeg?

best regards

---

### Post by FakeOutdoorsman on 2012-10-16
I've noticed that dvgrab will sometimes capture "junk" for a second of two before the actual video and audio streams begin. The junk may actually be on the tapes I'm working with, but I'm not sure. This junk stream will have an audio rate of 48000 kHz, but the actual audio may vary. Perhaps some players do not notice a change in the audio rate and assume it is all 48000 when it may actually be 32000 (I blame Sony).

If ffmpeg does not correctly recognize this then perhaps you can cut out the first section with *dd* and see if that makes an improvement.

```
dd if=input.dv of=output.dv bs=1024 count=100000 skip=2560
```

With the count option, this command will create *output.dv* with a file size of about 102 MB, or a duration of ~28 seconds. Be very mindful that you use the correct output file name otherwise you can overwrite something important. Also, you may have to vary the skip value. If the resulting file works as expected then remove *count=100000* to process the complete file.

---

### Post by mafeuser on 2012-10-17
thank You for the answer.
Your note is very interresting.
for klips with foo fast audio I checked
audio_time/video_time=0.647639762507

and for audio frequency comparison!:
32000/48000=0.666666666667

what is more for some clips tcprobe tells audio frequency is 48kHz and for others 32kHz.

thus maybe the following is true:
if:

tcprobe tells 48kHz, but the real frequency is 32kHz then sound goes too fast,
but if:
tcprobe tells 32kHz, but the real frequency is 38kHz, then sound goes too slow.

Why mistakes on audio frequency in AVI headers?
Maybe this happens when dv tape is recorded several times, and on some point overwriting clip takes somehow information from the overwritten one????

do You know any way how to fix frequency rate info in AVI files?

best regards,
Paul

---

### Post by FakeOutdoorsman on 2012-10-25
> **mafeuser said:**
> Why mistakes on audio frequency in AVI headers?
I don't know. I'm working with raw DV files.

> Maybe this happens when dv tape is recorded several times, and on some point overwriting clip takes somehow information from the overwritten one????
Seems like a good guess to me.

> do You know any way how to fix frequency rate info in AVI files?
For my files I've been simply cutting off the junk in the beginning with *dd* and then ffmpeg seems to work with it just fine. Otherwise I've seen a few videos that play at a faster rate, but it isn't consistent among all files.

You could always try to force the audio rate with *-ar* in ffmpeg.

---

