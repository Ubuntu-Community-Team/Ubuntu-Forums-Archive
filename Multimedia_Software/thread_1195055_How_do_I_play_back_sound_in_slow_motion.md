---
title: "How do I play back sound in slow motion?"
date: 2009-06-23
forum: Multimedia Software
---

### Post by KingNeil on 2009-06-23
I want to playback an mp3 file in slow motion. Is there any way or program to do this?

---

### Post by starcraft.man on 2009-06-23
> **KingNeil said:**
> I want to playback an mp3 file in slow motion. Is there any way or program to do this?

Open MP3 with VLC. Then push the << or >> on the sides of the main track bar. You can slow it down or speed it up to ridiculous speed. Hope that helps, VLC is easily installed from the repos. Go to Add/Remove in Applications, then select all applications to show and search for VLC. Simply install after that.

---

### Post by KingNeil on 2009-06-23
> **starcraft.man said:**
> Open MP3 with VLC. Then push the << or >> on the sides of the main track bar. You can slow it down or speed it up to ridiculous speed. Hope that helps, VLC is easily installed from the repos. Go to Add/Remove in Applications, then select all applications to show and search for VLC. Simply install after that.

Thank you very much.

---

### Post by KingNeil on 2009-06-23
I must say though: it doesn't work very well.

---

### Post by raboofje on 2009-06-23
Do you want to slow the mp3 down with or without affecting pitch?

Do you want to do this in 'real time', or do you want to convert an mp3 to another speed and then play it like normal? For the latter, audacity and rubberband are probably nice choices.

---

### Post by KingNeil on 2009-06-23
> **raboofje said:**
> Do you want to slow the mp3 down with or without affecting pitch?

Do you want to do this in 'real time', or do you want to convert an mp3 to another speed and then play it like normal? For the latter, audacity and rubberband are probably nice choices.

I don't want the affected pitch. I want it to sound normal, but just slower. If you can do that in Audacity, I'll have a look.

---

### Post by raboofje on 2009-06-23
> **KingNeil said:**
> I don't want the affected pitch. I want it to sound normal, but just slower.

OK. That requires resampling, which means there will be some quality loss.

> If you can do that in Audacity, I'll have a look.

The 'change tempo' effect should do just that - it was missing from hardy, but should be back since intrepid ( [https://bugs.launchpad.net/ubuntu/+source/audacity/+bug/193593](https://bugs.launchpad.net/ubuntu/+source/audacity/+bug/193593) ).

---

### Post by KingNeil on 2009-06-23
OK, thanks. "Change tempo" works just fine in Audacity. Thanks for you help.

---

