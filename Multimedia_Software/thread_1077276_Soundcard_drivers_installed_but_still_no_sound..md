---
title: "Soundcard drivers installed but still no sound."
date: 2009-02-22
forum: Multimedia Software
---

### Post by ekidd91 on 2009-02-22
I have the SoundBlaster Audigy 2 ZS Platinum Pro soundcard and I am running Intrepid Ibex. I have installed ALSA 1.0.19 drivers following [these instructions]("http://www.linlap.com/wiki/configuring+the+audio+and+updating+alsa+for+ubuntu+8.10#installing+the+cvs+alsa+modules") in an attempt to get my sound working. Sound was present when using the LiveCD.
Everything is unmuted but there is still no sound.

Please help, thanks in advance

---

### Post by Steve H on 2009-02-22
A lot of people are complaining about PulseAudio problems and get around it by uninstalling, try [here]("http://ubuntuforums.org/showthread.php?t=963914").

From personal experience I found that worked until I wanted to get my USB mic running at the same time as Eve Online, and so back to Pulse I went. I found [these]("http://ubuntuforums.org/showthread.php?t=789578") instructions worked.

It took a bit of tweaking but it's all working now.

Good luck!!

;)

---

### Post by ekidd91 on 2009-02-24
> **Steve H said:**
> A lot of people are complaining about PulseAudio problems and get around it by uninstalling, try [here]("http://ubuntuforums.org/showthread.php?t=963914").

From personal experience I found that worked until I wanted to get my USB mic running at the same time as Eve Online, and so back to Pulse I went. I found [these]("http://ubuntuforums.org/showthread.php?t=789578") instructions worked.

It took a bit of tweaking but it's all working now.

Good luck!!

;)

Thanks, I've now got it working, albeit in the headphone bit on the front panel (used to run through back panel). I'm happy with it like this, but just in case, does anyone know a way of getting playback through the back again (at the moment I'm using a large adapter because it's a 6.3mm jack on the front, so it sticks out a bit and doesn't look great.)

Thanks again!

---

### Post by Steve H on 2009-02-25
This might be a daft question but have you checked you mixer settings? It may be that the output channel for the back outputs have been muted. Might be worth a look.

;)

---

### Post by ekidd91 on 2009-02-25
> **Steve H said:**
> This might be a daft question but have you checked you mixer settings? It may be that the output channel for the back outputs have been muted. Might be worth a look.

;)

Yeah I've put every channel at maximum volume and still only get playback through the front headphone port/socket.

---

### Post by Therion on 2009-02-25
> **ekidd91 said:**
> I have the SoundBlaster Audigy 2 ZS Platinum Pro soundcard ...
For my Audigy II ZS I almost ALWAYS have to open the Sound properties, click on the "Switches" tab and then clear the **Audigy Analog/Digital Output Jack** tic-box to get my sound working.  Well it's a one-time fix, I mean with every fresh install I have to redo it.

---

### Post by Reeman on 2009-02-25
> **ekidd91 said:**
> Thanks, I've now got it working, albeit in the headphone bit on the front panel (used to run through back panel). I'm happy with it like this, but just in case, does anyone know a way of getting playback through the back again (at the moment I'm using a large adapter because it's a 6.3mm jack on the front, so it sticks out a bit and doesn't look great.)

Thanks again!
Try alsamixer -c 0 ...this will access the functions on the card not the functions through pulse. You should be able to unmute the mic. I do not use any of the silly add on mixers good ol' alsamixer will do it when interfaces get borked by desktop audio servers!

---

### Post by ekidd91 on 2009-02-26
> **Therion said:**
> For my Audigy II ZS I almost ALWAYS have to open the Sound properties, click on the "Switches" tab and then clear the **Audigy Analog/Digital Output Jack** tic-box to get my sound working.  Well it's a one-time fix, I mean with every fresh install I have to redo it.

I can't seem to find the 'Switches' tab, although I do recall seeing it somewhere before, I just can't find it now :confused:

---

### Post by ekidd91 on 2009-02-28
> **Therion said:**
> For my Audigy II ZS I almost ALWAYS have to open the Sound properties, click on the "Switches" tab and then clear the **Audigy Analog/Digital Output Jack** tic-box to get my sound working.  Well it's a one-time fix, I mean with every fresh install I have to redo it.

Thanks! Playback is back to normal now :D

---

