---
title: "FLV to MPG via ffmpeg; no sound in DVD"
date: 2006-10-09
forum: Multimedia &amp; Video
---

### Post by DoomedTX on 2006-10-09
As the title suggests, I've downloaded a Google video and converted via the following command line:

```
ffmpeg -i video.flv -target ntsc-dvd video.mpg
```

The resultant file plays fine in MPlayer. On Windows, WinAMP plays only the video and Vegas Video says it's a video-only file.

Also I burned the movie to a DVD and it plays without sound on both stand-alone and computer-based DVD players (except for VLC but that's not an option for my stand-alone).

When I check the file's properties it shows AC-3 audio and MPlayer reports that it uses the a52 codec. I thought AC-3 should be playable on other systems and stand-alone players.

Any ideas on what I need to do to make this video playable on a stand-alone? That's my ultimate goal; the Windows info was just to help troubleshoot.

Thanks.

---

