---
title: "no sound in rythmbox"
date: 2007-11-08
forum: Multimedia &amp; Video
---

### Post by RockTonic3 on 2007-11-08
suddenly i have no sound in rythmbox...  I'm not sure what happened and have no clue where to start looking, i've never had problems with sound before.  so far i've also noticed there's no sound when i log on to ubuntu, and no sound in embeded java video (but there is when mplayer is playing the video).

any ideas?

---

### Post by RockTonic3 on 2007-11-10
bump 

:(

---

### Post by csisgro on 2007-11-10
You need to turn on the sound daemon in System->Preferences->Sound
Under the sounds tab enable the sound daemon. Rythmbox seems to only play through the sound daemon.

---

### Post by caricc on 2007-11-10
I have had this same problem with rhythmbox. Now it's working.  I had gone into system-preferences-sound. I had set my default mixer tracks to the oss mixer. then I set all of the other settings to the oss open sound system. I finely got sound, after rebooting rhythmbox now works.

My system is a compaq presario v2000 laptop. 

After reading this post I started to play with the different setting. Yes, I have the intel  82801db-ich4 chipset in this laptop. but I kept getting error messages with testing, so I kept test until I didn't. Yes, I did get the testing window and not an error msg with the intel but, no sound. So I changed to the oss. Now I have sound. :guitar:

---

### Post by RockTonic3 on 2007-11-13
> You need to turn on the sound daemon in System->Preferences->Sound
Under the sounds tab enable the sound daemon. Rythmbox seems to only play through the sound daemon.

there is nothing in there about a sound daemon?  maybe i'm not sure what you mean.  the only options are 'enable software sound mixing (ESD)' and 'Play system sounds' which are both enabled.  

Trying to mess around with the available devices doesn't work either, if i change anything to anything other than autodetect, i get the following error message when trying to test:

```

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Resource busy or not available.
```

And here's the strange thing, a day or two ago I was playing around in there, and I was getting the same error messages but for whatever reason, the sound spontaneously started working again, even though I set everything back to the default settings...  nothing was working, then all of a sudden it decided to give me sound when I clicked test.  


So, needless to say, the sound once again decided to stop working for no apparent reason.

talk about buggy.  i think i'm having more issues with gutsy than i've had with any of the previous releases!

---

### Post by boast on 2007-12-09
I am also getting that error
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Resource busy or not available.
```


ubuntu/linux is great.

---

