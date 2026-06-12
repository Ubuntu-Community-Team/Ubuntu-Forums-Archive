---
title: "GStreamer didn't install vaapih264enc"
date: 2016-11-08
forum: Multimedia Software
---

### Post by rickblacker on 2016-11-08
Hi all. I'm trying to create an app with GStreamer. One of the plugins I need is the [FONT="Calibri"][COLOR=#000000]vaapih264enc[/COLOR][/FONT], it is supposed to be in the gstreamer-vaapi I was told.  However, it simply does not exist on my computer.  Does anyone know who to get this properly installed on my machine?  I've searched for solutions on the web but not finding what I need.

Any help will be greatly appreciated!

Thanks
Rick

---

### Post by mc4man on 2016-11-08
Sure it did,  though the odds of it producing anything useful are probably slim.
 ```
gst-inspect-1.0 vaapi
```

---

### Post by rickblacker on 2016-11-08
HI, I ran gst-inspect-1.0 vappi
I get back : No such elemetn or plugin 'vappi'

I even ran this just now.

sudo apt-get install --reinstall gstreamer1.0-alsa gstreamer1.0-libav gstreamer1.0-plugins-bad gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-plugins-ugly gstreamer1.0-pulseaudio libgstreamer-plugins-bad1.0-0 libgstreamer-plugins-base1.0-0 libgstreamer-plugins-good1.0-0 libgstreamer1.0-0

Then re-ran both 
* gst-inspect-1.0 vaapih264enc
* gst-inspect-1.0 vaapi

I'm still getting the same results, No such elements or plugin

---

### Post by mc4man on 2016-11-08
Based on your title query would've  assumed it's installed but - 
```
sudo apt-get install gstreamer1.0-vaapi
```
results here on 16.04 - 
```
$ gst-inspect-1.0 vaapi
Plugin Details:
  Name                     vaapi
  Description              VA-API based elements
  Filename                 /usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstvaapi.so
  Version                  1.8.2
  License                  LGPL
  Source module            gstreamer-vaapi
  Source release date      2016-06-09
  Binary package           gstreamer-vaapi
  Origin URL               http://bugzilla.gnome.org/enter_bug.cgi?product=GStreamer

  vaapijpegdec: VA-API JPEG decoder
  vaapidecode: VA-API decoder
  vaapipostproc: VA-API video postprocessing
  vaapisink: VA-API sink
  vaapih264enc: VA-API H.264 encoder
  vaapimpeg2enc: VA-API MPEG-2 encoder
  vaapijpegenc: VA-API JPEG encoder
  vaapivp8enc: VA-API VP8 encoder
  vaapih265enc: VA-API H.265 encoder
  vaapidecodebin: VA-API Decode Bin

  10 features:
  +-- 10 elements
```

---

### Post by rickblacker on 2016-11-08
rick@rws:~$ sudo apt-get install gstreamer1.0-vappi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gstreamer1.0-vappi
E: Couldn't find any package by glob 'gstreamer1.0-vappi'
E: Couldn't find any package by regex 'gstreamer1.0-vappi'
rick@rws:~$ 

Didn't look like it was found, but just for completeness, I decided to double check to see if it was installed.

rick@rws:~$ gst-inspect-1.0 vappi
No such element or plugin 'vappi'
rick@rws:~$ 



Thoughts?

---

### Post by &amp;KyT$0P# on 2016-11-08
Typo? -
> **mc4man said:**
> ```
sudo apt-get install gstreamer1.0-va**[COLOR="#FF0000"]a[/COLOR]**pi
```

> **rickblacker said:**
> rick@rws:~$ sudo apt-get install gstreamer1.0-va**[COLOR="#FF0000"]p[/COLOR]**pi

---

### Post by rickblacker on 2016-11-08
[COLOR=#000000]halogen2 [/COLOR][COLOR=#000000]mc4man

YOU TWO ARE MY NEW BEST FRIENDS!!!!

Thank you so much.  It was a typo on my part!!!



[/COLOR]

---

### Post by mc4man on 2016-11-08
There is some minimal docu i(html) in this package
gstreamer1.0-vaapi-doc
(- /usr/share/doc/gstreamer1.0-vaapi/gstreamer-vaapi-plugins-1.0/gstreamer-vaapi-plugins-vaapih264enc.html

---

