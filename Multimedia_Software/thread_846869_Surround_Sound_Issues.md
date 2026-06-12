---
title: "Surround Sound Issues"
date: 2008-07-01
forum: Multimedia Software
---

### Post by Literati on 2008-07-01
Hi, I'm trying to get my Surround Sound 5.1 to work on my Ubuntu machine.
I have an SB Live 5.1 sound card, and have edited my .asoundrc to the following:

```
# ALSA library configuration file

#Include settings that are under the control of asoundconf(1).
(To disable these settings, comment out this line.)
</home/matt/.asoundrc.asoundconf>

# for 5.1 speakers
pcm.ch51dup {
         slave.pcm surround51
         slave.channels 6
         type route
         ttable.0.0 1
         ttable.1.1 1
         ttable.0.2 1
         ttable.1.3 1
         ttable.0.4 0.5
         ttable.1.4 0.5
         ttable.0.5 0.5
         ttable.1.5 0.5
}

# for 4.1 speakers
pcm.ch41dup {
         type route
         slave.pcm surround41
         slave.channels 5
         ttable.0.0 1
         ttable.1.1 1
         ttable.0.2 1
         ttable.1.3 1
         ttable.0.4 0.5
         ttable.1.4 0.5
}

```

I get playback absolutely fine, and identified correctly when using 

```
speaker-test -Dplug:surround51 -c6 -l1 -twav

```

But when I do that test Speaker "4" or "Center" doesn't play any sound (nor does it any other time on my computer) and Speaker "5" or "LFE" doesn't play any sound.

The rest work fine. :(

Also, when I play music back in Banshee-1, it plays from all four speakers, and the subwoofer, but I still get nothing from the center. 

How can I fix this? 
Thank you!

---

### Post by Literati on 2008-07-02
Anybody have any ideas whatsoever?

---

### Post by markbuntu on 2008-07-02
Which mixer are you using?

---

### Post by Literati on 2008-07-03
ALSA Mixer
The centers volume is up, I've checked...

---

### Post by Literati on 2008-07-03
Anyone? It's kind of a pain having the speaker sitting in front of me, but getting nothing from it :D

---

### Post by Literati on 2008-07-04
Effortlessly bumping.
Losing hope :D

---

### Post by Literati on 2008-07-05
/me *sighs*

:D

---

### Post by Literati on 2008-07-07
No one? :(

---

