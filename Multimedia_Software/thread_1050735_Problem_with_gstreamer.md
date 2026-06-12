---
title: "Problem with gstreamer"
date: 2009-01-26
forum: Multimedia Software
---

### Post by underdog512 on 2009-01-26
Ok so I am taking an online class and going to happy as can be saying to myself "hmm I am really using Ubuntu to take an online course". Anyways this is the second class I have taken with the school using Ubuntu 8.10 and everything has worked fine....until now.

There are some recorded lectures that one has to stream live from the website.  They use some kind of Real Media stream. Totem has been handling them fine up until yesterday. When I click on the link and download the stream, totem opens like normal but I suddenly get an error message "internal data flow error" that is pretty much the extent of the error. 

So instead of just opening the stream directly from the website, I download it to my desktop and get a different error when I open it.   "Gstreamer encountered a general stream error"

I have tried every multimedia app on my computer including helix (since it is a real media file) and vlc, I am getting similar errors on each.

So I load up my trusty virtual box with WinXP installed download the real player and sure enough it works perfectly. So there is nothing wrong on the schools end.

By the way all other media files on my computer are playing just fine.

Sorry for the lengthy post but I wanted to provide as much info as possible.

---

### Post by underdog512 on 2009-01-26
bump

---

### Post by gettinoriginal on 2009-01-26
Sorry, misread your original post, have you tried reinstalling gstreamer ?? somehow it could have become corrupted.

---

### Post by underdog512 on 2009-01-26
yea that was the first thing i did.

---

### Post by Linuxdork on 2009-01-26
Have you installed any new media players such as songbird?

**[edit]** Also, did you get the gstreamer error when running totem from the console?  If so, was there anymore output?  If not, please try to run it from the console and post any error output.  Thanks.

---

### Post by dmizer on 2009-01-26
Error reporting is more verbose at the command line.

Try opening a terminal, and type:
```
totem
```
Then use "File" > "Open" to browse for the video and try to play it. Then, post the terminal output here.

---

### Post by underdog512 on 2009-01-29
this is the output from the terminal as requested.

```
** (totem:31066): DEBUG: Init of Python module
** (totem:31066): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:31066): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:31066): DEBUG: Creating Python plugin instance
** (totem:31066): DEBUG: Init of Python module
** (totem:31066): DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
** (totem:31066): DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
** (totem:31066): DEBUG: Creating Python plugin instance
** Message: Error: GStreamer encountered a general stream error.
rmdemux.c(943): gst_rmdemux_loop (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstRMDemux:rmdemux0:
stream stopped, reason not-negotiated

```

---

### Post by Linuxdork on 2009-01-29
Is there any way I can access these streams for troubleshooting?

---

### Post by dmizer on 2009-01-29
According to this bug report: [https://bugs.launchpad.net/ubuntu/+source/gstreamer/+bug/155894](https://bugs.launchpad.net/ubuntu/+source/gstreamer/+bug/155894)

You'll need to install the w32codecs package.

---

### Post by underdog512 on 2009-01-30
I already have w32codecs installed.

---

### Post by underdog512 on 2009-01-30
> **Linuxdork said:**
> Is there any way I can access these streams for troubleshooting?

Its my online class so I do not believe so.

---

### Post by dmizer on 2009-01-30
You said you could download them to your computer. Can you send one to me in PM?

---

### Post by underdog512 on 2009-02-03
> **dmizer said:**
> You said you could download them to your computer. Can you send one to me in PM?


I don't see how to attach a file to a PM.

---

