---
title: "Surround sound emulation?"
date: 2007-07-13
forum: Multimedia &amp; Video
---

### Post by rmco2003 on 2007-07-13
I was wondering if there was any way of getting Totem or Ubuntu in general to spread audio out amongst my speakers? Currently only the front left and front right speakers are being used, so there's three that are going unused, which is my only problem. I know I can get speakers that can do this through hardware but I'll have to get those when I get some money.

I've got an SB Live 24-bit, which is working perfectly normally, just wondering if there was a plugin or some software that could do this for me.

Thanks.

---

### Post by linuxwizard on 2007-07-13
Try some of these suggestion and see if they will help. Make sure and check volume manager setting and check the plugins to your jacks.

[http://ubuntuforums.org/showthread.php?t=472306](http://ubuntuforums.org/showthread.php?t=472306)

---

### Post by rmco2003 on 2007-07-14
I've tried the test in the terminal:
speaker-test -Dplug:surround51 -c6 -l1 -twav

And it worked fine out of all speakers, so it looks like it works in ALSA, however the Totem player ignores the fact that I have surround sound speakers, and still only plays out of two. I've set the speakers option in the Totem Preferences to 5.1 Speakers, so I'm not sure what else I have to do.

It said in the wiki about having to create custom routing ttables for different codecs, how would I go about doing this?

[edit] I've also tried aplay from the terminal and Rhythmbox and they both ignore the other speakers, in fact the other channels in the 5.1 wave files I tried are completely ignored, they don't play at all.

---

