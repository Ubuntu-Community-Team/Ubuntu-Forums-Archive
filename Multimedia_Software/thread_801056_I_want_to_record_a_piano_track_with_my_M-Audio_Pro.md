---
title: "I want to record a piano track with my M-Audio ProKeys 88..."
date: 2008-05-20
forum: Multimedia Software
---

### Post by thekylehome@gmail.com on 2008-05-20
Okay so the subject line pretty much describes what I want to do... I want to record a piano track with my M-Audio ProKeys 88 keyboard... It plugs into the computer via USB. What are the best audio recording applications? I want this track to sound at least somewhat like a piano, so no "junk" apps. that make my stuff sound really "cheep!" What does everyone recommend? And how do I set it up?
I hope I came across clear enough, but if you don't understand something feel free to ask...
Thanks for the help!

---

### Post by Stochastic on 2008-05-20
First, you should post issues like this in the Multimedia Production section of the forums.

Second, you should check out Qsynth and download a good soundfont for it (it doesn't make any sound until a soundfont is loaded into it).

Third you'll probably want to have Jack up and running to do this.  QJackCtl provides a nice gui for that.

Fourth to record the output of Qsynth, open any wave editor (Rezound is my choice, but Audacity or even Ardour would work), connect the output of Qsynth into the editor via QJackCtl's connections window, click record then play away.

Fifth, if you're looking to spend some money and want things to sound real nice, give this thread a read-through: [http://ubuntuforums.org/showthread.php?t=781105](http://ubuntuforums.org/showthread.php?t=781105) the plugin they're talking about is the best piano emulation software I've ever heard.

---

### Post by thekylehome@gmail.com on 2008-05-20
Wow! Okay thank you! This really helped me out...

---

