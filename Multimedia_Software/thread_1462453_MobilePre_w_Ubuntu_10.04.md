---
title: "MobilePre w/ Ubuntu 10.04"
date: 2010-04-25
forum: Multimedia Software
---

### Post by sL8 on 2010-04-25
I know there was going to be problems (beta), so this is more of a bug I guess.
The sound is very very quiet coming out of the MobilePre, I have my output turned all the way up on the MobilePre itself, my Stereo, and the volume's all the way up in Ubuntu; just to hear the same amount as I would hear if the MobilePre was turned half-way, and the stereo 1/5 of the way turned up.

Running 64 bit.

---

### Post by codyduncan on 2010-04-29
I am having the same problem.  I've tried configuring the hardware, but no success.

I'm running a fresh 32 bit install.

---

### Post by codyduncan on 2010-04-30
bingo - fixed it.

go to terminal, run alsamixer

Hit F6 to select the device, then notice that one of the volumes is really low.  Fix that.

---

### Post by StudioB on 2010-08-27
this was a great help. ive been looking all over for this advice. it is good!

---

### Post by StudioB on 2010-08-29
i read through the main audio instruction fix-all post but couldnt find what to do.
i have been manually fixing my mobilepre each reboot by running alsamixer and adjusting the volume.
today it wont let me run alsamixer. it says "cannot open mixer: No such file or directory"
what has happened? what should i do?

---

### Post by julipanette on 2010-10-31
I have the same problem, only the alsa mixer trick didn't help. PCM 1 was at zero but turning it up didn't make any difference, apart from making the buzz noise in my speakers a bit louder. So I have all volume controls turned up to the max, and still no sound from my MobilePre. Occasionally I can hear a very low signal when I fiddle around, but I haven't been able to detect any coherent pattern that would explain why that happens sometimes and not other (most) times. I know that my soundcard is working, I tested it on another computer which also ran Ubuntu 10.04 and got it to work there by simply choosing the right sound settings from the System menu. No such luck on my own computer though. The sound works with the internal soundcard but not my MobilePre. Any help would be most deeply appreciated!

---

### Post by julipanette on 2010-10-31
aaaand sometimes life is embarrassing and it's a good idea to check that you've actually restarted JACK before posting in forums. The alsamixer thing worked! Praise and glory!

---

### Post by Bluesthang on 2011-06-07
Hi, I just bought a M-Audio Mobile pre, and have the same problem... all my knobs on the mobilepre are turned up to the max. I have sound comming out in Audacity, but having the knobs at the maximum doesnt give me any more range to go up so I have to be very close to y mics.
I'm running Ubuntu 11.04. 
I tried the terminal with alsamixer, it sees the mobilepre, when I select mobilepre, it tells me that there are no volume controls for the mobile pre. 
I oubviously can't find drivers for ubuntu...
Should i return the mobilepre and get some other brand?
Or am I doing something wrong?
Thanks

---

