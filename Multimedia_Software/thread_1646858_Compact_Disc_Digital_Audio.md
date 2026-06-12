---
title: "Compact Disc Digital Audio"
date: 2010-12-16
forum: Multimedia Software
---

### Post by twinaxel on 2010-12-16
Hi   I have been trying to burn  a music CD for my  old Denon HI FI tried most of the 
 burners looked for codecs nothing seems to work or play!

 I had no problems with Nero on XP.

---

### Post by ajgreeny on 2010-12-16
How exactly are you trying to do this?

If you can play the music files, you should already have the codecs needed to burn them to audio CD, simply by dragging the mp3, ogg, wav, flac, etc etc files to the burner window after choosing Audio CD from the start menu of the burner, either brasero or k3b, though I seem to remember k3b needs an extra library file of some sort to play the restricted packages, **libk3b6-extracodecs**.  However, I thought that was installed automatically with k3b.

Are you getting error messages of some kind?  If so what are they?

---

### Post by twinaxel on 2010-12-16
Hi thanks for the reply. 
 Yes I have dragged the files to the burner after choosing Audio CD have tried K3b and & Brasero.
 Not getting any error messages.                                            

 Tried Reading package lists... Done
 Building dependency tree       
 Reading state information... Done
 E: Couldn't find package libk3b2-mp3

---

### Post by ajgreeny on 2010-12-16
What version of ubuntu are you using?  Libk3b2-mp3 is not used on recent ubuntu versions.

---

### Post by twinaxel on 2010-12-17
> **ajgreeny said:**
> What version of ubuntu are you using?  Libk3b2-mp3 is not used on recent ubuntu versions.
 

Lucid 10.04

---

### Post by ajgreeny on 2010-12-17
That libk3b2-mp3 package is for an older version of k3b than the lucid version, so I am a bit befuddled why you even need it.  It is not even in the lucid repositories.

---

### Post by Yellow Pasque on 2010-12-17
So they burn but don't play in your player? It could be that your player doesn't like certain types of CD-R's. Make sure you don't burn any CD-Text or extra information to the disc, as that might confuse players made before the invention of CD-Text (though it shouldn't in theory). I would also try to burn at a lower speed and verify the burn.

---

### Post by twinaxel on 2010-12-20
> **Temüjin said:**
> So they burn but don't play in your player? It could be that your player doesn't like certain types of CD-R's. Make sure you don't burn any CD-Text or extra information to the disc, as that might confuse players made before the invention of CD-Text (though it shouldn't in theory). I would also try to burn at a lower speed and verify the burn.


Hi Temüjin you are correct it was the CD-Rs bought a different brand burns and sounds perfect.

---

