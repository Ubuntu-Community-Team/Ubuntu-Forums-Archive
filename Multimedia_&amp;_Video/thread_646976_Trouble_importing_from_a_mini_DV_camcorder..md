---
title: "Trouble importing from a mini DV camcorder."
date: 2007-12-21
forum: Multimedia &amp; Video
---

### Post by cwrann on 2007-12-21
I have a canon ZR500 mini DV camcorder and am trying to import the video onto my computer via ieee1394. I have downloaded Kino for my video editing. I am not able to import the video.

Under the IEEE 1394 tab in the preferences in Kino it says.

```
The IEEE1394 subsystem is not responding.
The Raw1394 module must be loaded and you must have read/write access to /dev/raw1394 
```

I entered this code in the terminal to give it permission.

```
sudo chown 666 /dev/raw1394
```

But I still have the same message and am unable to import video.

---

### Post by z0mbie on 2007-12-22
Try using **dvgrab**:

```
sudo aptitude install dvgrab
```

---

### Post by cwrann on 2007-12-22
Thanks for the tip. I will try dv grab when my camcorder battery is recharged. I was able to gane permission to the ieee 1394 port by adding myself as a user of disk.

```
sudo usermod -aG disk $USER
```

I have imported one tapes worth of film into Kino and now find Kino to be very glitchy.

Time to search the forums for fixes or alternatives to Kino.

---

