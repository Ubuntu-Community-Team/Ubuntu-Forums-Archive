---
title: "pvr 250,150 install"
date: 2007-08-13
forum: Multimedia &amp; Video
---

### Post by jackalrules on 2007-08-13
hello peeps i have a pvr 150and a 250 how do i install them on unbuntu ? plz helpppppppppppppppp:)

---

### Post by wolfen69 on 2007-08-14
Originally posted by tropicflite

 I have a Hauppauge 150 card running on my Feisty box, and I get live tv by going to VLC Player and:
File -> open Capture Device -> PVR -> OK

Did you already install ivtv-utils by doing:
```
sudo apt-get install ivtv-utils
```
then you can do
```
ivtv-tune -h
```
to see the options which control the card. The interesting ones are

ivtv-tune -d(input number)

which changes the card's input from composite to s-video, and

ivtv-tune -c(channel number)

which changes the channel.

---

### Post by tgm4883 on 2007-08-14
They should both work OOB in Feisty

---

