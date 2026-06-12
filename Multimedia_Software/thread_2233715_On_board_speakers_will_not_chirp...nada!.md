---
title: "On board speakers will not chirp...nada!"
date: 2014-07-10
forum: Multimedia Software
---

### Post by dunbrokin on 2014-07-10
I have recently assembled my first box. My mother board is ASRock Z87 Extreme 3 and my box ia a Silverstone RL04. My problem is that I can get a usb speaker to chirp and I can get my logitech  headphones to chirp...but not the onboard speakers. They are detected as HDA Intel HDM1 and HDA Intel PCH. When I run Alsamixer, they are detected and volume is set at 00....I cannot get the volume to change. I have run AlsaInfo and (hopefully) it is attached for reference. Any help on sorting this out would be appreciated.

---

### Post by Yellow Pasque on 2014-07-10
Give more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

You are selecting HDA Intel PCH as the chosen device, correct?

> volume is set at 00
That is O for On (as opposed to M for Mute)

---

### Post by dunbrokin on 2014-07-11
AlsaInfo given in the attachment above already....Yes, I am choosing HDA Intel PCH as the chose device. Ah, OK, I thought it was the volume level...that makes sense.

---

### Post by Yellow Pasque on 2014-07-11
Oh, I see the info now.
Have you tried headphones with the onboard audio?

---

### Post by dunbrokin on 2014-07-11
Yes, it works with the headphones.

---

### Post by Yellow Pasque on 2014-07-11
I could see a couple potential problems then
1) The codec thinks headphones are always plugged in, even when they're not (try disabling auto-mute to test it)
2) EAPD not working properly (speakers need amp)

Of course, it could be something that I can't see from the log (I don't consider myself an expert). In that case, I would try the latest kernel module/driver  ( [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS) ) and file a bug report if it's still not working after reboot.

---

### Post by dunbrokin on 2014-07-11
Thanks for that suggestion. I disabled automute but it made no difference. I guess the speaker may be bust?! I updateded the kernel module/diver as suggested...no difference.

---

### Post by dunbrokin on 2014-07-24
Apparently the inbuilt speakers in a dektop box, are only there to give system sounds in case of hardware problems and do not relay music etc.

---

