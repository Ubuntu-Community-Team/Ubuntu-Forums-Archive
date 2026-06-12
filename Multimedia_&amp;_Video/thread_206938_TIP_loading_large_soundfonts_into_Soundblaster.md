---
title: "TIP loading large soundfonts into Soundblaster"
date: 2006-06-30
forum: Multimedia &amp; Video
---

### Post by Sheik Yerbouti on 2006-06-30
Ever try to load a really large sound font like titanic into a Soundblaster card and then find out it didn't really load right. Here's an option you can add to /etc/modprobe.d/alsa-base to define how much buffer to allow the Soundblaster to use by default I believe it is 128MB. You actually have to have the memory available of course just typing in a number won't make it so ;) 

```
options snd-emu10k1 max_buffer_size=512
``` 

this would of course be for 512MB max buffer.

It won't set aside 512MB it's just a max. One thing I am curious about and someone may know the answer the Soundblasters have more than one synth at least two I know from Windows alsa actually reports four synths! Anyway anyone know what the syntax is for asfxload to load a font into the second synth? The asfxload man page says something about the -D option and hwdep=name specifying a device anyone know how to get the hwdep names of the synths? Or what that might look like syntax wise?

---

### Post by Sheik Yerbouti on 2006-07-02
Just an update on this one multiple soundfonts does not work at least not with asfxload 5.0c or d the correct syntax would be.

asfxload -b2 somefile.sf2

-b2 meaning bank 2 but apparantly for some reason that along with most of the other switches listed in the man page where removed from the code. Beware the asfxload man page is full of all sorts of lies. you will mostly get stuff like this. 

the following should load the font into bank 2 with a chorus value of 20 and a reverb value of 50 according to the man page.

asfxload -b2 -c20 -r50 Soundfonts/PC51d.sf2
asfxload: invalid option -- b
asfxload: invalid option -- 2
asfxload: invalid option -- c
asfxload: invalid option -- 2
asfxload: invalid option -- 0
asfxload: invalid option -- r
asfxload: invalid option -- 5
asfxload: invalid option -- 0

So beware. Of course you can just load fluidsynth-dssi or qsynth or fluidsynth and load multiple fonts that way so it's all good. I was really just curious about this.

---

### Post by BobSongs on 2006-07-04
Thanks, Sheik, on the SoundFont tip. Coming over from the Windows world I wondered if Linux offered an application that allowed for SoundFonts to work like they do in Windows. I've done some midi programming with an elaborate set of SoundFonts in Windows and never dreamed I'd be able to replicate them in Linux. So any tips help.

Thanks.

---

### Post by BobSongs on 2006-07-04
If I used a largish SoundFont (blah.sf2) and wanted to replace the classical guitar from within that font with another font (classicalguitar.sf2) like I can in Windows... any clue as to how?

---

### Post by dolson on 2006-07-06
Have you tried Smurf?

---

### Post by BobSongs on 2006-07-07
Uhm... not really. I guess I'll have to look into it and see what they offer. Thanks for the lead.

---

### Post by Sheik Yerbouti on 2006-07-09
It is actually called swami now and here is the project page [http://swami.sourceforge.net/](http://swami.sourceforge.net/). It is a sound font editor much like vienna on Windows. In fact I just created my first sound font ever with it last weekend. It's a soundfont containing some samples from a really old cheesy beatbox called the Korg Minipops 35 from the 70s. I need to give it once over to make sure it's GM compatible but once I do I will post it on my website and throw up a link here.

Cheers

---

### Post by dolson on 2006-07-10
Ah yeah, that's what I meant. I don't use it myself, and I forgot which was the newer name. :)

---

