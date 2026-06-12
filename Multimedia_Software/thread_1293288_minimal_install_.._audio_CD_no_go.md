---
title: "minimal install .. audio CD no go"
date: 2009-10-16
forum: Multimedia Software
---

### Post by renkinjutsu on 2009-10-16
i have rhythmbox and Totem installed, but Audio CD's won't open/play~ i have tried mounting the CD but it throws back with an error message about incorrect filesystem.. i've tried with iso9660 and udf and it doesn't work.

i'm able to rip the CD's with asunder though, i just can't play the audio CD.. is there something other than rhythmbox that needs to be installed?

---

### Post by oboedad55 on 2009-10-16
> **renkinjutsu said:**
> i have rhythmbox and Totem installed, but Audio CD's won't open/play~ i have tried mounting the CD but it throws back with an error message about incorrect filesystem.. i've tried with iso9660 and udf and it doesn't work.

i'm able to rip the CD's with asunder though, i just can't play the audio CD.. is there something other than rhythmbox that needs to be installed?

Which version of Ubuntu are you running?

---

### Post by renkinjutsu on 2009-10-16
Karmic, but it was present in my Jaunty minimum install also... i haven't figured out what else i have to install...

---

### Post by aaronluis26 on 2009-11-06
I am also having this issue in Karmic. I searched around and found that some people had this issue in previous versions Ubuntu and someone recommended that doing a fresh install would fix the issue. I did a fresh install of Karmic this morning and the issue still exists. I'm not really sure what's wrong. I can mount a data CD and it works fine, but when I put in an audio CD, nothing happens. I'll probably just go back to Jaunty until this problem is fixed.

Edit: renkinjutsu, I may found have found a work around for this. I am not sure how to fix the issue per say, but try installing Banshee and using that to listen to audio CDs. I am able to still listen to audio CDs using Banshee despite it not showing up in Rhythmbox. When you are done listening to the CD, you can just right click the disc in the left panel of Banshee and hit eject CD. The reason why that's important is because I also tried using Exaile and while Exaile allowed me to listen to an audio CD, I was unable to eject the CD manually even after I disconnected it from the Exaile menu. The only way to eject the CD was to exit out of Exaile. You could also try out other media players to see if playing audio CDs is possible with this issue present, but I highly recommend Banshee :)

---

### Post by renkinjutsu on 2009-11-06
thanks for recommending banshee, but i already decided i would rip all the songs from my CD's and store them on my harddrive anyway, and ripping the songs work! But it's nice to know banshee can play CD's

---

### Post by wojox on 2009-11-06
I installed karmic mini.iso. Rhythmbox works for playing Cd's. Have you installed:

```
sudo apt-get install ubuntu-restricted-extras
```

Also [Medibuntu]("https://help.ubuntu.com/community/Medibuntu-test")

---

### Post by aaronluis26 on 2009-11-07
> **renkinjutsu said:**
> thanks for recommending banshee, but i already decided i would rip all the songs from my CD's and store them on my harddrive anyway, and ripping the songs work! But it's nice to know banshee can play CD's
You're welcome! That's a great idea. I might do the same for some of those CDs I was trying to play.

> **wojox said:**
> I installed karmic mini.iso. Rhythmbox works for playing Cd's. Have you installed:

```
sudo apt-get install ubuntu-restricted-extras
```Also [Medibuntu]("https://help.ubuntu.com/community/Medibuntu-test")
Well, the issue is not really with Rhythmbox and whether it plays CDs. The issue is that Ubuntu is not, for lack of better words, "mounting" audio CDs correctly and placing an icon for it on the desktop, so Rhythmbox doesn't recognize that a disc has been placed in a CD or DVD drive and you are unable to play it. For whatever reason, some players, like Banshee and Exaile, still recognize that a disc has been placed in the drive and allows for playback.

---

