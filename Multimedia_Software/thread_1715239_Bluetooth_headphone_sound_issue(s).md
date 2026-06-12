---
title: "Bluetooth headphone sound issue(s)"
date: 2011-03-26
forum: Multimedia Software
---

### Post by GSBoomer on 2011-03-26
Several days ago my bluetooth headphone (Motorola s9-hd) stopped working over bluetooth. They would pair fine on boot, but no sound. While the S9-HD's have some questionable reviews on Amazon, I knew they were not the problem as they still paired and worked fine on my mac laptop.

After much distress and lost sleep, complete reinstalls of the bluetooth stack and pulseaudio from Brian Roger's ppa (ppa:brian-rogers/ppa), I discovered using pavucontrol that somehow the headphone volume had become muted. None of the other available controls (regular volume control, or sound preferences) even show an OPTION to mute/unmute them, so pavucontrol was a life saver.

I post this so other souls won't take bluetooth in vain during the night.

---

