---
title: "No ALSA with Terratec Aureon 5.1 fun PCI under Ubuntu 9.04."
date: 2009-06-26
forum: Multimedia Software
---

### Post by DeltaSigma on 2009-06-26
Ubuntu 8.04 was installed on my old computer and the soundcard worked without any problems. But now I bought a new computer and the soundcard does not work in Ubuntu 9.04. The card is not defect because it works with proprietary driver in Windows. Also OSS seams to work but is not used. What should I do solve this problem? I'm no bloody noob anymore. Ubuntu forever!  Multimedia audio controller C-Media Electronics Inc CM8738 (rev 10) Subsystem: TERRATEC Electronic GmbH Device 114

---

### Post by tolotos on 2009-06-27
Here are some hints what you could check in order to narrow the problem down: 
What channels are muted in alsamixer? Make sure that something like Master or Front F isn`t muted. 
Are your audio-programms reporting errors, when starting them via the console?
Have you tried, directing your sound directly through alsa instead of pulsaudio?
Are the alsa-modules loaded?

---

### Post by DeltaSigma on 2009-06-30
Bad thing. Seems everything is ok but still no sound. All is unmuted and no errors occur. Ah, what I should mention is that my onboard soundcard works very fine. What could I do next?

---

### Post by tolotos on 2009-06-30
Do you mean, that you hear sound from your onboard soundcard in ubuntu?
You could try to disable the onboard sound in your bios, to force ubuntu to use your Terratec card. If you dont`t do this, the kernel might find your onboard soundcard first, and stops searching for additional pci cards.

 [B]
[/B]

---

### Post by DeltaSigma on 2009-08-06
Hello
I reinstalled Ubuntu 9.04 and voilá I have aureon sound.
But now I want restore my system to the old strength.
When I do so my sound settings will be restored too.
Where are the sound files, settings, etc.?
So that I can keep my strong sound.

---

