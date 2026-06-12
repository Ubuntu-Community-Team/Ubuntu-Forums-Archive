---
title: "USB Audio Jabra Speak410. Mic working, no Audio playback"
date: 2013-03-27
forum: Multimedia Software
---

### Post by kgokare on 2013-03-27
Hi Folks,

Hope this is the right part of forum to post. I have a Jabra speaker phone with a mic and a speaker. I have all the alsa configuration setup and everything seems to up. The usb device is properly enumerated, shows up in sound control. I am able to use mic to record, even change volume/mute, umute the speaker from the control panel. But when I play a sound, there is no error, volume seems to be 0. Checked alsamixer, selected the usb card, playback volume is properly set.
When I play a file through aplay, I check /proc/asound/..  for the usb pcm device, It seems to be up and hw_params and sw_params are properly set. But no sound, no error messages anywhere.

I can provide any specific info/config/logs if needed.

Any help is deeply appreciated.

thanks!

---

### Post by elirov on 2013-05-07
I'm getting the same problem.  Very strange.

> **kgokare said:**
> Hi Folks,

Hope this is the right part of forum to post. I have a Jabra speaker phone with a mic and a speaker. I have all the alsa configuration setup and everything seems to up. The usb device is properly enumerated, shows up in sound control. I am able to use mic to record, even change volume/mute, umute the speaker from the control panel. But when I play a sound, there is no error, volume seems to be 0. Checked alsamixer, selected the usb card, playback volume is properly set.
When I play a file through aplay, I check /proc/asound/..  for the usb pcm device, It seems to be up and hw_params and sw_params are properly set. But no sound, no error messages anywhere.

I can provide any specific info/config/logs if needed.

Any help is deeply appreciated.

thanks!

---

