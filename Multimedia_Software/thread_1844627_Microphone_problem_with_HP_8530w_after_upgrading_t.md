---
title: "Microphone problem with HP 8530w after upgrading to 10.04"
date: 2011-09-15
forum: Multimedia Software
---

### Post by Chadim_ibn_Kazan on 2011-09-15
Hi,

My upgrade to 10.04 went very well (previously 9.04), except for my microphon (I have an HP 8530 w elitebook). Sound plays perfectly, and I can hear myself typing and speaking (i.e. the internal microphone loops back to the speakers) but it never works for skype/ audacity / etc.). Everything worked perfectly in 9.04

I tried many fixes for microphone problems posted here, to no avail. I played around with pavucontrols and alsamixer, tried many suggested options in modrpobe/alsa.conf, and made sure that nothing is muted. pavucontrols shows only one input device instead of two (my internal microphone and the microphone jacks for an external one), and an external microphone somehow works, but way too silent (I can hear a lot of static hiss and my own voice very silently in an external microphone). 

Please also find at this link the output of the alsa-info script
Your ALSA information is located at 
[http://www.alsa-project.org/db/?f=17f2fc5a305fd1b64a4aaa7318d885ffd9cec43c](http://www.alsa-project.org/db/?f=17f2fc5a305fd1b64a4aaa7318d885ffd9cec43c)

Any help is greatly appreciated

---

### Post by Chadim_ibn_Kazan on 2011-09-16
Finally fixed: After trying different options for two days, I simply purged PulseAudio from my system, and replaced it with esound using [http://www.ubuntugeek.com/fix-for-all-pulseaudio-related-issues.html](http://www.ubuntugeek.com/fix-for-all-pulseaudio-related-issues.html)
Everything worked fine again without additional tuning.

---

### Post by awcyber on 2011-09-16
> **Chadim_ibn_Kazan said:**
> Finally fixed: After trying different options for two days, I simply purged PulseAudio from my system, and replaced it with esound using [http://www.ubuntugeek.com/fix-for-all-pulseaudio-related-issues.html](http://www.ubuntugeek.com/fix-for-all-pulseaudio-related-issues.html)
Everything worked fine again without additional tuning.
I have the same problem with you, after I tried all back to normal .. thanks :popcorn:

---

