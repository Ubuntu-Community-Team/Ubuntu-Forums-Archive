---
title: "Audio input disappears randomly"
date: 2010-12-18
forum: Multimedia Software
---

### Post by Moshanator on 2010-12-18
Same question asked in [Launchpad]("https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/138073")
Same question asked on [askubuntu]("http://askubuntu.com/questions/18260/audio-input-disappears-randomly")
Same question asked in [LinuxQuestions]("http://www.linuxquestions.org/questions/showthread.php?p=4198440")
I'm running Lubuntu 10.10 on a HP Compaq nx6325. I use it to digitize tape records - connecting the tape deck's headphone output to the notebook's microphone input. Audacity then records the 45 minutes of sound.
However, from time to time, audio input just disappears. There is no data incoming; instead of audacity recording silence, the track cursor completely stops in its way. When using gnome-sound-recorder, the clock counter stays greyed out even though I start recording. Issuing
sudo alsa force-reload
fixes things again. The system logs show little useful, although I can post the more relevant parts if asked.
Does alsa (or pulseaudio) have some kind of log somewhere? Can I make one? Is there any other or better way to find the problem?
Feel free to ask any information needed, will post as necessary.

---

### Post by ice-beam on 2011-01-16
Have same problem with Ubuntu 10.10 on a desktop. Audio input works perfect for a while, then disappears and stops working in different sound recording software (skype, audacity, gnome-sound-recorder). After reboot I get same situation. 'sudo alsa force-reload' don't work for me, only reboot helps. 

$cat /proc/asound/cards 
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfbbf4000 irq 16

---

### Post by Moshanator on 2011-01-16
Yes, alsa force-reload only works on lubuntu. Probably because there's no Pulseaudio involved (in contrast to every other *ubuntu).
Doesn't solve the problem though. One could automate this reloading, but the breaking moment leaves no traces (that I can spot) behind, there is no way for the system to know when it needs to reload alsa.
Ice-beam, what kind of hardware are you using aside from the soundcard?

---

