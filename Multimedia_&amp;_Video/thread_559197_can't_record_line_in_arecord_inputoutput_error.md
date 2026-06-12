---
title: "can't record line in: arecord: input/output error"
date: 2007-09-24
forum: Multimedia &amp; Video
---

### Post by tedder on 2007-09-24
So if I try to run arecord, it'll time out after 10 seconds with an i/o error. The resulting file (or stdout) will be blank, minus headers.

```
$ cat /proc/asound/devices
  2:        : timer
  3:        : sequencer
  4: [ 0- 2]: digital audio playback
  5: [ 0- 1]: digital audio capture
  6: [ 0- 0]: digital audio playback
  7: [ 0- 0]: digital audio capture
  8: [ 0]   : control
  9: [ 1- 0]: digital audio capture
 10: [ 1]   : control

```

(only showing with input 0,0 but the result is the same for all three capture sources)
```
$ time sudo arecord --device=hw:0,0 -f dat -d 16000 -
Recording WAVE '-' : Signed 16 bit Little Endian, Rate 48000 Hz, Stereo
RIFF$WAVEfmt »îdataarecord: pcm_read:1346: read error: Input/output error

real    0m10.031s
user    0m0.000s
sys     0m0.008s
```

I've looked at my device mapping in alsamixer, but ultimately, even if a source was muted, there would be output. So I'm having trouble grabbing the device, it seems.

FWIW, sox times out in a similar manner:
```
$ time sudo /usr/bin/sox -t ossdsp -w -s /dev/dsp -t raw  -

Input File     : '/dev/dsp' (ossdsp)
Sample Size    : 16-bit (2 bytes)
Sample Encoding: signed (2's complement)
Channels       : 1
Sample Rate    : 8000

/usr/bin/sox sox: /dev/dsp: Premature EOF while reading sample file. (Input/output error)


Done.

real    0m10.003s
user    0m0.000s
sys     0m0.004s

```

What are the next things to troubleshoot? Am I missing something obvious?

My audio card certainly works for playback.

---

### Post by tedder on 2007-10-13
This ended up being due to a bug in the ivtv drivers, which has been patched. Here's information on it:
[http://ubuntuforums.org/showthread.php?t=568469](http://ubuntuforums.org/showthread.php?t=568469)

---

