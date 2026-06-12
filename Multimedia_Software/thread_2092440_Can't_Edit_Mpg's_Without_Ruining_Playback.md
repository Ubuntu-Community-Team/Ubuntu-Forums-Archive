---
title: "Can't Edit Mpg's Without Ruining Playback"
date: 2012-12-07
forum: Multimedia Software
---

### Post by strafe_sawdoffe on 2012-12-07
I've just completed transferring about 18 hours of home video from VHS to DVD, and in turn ripped the contents of the DVDs onto my computer using Acidrip. The videos are all in mpg format.

The videos play fine in Totem, but literally *any* attempt to edit them results in choppy playback to the point of being unwatchable. The sound is fine, but the picture pauses 2-3 times every seconds, as if it's missing frames. I've had the same result using kdenlive, ffmpeg, and mencoder (and attempting multiple formats/bitrates in each). I even used DeVeDe to generate a preview of an unmodified clip--same thing. As a test, I used ffmpeg to remove the sound from a clip, and then add it back in. Same thing! My understanding is it should result in an identical output file, but instead the output has perfect sound and horrible video.

The plan was to edit out some sections, improve the volume a bit, re-order them, and re-burn them to DVDs. Any ideas?

This is on Mint 13 x64.

Thanks,

---

### Post by andrew.46 on 2012-12-09
You will tend to lose a little quality each time you edit, despite the best intentions. Can you give a specific example of one such editing effort with FFmpeg, including command and full terminal output?

I would suggest also that you get a recent copy of FFmpeg up and running, not sure if this runs on Mint:

[http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)

My suspicion is that with FFmpeg you may have re-encoded with the defaults and this might explain the big drop in quality. Need a commandline + output to really tell though.

---

### Post by strafe_sawdoffe on 2012-12-09
Thanks for the assist. After hours of experimenting I "solved" it effectively but inelegantly: ffmpeg2theora. For some reason, once I got them all into ogv format, I can trim them, mess with the sound, etc and everything's ok.

It wasn't necessarily a decline in quality *per se* with ffmpeg: imagine watching a DVD and somebody keeps hitting pause/play every 3 seconds, but the sound keeps going. Really weird.

I can't reproduce it with other mpg files: only this massive batch that were transferred from VHS onto DVD-R, and who knows if the hardware I used conforms to DVD encoding standards? Oh well...

Resolved. Thanks again.

---

