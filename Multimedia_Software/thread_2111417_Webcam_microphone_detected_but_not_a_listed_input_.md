---
title: "Webcam microphone detected but not a listed input device"
date: 2013-02-01
forum: Multimedia Software
---

### Post by compiz addict on 2013-02-01
**Issue:**
My microphone currently isn't in the list of input devices in either KMix or PulseAudio Volume Control. It is, however, listed in the hardware tab as an analogue mono input (which as far as I can tell, it is). Since I can't select the microphone as my input device, it doesn't work, rendering it useless. My microphone does function in Unity after unplugging it and plugging it back in, though I prefer KDE (that is, when KDE isn't broken somehow).

**Background:**
In my fresh install of Ubuntu 12.04, my sound had been working inconsistently. My sound card wouldn't appear in the sound settings until I used "sudo alsa force-reload" multiple times. Eventually those would work, and then my microphone would work after unplugging it and plugging it back in. I recently installed KDE, and my sound started working perfectly, in both Unity and KDE. I later discovered that my microphone doesn't work in KDE (this was after managing to screw up KMix somehow after starting up pavucontrol and having to delete my .kde folder). This was while trying to get Skype to work.

**Goal:**
I want my microphone to function in KDE, and I would also prefer that it function using pulseaudio so I can later take full advantage of the many features of pavucontrol.

EDIT: Sound card is still not always detected in Unity (though on some boots it works fine). I made the assumption that it worked too quickly.

---

### Post by compiz addict on 2013-02-02
*bump*

---

