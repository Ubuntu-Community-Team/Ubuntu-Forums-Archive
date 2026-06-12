---
title: "New 9.10 install, epg issues + others"
date: 2009-11-12
forum: Mythbuntu
---

### Post by 365nice on 2009-11-12
Hi there - I've been running mythtv on ubuntu for many years now (first on an asus pundit, then a sony vaio desktop and now an asus mobo with an antec case) -  and I have to reluctantly say that my original build with ubuntu hoary on myth 0.18 was probably the best running and most stable. I'm hoping someone can offer some ideas to help me change that.
 
Currently my biggest problem is that my trusty AverMedia 771 cards now no longer seem to get good epg data (I get some, but many channels have holes in the guide data in the UK). I can record and watch tv whe there is data but its frustrating not to have all the channel info that i'm used to (if I put the cards back into my old box - Ubuntu 8.04 with with 0.21 - I get good data). I've searched around - and seen some mention of this in reference to epg data for other cards (e.g. haupage). I don't notice anything in the logs (although with mythbuntu not much logging seems to come out?)
 
I had high hopes with my new hardware and this new mythbuntu installation - but I am a bit disappointed.
 
I've also notice that MythWeb doesn't seem to have a password setup when you install myth (nasty - the regular mythtv install on 0.21 took care of this).
 
Hopefully someone might have some ideas for me - at the moment I am thinking of maybe going back to Ubuntu 9.04 (maybe the newer kernel has broken the dvbt driver stability).
 
Tim

---

### Post by superm1 on 2009-11-12
You can set a password in MCC for Mythweb.  Not sure on the guide data bit.

---

### Post by 365nice on 2009-11-13
Thanks for the tip on editing the password - I do think that the initial install should just add your current password for you (or at least prompt you for one).

As for the missing epg data - given the lack of errors, I decided to try a tv signal booster (I bought one from Maplin in the uk) - and guess what, plugging the antennae into that, and then running a cable from the booster and splittng to my card seems to fix it. 

Not sure why changing versions of ubuntu and myth would change this (same tv cards - although different mobo) - but something has made it more sensitive to a weaker signal.

Now I'm getting good guide data. Now I am contemplating some of the changes in 0.22 - some of them I find have made the ui worse (quite obvious when I watch my wife use it, and struggle with some of the changes they made.

Thanks for the response.

Tim

---

