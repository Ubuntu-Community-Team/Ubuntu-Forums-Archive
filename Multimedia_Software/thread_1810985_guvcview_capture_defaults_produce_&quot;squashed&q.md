---
title: "guvcview capture defaults produce &quot;squashed&quot; sound"
date: 2011-07-24
forum: Multimedia Software
---

### Post by taojian on 2011-07-24
Capturing video on natty with a builtin webcam, using guvcview, produces an AVI file where the sound track is "squashed" into about two-thirds of the total clip time. Ie, it sounds like it's been compressed down in time, you can't hear things clearly, and then the last third of the video clip is silent.

A friend sent me a video with this problem. I thought she'd screwed something up, so I recorded a test clip, using factory defaults, and the same thing happened.

The problem seems to be that gucview records audio directly from your microphone by default. If I switched the input source to pulse audio, it recorded correctly.

So two things:

1. Could it do that by default?
2. Now that I have a video clip with screwed up audio, is there anyway to "fix" it? I assume there's lost sound data there, but could the track be "stretched" out to its proper length somehow?

Thanks,
Eric

---

