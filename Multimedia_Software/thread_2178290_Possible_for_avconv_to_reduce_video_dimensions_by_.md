---
title: "Possible for avconv to reduce video dimensions by percentage?"
date: 2013-10-02
forum: Multimedia Software
---

### Post by MrnKGph on 2013-10-02
Long story short, is it possible for avconv to reduce the dimensions of a video by a percent? In my case, 50% smaller.

If the original video is 1280x720, I would like the output to be 640x360.
If the original video is 1024x768, I would like the output to be 512x384.
... and so on.

Is there a single generic parameter I can use that would allow me to automate the process in a script?

---

### Post by TheFu on 2013-10-02
Only deal with the 2nd resolution and have your script divide by 2 then look for the closes mod-16 number.  Turns out that using modulus 16 numbers is more efficient with many codec transcodes.

Or you could build a table.

I don't use avonv myself, switched to handbrakeCLI about 2 yrs ago to use the "constant quality" setting under h.264.  When I was using mplayer with xvid, I scripted this stuff.

BTW, there no need to ask about options for most Linux tools. The "man page" will explain all available options.  Just looked at the avconv man page - no percent resize option exists in the version that I have loaded, however, simple calculations ARE supported, including trig functions.

---

### Post by FakeOutdoorsman on 2013-10-02
You can do this with the [scale](http://ffmpeg.org/ffmpeg-filters.html#scale) video filter:

```
ffmpeg -i input -vf scale=iw*0.5:-1 -codec:a copy output
```

"-codec:a copy" will allow you to [steam copy](http://ffmpeg.org/ffmpeg.html#Stream-copy) the audio and avoid re-encoding.

Note that my advice only applies to ffmpeg from FFmpeg, and not anything from the fork Libav, so it may not work for anything from the repository.

---

