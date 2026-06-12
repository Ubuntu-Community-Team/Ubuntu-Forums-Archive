---
title: "USB Soundcard won't become default (Xmod)"
date: 2008-07-18
forum: Multimedia Software
---

### Post by koolcracker on 2008-07-18
Okay, I have tried using the system>preferences>sound to set all of the outputs to USB card, and I've tried editing the asoundconf default card to be the "Xmod" that i got from asoundconf list, but my laptop continues to play all sound through the computer speakers.

I have only managed to play music throguh Amarok through the Xmod by setting the output plugin to alsa and configuring the stereo to be "plughw:Xmod,0"

Could anybody lend me a hand, I've serached every forum I could to find help, but nothign will allow my sound to be played through the USB Xmod soundcard. Help would be greatly appreciated, I just bought this card and would be disapointed if I couldn't get it to properly work.

---

### Post by steefjeqv on 2008-07-19
Have a look at this :

[https://help.ubuntu.com/community/SoundTroubleshooting#Configuring%20default%20soundcards%20/%20stopping%20soundcards%20from%20switching]("https://help.ubuntu.com/community/SoundTroubleshooting#Configuring%20default%20soundcards%20/%20stopping%20soundcards%20from%20switching")

Greetings,
Steven

---

### Post by koolcracker on 2008-07-19
Thank you so much, I thoguht I'd tried everything, but that worked like a charm.

Also, this isnt as big of a problem, but if anyone knows how to change the volume control that would be helpful. I want to use the sound knob on my xmod to change volume, but when I use the system>prefs>sound and change the default mixer tracks to the xmod, then when i turn the knob, it changes the volume erratically and eventually mutes it.

---

### Post by koolcracker on 2008-08-23
Okay, sort of a follow up, I got a USB hub, but now I cant get it to work at all with my computer, in any manner. Any ideas?

---

