---
title: "Problem with FFMPEG and AutoPlay"
date: 2010-06-03
forum: Multimedia Software
---

### Post by vesolovski on 2010-06-03
Hi all!
I have a following problem. After converting and encoding avi movie to mp4 with ffmpeg (-vcodec is libx264) and uploading movie to server I am trying to watch this using flowplayer. I can do it, but only after the WHOLE movie gets buffered.

I would like to watch this instantly, not being forced to wait until it all buffers. My FlowPlayer flashvars are:

config={autoPlay: true,loop: true,autoRewind: true, startingBufferLength: 5, bufferLength: 5, allowScriptAccess: sameDomain, initialScale: 'scale',useNativeFullScreen: true, showMenu:false}

On the other hand after converting and encoding avi movie to mp4 with Adobe Media Encoder CS4 I can watch movie as expected.

Can you please help me? I suppose it is all about proper ffmpeg settings, which I do not know.. yet :/

Thank a lot.
Regards!

---

