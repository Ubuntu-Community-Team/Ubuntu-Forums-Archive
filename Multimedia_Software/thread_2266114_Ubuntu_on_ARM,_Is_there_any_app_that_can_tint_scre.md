---
title: "Ubuntu on ARM, Is there any app that can tint screen during video playback?"
date: 2015-02-19
forum: Multimedia Software
---

### Post by ultragamer2 on 2015-02-19
I ordered an Odroid C1 (an arm cpu device) which runs Ubuntu using Kodi with hardware accelerated graphics to play videos.

I want to be able to tint the screen while watching videos, kodi can't due this, but is there a program I can run in Ubuntu to tint the entire screen for everything all at once?

---

### Post by papibe on 2015-02-19
Hi ultragamer2.

'tint' as in general management of color? or are you looking for reducing the blue light?

Regards.

---

### Post by ultragamer2 on 2015-02-19
I would like to colourise/tint the whole screen a certain colour (including hardware accelerated video).

Since Kodi can't do it.

So yes reducing blue light would achieve the effect but I would probably want to boost the red and green slightly so I'm not making the screen darker overall.

---

### Post by tgalati4 on 2015-02-20
*mplayer* has some color correction:

>     c      Change YUV colorspace.

       (The  following  keys  are  valid  only  when  using a video output that supports the corresponding adjustment, the software equalizer (--vf=eq or
       --vf=eq2) or hue filter (--vf=hue).)

       1 and 2
              Adjust contrast.

       3 and 4
              Adjust brightness.

       5 and 6
              Adjust hue.

       7 and 8
              Adjust saturation.


Don't know of a way to do it for the entire desktop.

---

### Post by ultragamer2 on 2015-02-20
Ok thanks, unfortunately that won't work since I cant adjust hue when there is no colour.

So you know how colours on the screen are made up a red green and blue.

Is there a way I can boost the red and the green but turn down the blue for example?

---

### Post by papibe on 2015-02-23
'redshift' does that.

It is not a general tint/color management application. It's purpose is completely different.

Having said that, it reduces blue color, and it may help you.

Since by default the tint varies during the day, you would have to play with the options and the config file. The -o option (One shot mode ) should be helpful.

Let us know if that helps.
Regards,

---

