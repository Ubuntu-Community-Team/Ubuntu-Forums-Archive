---
title: "Gstreamer: how do I register my &quot;own&quot; plugins?"
date: 2006-06-11
forum: Multimedia &amp; Video
---

### Post by Patsoe on 2006-06-11
Hi all,

I'm having this problem with some gst-plugins I compiled and installed (they are from farsight). By convention, I keep them under /usr/local/lib/..., whereas the other gstreamer plugins are from the main Ubuntu repository, so they are in /usr/lib/...

Now, if I run "gst-inspect-0.10", the new plugins aren't listed (I even tried rebooting the machine for that :)). How can I tell gstreamer to update its registers? Thanks!

---

### Post by Patsoe on 2006-06-11
I found that I can set an environment variable GST_PLUGIN_PATH to define alternate places for gstreamer to look for plugins. My plugins are loaded now, yay!! :)

Sad bit: if I close the terminal on which I define it, they get removed again. I'm still looking where to put the environment variable... I wouldn't want to make it a system-wide, global thing, or would I?

---

