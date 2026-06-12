---
title: "Sound keyboard hotkeys - change volume gap"
date: 2007-09-11
forum: Multimedia &amp; Video
---

### Post by GaMeFaNaTiC on 2007-09-11
i use keyboard hotkeys (fn + up/down) to change the volume and it shows a bar while im doing it but it goes up in 10s eg. 10% 20% 30% 40%, is there a way to change this so it increases and decreases by a smaller number such as 2 instead of 10? thanks.

EDIT: updating sound drivers made it different the gaps are different now i think. mod can delete this thread.

---

### Post by kidders on 2007-09-12
Hi there,

You may no longer be interested in this topic, but just in case, I thought I would add a few comments.

As you've noticed, exactly what an audio driver does with a particular instruction seems to be somewhat "flexible". For instance, I've noticed with mine that an instruction to lower the volume by 10% is always obeyed ... *increasing* it by 10% however seems to consistently result in only a 7% increase, for some reason. I have no idea why that is, but since updating your sound drivers seemed to somehow alter the way your system reacts to the same instructions, I thought it might be worth mentioning.

In any case, if you're unhappy with the way Ubuntu does things like raise & lower your volume by default, the surest way to get what you want is to take control of them yourself. On my box, for instance, I don't have any multimedia key managers installed. Instead, I've used xmodmap and KDE's dcop to handle volume control. The result is that I can manipulate exactly how quickly my volume goes up and down, or perhaps tie my keyboard's volume buttons into a specific audio channel (eg PCM, CD audio, my PC speaker, etc.) ... whatever I want.

---

