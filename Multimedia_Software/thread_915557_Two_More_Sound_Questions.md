---
title: "Two More Sound Questions"
date: 2008-09-10
forum: Multimedia Software
---

### Post by blackknight438 on 2008-09-10
So, I now have sound, but I can't figure out two problems that I'm having (possibly related).

My system volume seems incredibly low compared to what it was on Windows. I have master volume (and every other volume bar for that matter) up to full, but I still have to turn my speakers almost all the way up to get a moderate level of noise. Also, whenever I push the volume up and volume down keys on my keyboard, a speaker with a bar below it appears and adjusts accordingly; however, this has no effect on my sound or the actual master volume. Any clue what that's all about or how to fix it?

I also can't use Skype. It says there is a problem with audio playback when I try to make a call, so it won't dial. Is this related or do I also fail at using Skype? 

Thanks in advance for the help.

---

### Post by kpkeerthi on 2008-09-10
> **blackknight438 said:**
> 
My system volume seems incredibly low compared to what it was on Windows. I have master volume (and every other volume bar for that matter) up to full, but I still have to turn my speakers almost all the way up to get a moderate level of noise.
Open a terminal and type **alsamixer**. Make sure the channel marked **PCM** is turned up full. Use arrow keys to adjust volume level. Press 'Esc' key to quit alsamixer.

> 
 Also, whenever I push the volume up and volume down keys on my keyboard, a speaker with a bar below it appears and adjusts accordingly; however, this has no effect on my sound or the actual master volume. Any clue what that's all about or how to fix it?


Go to System -> Preferences -> Sound and select 'Master' & 'Headphone'. Now your keyboard volume control should adjust both master and headphone volume.

Not sure about your Skype. I don't use it (Qt!).

---

