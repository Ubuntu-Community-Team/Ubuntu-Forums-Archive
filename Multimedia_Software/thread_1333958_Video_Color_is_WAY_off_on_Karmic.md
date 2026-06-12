---
title: "Video Color is WAY off on Karmic"
date: 2009-11-21
forum: Multimedia Software
---

### Post by fiveacez on 2009-11-21
Just dual-booted Karmic on my computer, and  red colors aren't showing up at all when I watch a video on Totem or VLC.

For example: when I'm watching an epsisode of Firefly or watching some other movie, the people are blue.

Does anybody know what is going on?

---

### Post by fiveacez on 2009-11-22
Oh, never mind.  Different topic solved issue.

---

### Post by TygerFish on 2009-11-23
> **fiveacez said:**
> Oh, never mind.  Different topic solved issue.

Can you post a link so other people can find the solution easily?

---

### Post by BelzeBob on 2009-11-25
Hi

Yes. I was really satisfied, as I had become able to play virtually any file in Ubuntu. Even "difficult" audio and video formats. But yesterday "everything turned blue". People's faces are blue. What to do?

...If this has been answered elsewhere - please be so kind and show me the way.

:) Thanx.

B

---

### Post by pleur on 2009-11-25
I had this same problem. I found that in the Totem-preferences the "hue" was turned all the way down.

Solution? Open your totem-player, navigate to "Edit > preferences" and then the "display"-tab. Press "reset to defaults". 

This solved the problem for me

---

### Post by BelzeBob on 2009-11-25
Didn't solve it for me.

---

### Post by TygerFish on 2009-11-29
> **pleur said:**
> I had this same problem. I found that in the Totem-preferences the "hue" was turned all the way down.

Solution? Open your totem-player, navigate to "Edit > preferences" and then the "display"-tab. Press "reset to defaults". 

This solved the problem for me

This fixed it for me.

---

### Post by BelzeBob on 2009-11-29
Ah yes - turning the "hue" down worked. Thanks folks!

---

### Post by will177 on 2010-01-27
It seems that when you play Totem/Movie player on a video it screws with the hue, so when afterwards your try VLC say, the hue is still blue.

Anyway, mine cleared up after going into nvidia settings, but came back when I next used totem, so I had to run totem and correct the hue in there (slider) as it was on 0 instead of a central position.

Totem -> Edit -> Preferences -> Display (Tab)

Align the Hue slider with the others :)

Hue is correct now and is staying correct.

---

### Post by Nick_Jinn on 2010-06-25
> **will177 said:**
> It seems that when you play Totem/Movie player on a video it screws with the hue, so when afterwards your try VLC say, the hue is still blue.

Anyway, mine cleared up after going into nvidia settings, but came back when I next used totem, so I had to run totem and correct the hue in there (slider) as it was on 0 instead of a central position.

Totem -> Edit -> Preferences -> Display (Tab)

Align the Hue slider with the others :)

Hue is correct now and is staying correct.


For me this worked for everything but VLC media player.

---

### Post by EpicMe on 2011-02-05
This thread helped, I reset the defaults on the video player and the color is fixed. Thanks so much!

---

