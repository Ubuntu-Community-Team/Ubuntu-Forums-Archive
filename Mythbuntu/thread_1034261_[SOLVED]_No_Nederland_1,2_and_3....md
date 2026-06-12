---
title: "[SOLVED] No Nederland 1,2 and 3..."
date: 2009-01-08
forum: Mythbuntu
---

### Post by ikke2808 on 2009-01-08
Hi,

I built myself a mythbuntu PC and all seems to work fine.
The C-1505 Technotrend card including CI and CAM is working and recognized. 
The Casema smartcard is working so I started to scan for channels.
Being a relatively new at Linux/Mythbuntu 

And (you guessed) there I start to have troubles:
1. Mythtv seems to scan on Network ID 0500 instead of 5555 (Utrecht). I have googled on this but I cannot find a way to set this.
2. It cannot find the "Nederland 1, 2 & 3" channels. All others are found and set up. 

Has anybody expirienced something like this? Or is a solution around I overlooked searching?

---

### Post by ian dobson on 2009-01-09
Hi,

Try installing w_scan to do a channel scan the use the configuration file created by importing it into mythtv.

I've quite often seen this problem that the inital scan with mythtv doesn't always find all channels.

Regards
Ian Dobson

---

### Post by Da_Teach on 2009-01-10
Hi Ikke,

You will need to get the latest v4l-dvb drivers and probably patch them with this patch:

[http://www.linuxtv.org/pipermail/linux-dvb/2008-October/029664.html](http://www.linuxtv.org/pipermail/linux-dvb/2008-October/029664.html)

There is a bug in the drivers (and at least a week or 2-3 ago it wasnt fixed yet in the latest v4l drivers) where it wont lock on the transponder of Ned1-3. The patch attached to the link above will fix this and will enable a lock on that transponder.

Gr. Da_Teach

---

### Post by ikke2808 on 2009-01-11
Hi  Da_Teach,

I am hoping the right way is in your reply as I tried Ian's (thx. btw Ian!) but without result. The tuner still doesn't find the Dutch channels. 

The post states a tda827x.c, but that I do not have on my system. 
I installed Mythbuntu 8.10 and until now DVB in mythtv worked without any patching.

Should I download any package and compile it to be able to work with this patch? If so can you tell me where to find the download and a HOWTO? At TechnoTrend I do not find any Linux stuff....

Gr.

---

### Post by Da_Teach on 2009-01-11
You'll have to build new drivers from scratch, see:

[http://linuxtv.org/wiki/index.php/How_to_build_from_Mercurial](http://linuxtv.org/wiki/index.php/How_to_build_from_Mercurial)

I suggest doing this from /usr/src directory, which should then create a /usr/src/v4l-dvb directory, somewhere in that tree there should be a tda827x.c file.

Once you've patched/updated that file you need to make and install the drivers.

One small note, each kernel update will require you to redo this step!

I'm a rather linux newb so I cant help you on the exact steps to get this working, but I'm sure someone here can help out more if needed.

---

### Post by ikke2808 on 2009-01-12
Hi DA_Teach,

It worked! Thanks a lot! :D
I installed the driver source, changed tda827x.c and ran a make and make install...

Scanned again for channels and they are found!

Again thanks!

Cheers.

---

