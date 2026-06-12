---
title: "totem 2.19.90 wont configure on ubuntu 6.06.1 LTS inspite of installing Gstreamer"
date: 2007-08-21
forum: Multimedia &amp; Video
---

### Post by matrix_neo on 2007-08-21
Hi all,

I installed libgstreamer0.10-dev on my ubuntu 6.06.1 LTS. 
Now I am trying to install totem 2.19.90 from source. While running configure script it gives me this errors "***checking for backend libraries... configure: error: you need the GStreamer or the xine-lib development packages installed***"

any help on this is highly appreciated.

Neo

---

### Post by FuturePilot on 2007-08-21
```
sudo apt-get install libxine-dev
```
Then try again.

---

### Post by matrix_neo on 2007-08-21
hi Future Pilot,

Thank you for your reply, but I m supposed to use _only_ GStreamer and _not_ xine for development. Can you or anyone plz tell me how to get this thing working with GStreamer


-Neo

---

### Post by sharp11 on 2008-05-03
I ran into the same problem trying to build Totem on Gutsy. The short answer is you probably need to install **libgconf2-dev**. 

Longer answer: *configure* relies on* pkg-config *to look up the compiler flags that it will use for gstreamer. However, if you look at the actual exec statement that configure uses when it runs pkg-config, at the end of the line is "gconf-2.0". For some reason, it wants to look up info about gconf2 at the same time. (gconf2 is the Gnome config system for storing application preferences; maybe gconf gets compiled into gstreamer?).

---

