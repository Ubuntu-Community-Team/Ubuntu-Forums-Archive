---
title: "best tv card for gutsy"
date: 2008-01-24
forum: Multimedia &amp; Video
---

### Post by Paul Barnett on 2008-01-24
What is the best tv card to use with gutsy?

---

### Post by .nedberg on 2008-01-24
I use a Hauppauge PVR-500 MCE with mythbuntu. Very pleased!

[http://www.hauppauge.com/pages/products/data_pvr500mce.html](http://www.hauppauge.com/pages/products/data_pvr500mce.html)

---

### Post by wolfen69 on 2008-01-24
+1 for the Hauppauge PVR (150/250/350/500) line of tuner cards. if you get one, just remember to " sudo apt-get install ivtv-utils".

here's a guide for getting tv to work.

I have a Hauppauge pvr card running on my gutsy box, and I get live tv by: 

sudo apt-get install ivtv-utils 

open VLC player

File -> Open Capture Device -> PVR -> OK

then you can do (in terminal)

ivtv-tune -c25 (25 is channel number)

which changes the channel.

ivtv-tune -h

to see the options which control the card. 


for a cool desktop tv remote,(so you dont have to use terminal to change channels) go to: [http://tvremote.sourceforge.net/](http://tvremote.sourceforge.net/)

remember to have java installed first. then you can right click: open with java.

---

