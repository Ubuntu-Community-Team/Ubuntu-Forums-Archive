---
title: "system sees only one speaker instead of two"
date: 2013-05-22
forum: Multimedia Software
---

### Post by sowdust on 2013-05-22
Hello everyone,

I have a simple Ubuntu server I used as music player. All has always worked fine, but one day (maybe after an update? I can't recall) the sound started playing only from the right speaker.
I am sure the speakers are ok: if i plug them into another pc all works fine. If I plug headphones in the server's jack i still hear music only on one side.

apay -l outputs 
```
**** List of PLAYBACK Hardware Devices ****
card 0: ICH7 [Intel ICH7], device 0: Intel ICH [Intel ICH7]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH7 [Intel ICH7], device 4: Intel ICH - IEC958 [Intel ICH7 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

if i try speaker-test -s 1 i can hear the noise coming from the right speaker.
if i type speaker-test -s 2 it tells me "Invalid parameter for -s option"


I have tried messing around with the volumes from alsamixer but I do not get any result...  
anyone has an idea on what this could be? Hopefully the jack/soundcard did not break

thanks!

---

### Post by mikeym on 2013-05-22
> **sowdust said:**
> 
if i type speaker-test -s 2 it tells me "Invalid parameter for -s option"


I get weird results with "speaker-test -s 2" as well; I get the same error you do. Although my lubunutu setup is pretty screwy in the sound department so I could be me as well.

With "speaker-test -s 1" I get a message it's outputting to the left channel but actually it outputs to *both*. 

What works for me as a test is:

```

speaker-test -c 2

```

Hope this helps. 

Also if I were debugging it I would definitely find a pair of headphones or another pair of speakers to plug into my computer just to rule out that there's something going wrong with the speaker / soundcard combination.

---

### Post by sowdust on 2013-05-23
Hi mikeym, thanks for your reply. As mentioned earlier I did try to plug a pair of headphones into the jack and also than I could not hear anything from the left side, so it is not a speakers problem.
I have tried speaker-test -c 2 and it alternatively tests both speakers: I can hear the noise from the right one, but the left is still completely silent

---

### Post by mikeym on 2013-05-23
Um... have you checked the balance? I'm not sure what mixer you would be using, but *alsamixer* on the command line would show one of the volumes as being half width if it were unbalanced, and you could adjust it using the q, w (up) and z, x (down) keys.

---

### Post by sowdust on 2013-05-23
yes I have, tried to change balance of every channel but nothing changes (I mean, the volume of the right speaker does move, but the left remains silent).
Also, I think if it were a balance problem the speaker-test would still show some results, while nothing comes out while testing the left speaker.

---

### Post by sowdust on 2013-05-27
any ideas? I really don't know where to look!

---

### Post by sowdust on 2013-06-17
lil bump?

---

