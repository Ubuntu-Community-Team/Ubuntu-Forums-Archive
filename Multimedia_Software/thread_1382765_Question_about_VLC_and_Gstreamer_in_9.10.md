---
title: "Question about VLC and Gstreamer in 9.10"
date: 2010-01-16
forum: Multimedia Software
---

### Post by koerber on 2010-01-16
So, as you all know Ubuntu 9.10 comes with Totem installed by default. Although totem was working fine and giving me no problems I decided to switch to VLC. As far as I can tell, Totem uses the Gstreamer back end to play its codecs. After removing totem-gstreamer, I'm left with a lot of non totem related gstreamer packages. Are those other gstreamer packages required, or can I remove them? Are there anything I need to do to get firefox and chromium to be "aware" of vlc?

Thanks much.

---

### Post by fancypiper on 2010-01-16
I think you can remove them. **sudo apt-get autoremove** should take care of removing them, but read the list carefully before you agree to remove.

I think you are looking for **mozilla-plugin-vlc**. That should do for VLC what your totem plugin did.

---

