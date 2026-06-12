---
title: "Firefox soundcard problem"
date: 2008-06-10
forum: Multimedia Software
---

### Post by rubyman on 2008-06-10
Hi all
I have 2 soundcards in my pc, a good one and a not so good one :), both are detected just fine. I can playback the sound tests in the sound panel in gnome. I am using banshee to play back my mp3s and it works just fine with my good quality soundcard. However, when I browse the internet Firefox is using the other soundcard in the computer to play back youtube and other content. The gnome sound panel is configured to implicitly use the good soundcard. How can I change firefox so that is will use the good soundcard. I dont want to have to take out the other soundcard because i use it for other apps in XP.
Can anyone help
Thanks in advance
Steve

---

### Post by zbrox on 2008-06-10
If you're using Hardy the default sound server is PulseAudio which has some nice tools to determine which sound stream goes through where. I'm guessing here, cause I haven't done it myself. But you can set Firefox to use only one of the cards and even determine the wholesome volume of its stream.

I think this can be done through "pavucontrol" (the audio control program of PulseAudio).

---

### Post by rubyman on 2008-06-10
I cant get the sound to work with pulse audio at all. I had to tell it which sound card to use in the gnome sound config panel. It works fine for banshee, but firefox is using the old soundcard.

---

