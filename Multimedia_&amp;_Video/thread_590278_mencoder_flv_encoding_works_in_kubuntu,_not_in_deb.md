---
title: "mencoder flv encoding works in kubuntu, not in debian"
date: 2007-10-24
forum: Multimedia &amp; Video
---

### Post by jqp on 2007-10-24
I've been working on a PHP script to encode uploaded videos to FLV to be played in flash.

On my computer, the encoding works fine.  I have w32codecs, mencoder and mplayer installed with dependencies

My command line looks like this;
```
mencoder $infile -o $outfile.flv -ffourcc FLV1 -oac mp3lame -of lavf -ovc lavc -lavcopts vcodec=flv:acodec=mp3:abitrate=56 -lavfopts i_certify_that_my_video_stream_does_not_use_b_frames -srate 22050 -vf scale=450:-3::::::1
```

On my computer, this works fine - the video plays fine in Flash player.  I'm running Kubuntu Gutsy.

The server is running Debian Etch, and has mencoder, w32codects, and mplayer-nogui installed.

Running the same code, the encoding appears to work without an error, but the new flv video does't play in Flash player.  I tried also playing the video in player, and I get this output:

```
...
AO: [alsa] 48000Hz 1ch s16le (2 bytes per sample)
Video: no video
Starting playback...
[flv @ 0x87940c8]Unsupported video codec (6)
[flv @ 0x87940c8]Unsupported video codec (6)
[flv @ 0x87940c8]Unsupported video codec (6)
[flv @ 0x87940c8]Unsupported video codec (6)
...
```

Any idea what I need to do to make it work on the debian server?

---

