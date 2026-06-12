---
title: "Connecting 2 alsa devices together? (output from one as input to other)"
date: 2008-03-25
forum: Multimedia &amp; Video
---

### Post by tvst on 2008-03-25
I have two alsa devices (well, 3 actually but I only care about two of them for the discussion in this post) so let's call them hw:0 and hw:1. I would like to have the output of hw:1 to be channeled into the input of hw:0 without using actual cables. I'm sure I can do this by changing my asoundrc somehow, but I just can't seem to figure out what exactly I should be typing. The documentation on that is really cryptic.

To clarify, this is what I want:
(hw:1) --> (hw:0) --> speakers

I can easily do this with JACK but that's not a good solution for me. Plus I get lots of crackling on the audio, although there should be some buffer length somewhere that can be increased to deal with this.

If you're wondering why I need this: hw:1 is my USB TV tuner card, which is only half-compatible with Linux. That is, it gives me perfect video, but no audio. However, I found it is recognized by ALSA as an audio card and that I can connect it to my real audio card using JACK. So now that I know each separate piece of hardware is working properly, I would like to find a more definite solution to my problem.

Any suggestions?

---

