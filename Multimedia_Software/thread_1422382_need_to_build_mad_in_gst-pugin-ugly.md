---
title: "need to build mad in gst-pugin-ugly"
date: 2010-03-05
forum: Multimedia Software
---

### Post by co.sam on 2010-03-05
Hi friends,
I want to install "mad"(gstreamer mm3 plugin), it comes in gst-plugin-ugly but when i do ./configure it show mad in list of plugins that will not be build I also intalled libmad.

can u please tell me how can i build mad in gst-plugin-ugly

---

### Post by Yellow Pasque on 2010-03-05
The Ubuntu version has that plugin enabled. Just:
```
sudo apt-get install gstreamer0.10-plugins-ugly
```

For future reference, you need the -dev package when building things from source (libmad0-dev in this instance).

---

