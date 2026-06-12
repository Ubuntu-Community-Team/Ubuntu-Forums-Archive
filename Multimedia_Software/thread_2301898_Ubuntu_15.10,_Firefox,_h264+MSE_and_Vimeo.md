---
title: "Ubuntu 15.10, Firefox, h264+MSE and Vimeo"
date: 2015-11-06
forum: Multimedia Software
---

### Post by monkeybrain20122 on 2015-11-06
Not sure where to post this. Just noticed that for Firefox 42 and Ubuntu 15.10, if I set media.fragmented-mp4-exposed = true in about:config, html5 player in vimeo doesn't load. But if set to false (default) then vimeo works but at [https://www.youtube.com/html5](https://www.youtube.com/html5) the box MSE & H264 is unchecked (though I haven't encountered any problem playing youtube videos) 

The same version of FF with media.fragmented-mp4-exposed = true works perfectly with vimeo in Ubuntu 15.04. Seems like a problem with some Ubuntu 15.10 media packages.

---

### Post by mc4man on 2015-11-06
That seems to be the case. (have 14.04.3 & 16.04 that shows this.
The main diff between 14.04/15.04 & 15.10/16.04 is that the gstreamer1.0-libav plugin in 15.10/16.04 uses FFmpeg whereas older use Libav.

---

