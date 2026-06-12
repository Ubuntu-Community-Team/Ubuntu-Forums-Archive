---
title: "dvgrab &quot;# no audio&quot; warnings worth concern?"
date: 2010-12-14
forum: Multimedia Software
---

### Post by gewone on 2010-12-14
Hi guys!
I'm grabbing a bounce of one-hour DV tapes into my box.
Thing is, quite often I get a bounce of "# no audio" warnings during the grab.
Is this something I should pay attention to? Or simply ignore?
Like this time for example:

[I]```
gewoh@rax:/dvstuff$ dvgrab -s 0 -f dv2
Found AV/C device with GUID 0x0800460103cfcc7f
Turning on OpenDML to support large file size.
Waiting for DV...
Capture Started
# no audio
# no audio
# no audio
# no audio
# no audio
# no audio
# no audio
# no audio
# no audio
# no audio
# no audio
# no audio
# no audio
# no audio
# no audio
# no audio
# no audio
# no audio
# no audio
# no audio
# no audio
# no audio
# no audio
Capture Stopped

```[/I]

A total of 23x *"# no audio"* warnings.
Does this simply imply that 23 frames (out of the total of 25x3600) dropped audio? I can live with that.
However, I'm more scared that each such audio drop is causing the audio to go progressively out of sync! :/

Any ideas?
Please calm me down.

---

