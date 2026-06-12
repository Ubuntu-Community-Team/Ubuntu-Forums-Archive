---
title: "Multitrack Recording on Computer"
date: 2007-12-04
forum: Multimedia Production
---

### Post by reesy on 2007-12-04
I was at a studio before with my old band and somehow they recorded the whole band in one take onto the computer and everything was still in separate tracks. I was wondering what hardware do i need to be able to do this. Or can i do it with the mixer I have which  is a  Europower PMH 8805 and my Behringer U-control UCA200 which send the sound to computer through the usb port and just need to change some settings in Ardour GTK2. I'm running Ubuntu Studio 7.10 and i don't have a special sound card its just "on board sound" i believe the definition is correct me if i'm wrong.

---

### Post by eric71 on 2007-12-05
I believe your Behringer USB adapter will only record in stereo, so you would be limited to 2 tracks at a time. To do more, you would need something like the M-audio Delta 44 or 66 (PCI) or Fast Track Pro (USB). 

To use what you have you will need to select the correct device in QJackctl under "input device". The onboard soundcard is usually something like HW0 and the USB device will be HW1. Maybe your onboard sound card already can record in stereo, but many can't. At least with your USB interface you should be able to select left or right channel for recording mono tracks in Ardour now, and record 2 different tracks simutaneously.

---

### Post by Stochastic on 2007-12-05
For every individual track you'll need a separate input on your soundcard.  In most small garage bands an eight-channel card should do just fine.  I'd check out ffado [www.ffado.org](www.ffado.org) compatible cards if you're looking for that many inputs.

---

