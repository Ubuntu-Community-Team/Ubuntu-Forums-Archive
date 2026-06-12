---
title: "recording via mic no longer works"
date: 2008-08-05
forum: Multimedia Software
---

### Post by lmsurprenant on 2008-08-05
In the past I have been able to record myself using gnome-sound-recorder with no issues.  I have probably updated many packages since then (including moving to 8.04).  Now, when I try to record, although the status bar reads "Recording.." and the Length is increasing, I am unable to play the recording (by hitting play nor by saving as a wav/speex file).

My sound settings should be the same as my previous config which worked...if I open volume control I can see my device is set to HDA ULI M5461 (ALSA Mixer).

When run from command line, the only error I get is:

lee@lee-desktop:~$ gnome-sound-recorder --gst-debug-level=2
0:00:00.478872599 13196 0x805e408 ERROR         GST_PIPELINE ./grammar.y:558:_gst_parse_yyparse: no element "lame"

Similarly, when trying to record in audacity, I can see my voice being picked up and recorded...but cannot play it back at all.  In fact, if I click the play button in audacity I see

"Error while opening sound device. Please check the output device settings and the project sample rate."

All other audio seems to be working fine.  Please help!

---

### Post by lmsurprenant on 2009-01-25
This problem seems to have magically taken care of itself.  For future reference, this problem may be related to the fact my integrated sound card(Realtek ALC880) blows.

---

