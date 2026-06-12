---
title: "Sound Card Problem"
date: 2009-06-17
forum: Multimedia Software
---

### Post by JustinHD on 2009-06-17
I have a problem with my sound card (i think its from the factory), my center/subwoofer channels are swapped. Even had this problem under Windows but the software that came with the card drivers had an option to swap them (again).

Now the question is, how can i fix this under Kubuntu 9.04?

Already tried getting the linux drivers from the manufacturer but when they install they screw up ALSA.

Please Help.

Cheers,
Justin

---

### Post by JustinHD on 2009-06-18
Bump. Oh come on...nobody had this problem?

---

### Post by Chris Musampa on 2009-06-18
Open KMix, then click Settings > Configure Channels

Scroll down the list and tick "Exchange Center/LFE", click OK and the new control will appear in Kmix.

---

### Post by JustinHD on 2009-06-18
> **Chris Musampa said:**
> Open KMix, then click Settings > Configure Channels

Scroll down the list and tick "Exchange Center/LFE", click OK and the new control will appear in Kmix.

There is no control for that. Thats the first thing i checked.

Screen shot to prove my sayings.

[IMG]http://i44.tinypic.com/wbpcth.png[/IMG]

---

### Post by Chris Musampa on 2009-06-18
Sorry Justin, I'm out of ideas.

Edit:
Depends on your connections but they're similar to mine (3.5mm stereo jack at the PC end, one red one white phono plug at the speaker end) you could just swap the red and white at the speaker end.

---

### Post by JustinHD on 2009-06-18
Can't do that Chris, my Center/LFE are on the same audio jack. I think the only option is to make a script that tells ALSA to swap the outputs....but i don't know scripting in linux, i'm a beginner...

---

### Post by JustinHD on 2009-06-18
Ok, news flash. I spoke to a friend of mine who uses Slackware with KDE 3.5.x and he said that his Kmix has a tab that can Switch Center/LFE channels, but in my KDE 4.x that tab doesn't exist. Only option is to revert to KDE 3.5.x, question is, how do i do that?!

---

### Post by Chris Musampa on 2009-06-18
I'd hazard a guess (it is only a guess) the control wouldn't show up in KDE 3 if it doesn't in KDE 4. Does it show up if you type "alsamixer" in a terminal (right and left arrow keys to see more controls)?

This thread might help if you still fancy KDE 3 though I've not tried (it might also be worth posting your question on kubuntu forums as well).
[http://kubuntuforums.net/forums/index.php?topic=3103125.0](http://kubuntuforums.net/forums/index.php?topic=3103125.0)

---

### Post by JustinHD on 2009-06-18
Posted in Kubuntu since this morning, but i think nobody actually visits those that often. I'll give it a try and post the update. 
I'm in windoze right now cos i need to work in some 3D Apps :)

---

### Post by JustinHD on 2009-06-18
Ok, just checked ALSAMIXER in terminal and no, the swap controls don't show up in there either...

Edit: Thanks for that link, i'm trying KDE 3.5.x now, will post the feedback.

---

### Post by JustinHD on 2009-06-19
Damn it. I give up.

I installed KDE 3.5 and it turns out that the switches tab contains the extended channels in that show up in Kmix in KDE 4.....so no progress at all.....

Any other ideas how to switch my center/lfe channels?

---

### Post by Chris Musampa on 2009-06-19
I've never had to do anything to get alsa to recognise the swap control, it just happens automagically for my card, maybe someone more experienced will chime in with a way to force it to happen. In other words - bump :p

---

### Post by JustinHD on 2009-06-20
Damn right bump.

---

