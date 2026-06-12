---
title: "Simultaneous Audio Output"
date: 2011-12-18
forum: Multimedia Software
---

### Post by stumpalump on 2011-12-18
Just thought I would share this because I googled around for a long time before finally finding an answer.

This is for people who want to be able to output audio to multiple soundcards.

I use this because I have no center speaker hooked-up to my surround because I prefer to use the TV Speakers as center channel instead. So I have 5.1 signal going to the surround through coax and stereo to my TV through HDMI audio.

Install Pulseaudio preferences

```

sudo apt-get install paprefs

```

Run paprefs and there is a checkbox to enable simultaneous output to all local sound cards.

Once you do that simply select simultaneous output as default output in sound preferences. (I prefer pavucontrol on 11.10) From there you can set-up, in sound preferences, your speaker types to each device.

---

### Post by aeiah on 2011-12-19
god damnit i spent about 3 hours the other day messing with pacmd commands to do this :p ill keep this in mind next time

---

