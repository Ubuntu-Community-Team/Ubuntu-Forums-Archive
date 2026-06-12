---
title: "KWorld DVD Maker USB in MythTV"
date: 2009-05-30
forum: Multimedia Software
---

### Post by coolen on 2009-05-30
I recently purchased a KWorld USB DVD-Maker. Fiddled around for a bit, and was very glad to see that it was possible to get it working with Linux.

All I'm doing is using it to watch (and hopefully record) video from my settop box. Video and audio go into this little box, with a USB cable and audio jack on the other side.

Cheese and MPlayer can both get video just fine. Cheese can also get audio and make recordings (at the moment I'm using it to watch Dilbert from my XBox ^_^).

The problem is with MythTV. I want something with better recording abilities than Cheese, so I thought I'd give it a try at long last. I it up correctly, I think (/dev/video0, which is what Cheese sees it as, MPlayer just takes tv:// by the look of it). The card type is set as an Analog V4L capture card, the probed info matches what Cheese gives me, input is composite (this is what I'm using)...not sure what other settings to use, honestly. VBI device is blank.

Anyway, when I go to Watch TV in MythTV, the screen flickers momentarily and I get the menu again. Am I missing something?

---

