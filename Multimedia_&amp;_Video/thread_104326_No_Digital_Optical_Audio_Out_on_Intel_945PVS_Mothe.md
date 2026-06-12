---
title: "No Digital Optical Audio Out on Intel 945PVS Motherboard"
date: 2005-12-15
forum: Multimedia &amp; Video
---

### Post by polt on 2005-12-15
This motherboard has onboard SIgmaTel STAC92xx audio with both analog and digital outputs. There are two devices (hw:0,0 and hw:0,1). hw:0,0 works fine in the default Breezy Badger installation but hw:0,1 gives no sound. Here is what I have tried:

1. Plugged optical cable into a stereo amplifier first, then a computer with optical in. No sound even though both systems work fine, were turned on, volume level up, etc. (verified by attaching a CD player.) The amp knew that an optical source was attached, but no sound came out.

2. Adjusted levels, mutes, etc. with Volume Control. There is no IEC958 entry.

3. Adjusted controls in many permutations with alsamixer and alsamixergui. There is an IEC958 entry.

4. Tried

aplay -D hw:0,1 test.wav

as suggested on [alsa-project.org]("http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php?company=Generic&card=Generic&chip=Generic&module=Generic"). No sound. (Using hw:0,0 this works fine.)

5. Using XMMS to play mp3 output with hw:0,0 works fine. Went into preferences and changed output to hw:0,1. No sound.

Is this a driver problem? On [alsaopensrc.org]("http://alsa.opensrc.org/hda") there is a claim thet you need snd_hda_intel and snd_hda_core. modprobe says the second isn't there, but it also doesn't appear to be in any available package.

---

