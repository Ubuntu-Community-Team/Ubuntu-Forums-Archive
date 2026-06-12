---
title: "mp3 codec bitrate always shown as 48 kbs now"
date: 2011-03-05
forum: Multimedia Software
---

### Post by StephenDavison on 2011-03-05
This may be a minor irritation, but I'm puzzled by it nonetheless.  I'm ripping my CDs to MP3 using Sound Juicer with the lamemp3enc plugin and following gstreamer pipeline.
[CENTER]audio/x-raw-int,rate=44100,channels=2 ! lamemp3enc name=enc target=0 quality=0 ! xingmux ! id3v2mux[/CENTER]

All was great a couple days ago, but suddenly the files' audio properties show 48 kbps bitrate when it should be well over 200.  I even changed the pipeline to use "target=1 bitrate=256" with the same result.  The files are being encoded as expected and that is reflected in the file size and the Statistics view in VLC.

I have two computers running Ubuntu 10.10.  One has all the latest updates, but the other has not been updated in several days.  This problem is happening on the former, but not the latter.  gst-inspect lamemp3enc shows both computers have the same version of the encoder.

Can somebody confirm this behavior?  I thought I'd put it out to the forum here before submitting a bug in launchpad.

Thank you for your time and effort.

-Stephen

---

### Post by Yellow Pasque on 2011-03-06
I used to to experience something similar in rhythmbox because it didn't know what to mark VBR mp3's as. I suggest trying the latest stable version of gstreamer before filing a bug, because it may already be fixed upstream: [https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

---

### Post by johntaylor1887 on 2011-03-06
Boot up choosing a different kernel. There seems to be a rash of problems with recent updates.

---

### Post by StephenDavison on 2011-03-06
Booting the last two kernels (.25 and .23) didn't fix it.  Must be something else that changed since last Wed.  I'll keep working on it.

---

### Post by vanadium on 2011-03-06
Do the files also *sound* like 48 bit? If not, it might not be a gstreamer problem but an issue with the properties dialog. The utility encspot, which currently can be installed straight from the Ubuntu Software Centre, will show you the truth about your mp3 file.

---

### Post by StephenDavison on 2011-03-06
Sorry, thought I was clear about that in the original post.  The encoding is fine, it's just the wrong bitrate showing whenever I look at the audio properties: like gstreamer is tagging the file as 48 kb/s when it's actually much higher.

---

