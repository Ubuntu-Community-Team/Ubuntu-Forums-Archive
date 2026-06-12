---
title: "No sound from Supercollider and Sonic-Pi on Ubuntu 18-04"
date: 2018-08-04
forum: Multimedia Software
---

### Post by AkiraBergman on 2018-08-04
I get sound from the browser, VLC and Audacity, but no sound from Supercollider and Sonic-Pi. I think Sonic-Pi uses Supercollider anyway.

I guess the problem has to do with the PulseAudio and Jackd relationship. I tried starting QJackCtl before Supercollider to no avail. I also tried using "pasuspender -- /usr/bin/jackd" in the "Server Prefix" field of "Advanced Settings" of QJackCtl. This did not help either.

I have a desktop with P7P55D-E mobo, 4G RAM and a SB060 SBLive! Player 5.1 sound card.

---

### Post by AkiraBergman on 2018-08-05
Found a solution. QJackCtl-Settings-Advanced-OutputDevice-InputDevice: Sound card channel 0, instead of default. Start QJackCtl before Sonic-Pi or scide. Obviously there is a device allocation problem.

---

### Post by giannismet on 2019-02-23
I have tried but it didn't work. Do you know any other way I can listen to it? Thanks in advance.!

---

