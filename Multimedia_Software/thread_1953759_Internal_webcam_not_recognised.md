---
title: "Internal webcam not recognised"
date: 2012-04-06
forum: Multimedia Software
---

### Post by Nasurate on 2012-04-06
Ubuntu 11.4 has stopped detecting the internal webcam on my laptop (Toshiba Satellite L350 is the laptop, I have no idea what the webcam is. >.<) I have no idea how to fix this, any thoughts?

---

### Post by kpdutta on 2012-04-07
> **Nasurate said:**
> Ubuntu 11.4 has stopped detecting the internal webcam on my laptop (Toshiba Satellite L350 is the laptop, I have no idea what the webcam is. >.<) I have no idea how to fix this, any thoughts?

Hi,
    try the following...
 In the unity, search " multimedia system selector". Configure the input video as:
    
Plugin:  Video for linux 2(v4l2)
Device: Default 

Press test button and see if the webcam is working or not.  This is the preliminary, but if it will not work then there is other option also...
good luck..... 

KamalpDutta

---

### Post by Nasurate on 2012-04-07
I can't even find the unity, which I've never heard of. Is it a terminal-like programme?

---

### Post by tuxtout on 2012-04-07
Open a terminal and type
gstreamer-properties
hit enter
click the video tab
under default input select your webcam
click test
What happens?

---

### Post by Nasurate on 2012-04-07
Under default input there is no option to select my webcam. It doesn't acknowledge that the device is there.

---

