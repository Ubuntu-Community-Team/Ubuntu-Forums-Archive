---
title: "NVIDIA Drivers"
date: 2006-11-07
forum: Multimedia &amp; Video
---

### Post by JNowka on 2006-11-07
Tonight I check to see if any updates are avalible and I see that the nvidia drivers need to be updated.  So I hit Install updates, go eat dinner, and come back.  I reboot the computer for the hell of it,  and what happens the X-server breaks.  I get an error message saying the NVIDIA module is 8776 and the Xserver is 8762.  I have the latest restricted drivers, and nvidia-glx downloaded and installed.  I have reinstalled both just in case something happened.  And yet I continiue to get the same error message.

Thank you for any help in advance.

---

### Post by BitTorrentBuddha on 2006-11-07
When you get to a terminal after hitting OK at the X fails to load screen, simply run this command:```
sudo nvidia-xconfig
```That should automatically redo your configuration to account for your new driver, if that doesn't work post back.

---

### Post by JNowka on 2006-11-07
I did as you said to do, and I got the same error message.

Version Mismatch

X Driver version: 1.0-8762
GLX module version: 1.0-8776

And was told to reinstall NVIDIA, which I have tried.

---

### Post by syxbit on 2006-11-08
remove all drivers, install the newest 96.29, and then run
sudo nvidia-config

---

### Post by JNowka on 2006-11-08
I am trying to install the nvidia-glx driver avalible in the repositories.  It should be nothing more than an update, because I had the previous version installed.  But all I get is that I have a version mismatch, X Driver version = 1.0-8762 and GLX module version = 1.0-8776.  I really don't look forward to the drivers from scratch method.

---

### Post by tseliot on 2006-11-08
try this:
```
sudo aptitude install linux-generic linux-restricted-modules-`uname -r`
```

```
sudo aptitude install nvidia-glx
```

---

