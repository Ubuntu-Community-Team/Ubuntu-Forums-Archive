---
title: "Sound Source Hangs After Few Minutes"
date: 2011-11-13
forum: Multimedia Software
---

### Post by ttoolin on 2011-11-13
I am having problems keeping sound sources (Movie Player, Rhythmbox, Internet Audio, etc) running more than a few seconds or a few minutes.  With Pulseaudio running, it most often hangs with a:

pa_stream_writable size failed

error, so I disabled pulseaudio from my startup programs, rebooted, and got a few:

Connection Error

errors, and then I even got a pa_stream_writable error with pulseaudio having never been started.

I am running a PIII 800MHZ 1.5Gb with a C-Media CMI8738 PCI soumdcard, and no onboard audio available.  I'm running Ubuntu 10.04.

Additional information:  This same sound card was previously installed in another older machine, and when it was giving me problems, I reverted to the onboard audio that was on that system.  I do not have that option, now.

Also, Rhythmbox has tended to stop loading after a few days, but Movie Player and other sound-using programs run okay.  What I did, the last time, is uninstalled some of the multimedia programs that I don't use often, and it started working again.  I've reloaded some of those programs I don't often use, and I will uninstall some or all of them, again, and see if I can get Rhythmbox back.

Regardless of the multimedia program I'm using, I only use one at a time.  I don't know why Rhythmbox would fail, just because I have other programs available to use.

Thanks.

---

### Post by Rodney9 on 2011-11-13
Have a look at this site - 

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

and this one, more up todate, but still a work in progress, however very good - 

[https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit?pli=1](https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit?pli=1)

Rodney

---

### Post by MoreOrLess on 2011-11-13
If you're going to stop pulseaudio or prevent it from running, then you should change your output to not use it.
```
sudo apt-get install gstreamer0.10-alsa
gstreamer-properties
```
Select alsa sink and see if movie player works.

---

### Post by ttoolin on 2011-11-13
Thank you, both for the advice.  I tried both of your suggestions, without luck.  The best I can figure is that the soundcard is faulty or the driver support is not quite 100%  I did see some less than positive discussion of the CMI8738 audio chip.

I had a backup soundcard, which I've installed, for now.  It could be better, but it is compatible with the hardware and software.  I'll buy a new one in the next while.

Thanks again for the help!!!!!

terry

---

