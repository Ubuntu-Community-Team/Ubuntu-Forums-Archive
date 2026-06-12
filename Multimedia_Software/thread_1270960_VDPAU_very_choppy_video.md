---
title: "VDPAU very choppy video"
date: 2009-09-20
forum: Multimedia Software
---

### Post by frunns on 2009-09-20
Ok, as the title says, I'm trying to use VDPAU but the video is very, very choppy, basically just repeats the same 0.5 seconds 20 times, then jumps a few seconds to do the same thing again.

This is the error message I get in mplayer (using smplayer).

```
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
```

Anyone knows what this means?

Edit: Found some new errors on another video.
```

Starting playback...
[VD_FFMPEG] XVMC-accelerated MPEG-2.
VDec: vo config request - 1920 x 824 (preferred colorspace: H.264 VDPAU acceleration)
VDec: using H.264 VDPAU acceleration as output csp (no 0)
Movie-Aspect is 2.33:1 - prescaling to correct movie aspect.
ID_VIDEO_ASPECT=2.3301
VO: [vdpau] 1920x824 => 1920x824 H.264 VDPAU acceleration 
[vdpau] Failed creating VDPAU decoder: The display was pre-empted, or a fatal error occurred.
FATAL: Cannot initialize video driver.
[h264_vdpau @ 0xd72aa0]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0xd72aa0]decode_slice_header error
[h264_vdpau @ 0xd72aa0]no frame!
Error while decoding frame!
[h264_vdpau @ 0xd72aa0]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0xd72aa0]decode_slice_header error
[h264_vdpau @ 0xd72aa0]no frame!
Error while decoding frame!

FATAL: Could not initialize video filters (-vf) or video output (-vo).


Exiting... (End of file)
ID_EXIT=EOF

```

---

