---
title: "Studio upgrade, now Mplayer dumps"
date: 2007-12-24
forum: Multimedia Production
---

### Post by skyemoor on 2007-12-24
Made the upgrade to Ubuntu Studio, now mplayer exits when I play online videos.  Several small boxes show up then disappear and Firefox exits.

Here's the Ubuntu Studio link I've been using;
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

The following lines made me wonder, but I ran them anyway;

[INDENT]"Install the video codecs"

 sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-tools[/INDENT]

Was not able to install the Linux-rt.

Any thoughts?

---

### Post by Pocadotty on 2007-12-25
Try installing the generic kernel in Synaptic

I have had a fair amount of grief with the realtime kernel (Linux-rt) running non-studio type tasks and applications.

I got around this by using the generic kernel when I want to do non-studio type things, and boot into the realtime kernel when fast low-latency IO stuff becomes important.

Thanks all that comes to mind for me.

---

