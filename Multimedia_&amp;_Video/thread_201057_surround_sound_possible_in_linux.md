---
title: "surround sound possible in linux?"
date: 2006-06-21
forum: Multimedia &amp; Video
---

### Post by Vlatko on 2006-06-21
well few days ago i have installed kubuntu breezy, while waiting for the dapper to arrive from shipit. anyway i really like it so far, mainly thanks to automatix which is a utility godsend to complete newbies like me.

there is one thing that is troubling me. surround sound. i have some pretty good 5.1 speakers which work like a charm in windows. however in linux they don't. i have the old creative live 5.1 pci-card which works well in windows and i'm pleased with it. however linux doesn't seem to like it as much. **fiddling about in k-mix i managed to get all 6 speakers to work but from what i noticed i don't get surround, i get the same sound from all 6 speakers!! defintely not what i had in mind....**

anyway since i like linux so much i have even decided to go out on a limb and even buy a new sound card. my budget is limited but i can get lets say the Creative Audigy 4, 7.1 surround, hardware accelerated, for a pretty reasonable price.

**my question is; if i buy a new card, lets say the audigy 4, will i be able to get surround?** that is something really important to me and if i can't have that, things to do in linux are really limited for me, since i'm listening to music 90% of the time. **is the problem in my old card or is linux simply not able to re-produce surround sound properly?**

thanks! :)

---

### Post by george_apan on 2006-06-21
What are you listening to? If it is music which is usually only stereo it's prefectly normal to hear the same thing on surround channels. If you have a DVD movie with a 6-channel AC3 soundtrack then you should be getting different signal on your surround speakers.

What are you using for sound reproduction? Alsa, OSS?

I have a Terratec USB Aureon MkII soundcard and surround speakers work fine. I needed to tweak alsa a bit but no big deal. So yes, it is possible to have surround sound in Linux. And I don't think that you should get a new soundcard anyway.

---

### Post by Vlatko on 2006-06-21
first i tried to play mp3's and got only front speakers working. i know that is normal as mp3 is stereo and has only two channels. however i like it better when all 6 channels are playing, i know it's not surround but it sounds good in windows, at least to me. in linux with fiddling in kmix i managed to get sound from all speakers but as i said, every speaker played the same sound, whereas in windows it wasn't like that. it was surround emulation and it sounded good.

then i tried and play a dvd(revenge of the sith) which is encoded with surround sound but got the same problem as well. all channelrs reproduce the same sound, no surround at all. i don't know what to do.

i use alsa as those are the drivers automatix installed for me.

---

### Post by george_apan on 2006-06-21
What is your .asoundrc file like? It should be in your home directory. If it isn't create it and put the following in it: ```
  pcm.emu10k1 {
           type hw
           card 0
        }

        ctl.emu10k1 {
           type hw
           card 0
        }
```
I don't know if it will fix anything, I found it at the relative [alsa page]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+5.1.&chip=emu10k1&module=emu10k1").

---

### Post by Vlatko on 2006-06-21
i'll have to get back to you on that. am at work now and only windoze here. ;)

---

### Post by Vlatko on 2006-06-21
well i don't have that file but after installing xine and using it as engine i can watch dvd's in kaffeine with goog surround sound. mp3's still reproduce same sound out of every channel though.

i don't know why but i every time i start kaffeine, the volume on "wave lfe" in k-mix always goes down and i have to manually turn it up again. if i don't my subwoofer stays mute.

---

### Post by george_apan on 2006-06-21
I don't think that you can achieve what you want with mp3s. I'm sure it was some software thing by creative that created the effect you want. Maybe you could try some output plugins like stereo expansion or whatever...

And sorry I can't help you with your k-mix issues, I don't know anything about it.

---

