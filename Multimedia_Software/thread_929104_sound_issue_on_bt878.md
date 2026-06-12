---
title: "sound issue on bt878"
date: 2008-09-24
forum: Multimedia Software
---

### Post by AndrewRoyCarter on 2008-09-24
Hello friends!
I am in the process of settings up a mythtv box, and have hit a few snags.
I am using a bt878 model capture card (if you need the exact model number i can get it). After some intense googling, i got video capture to work just fine (coming in through /dev/video0). I am having a bit of trouble with audio though. Heres the thing. Im using mythbuntu. If i go into the sound setup in the control panel, the bt878 is listed. if i go in the alsamixer, it is listed as well. Right now i have speaker plugged into the audio out port of the capture card. In the future i plan to line out of the capture card into the computer to record sound, but for now just trying to get sound working in general ^_^. So, if im in mythtv watching tv, i get no sound at all. i have tried using /dev/dsp, and /dev/radio0 to capture sound (i think i saw in dmesg that the bt878 was registering as a device at /dev/radio0 , and neither worked. so i figured for testing purposes, i'd install tvtime and see what happens. in tvtime, i get no sound either. but if i set the sound to mono in tvtime, sound works just fine (again, from the audio out of the capture card). So i thought that if i could figure out what tvtime was using to get sound, i could replicate this in mythtv. i could not find a way to see the audio device tvtime was currently using, but in the man pages it said that by defauly it uses /dev/mixer:line. so i enter /dev/mixer for the audio source in mythtv, and sound started playing even though i was not watching tv. then when i went to watch tv, the sound stoped. after a ton of googling, it seems many people have had similar issues with this type of card, but no solid fix.i have tried alot of fixes, with no luck, but because tvtime works with it, i have hope! if anyone wants any dmesg outputs or anything let me know! i greatly appreciate any help, and thanks for your time!  

-Andrew

---

### Post by AndrewRoyCarter on 2008-09-24
an update!
well, i got it working- sort of. i found that if i start tvtime through
the terminal with mythtv not playing, set the sound to "mono" and then [ctrl+c] in the terminal that spawned tvtime, mythtv can then use the card.
so i guess im having tvtime initilize the card, then crash the program in
order to leave the card active for mythtv?

---

