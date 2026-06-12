---
title: "Jaunty / MTP device annoying behavior"
date: 2009-05-11
forum: Multimedia Software
---

### Post by brentn on 2009-05-11
Since upgrading to Jaunty, every time I plug my **MTP player** in, Ubuntu prompts me to mount/open/cancel.  

1) I would like to **cancel** and have it **remember my choice**, but it does not appear that it can do so.
2) The **sync icon** appears on my device, causing it to stop playing and forget what it was playing - **before I make any choice at all!!**
3) When I cancel this dialog, it continues to appear every minute or two - obscuring whatever I am working on.

**Can I turn off this autodetect feature** and still maintain the ability to manually mount the device for synching when necessary?

---

### Post by dsfitzpat on 2009-07-04
I have the same problem, and no idea how to turn it off.  In my case it's even worse - my player (Philips gogear) doesn't mount properly, because it gets detected as the wrong model.  What really makes it annoying is that it takes something like ten minutes from when I plug it in before it shows up in the places menu - and in the meantime it's inaccessible to mtp-tools, gnomad2, or any other mtp device manager.

---

### Post by gnimsh on 2009-07-11
This worked for me:

This is just a work around. I changed /usr/share/gvfs/remote-volume-monitors/ gphoto2.monitor to allow the device to be mounted.

[RemoteVolumeMonitor]
Name=GProxyVolumeMonitorGPhoto2
DBusName=org.gtk.Private.GPhoto2VolumeMonitor
#IsNative=false
IsNative=true

Taken from [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/330383](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/330383)

Remember to restart after you do this.

---

