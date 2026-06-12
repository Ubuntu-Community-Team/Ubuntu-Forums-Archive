---
title: "Banshee: GStreamer-CRITICAL"
date: 2013-01-21
forum: Multimedia Software
---

### Post by Argentino on 2013-01-21
Hey All, 

I am having a problem with Banshee. Every time I start it, then click on a song, it crashes. This is the error the term gives:

```


pablo@Argenox ~> banshee
[Info  23:10:22.762] Running Banshee 2.6.0: [Ubuntu 12.10 (linux-gnu, x86_64) @ 2012-12-12 06:24:28 UTC]
[Info  23:10:28.026] Updating web proxy from GConf
[Warn  23:10:29.004] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[Warn  23:10:29.005] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.
[Warn  23:10:29.154] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[Warn  23:10:29.154] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.
[Info  23:10:29.156] All services are started 5.143225
[Info  23:10:30.960] AmazonMP3 store redirect URL: https://one.ubuntu.com/music/store/amz/

** (Banshee:8990): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Lubuntu-default/gtk-2.0/images/null.png,
borders don't fit within the image

** (Banshee:8990): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Lubuntu-default/gtk-2.0/images/scrollbar_vertical.png,
borders don't fit within the image
[Info  23:10:31.831] nereid Client Started
[Info  23:10:33.439] GStreamer version 0.10.36.0, gapless: True, replaygain: True

(Banshee:8990): GStreamer-CRITICAL **: gst_element_query: assertion `GST_IS_ELEMENT (element)' failed
(!) [ 9019:    0.000] --> Caught signal 24(!) [ 9020:    0.800] --> Caught signal 24(!) [ 9014:    0.800] --> Caught signal 24 (unknown origin) <--
(!) [ 9018:    0.800] --> Caught signal 24 (unknown origin) <--
(!) [ 9021:    0.800] --> Caught signal 24fish: Job 1, “banshee” terminated by signal SIGABRT (Abort)



```

I have installed ubuntu-restricted-extras, uninstalled and reinstalled banshee a few times now.

Gstreamer seems fine as all audio players I have installed work fine, video and audio.

Any ideas guys?

Ta in advanced :)

---

### Post by blacksheepwall on 2013-03-25
I had the same problem and the exact same error.  I didn't have the following packages:

gir1.2-gstreamer-0.10
gir1.2-gst-plugins-base-0.10

I installed rhythmbox through the Lubuntu Software Center, and it requested and installed them.  Hope this helps

---

### Post by swaan on 2013-03-28
I have the same problem on 12.10/64 with banshee 2.6.0

Those rhythmbox related packages didn't help. :/

Filed bug: [https://bugzilla.gnome.org/show_bug.cgi?id=696786](https://bugzilla.gnome.org/show_bug.cgi?id=696786)

---

### Post by robertmf on 2013-03-28
[COLOR="#800000"]12.04/32b/Precise 

No audio output from banshee nor rhythmbox.  

:confused: Both programs open, but choose a music file to play and the progress bar moves without any audio  :confused:
[/COLOR]

---

### Post by swaan on 2013-03-30
Is your problem related to the GStreamer-CRITICAL error?
Pulseaudio can mess up the Lubuntu audio system ALSA so I suggest you purge it. Assuming you checked volume and devie settings already and that you didn't install pulseaudio on purpose.


I can now confirm that installing Rhythmbox solves the problem described in the first post.
You can purge rhythmbox and autoremove the rest and its still working.

A workaround alright :D

---

### Post by robertmf on 2013-03-30
> **robertmf said:**
> [COLOR="#800000"]12.04/32b/Precise 

No audio output from banshee nor rhythmbox.  

:confused: Both programs open, but choose a music file to play and the progress bar moves without any audio  :confused:
[/COLOR]


**[COLOR="#800000"]SOLVED :)[/COLOR]**
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

---

