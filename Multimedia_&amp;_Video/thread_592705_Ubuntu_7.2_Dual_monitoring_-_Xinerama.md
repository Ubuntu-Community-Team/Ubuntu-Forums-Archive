---
title: "Ubuntu 7.2 Dual monitoring - Xinerama???"
date: 2007-10-26
forum: Multimedia &amp; Video
---

### Post by talkz396 on 2007-10-26
hey, i expected the new screen tool to configure my dual screen monitor for long time, 
i downloaded the new ubuntu 7.2 and i was very disapointed to discover it still not
slove my problem with the dual monitor.this is the only reason i keep using windows in my work
any idea how to enable Xinerama TWO Screens one 
17" ProView's should be 1152x864 
and 19" NEC's should be  1280x960...


 please help me to get rid of windows!

---

### Post by dei on 2007-10-26
hey, calm down.
RandR (This out of the box dualscreen-magic included in Gutsy ;-) ) sadly isn't supported by all graphic-card-drivers (as far as i know only by intel 815) but there are other very quick ways of getting your dualscreen to work:

**first we need to know what grafic-card you are using: nvidia, ati, some intel (eventually on-board) or something else...?**
with nvidia its very easy, simply install and start nvidia-settings out of the console and there you have an easy settings-tool
with intel as already said, the included displayconfig-gtk should work (the normal display and driver tool in gutsy)
for ati I can't help any further, but I'm sure Google can teach it to you in less than a half hour or just post your card-type and I'm sure you'll be helped by an ati-enthusiast (that's the linux-community)

Note: In the most cases you dont even need xinerama, but for example with nvidia twin-view will do the trick (with fully enabled compiz-fusion --> Desktop-Effects which you don't have with xinerama)

By the Way: If your graphic-card is absolutely not supported check [http://ubuntustarter.blogspot.com](http://ubuntustarter.blogspot.com) before buying a new one. I'm currently testing Xdmx on Gutsy wich will enable any network-connected pc/laptop with monitor to extend your desktop to it (--> no dualhead graphic-card needed) (Perhaps you know it from Windows from the commercial Software Maxivista)

;-) another P.S. I think you meant gutsy gibbon 7.10 with "ubuntu 7.2" which doesn't actually exists

---

### Post by talkz396 on 2007-10-26
Well first of all , thanks for the quick response! :) 
My graphic card is GeForce 6800GS (nVidia) ....
Do u know if it supports it?
damn, i really want remove this ugly windows from my work :KS

---

