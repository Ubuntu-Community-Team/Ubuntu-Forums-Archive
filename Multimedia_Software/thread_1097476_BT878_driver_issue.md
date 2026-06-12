---
title: "BT878 driver issue"
date: 2009-03-16
forum: Multimedia Software
---

### Post by spunmonkey on 2009-03-16
Having dramas getting my machine to see the capture card

I have tried adding the following to the /etc/modprobe.conf file

alias char-major-81 bttv
options bttv card=105,105,105,105

i'm just unsure why i don't get bttv1, bttv2 & bttv3 lines as i do on another machine with a similar card in it.
[IMG]http://www.masterhire.net.au/uploads/ubuntu-error-1.jpg[/IMG]

---

### Post by mocha on 2009-03-16
What are bttv1, 2, and 3 supposed to represent?  Is it a multiple tuner card or something?

---

### Post by spunmonkey on 2009-03-16
Yes, the card has 4 inputs.

each can take a different source.
at the moment i am trying to connect a camera to each input to set up a close circuit security system.

i'm using Zoneminder as the software to view the output of the camera. As far as i have been able to find the issue is with the hardware but will be checking out their support as well.

---

