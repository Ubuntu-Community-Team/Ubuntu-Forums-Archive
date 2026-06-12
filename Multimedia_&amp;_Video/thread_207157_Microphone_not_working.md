---
title: "Microphone not working"
date: 2006-07-01
forum: Multimedia &amp; Video
---

### Post by greengrocer on 2006-07-01
Hope some one can suggest somethings to try. 

I cannot get microphone to work, not even if I use the sound recorder from the applications menu.  The following describes my setup here.

* Ubuntu Breezy Badger.
* Realtek ALC880 high definition sound hardware integrated onto motherboard with Intel 925XE chipset.

* ALSA sound output working fine
* System sounds are fine
* CD play back is fine
* Skype sound output fine
* alsa-oss has been installed using apt-get
* Mixer volumes are all up and nothing is muted

I just cannot get any response for the microphone.

I have had a look at the file: /etc/modules.d/alsa-base

but nothing makes much sense to me and there is a lot of stuff in that file.

Does anybody know of any tweaks to any config files that may solve the problem?

Regards,
greenie.

---

### Post by Nonno Bassotto on 2006-07-01
Maybe I'm telling you something you already have tried, but the problem for me was that I had the Capture volume down. I thought I already had every volume up, but Capture didn't show up in the mixer until I explicitly chose it in the edit menu. So I was not able to record from the sound recording utility.

---

### Post by greengrocer on 2006-07-01
Hi,

All levels are up and nothing is muted.  And now, all of a sudden, my Gnome sound recorder program is crashing.

I am experiencing the following very strange behaviour.

1) If I set ALSA to be the input device in the "Multimedia Chooser settings", the Gnome sound recorder crashes when I click record.

2) If i set OSS to be the input device in the "Multimedia Chooser settings", the Gnome sound recorder does not crash when I click record.

3) If i set ALSA to be the output device in the "Multimedia Chooser", the Gnome sound recorder will crash when I click Play.  BUT the CD PLayer will still play.

4) If i set OSS to be the output device in the "Multimedia Chooser", the Gnome sound recorder will trigger a /dev/dsp already in use error when I click Play.  And as an added bonus, CD Player will no longer play.

5) The microphone does not work in the front mic socket, but in the rear line in socket I can hear myslef speak into the microphone.  (Windows sees the Microphone in the reverse order to this, Windows likes the mic in the front mic socket and not in the rear line in).

6) If I have two occurances of Gnome Sound Recorder running, the second instance is able to record sound from the mic, the first instance does not 'hear' the mic.

7) When playing back a file in Gnome Sound Recorder, I have to click the stop button before playback ends, otherwise Gnome Sound Recorder crashes.

All Gnome Desktop system sounds are always working, through out all tests.


But the microphone never works with Skype.  Skype is the only reason to use windows, If the microphone problem could be resolved, I could sent Windows to hell.

---

