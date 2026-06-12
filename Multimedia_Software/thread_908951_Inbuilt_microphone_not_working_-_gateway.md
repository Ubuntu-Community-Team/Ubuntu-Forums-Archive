---
title: "Inbuilt microphone not working - gateway"
date: 2008-09-03
forum: Multimedia Software
---

### Post by Zorgoth on 2008-09-03
I just bought a Gateway M-6881 with Vista and dual booted it with Ubuntu 8.04, and I have gotten all the hardware I care about working now except for my microphone.  

I have tried all the options in System -> Preferences -> Sounds and have attempted messing with alsamixer, although I didn't really have any idea what I was doing, but nothing has made any recordings at all on Applications -> Sounds and Video -> Sound Recorder or Skype Test Call.

I'm not sure exactly what my microphone is but SigmaTel was what came up in the Windows hardware devices under sound.

If this problem can't be fixed, could someone suggest a good brand of USB Microphone/Headset to use with Ubuntu and Skype?

Note that I am entirely new to both Ubuntu and Linux and don't assume I know anything :)

Thanks!

---

### Post by Slug71 on 2008-09-05
Try this, 
Double click the speaker at the top right of the screen. This opens AlsaMixer.
Click on preferences and check Capture(not Capture 1)
Also check Digital
Make sure front, front mic boost and mic boost is also checked

On playback tab of the mixer make sure everything is turned up except front mic boost(turn it right down) and mic boost(mine is set half).

On the recording tab, turn Didital and Capture to half and make sure there are no red x's at the bottom.

Give sound recorder a try.

If that doesnt work you may want to Install Intrepid Ibex Alpha 5. As the new kernel in that along with Alsa v1.0.17 should fix it as it did on mine.

---

