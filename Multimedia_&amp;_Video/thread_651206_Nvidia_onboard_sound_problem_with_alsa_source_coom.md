---
title: "Nvidia onboard sound problem with alsa source coompile"
date: 2007-12-27
forum: Multimedia &amp; Video
---

### Post by ecullerton on 2007-12-27
Hello,

I am having problems with the sound in ubuntu studio 7.10.  I have an Nvidia 650i Ultra motherboard with onboard sound.  When I first installed, the onboard sound worked fine.  I then compiled and installed the source files from the alsa website because I have an EchoMia sound card.  When I finished I had the Echo Mia working, but now I have no onboard sound.  Can someone help? 

I followed the guide at:
[https://help.ubuntu.com/community/EchoMia](https://help.ubuntu.com/community/EchoMia)   

Thanks, Ed

---

### Post by nirudha on 2007-12-27
I don't have experience with your hardware but after looking at the site you mentioned I thought it might be worth double checking that you altered the following line as appropriate

./configure --with-cards=**_intel8x0_**,mia --with-oss=yes --with-sequencer=yes

to indicate the soundchip on your motherboard in place of the intel one... most likely you did but sometimes some small things like that get overlooked.

good luck!

---

