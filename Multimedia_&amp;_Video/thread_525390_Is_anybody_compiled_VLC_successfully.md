---
title: "Is anybody compiled VLC successfully?"
date: 2007-08-14
forum: Multimedia &amp; Video
---

### Post by feistybee on 2007-08-14
Hi,

Is anybody compiled VLC successfully?

When I tried to compile, I faced the following error,

conftest.c:177:28: error: ffmpeg/avcodec.h: No such file or directory

Please suggest me, how I can do offline VLC installation. Not using apt-get in online.

Regards,
bee

---

### Post by deadgobby on 2007-08-14
Yes, it is going to this link and DL it.
[http://packages.debian.org/stable/graphics/vlc](http://packages.debian.org/stable/graphics/vlc)
 If you have all the depends that the package ask for you should be good to go.

Gobby

---

### Post by Chappy7777 on 2007-08-17
I just copied this off of VLC's Ubuntu page. Seems straight forward enough. I guess I am assuming VLC knows how to install their product. That doesn't mean it will work in the real world.
------------------------------------
Graphical way

Open Synaptic (System -> Administration -> Synaptic Package Manager). In Settings -> Repositories, make sure you have a "universe" repository activated.

Search for vlc and install it. You should also install vlc-plugin-esd, mozilla-plugin-vlc (and libdvdcss2).
--------------------------------------

I will be trying it later, so I really hope they're right. Let me know if this helped you, ok? maybe you already tried this? Anyhow.....

---

### Post by kelvin spratt on 2007-08-17
vlc installs from synaptic with no problems,

---

