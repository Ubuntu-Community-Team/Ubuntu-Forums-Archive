---
title: "How to adjust audio ?"
date: 2019-02-21
forum: Multimedia Software
---

### Post by bitsnpcs on 2019-02-21
Hello,

I want to adjust the audio sound of playback, the bass is overwhelming the lyrics of songs, the speakers and headphones are working correctly.
In the audio settings it only has volume control, do I need to install a software to do this ?
If so can you recommend a basic software ?

---

### Post by ajgreeny on 2019-02-21
See if **pulseaudio-equalizer** helps; it's in the repos, though I've never needed to use it so can't vouch for how good or bad it is.

---

### Post by bitsnpcs on 2019-02-21
Thank you for your help.
I have just tried to install pulseaudio-equalizer, from Ubuntu Software it gives an error and turns off the extension, it says it needs pulseaudio installed, I installed pulseaudio and this also gave an error and turned itself off in the extensions. So I have removed both.
Are there any other ones to try ?

I have found a way to fix this.
In the terminal I typed **alsamixer ** this brought a EQ up in the terminal, I used the left and right arrows of keyboard to move between the choices, and the up and down arrows to adjust each. 
It seemed the one named Master, was what I needed to reduce, and also the surround (I use headphones for music).

---

