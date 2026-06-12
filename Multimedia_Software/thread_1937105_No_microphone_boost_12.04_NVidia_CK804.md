---
title: "No microphone boost 12.04 NVidia CK804"
date: 2012-03-07
forum: Multimedia Software
---

### Post by trindflo on 2012-03-07
I can not enable the +20 boost for my microphone using alsamixer in the 64 bit Beta 12.04.  AlsaMixer identifies the device as NVidia CK804 and identifies the "Mic Boost" setting as on/off +20, but the up/down arrows do not change the setting.  With the gain on the microphone set to the maximum, it is barely audible and effectively unusable.  Is there a workaround?

 Item: Mic Boost (+20dB) [Off]

I have this working well enough now.  I installed the Gnome Alsa Mixer from the Ubuntu Software Center (USC); I believe this can be accomplished from the command line as ```
sudo apt-get install gnome-alsamixer
```.  The setting is available from that mixer.

On a related note, I found that (at least in 12.04) Skype:
[LIST=1]
[*]uses the pulse audio server, which you may need to install
[*]the volume settings on the microphone are very different between pulse audio an the sound recorder app
[*]Skype does not sign out properly if I just close the app and I need to sign back in under Windows to reset the condition.
[/LIST]

---

