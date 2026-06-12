---
title: "Poor sound quality with Ubuntu"
date: 2011-07-16
forum: Multimedia Software
---

### Post by Mellifluous on 2011-07-16
I've just managed to install the latest Ubuntu version with Wubi on my nearly 4 year old Dell Inspiron laptop. I've got everything working great, even the wireless (after a struggle). Unfortunately I've noticed the sound quality is significantly poorer than on Windows. It has a more muffled quality to it and seems to distort more easily.

The sound card is a Intel Corporation 82801H and it's using whatever drivers came with Ubuntu (don't know how to find out what my drivers are in Ubuntu, sorry). It has no equalizer so I can't adjust the frequencies. How can I find out if there's a better driver out there to improve the sound? Or is there some equalizer app I can download?

---

### Post by Mellifluous on 2011-07-17
Just want to say for anyone who's not liking the poor sound quality of Ubuntu that I found a solution here: [http://www.webupd8.org/2011/04/system-wide-pulseaudio-equalizer.html](http://www.webupd8.org/2011/04/system-wide-pulseaudio-equalizer.html)

Basically Ubuntu doesn't come with a sound equalizer as standard. Luckily there exists one by Pulse Audio. Why this isn't part of the bundled package I don't know. It should be. Follow the instructions at the link provided and you'll be able to make things sound so much better :D

---

### Post by beew on 2011-07-17
You will have more problems with WUBI than a regular install. Sound in all versions of  Ubuntu have been fantastic for me on different machines.

---

### Post by lidex on 2011-07-17
A lot of sound quality issues in ubuntu can be rectified in alsamixer. Levels too low or high and many options can exist for master, front, pcm, surround, lfe, etc. A wrong selection of profile in 'Sound Preferences' will cause issues as well.

---

### Post by Mellifluous on 2011-07-18
What's alsamixer? I can't find it in my list of applications under Sound & Video and it's not in System > Preferences > Sound. All I get there is a basic Sound Preferences box with various volume sliders and no equalizer. Anyway the Pulse Audio equalizer has done the trick.

---

### Post by lidex on 2011-07-18
> **Mellifluous said:**
> What's alsamixer? I can't find it in my list of applications under Sound & Video and it's not in System > Preferences > Sound. All I get there is a basic Sound Preferences box with various volume sliders and no equalizer. Anyway the Pulse Audio equalizer has done the trick.

**Alsamixer**
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

---

### Post by Unterseeboot_234 on 2011-07-18
alsamixer, and make sure your volume control for the sound card is turned up.

But also, I noticed through the years with Ubuntu I was losing my sound quality. One day my computer refused to even boot. Investigation proved I had a fried Power Supply Unit.

I replaced my PSU with a 550 watt over the original 400 watt. The extra watts had an immediate and profound effect on my stereo sound. For the first time I had hi-fi audio with selectable volume. I made sure I was using the onboard sound chip to my nVidia card.

---

