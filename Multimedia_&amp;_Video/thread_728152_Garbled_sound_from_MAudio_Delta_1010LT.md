---
title: "Garbled sound from MAudio Delta 1010LT"
date: 2008-03-18
forum: Multimedia &amp; Video
---

### Post by stwillia on 2008-03-18
Hello all, been a lurker for a while but this is my first time posting. I have searched the crap out of these forums as well as the all-knowing oracle google but haven't even found anyone with the same problem yet.

I recently finally got my hands on an MAudio Delta 1010LT. When I installed it and booted up the machine it seemed to have been detected and installed completely automatically. Jack would even start up and connect to it and show all of the appropriate channels, however...when I play audio through it from *any *source (Ardour, Audacity, CD Juicer, etc) the sound is all garbled. This effect gets worse if I minimize or maximize windows or drag them around - it sounds like the playback is slowing down too. Seems like it's conflicting with something. I just have a simple basic pci graphics card that came with my machine (Dell Poweredge 400sc running Ubuntu Studio) and am not running anything special graphically. System has plenty of CPU and memory available. Previously I was running a Soundblaster Live and everything worked fine. The system also has an on-board sound card, AC'97 I believe. 

Any ideas? If this has been addressed before, feel free to flame away but please at least point me in the right direction. 

Thanks in advance for any help.

---

### Post by lemmalone on 2008-03-18
I am brand new to Ubuntu but have some Debian experience, and since there are no answers yet I'll give it a shot. Also, I have an M-Audio 2496, so maybe I can help. The easiest fix might be to open alsamixer, "sudo alsamixer", although I don't think you even need sudo, and see if the card has been detected properly and that the right boxes are checked and unchecked, (pressing m when the cursor is within a box unmutes that setting if it is muted, and vice-versa) and that the volume sliders are high enough to produce sound. (Use arrow keys to navigate.) You may be able to start an application, eg, audacity, and then fool around with the controls to hear whether the sound plays differently. In my alsamixer setup some of the boxes control a variety of settings depending on the position of the up/down keys, and when I pressed m to unmute one of them there was suddenly sound where before there was none. Also, you may need to select correct inputs/outputs in the various applications. In audacity, for example, I believe that you would look in Edit Preferences I/O and then see a variety of inputs and outputs to choose from.

---

### Post by tgalati4 on 2008-03-18
I would check for sharing of interrupts.  Examine /proc/interrupts.  You want the sound card on it's own interrupt.

---

### Post by stwillia on 2008-03-19
Thanks very much for the replies. I have messed with alsamixer for hours seems like but haven't had any luck there. I will give it another shot though. The info about /proc/interrupts sounds interesting, I had suspected that it could be an IRQ issue. I will check out both of those things and post the results.

---

### Post by tgalati4 on 2008-03-19
You might try turning off the on-board sound card through the BIOS.  Also realize that the Delta card runs at 96 kHz and most onboard cards run at 48 kHz so the conflict in running speed could cause stuttering as the sound mixer has to interpolate.  Try setting the Delta to 48K or turn off the on-board sound.

---

### Post by stwillia on 2008-03-26
Well I have tried all of your suggestions but no change. In /proc/interrupts it showed the on-board sound card on the same interrupt as the Delta. So I disabled the on-board sound in the BIOS and now the Delta is on it's own interrupt (20) by itself. But nothing changed. I have no problem at all getting sound, it is just all garbled and is badly affected by moving things around on the screen. Seems to be conflicting with the video somehow. I have moved the card around in the PCI slots but that doesn't change anything either. Again I do have the simple PCI graphics card that came with the machine (no on-board graphics card) - do you think that could be the source of the conflict? Should I look at moving to an AGP graphics card? The Soundblaster Live! still works fine if I throw it in there. I'm getting frustrated here. I want to play with my new toy! :mrgreen:

Thanks for all the advice.

---

### Post by stwillia on 2008-03-28
Ok, after many frustrating hours, I have deducted the problem. It was conflicting with the graphics card after all. Apparently an ATI Rage doesn't play well with the Delta 1010lt. So there you have it. Guess I have to buy a new graphics card as well.

#-o

---

### Post by tgalati4 on 2008-03-28
Try moving the card to a different slot.  Sometimes the PCI slots have a hard-wired interrupt that will change when you move the card.  You may have to move other cards around as well.

Be sure to turn off Plug-N-Play OS in BIOS.  Linux is not a plug-N-play OS.  This changes the way the BIOS presents the interrupts to the OS so that the OS can make better assignments.

---

