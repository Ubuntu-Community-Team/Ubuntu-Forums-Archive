---
title: "Controlling bitrate in avconv"
date: 2012-03-26
forum: Multimedia Software
---

### Post by Digitante on 2012-03-26
I'm trying to use the commandline "avconv" tool to do some video encoding. I'm outputting MKV/VP8 container and codec.

I'm trying to encode high-definition/high-quality video at about 18 mbps (i.e. similar to broadcast HDTV or Blu-Ray disk) from the original uncompressed stream.

From the manpage, I think I can set this with these options:

-b:v 18000k -maxrate:v 20000k -minrate:v 16000

When I do this, I get a correct-looking response from avconv on the console:

```

Stream #0.0(eng): Video: libvpx, yuv420p, 1920x1080, q=-1--1, 18000 kb/s, 1k tbn, 24 tbc

```However, the status during decoding reports the bit rate at about 2000 kbps -- about 10X lower bitrate:

```

bitrate=2078.1kbits/s 

```And the resulting file's size concurs with this.

Now, if it were doing a perfect job, the low bitrate would be good news, and I wouldn't complain, but in fact, I still see a lot of obvious artifacts, even on my desktop screen. On a home theater, it would probably be pretty disappointing.

So what's up? How do I get it to use more bits? Why is it not honoring the target or minimum bitrates? What am I missing here? I'm still pretty new at this, so I could easily be doing something dumb.

FWIW, here's the entire commandline I used:

```

avconv -i SSTB_Feb09_1920x1080.mov -c:v libvpx -c:a libvorbis -q:a 10 -r:v 24 -s hd1080 -b:v 18000k -maxrate:v 20000k -minrate:v 16000k SStB-avconv-160_200mbps-3.mkv

```

Is it possible that avconv just can't do this? (If so, what can?) I tried using vpxenc directly but I just got garbage out -- I think maybe it couldn't read the input file correctly (the original is an uncompressed MOV file -- I could conceivably make a PNG-stream from it or some other intermediate step, though I haven't tried that yet).

Any help appreciated! :)

---

