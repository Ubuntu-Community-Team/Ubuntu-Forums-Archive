---
title: "VLC blank video begining of playback"
date: 2008-12-23
forum: Multimedia Software
---

### Post by potam on 2008-12-23
Hello guys,

I have problem with vlc 0.9.4 under Intrepid. Problem never existed in earlier versions.

So when I start playing a file (vlc is not opened yet), opens the vlc window, I can hear the sound, but no picture. Then after 2 seconds scratchy picture, and after 3-4 seconds a perfect picture.

If I rewind to the begining the picture is perfect, if I open the video vlc started, the picture is perfect too.

This is a vlc problem, disabling desktop effects, selecting different video output did not solve it. The problem is only with AVI files (not new one, played perfectly in earlier vlc versions)

I think the base of the problem is:
There is a keyframe at the begining of the AVI, vlc miss this keyframe (but why?) that's why there is no picture. And also miss some beta frames. When vlc reaches the next keyframe, the picture is perfect.

But why miss the first keyframe?

---

