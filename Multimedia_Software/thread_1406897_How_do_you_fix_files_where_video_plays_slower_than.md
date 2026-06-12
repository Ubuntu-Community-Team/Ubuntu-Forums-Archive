---
title: "How do you fix files where video plays slower than audio"
date: 2010-02-14
forum: Multimedia Software
---

### Post by Replicon on 2010-02-14
Sorry if this is a common topic, but all the "video out of sync" google results I'm finding are for cases where the video is just statically "2 seconds behind the audio" whereas this seems to be a more complicated issue.

I've got a few video files where the audio and video start out in sync, but then the video slowly gets more and more behind. But it seems like the video "knows" this and attempts to self-correct:

In MPlayer, it doesn't self-correct, but if I seek ahead, it resets the sync... so it KNOWS what parts of the stream need to be together.

In VLC, it attempts to correct itself by interrupting the audio, so while the video plays out fine, the audio has a little interruption in it a couple of times a second.

It looks like the file can still tell you which frame corresponds to where on the audio, so I imagine someone would have written some app I can run like "resync borked_video.avi -o fixed_video.avi" or something. :) I mean, shouldn't it be a matter of slowing down the video frame rate just enough that the lenths of the streams are just about equal?



Thanks!

---

