---
title: "RhythmBox Iphone sync Audible files"
date: 2010-05-17
forum: Multimedia Software
---

### Post by lippsmasta on 2010-05-17
I recently found the [Ubuntu iPhone Page ]("https://help.ubuntu.com/community/PortableDevices/iPhone") and was excited to discover that I am now able to sync music my iphone without depending on itunes. The only remaining dependency I have is the syncing of Audible (.aax) files so that I can listen to audio books. When I try to drag the .aax from nautilus to the iphone in RhythmBox it silently ignores the action.

 I also am unable to import the .aax file into the RhythmBox Library which doesn't surprise me on account of the DRM. When i try to import it tries to find an acceptable plugin and i get a message about 'audio/x-gst-fourcc-aavd decoder' plugin not able to be found. heres terminal output from import attempt.

(<unknown>:7387): GLib-WARNING **: g_set_prgname() called multiple times
Rhythmbox-Message: Missing plugin: gstreamer|0.10|<unknown>|audio/x-gst-fourcc-aavd decoder|decoder-audio/x-gst-fourcc-aavd
/usr/lib/python2.6/dist-packages/GnomeCodecInstall/MainWindow.py:300: DeprecationWarning: Accessed deprecated property Package.candidateRecord, please see the Version class for alternatives.
  record = pkg.candidateRecord
/usr/lib/python2.6/dist-packages/GnomeCodecInstall/MainWindow.py:305: DeprecationWarning: Accessed deprecated property Package.candidateRecord, please see the Version class for alternatives.
  major, minor = pkg.candidateRecord["Gstreamer-Version"].split(".")

If there are other applications that this might work with i am willing to try those as well. I have also attempted to use gtkpod with similar results. 

Thanks in advance.

---

### Post by lippsmasta on 2010-05-30
Is this posted in the wrong form or something? I would love to hear from someone else to see how they deal with Audible content in linux.

---

### Post by jjjjeremy on 2010-09-03
Did you ever get an answer? I'm trying to get an Audible.com download onto my ipod touch right now.

---

### Post by lippsmasta on 2011-01-25
Just close the loop on this. 

Although i was never able to really get .aa files transfered from ubuntu I was able to avoid this problem when Audible came out with their App for both android and ios. 

I am now able to download audio books directly to my phone from the app itself.

---

