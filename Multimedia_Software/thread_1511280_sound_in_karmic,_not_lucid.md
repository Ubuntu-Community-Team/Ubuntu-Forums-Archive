---
title: "sound in karmic, not lucid?"
date: 2010-06-16
forum: Multimedia Software
---

### Post by chitowner2 on 2010-06-16
OK folks, here's a real stumper for ya.

I have a recent lucid install with kde-desktop added post-hoc. I can not find any way to get sound to work in lucid, but if i grub-boot into my old karmic, or boot from an ISO, sound is OK. (external speakers)

I suspect some *.rc file or similar in /home is the root of the problem, but after a fair amount of fruitless rummaging, have decided to ask for outside help.  :-)

Thanks, 
CT

---

### Post by lidex on 2010-06-17
Do you have kmix installed? You might try configuring with that.

---

### Post by chitowner2 on 2010-06-17
Got it figured out with some help from here:
[http://kubuntuguide.org/Lucid#How_to_determine_which_version_of_Kubuntu_you.27re_using](http://kubuntuguide.org/Lucid#How_to_determine_which_version_of_Kubuntu_you.27re_using)

Turns out I had to configure pulseaudio stuff beyond what the base-install has tools for.

GENERAL NOTE: THE ABOVE LINK HAS A HUGE AMOUNT OF HELPFUL STUFF IN IT, AND IT WORKS!


CT

---

### Post by chitowner2 on 2010-06-22
Oh dang....
Shot myself in the foot!

I installed Audacity to be able to chop out segments of audio files for ring tones, but it apparently can not use pulseaudio, so I tried to remedy that with instructions I found here:

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

Result?

No sound again. 

Now I'm really confused. apart from writing a new file "asound.conf, it seems most of the instructions are similar to what I did from the previous page: 
[http://kubuntuguide.org/Lucid#Sound](http://kubuntuguide.org/Lucid#Sound)

Any multimedia gurus out there?

Thanks, 
CT

---

