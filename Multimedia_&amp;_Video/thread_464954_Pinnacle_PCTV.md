---
title: "Pinnacle PCTV"
date: 2007-06-05
forum: Multimedia &amp; Video
---

### Post by RedXIII on 2007-06-05
Hi all!
I just installed the latest version of Ubuntu Feisty Fawn and i have some problems in making tvtime recognize my tv card, Pinnacle PCTV. It's a card based on BT878 chip. I succeeded in making tvtime recognize the card, but i can't tune on any channel. I followed some internet guide i found with google but that didn't help :(
Sorry for my poor english and thanks to all who will reply!

Bye,
Giulio

---

### Post by bluntz on 2007-12-01
Its a kernel bug,
and a very old and annoying one too.
try this first
sudo rmmod bt878
sudo rmmod bttv
sudo modprobe bttv card=39 tuner=33

This works for me,you may have to change the tuner and card # for your card.
This bug has been in the kernel since 2.6.10 as far as I can tell.
I am running Gutsy with 2.6.22-14 and its still here....very sad.
modules.conf has been changed too so its not clear how to handle the loading order or even if btaudio exists. It may be multiple bugs with snd_bt87x getting in the way too.
Clear as mud.

---

