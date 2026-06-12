---
title: "Just a simple TV viewer?"
date: 2007-06-20
forum: Multimedia &amp; Video
---

### Post by botulismo on 2007-06-20
I was wondering if anyone knew of a program that acted just as a simple TV viewer. I have a WinTV card that's sitting in the computer collecting dust, and no desire to convert my desktop into a mythtv media center. I just want the option to watch, and perhaps if I'm lucky, record a show or two on the computer. Does anything like this exist for ubuntu/linux?

---

### Post by david_2001 on 2007-06-20
Analog: TVTime to view, xdtv to view and record.
Digital: Kaffeine.

---

### Post by wolfen69 on 2007-06-25
Originally posted by tropicflite

 I have a Hauppauge 150 card running on my Feisty box, and I get live tv by going to 

File -> open Capture Device -> PVR -> OK

Did you already install ivtv-utils by doing

sudo apt-get install ivtv-utils

then you can open terminal:

ivtv-tune -h

to see the options which control the card. The interesting ones are

ivtv-tune -d(input number)

which changes the card's input from composite to s-video, and

ivtv-tune -c(channel number)

which changes the channel.

---

