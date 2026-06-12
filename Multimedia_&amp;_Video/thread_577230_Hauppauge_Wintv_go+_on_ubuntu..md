---
title: "Hauppauge Wintv go+ on ubuntu."
date: 2007-10-16
forum: Multimedia &amp; Video
---

### Post by Ikith on 2007-10-16
Will this work with ubuntu if so is there a guide out there?

---

### Post by wolfen69 on 2007-10-16
I have a Hauppauge 150 card running on my Feisty box, and I get live tv by: 

sudo apt-get install ivtv-utils (drivers)

open VLC 

File -> open Capture Device -> PVR -> OK

then you can do

ivtv-tune -h

to see the options which control the card. The interesting ones are

ivtv-tune -d(input number)

which changes the card's input from composite to s-video, and

ivtv-tune -c(channel number)

which changes the channel.

for a cool desktop tv remote, go to: [http://tvremote.sourceforge.net/](http://tvremote.sourceforge.net/)

remember to have java installed first. then you can right click: open with java.

---

### Post by Ikith on 2007-10-17
Oh wow that sounds fun :-P! Any other features? Stereo output and so on?

---

