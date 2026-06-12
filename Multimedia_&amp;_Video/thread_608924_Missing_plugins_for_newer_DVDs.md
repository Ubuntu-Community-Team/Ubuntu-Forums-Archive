---
title: "Missing plugins for newer DVDs"
date: 2007-11-10
forum: Multimedia &amp; Video
---

### Post by geovino on 2007-11-10
I have installed Gutsy and have the codecs to play music and DVDs for most movies but this morning I have bought a copy of Disney's Ratatouille DVD. I tried to play it in totem and kaffeine and both said that I was missing plugins, but it didn't say which plugins.  I have another PC that has Mint 3.1 installed and I was able to play the DVD in Mint. What plugins does Mint have that Ubuntu doesn't have?

---

### Post by JawsThemeSwimming428 on 2007-11-10
Try VLC if you have all of the GStreamer plugins installed.

---

### Post by geovino on 2007-11-10
I tried it with VLC and I got it to work after a little playing around, but it doesn't just start when you put the DVD in. 

What are all the files needed to play DVDs on totem or kaffeine?

---

### Post by suspend on 2007-11-10
I have been having the same problem.  Similar, yet a little worse.  I am running G. Gibbon with the GStreamer plugins and VLC; I have also tried Mplayer ant Totem.  Only my home made DVDs will run.  None of my bought DVDs will run.  I have tried a few Disney, Pokemon, et.  and no luck, yet.  I happen to have those handy do to my daughter having her case nearby.  

DVD have played for me in the past under PCLinuxOS with no issues.  Any suggestions?  Should I remove Totem and MPlayer and just try to use VLC with the GStreamers in a "clean" environment.  Any assistance will be GREATLY appreciated.

Thanks!

---

### Post by suspend on 2007-11-10
> **geovino said:**
> I tried it with VLC and I got it to work after a little playing around, but it doesn't just start when you put the DVD in. 

What are all the files needed to play DVDs on totem or kaffeine?

What "playing" did you have to do to get the films to work?  I've run them from the File/Open DVD menu before on other distros, I get nothing when I try it in Gutsy, no error or anything.

---

### Post by geovino on 2007-11-10
In VLC I went to > File > Open Disc > and there select DVD (menus) or DVD and hit open and see what happens. I got the Disney DVD to work that way.

---

### Post by disturbedite on 2007-11-10
i think you guys *might* have it all wrong.  the "Missing Plugin(s)" message doesn't mean what it sounds like, exactly...
it prolly means that the library to decrypt copy protected dvds (like libdvdcss2) that you need to actually play those dvds doesn't support the newer copy protection schemes that newer dvds use.

---

### Post by Rog-Mahal on 2007-11-11
So there is a new encryption scheme for new dvds? I'm having an awful time getting them to run in gutsy 64bit

---

### Post by geovino on 2007-11-11
> **disturbedite said:**
> i think you guys *might* have it all wrong.  the "Missing Plugin(s)" message doesn't mean what it sounds like, exactly...
it prolly means that the library to decrypt copy protected dvds (like libdvdcss2) that you need to actually play those dvds doesn't support the newer copy protection schemes that newer dvds use.

But that new Disney DVD plays just fine in Mint 3.1. What does Mint have that Ubuntu does not?

---

### Post by williammanda on 2007-11-11
I agree with geovino... what is the difference? If it works with mint...it should work with gutsy 7.10! I have several computers with 7.10 and a laptop that doesn't play dvds. I can't seem to get that one to work even though it has the same files as the others.
Thanks

---

### Post by mc4man on 2007-11-11
Considering that video playback is randomly unreliable in gutsy it doesn't surprise me that some titles play, others don't or today you have video and tomorrow a pink/green screen. I've had video playback break (green screen) 5 times since rc1. I'm trying something new but it's too early to say if it will hold. That being said as far as some newer dvds you might want to try installing ubuntu restricted extras - they're in add/remove - set it for all available applications and search for ubuntu restricted extras

---

### Post by disturbedite on 2007-11-11
its entirely possible that mint linux has a newer libdvdcss2 package that does support newer encryption schemes (copy protection/drm) or some other library that decrypts dvds...

---

