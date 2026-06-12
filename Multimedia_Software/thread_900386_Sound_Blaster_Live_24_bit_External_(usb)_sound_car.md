---
title: "Sound Blaster Live 24 bit External (usb) sound card"
date: 2008-08-25
forum: Multimedia Software
---

### Post by residualbit on 2008-08-25
I was surprised to find out that Ubuntu recognized what it was as soon as i plugged it inIt all shows up as being installed when I type "aplay -l" in the console. I have "SB Live 24 bit" selected as the device through the volume control menu and I also went the the sounds menu (System>Pref>Sounds) and selected USB audio for everything. I ran the tests and heard the beep through the speakers I have connected to the sound card. I thought everything would work fine, but other then those simple tests, nothing will play through the card, everything plays through my default laptop speakers. What should I do?

---

### Post by residualbit on 2008-08-25
bump. this is really frustrating!

---

### Post by residualbit on 2008-08-25
i'm sorry to bump this again, but does anyone have experience with this card? i don't know anywhere else to look

---

### Post by kostkon on 2008-08-25
> **nkirk1 said:**
> I was surprised to find out that Ubuntu recognized what it was as soon as i plugged it inIt all shows up as being installed when I type "aplay -l" in the console. I have "SB Live 24 bit" selected as the device through the volume control menu and I also went the the sounds menu (System>Pref>Sounds) and selected USB audio for everything. I ran the tests and heard the beep through the speakers I have connected to the sound card. I thought everything would work fine, but other then those simple tests, nothing will play through the card, everything plays through my default laptop speakers. What should I do?
Do you use 8.04? I am asking this, because 8.04 uses PulseAudio for its audio and you may have to do different things compared to previous versions of Ubuntu.

---

### Post by residualbit on 2008-08-25
yes sorry, i am using hardy (8.04).

---

### Post by residualbit on 2008-08-25
is there something special i need to do? i have run out of ideas

---

### Post by residualbit on 2008-08-29
any word on this yet?

---

### Post by ezzieyguywuf on 2009-06-14
Try opening the pulse-audio volume controller and in the output devices tab, make sure your external soundcard is showing up. Next, click on the Playback tab, and you should see an entry for any audio-stream. Right-click on the one that you want to send to th soundblaster and under move-stream, select you soundblaster. hope this helps!

---

