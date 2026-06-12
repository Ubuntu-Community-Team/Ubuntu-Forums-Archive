---
title: "ESI Gigaport with Jack / Ubuntu 9.04"
date: 2010-05-06
forum: Multimedia Software
---

### Post by cmpmj on 2010-05-06
Hello

I have an ESI Gigaport HD USB external soundcard which I'd like to use via Jack with my Thinkpad T40 running Ubuntu 9.04.

This is the card, it has no inputs and 8 x outputs:

[http://www.esi-audio.com/products/gigaporthd/](http://www.esi-audio.com/products/gigaporthd/)

The card is autodetected on plug in. I can see the 8 x outputs in the Jack connection window but I can't run any sound to it.  Anything I connect to it on any of the 8 channels is silent.

Does anyone have any suggestions - visually it seems that all is working, I just can't hear anything being outputted?

---

### Post by cchhrriiss121212 on 2010-05-06
Have you tried alsamixer? (Open a terminal and type it in) 
Also, is jack actually running without errors when you press start?

---

### Post by cmpmj on 2010-05-06
Jack starts up fine and returns no errors.

Alsamixer shows the Gigaport at the foot of the screen with 8 faders in mid position.

Still nothing I try to connect in Jack seems to get to the outputs of the Gigaport.  

I'm principally using the audio test facility within Pure Data to do this, so perhaps this is the problem.  Does Pd require extra setting up in order to see external sound cards?

---

### Post by cchhrriiss121212 on 2010-05-07
I have no idea about Pure Data, but I found [this]("http://en.flossmanuals.net/PureData/ConfiguringPD") which should help. I would suggest you try something simple first like playing an mp3 alsaplayer or vlc using the jack plugins.

---

### Post by cmpmj on 2010-05-10
OK, solved.

Stupidly hadn't checked the buttons underneath the device output faders in the alsamixer gui window, so all seemed OK visually (also Jack looked OK), but essentially no outputs were enabled...

Doh.

Oh well, in business again ~ what it does mean is that ESI Gigaport HD's work under Unbuntu 9.04 without any command line tweaks and are auto detected, just remember to check the enable buttons in alsamixer.

---

