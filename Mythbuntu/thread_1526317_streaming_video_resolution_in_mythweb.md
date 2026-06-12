---
title: "streaming video resolution in mythweb"
date: 2010-07-07
forum: Mythbuntu
---

### Post by mdaitc on 2010-07-07
Hi,

anyone know how to (easily) change the resolution at which the video is streamed via mythweb using the flowplayer? the default (my current) seems to be 320x260 and lower audio quality. it would be nice to get this at higher quality so i dont have to wait for a download to complete before watching the higher quality.

FWIW, the pop-out video player doesn't seem to function  mythweb                         0.24.0~trunk25265-0ubuntu0~mythbuntu1 

thanks,

---

### Post by nickrout on 2010-07-07
> **mdaitc said:**
> Hi,

anyone know how to (easily) change the resolution at which the video is streamed via mythweb using the flowplayer? the default (my current) seems to be 320x260 and lower audio quality. it would be nice to get this at higher quality so i dont have to wait for a download to complete before watching the higher quality.

The code appears to be in /usr/share/mythtv/mythweb/modules/stream/stream_flv.pl
> 
FWIW, the pop-out video player doesn't seem to function  mythweb                         0.24.0~trunk25265-0ubuntu0~mythbuntu1 

thanks,

things break in trunk, thats why it is not a release :)

---

### Post by mdaitc on 2010-07-08
in case someone else wants the answer:

actually, there's some convenient settings in the mysql database (settings table) - look for WebFLV_w (there's a few other _ entries too) to adjust the video properties.

---

### Post by managementboy on 2010-07-09
even easier: in mythweb go to Settings, then "MythWeb", then Video Playback.

---

