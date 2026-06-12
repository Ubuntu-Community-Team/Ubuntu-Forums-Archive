---
title: "Sound driver missing in fresh install"
date: 2010-09-15
forum: Multimedia Software
---

### Post by Speedwagon on 2010-09-15
I've never had any problems before, but I just did a fresh install of 10.04.1 on a brand new drive yesterday.  I noticed this morning that I have no sound drivers(under the hardware tab of sound preferences, there is nothing listed).

I found a thread that had this line to run:
```
cat /proc/asound/card0/codec#* | grep Codec
```
And I got:
```
Codec: Realtek ALC888
```

Not sure what to do now though.

---

### Post by lidex on 2010-09-17
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

