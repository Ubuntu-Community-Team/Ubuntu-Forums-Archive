---
title: "How to set 7.1 sound card to work in 5.1 mode"
date: 2008-08-09
forum: Multimedia Software
---

### Post by gutko on 2008-08-09
Hello,
I have Asus xonar dx card and after upgrafing alsa to 1.0.17 in hardy i have it working in 7.1 mode but i have 5.1 speakers. How can I set it to mix in 5.1? Is it something in /proc dir?

---

### Post by ProbablyX on 2008-08-09
Isn't it just to turn down the volume of the non-used spekers in alsamixer? Applications that use non-stereo, such as 7.1 or 5.1, sound usually have their own setting on what to output. Games especially have this setting.

When you play music, the output is the same on the rear and front speakers. It's just upmixed, so not having the rear ones plugged in doesnt make you miss anything.

I only have 2.1 speakers on my Audigy 4 card without any ALSA settings or system settings. Works fine.

---

### Post by gutko on 2008-08-09
ok so the real core of the problem is i cant get world of warcraft soud exactky the same eay it sound on windows xp. baisicly the rear speaklers are dead and i can hear only stereo from center and both front. but in windowz the sound soround me, when fire is behind be i can hear crakcling behind me. I cant beleieve linux/wine cant do it...:( any1 tried to set it all up properly?

---

### Post by markbuntu on 2008-08-09
Edit the file
/etc/pulse/daemon.conf

find the line:
default-sample-channels=2

change it to 6 for 5.1 surround

---

### Post by gutko on 2008-08-09
It didnt work. I just removed pulse completly. Problem seems to be somewhere in wow/wine/alsa. Volume control applet shows 8 channels. I was looking for some options for snd-virtuoso module and poking in /proc/asound - no clue

---

### Post by markbuntu on 2008-08-09
Yes, I know wine has some issues with pulseaudio. You can try running wine with aoss so it uses the alsa wrapper. That might work. I don't use wine myself so cannot be sure.

---

