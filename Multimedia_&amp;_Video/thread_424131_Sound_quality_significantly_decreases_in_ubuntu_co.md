---
title: "Sound quality significantly decreases in ubuntu compared with other sources"
date: 2007-04-26
forum: Multimedia &amp; Video
---

### Post by jtreach on 2007-04-26
After upgrading to feisty the audio quality on my system has decreased significantly this is not due to my speakers as playing exactly the same music track from another source through the same speakers works perfectly (from my mp3 player).

I have the same problem on at least .m4a and .mp3 file types. I have recently installed real player and the helix player (was trying to listen to internet radio).

My music sounds awful can anybody help?

---

### Post by beaudoin996 on 2007-04-26
Have you try to convert your files in other format ?

---

### Post by Patrick K on 2007-04-26
No idea if this is of any help but...

Are you using ALSA drivers? If so, they could be compiled for the old kernel. I'm researching this right now as my sound quality has dropped since going to Feisty. 

Take a look in /usr/src/alsa/alsa-driver-1.0.13/config.log to see what kernel it is compiled for.

---

### Post by jtreach on 2007-04-26
I'm not sure which drivers I'm using to be honest I think I used which ever ones automatix used to install on edgy. At least it's not just me having this problem. I looked for the you file mentioned  above but it doesn't exist and neither does the folder so I assume I'm not using that driver set.

I'm gunna see if it's still happening in the older kernel.

---

### Post by zasf on 2007-04-29
I have this problem too, any other ideas?

---

### Post by mcduck on 2007-04-29
Check your mixer settings. You should not have any of the channels at 100%, that will cause distortion on most machines. Drop them to around 90% and your sound should be fine.

If that didn't help, make sure you have all channel controls in use (in Edit/Preferences and enable all).

---

### Post by jtreach on 2007-04-29
I think this helped it's still distorted but almost bearable. Is there any harm in dropping it lower will this help? And has this sound problem been reported as a bug it's obviously affecting a lot of people.

To get to the mixer settings just type the word 'alsamixer' into the terminal.

EDIT: Dropping the PCM setting seemed to clear up the distortion. I dropped mine to 74 and the sound seems fine now.
Thanks to everyone for their help. :]

---

### Post by zasf on 2007-04-30
hum.. if you drop the volume to 0% you won't hear any distorsions at all :D

I believe there must be something connected with the upgrade from edgy to feisty.. since I didn't change my volumes but didn't have this problem with edgy. If you find any bugs related to this problem, please post them here so that I can subscribe to them.

---

### Post by jtreach on 2007-04-30
Kk will do!

p.s. thanks for the 0% tip..... really worked!!! :P

---

### Post by zasf on 2007-04-30
I'm glad it worked 8)

---

