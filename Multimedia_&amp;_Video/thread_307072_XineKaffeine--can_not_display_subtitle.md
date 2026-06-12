---
title: "Xine/Kaffeine--can not display subtitle"
date: 2006-11-26
forum: Multimedia &amp; Video
---

### Post by Phulerock on 2006-11-26
I'm using Xine and kaffeine + w32codecs in 6.10 Edgy (install by Synaptic)

I try to play file.wmv with its own subtitle .smi but the subtitile can not display in screen, only the black bar on the top and the bottom (both xine and kaffeine).

All another subtitle format are the same.
Please show me how to troubleshoot this
Regards,

---

### Post by Linuxfan2 on 2007-01-20
Go to Kaffeine settings and make this:
Settings->xineEngineParameters->video->ExpertSettings->2D_Tex

Or in xine (conf file) make this:
video_out_opengl: setup of '2D_Tex_Fragprog'
change to this:
video_out_opengl: setup of '2D_Tex'

---

