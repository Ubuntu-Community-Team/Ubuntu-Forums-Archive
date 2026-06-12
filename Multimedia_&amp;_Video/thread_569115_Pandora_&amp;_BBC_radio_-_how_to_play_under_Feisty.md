---
title: "Pandora &amp; BBC radio - how to play under Feisty?"
date: 2007-10-06
forum: Multimedia &amp; Video
---

### Post by starbase1 on 2007-10-06
Question from a newbie here...

I've got MP3's playing OK under Feisty, though I had to change the sound device before it started working...

I'd also like to listen to Pandora and BBC radio via Firefox - is there some trick to this? It tried to download the realplayer, but said it couldn't and offered a manual install. I downloaded RealPlayer10Gold.bin, but I'm not sure what to do with it now it's on my desktop.

Apart from which I'd really like something along the lines of Real Alternative (under windows), which plays the music without sending me 'messages' that are adverts...

Nick

---

### Post by damir_1105 on 2007-10-06
you can move RealPlayer10Gold.bin to your home folder and then:

```
chmod +x RealPlayer10Gold.bin
```

```
./RealPlayer10Gold.bin
```

that's all you need to install realplayer. :)

---

### Post by starbase1 on 2007-10-07
Thanks - that mix of upper and lower case in the filename took me three goes to get correct...

And the instruction to "Enter Finish to begin..." is worthy of using the windows start button to stop!

Anyway, it seemed to work, (I accepted the default installation options), and indeed I was able to run it, but when I tried the BBC again it told me "could not find an appropriate hxplay or realplay in the system path to use as an embedded player..."

Any clues?

---

### Post by damir_1105 on 2007-10-07
ok. now.

```
cd ~/.mozilla/plugins
```
```
ln -s /home/user/RealPlayer/mozilla/nphelix.so nphelix.so
```
```
ln -s /home/user/RealPlayer/mozilla/nphelix.xpt nphelix.xpt
```

replace user with your username.

---

### Post by starbase1 on 2007-10-07
Tried that and the commands returned 'file already exists' in both cases...

Nick

---

### Post by BLTicklemonster on 2007-12-14
Anybody ever figure this out? I have added ubuntu restricted stuff from add/remove in gutsy. what else should I do?

---

### Post by BLTicklemonster on 2007-12-14
Okay, if I go to my profile and try to play something, it won't play.

But, if I go to pandora.com and see that I'm already logged in, I can play from my stations.

Odd, but it works.

---

