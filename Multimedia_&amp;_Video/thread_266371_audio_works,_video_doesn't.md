---
title: "audio works, video doesn't"
date: 2006-09-27
forum: Multimedia &amp; Video
---

### Post by irsic on 2006-09-27
I've got a little problem with my movie player. (I am not sure if this is the place to ask questions about it?!). I am using Totem Movie Player, that comes with ubuntu dapper when you install it. It is totem-gstreamer as default. 
When I play a AVI movie I get sound ok, but no movie itself, no video.
I've got the gst-plugins-good installed, where it says the avi plugin is, but   still no difference.
Can anybody help, please?

---

### Post by Kateikyoushi on 2006-09-27
I think you need more codecs.

[Try this]("https://help.ubuntu.com/community/RestrictedFormats").

---

### Post by irsic on 2006-09-27
tnx. I think those did it:
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse w32codecs

along with gxine

---

