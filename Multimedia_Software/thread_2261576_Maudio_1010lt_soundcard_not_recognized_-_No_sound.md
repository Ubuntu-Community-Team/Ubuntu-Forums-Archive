---
title: "Maudio 1010lt soundcard not recognized - No sound"
date: 2015-01-19
forum: Multimedia Software
---

### Post by eamner on 2015-01-19
Hello
A few days ago I had a problem with the sound... strong, distorted noise. Same thing happened in my Win7 boot. I had to remove all cards, clean up well, etc. 
After that, i recovered sound in my Win7 boot. That's fine. But in Kubuntu I lost all sound. First, I think it's because my ICE1712 card was set as 3rd card, and default was the HD onboard output. 
Long story short, I tried several workarounds, and then I had the 'brilliant' idea of reinstalling the OSS driver (using .deb). After that, I have no soundcards registered at all. There's nothing in Kmix. If I run envy24control, it says *'no ICE1712 cards found'*. Same with mudita24. If I run alsamixer, I get *"No such file or directory"*. I guess I messed up all ALSA configuration.
If I run **lspci | grep -i audio**, I get this:
```

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
01:00.1 Audio device: NVIDIA Corporation GK106 HDMI Audio Controller (rev a1)
05:06.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)

```

If I run **cat /proc/asound/cards**, I get:
*cat: /proc/asound/cards: No such file or directory*

Same result with **/proc/asound/modules**

I don't have the asound.conf file (I read somewhere it's not used anymore?).
Any help? 
I'm using Kubuntu 14.04.

---

