---
title: "Wintv Pvr-150"
date: 2007-07-02
forum: Multimedia &amp; Video
---

### Post by sbclifton on 2007-07-02
I have a PC with a Hauppauge Win-TV PVR-150. Hauppauge shows driver deelopment for redhat and another kernel. Is there drivers for the Ubuntu distribution?

---

### Post by md2020 on 2007-07-02
I am running Ubuntu Feisty with the WINTV PVR-150.  (not the MCE version) It recognizes the card out-of-the-box (without having to download any extra drivers). However, I have yet to get my remote working.

Should you accomplish that, I would be interested in knowing how you accomplished that task.

Best of luck....

---

### Post by wolfen69 on 2007-07-02
Originally posted by tropicflite

 I have a Hauppauge 150 card running on my Feisty box, and I get live tv by going to 

File -> open Capture Device -> PVR -> OK

Did you already install ivtv-utils by doing

sudo apt-get install ivtv-utils

then you can do

ivtv-tune -h

to see the options which control the card. The interesting ones are

ivtv-tune -d(input number)

which changes the card's input from composite to s-video, and

ivtv-tune -c(channel number)

which changes the channel.

---

