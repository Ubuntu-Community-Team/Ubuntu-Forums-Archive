---
title: "Syncing .ogg With an iPod"
date: 2011-07-27
forum: Multimedia Software
---

### Post by dniMretsaM on 2011-07-27
I know that iDevices do not support OGG, but on Ubuntu 10.10 when I synced my iPod Touch with Banshee, it would convert my music (all .ogg) and then sync it to the iPod without changing the original files. Now I'm on Kubuntu 11.04 (still using Banshee, I prefer it over Amarok) but when I try to sync now I just get errors saying .ogg is not supported. How can I fix this? I'd rather not convert all my music into .mp3 because (a) It goes against my free software values and (b) it would take forever.

---

### Post by daniel_w93 on 2011-07-28
Try this:

1. Plug in your iPod
2. open banshee 
3. select your iPod in banshee and click Edit->Device properties (or something like that)

Now you should see a screen that lets you select the format you want to decode your audio to.
If Mp3 doesn't show up you probably don't have Lame Mp3 Encoder installed.

Try install it and see if it works (also make sure all the iPod compatibility plugins are activated :P)

---

### Post by dniMretsaM on 2011-07-28
No difference.

EDIT: I tried GTKPod, but it won't load my device.

---

### Post by dniMretsaM on 2011-08-02
Bump. Might try Amarok.

---

### Post by dniMretsaM on 2011-08-04
Ok, well I ended up just using my sisters computer to sync with iTunes. I also think I (kind of) figured out the issue. I read up on a few bugs relating to the "no converter found" bug and it seems that it's an issue with libimobiledevice not recognizing the device properly. On 10.10, the default was libimobiledevice1 which didn't work with newer versions of iOS (on any device). I used libimobiledevice0, which did work. 11.04 uses libimobiledevice2 which, I believe, is mainly for new *devices*. I have a 2G, which is not a new device. My guess is that libimobiledecive2 has problems with older devices. Can anybody confirm this?

---

