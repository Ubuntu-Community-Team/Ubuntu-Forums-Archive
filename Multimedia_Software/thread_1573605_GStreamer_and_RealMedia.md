---
title: "GStreamer and RealMedia"
date: 2010-09-13
forum: Multimedia Software
---

### Post by snowsmash on 2010-09-13
I am running Ubuntu 10.04 with ubuntu-restricted-extras installed. I believe RealMedia (.rm) files used to play fine in Totem via GStreamer. However, admittedly after doing a sequence of package installs and removals on the computer in an effort to try to get something else to work, Totem now fails to play .rm files:

** Message: Error: GStreamer encountered a general stream error.
rmdemux.c(942): gst_rmdemux_loop (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstDecodeBin2:decodebin20/GstRMDemux:rmdemux0:
stream stopped, reason not-linked

I did an aptitude reinstall ubuntu-restricted-extras but that did not help. I also tried removing gstreamer0.10-plugins-ugly, which causes Totem to ask to search for a suitable plugin when attempting to play a .rm, but we just go back to the above error after successfully installing gstreamer0.10-plugins-ugly again.

I would appreciate if anyone has an idea on how to pursue this problem further.

---

### Post by myandylai on 2010-09-13
I am not too sure about your problem cause I am also new to Ubuntu. But you can sure try remove all gstreamer packages and use Medibuntu repository.

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

then,

sudo apt-get install non-free-codecs

or you can also install RealPlayer by downloading the packages from [http://www.real.com/realplayer/linux](http://www.real.com/realplayer/linux) if you just having problem with playback rm, rmvb files.

hope you can resolve you rm playback issue.

---

### Post by Yellow Pasque on 2010-09-13
Looks like a gstreamer error. I would try the latest stable gstreamer using: [https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

> But you can sure try remove all gstreamer packages and use Medibuntu repository.
Medibuntu doesn't have gstreamer packages, so doing that will probably try to remove a lot of vital packages. Not advised...

---

