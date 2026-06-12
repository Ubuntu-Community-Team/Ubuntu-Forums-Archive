---
title: "PreSonus FireStudio Project firewire: how to get stereo output via Jack + PulseAudio"
date: 2013-07-31
forum: Multimedia Software
---

### Post by Ubutuxer on 2013-07-31
I have the PreSonus FireStudio Project firewire sound card working well with PulseAudio via Jack & QjackCtl, but it only outputs mono. After some weeks of going through every setting I still can't figure how to change it to stereo. Any ideas?

---

### Post by gordintoronto on 2013-07-31
It's possible that telling people the exact version of Linux you are using might help them to help you.

It only outputs mono to what? The computer, or headphones plugged into the device? What is your sound source?

---

### Post by Ubutuxer on 2013-07-31
> **gordintoronto said:**
> It's possible that telling people the exact version of Linux you are using might help them to help you.

It only outputs mono to what? The computer, or headphones plugged into the device? What is your sound source?

Ahh... yeah the Ubuntu version is 13.04. And the 64-bit x86 version, with latest updates installed. Sorry for forgetting to mention that, although it's not very important in this particular case. Because if you're familiar with the PreSonus studio sound cards, they always output mono by default (to speakers, to headphones, to everywhere). Whether you use Linux, OS X or Windows. In OS X and Windows you join the 2 (L and R) channels together from the mixer. I've yet to find such an option in the mixers on Linux side but I guess it's somewhere.

So it's not really that it wasn't already working correctly on Linux, I just need to find that mixer setting to join the left and right channels together. And the sound source is, as mentioned, PulseAudio & Jack & QjackCtl, with any application... browsers, video players, audio players, etc.

If someone is using this audio interface on Linux and has found the setting in question I'd be very grateful. :)

---

### Post by frederic.philip on 2014-05-15
Hello Ubutuxer

Have you found a solution to your problem? I found myself in the same situation yesterday (I use Tango Studio) and couldn't manage to get a stereo output (main or headphones).

I use Jack as well (with Qtractor) but can't find a way to make the stereo output work. To me this seems like something that ffado should manage through a mixer but is not able to, due to the fact that the firestudio mobile is not perfectly supported.

Thanks in advance if you have an update on this.
Fred

---

