---
title: "IR-Rock 3230 webcam"
date: 2010-10-06
forum: Multimedia Software
---

### Post by redtop on 2010-10-06
I have an IR-Rock 3230 USB webcam which I have tried to connect to Ubuntu 10.04 for use in connection with Skype, but it does not seem to work!

Does any one have any idea about which driver I need?

I have looked at the IR-Rock web-site but there does not seem to be any Linux drivers available.

---

### Post by no2498 on 2010-10-06
try the cam in cheese webcam booth first

it may be loaded already look in sound and video for it

if it does not come on try this


gstreamer-properties


open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's

hope this helps

---

### Post by redtop on 2010-10-06
Well, I have now worked out that it is on v4l2 and that it works.

The image as it stands right now is not the best of quality, so now the next question is whether there are an application which can be used to control it (luminescent, colours, contrast etc.)?

Any ideas?

---

