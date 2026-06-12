---
title: "Mythttv .20, on Edgy with DCT2000 cable box - no signal!"
date: 2006-11-21
forum: Multimedia &amp; Video
---

### Post by lokimon on 2006-11-21
i'm having a frustrating problem getting my mythtv system running using my external cable box, and even though i have fixed all the common errors, i still am left with nothing but static!

i am running edgy with mythtv .20 (see signature for exact specs)
mythtv is working fine in all ways other than the cable box issue.

i have two tuner cards (a PVR-350 and a PVR-150) and they both work just fine when set up with the coaxial run straight into them.  i can watch/record any of the basic cable channels.

if i run one of the coax lines into the cable box, i can run the coaxial line out of the box into my tv directly and get perfect picture, and all the extra channels i pay for.

i have set up the channel changer script for this cable box, and can use it to change the channel when i am watching tv in this manner (cable box sending coax to the tv directly.) i have also made sure that i can run this script as the same user that mythtv is running under.

the problem comes when i plug the coax cable into my PVR-*50 card.  i plug the cable in, stop the mythbackend, run mythtv-setup, and set the channel to 3, as well as putting the "channel" command in the field for it.

restart the backend and frontend, and all i get is static from that input.  the channels change and i see mythtv data, but only static in the picture.

i wonder what is different from the tv to the PVR-*350 card?

i tried replacing the channel number with 03, 04, 4, and even leaving it blank, but that makes no difference.

has anyone seen this before?

---

### Post by NT4usB on 2006-11-21
No idea...
Have you run the scan for channels option in mythtv-setup to see if it will find the channel the box is transmitting on?

I did that once. (Got to play with all them buttons!)
Along with the usual download from zapit I ended up with duplicate everything... oops!
Since your card(s) should only 'see' one channel coming out of the box, shouldn't jack things up too much.

Your signal's not HD is it?

---

### Post by lokimon on 2006-11-23
i did try that a while ago, the only channels that come through are 3 and something in the teens.  i can certainly try it again though.

no the signal is not HD.

---

