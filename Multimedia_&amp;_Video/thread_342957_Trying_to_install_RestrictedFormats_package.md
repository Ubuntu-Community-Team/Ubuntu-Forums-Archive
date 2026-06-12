---
title: "Trying to install RestrictedFormats package"
date: 2007-01-20
forum: Multimedia &amp; Video
---

### Post by allenwal on 2007-01-20
Hi,

Newbie question:

Using version 6.06

I've been trying to add the RestrictedFormats package that allows mp3 files etc. to be played, using the method described in Community Docs on the RestrictedFormats page. This command is upposed to be pasted into the terminal and run:

sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui

But I keep getting the following error message in response:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?

I don't know what this means or how to fix it. Would someone please explain it to me?

Thanks.

---

### Post by ahaslam on 2007-01-20
Have you got Synaptic (or another package manager) open?

;)

---

### Post by meng on 2007-01-20
This message will come up if you are running a separate instance of Add/Remove, Synaptic, apt-get or aptitude at the same time.

---

