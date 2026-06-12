---
title: "Digital Audio with Digital Amplifier"
date: 2007-10-14
forum: Multimedia &amp; Video
---

### Post by Roberto Musso on 2007-10-14
I'm using Ubuntu 7.10 RC with Amarok
my audio hardware is the onboard Realtek ALC888
my audio amplifier is a TEAC with digital input and dolby digital decoder

here my problem
when I start  to play the playlist in Amarok (or other players) the Amplifier switch for 2 second to the Doby digital decoding and after that go back to the PCM status.
because that I loose around 3 second of the first song
trying to prevent this problem I placed as the first element of the playlist one blank audio clip 5 second long
this did not solved my problem because the Amplifier switch to the Dolby digital decoding at the beginning of the blank element and at the beginning of the first song......
The only solution that I have found is to place the blank audio clip and to enable the crossfading feature. In this way the switch of the amplifier to the Dolby decoding it happen only on the first blank clip, but the crossfade "cut" the beginning of the song.....

With UBUNTU 7.04 I did not have this problem, the Amplifier was not switching to the Dolby digital.

any suggestion?

---

### Post by tgalati4 on 2007-10-14
Check all of the switches in the Volume Mixer/Control.  Edit-->Preferences, check all of the channels and switches.  There may be an amplifier/headphone sense switch that is turned off by default.

Check the output of dmesg during the beginning of recording:

>dmesg | tail -50

There may some messages that explain what is going on.

---

