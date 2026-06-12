---
title: "trouble playing divx/xvid fullscreen"
date: 2010-08-13
forum: Multimedia Software
---

### Post by darklord06 on 2010-08-13
Hello,

I recently installed ubuntu in my laptop (hp dv5000) and I am learning how it works (so far I like it !) but I have one main issue with the xvid or divx videos playback in full screen.

right after having installed ubuntu, I tried to play a divx video using totem, apparently the required codecs weren't installed so it automatically downloaded those, it was ok as long as I tried to play the video in window mode but as soon as I tried to play it full screen, it was noticeably more laggy than it was under windows seven.

I thought that it was maybe a problem with totem itself so I installed VLC (it supposedly has its own codecs) but i have the same problem with in in full screen mode, I also have difficulties moving the cursor using my touchpad in full screen mode.

i thought that it was a graphical card driver issue but i was no problem playing mkv videos in full screen, i only have a problem with xvid and divx videos.

I am completely new to ubuntu and if somebody could help me with it that would be very cool :)


if it helps, my laptop is an hp pavilion dv5000 with an amd turion 64 ML-32 1,80GHZ chipset, 1GB of ram and a ATI mobility radeon xpress 200 series 128mb graphical chipset

thank you

---

### Post by darklord06 on 2010-08-13
I have just noticed that when i deactivate the visual effects, full screen playback of divx/xvid videos aren’t laggy anymore, the only strange thing remaining is that if i keep the original aspect ratio for a 16:9 video, i have an horizontal line appearing on the upper side of the screen, when i switch to a 16:10 aspect ratio it disappears. 
  Again I have no problem playing mkv files in full screen even with advanced visual effects activated, I am really puzzled...

---

### Post by sydbat on 2010-08-13
> **darklord06 said:**
> I have just noticed that when i deactivate the visual effects, full screen playback of divx/xvid videos aren’t laggy anymore, the only strange thing remaining is that if i keep the original aspect ratio for a 16:9 video, i have an horizontal line appearing on the upper side of the screen, when i switch to a 16:10 aspect ratio it disappears. 
  Again I have no problem playing mkv files in full screen even with advanced visual effects activated, I am really puzzled...It has to do with your hardware. Above and beyond the fact you have an older laptop, you are only running 1GB RAM with ATI shared video. Your older 64bit AMD processor can only do so much.

Running without ANY eye candy (like Compiz) will make your laptop quite snappy. And you won't have to worry about laggy videos or games.

So, your solution is the only one I can think of...unless you can find some cheap laptop RAM to bring it up to the max 2GB. Still, turning off all the visual effects is best.

---

