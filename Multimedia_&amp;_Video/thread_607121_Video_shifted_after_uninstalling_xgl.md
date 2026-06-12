---
title: "Video shifted after uninstalling xgl"
date: 2007-11-08
forum: Multimedia &amp; Video
---

### Post by dungodung on 2007-11-08
Now, this looks like a weird problem. But please bear with me :)

OK, So I've installed dapper, updated to edgy, then to feisty (all this back when they were current) and recently to gutsy. And during edgy, I enabled xgl and compiz/beryl. Now, I have ATI Radeon and it is beyond me why the desktop effects didn't work throughout feisty. Anyway, after installing gutsy, effects started working again, but they were buggy, so I decided to remove compiz-fusion. However, xgl stayed on and kept slowing down my system, even though I didn't use it (I hate some bits in xgl, like alt+shift bug and voluntary screen turn off). So I decided to uninstall it altogether and I did that a few days ago. But a problem came about.

I've long had no problems with video playback. However, after uninstalling beryl, xserver-xgl and related libs, my video stopped functioning properly. Namely, anywhere I play the video (mplayer, totem, vlc), it "sparkles" a bit, it's shifted downwards and generally, the playback of video has become useless. It's as if a codec is broken or missing, but all the video files (in various formats) share this weird property all of a sudden. The only way I could get normal playback was by running
```
gmplayer -zoom -fs /path/to/video.file
```
because running normal mplayer (by doubleclick/shortcut) doesn't solve the problem. I've attached the screenshot.

Now, I have got to be missing something, so I'm quite clueless as to what is happening and why my gutsy is experiencing this. It can't be that uninstalling xgl has caused this, can it?

Any help would be appreciated. Thanks

---

### Post by dungodung on 2007-12-03
Bump.

---

