---
title: "Switching Port Function"
date: 2011-07-15
forum: Multimedia Software
---

### Post by kijuhy on 2011-07-15
Hello

I am trying to get surround sound on my PC through my realtek
onboard sound, but it only has 3 audio ports. On windows, the realtek drivers had the option for me to switch the function of any audio port so I switched the line in port I don't use to a rear out port. 

How can I do this on Ubuntu?

PS Does anybody know any good 2 channel to 4 channel converters that are or linux?

---

### Post by Too Late on 2011-07-15
I don't know which version of Ubuntu you are using, but in 10.04 you could try to go to System -> Preferences -> Sound (or right-click the volume icon on panel) and go to Hardware tab. I can select different profiles there, but I don't have "multifunction ports", so I don't know how those profiles work with them.

> **kijuhy said:**
> PS Does anybody know any good 2 channel to 4 channel converters that are or linux?
Do you mean a software which "copies" front audio to rear channel? If so, I'm asking the same. I recall that in Ubuntu 8.04 there was a checkbox named "spread front stereo to rear channel" or something like that. It was somewhere inside volume control or sound preferences, but I can't find anything in Ubuntu 10.04. In 8.04 the setting was "system wide" (worked with every application) and I think it was also totally hardware independent.

For me it would be sufficient if there is an easy way to "move" (instead of "copying") front sound to rear channel (and back to front when needed).

---

### Post by kijuhy on 2011-07-15
> **Too Late said:**
> I don't know which version of Ubuntu you are using, but in 10.04 you could try to go to System -> Preferences -> Sound (or right-click the volume icon on panel) and go to Hardware tab. I can select different profiles there, but I don't have "multifunction ports", so I don't know how those profiles work with them.


Do you mean a software which "copies" front audio to rear channel? If so, I'm asking the same. I recall that in Ubuntu 8.04 there was a checkbox named "spread front stereo to rear channel" or something like that. It was somewhere inside volume control or sound preferences, but I can't find anything in Ubuntu 10.04. In 8.04 the setting was "system wide" (worked with every application) and I think it was also totally hardware independent.

For me it would be sufficient if there is an easy way to "move" (instead of "copying") front sound to rear channel (and back to front when needed).

Thanks for your reply, I am using version 11.04. I have found it to be completely different from the older version of ubuntu I have used before. I am using a Realtek onboard ALC883 which is listed as an HDA nVidia audio device in alsa mixer.

For copying the sound, I usually just use a hardware 3.5mm splitter that puts the sound into 2 audio jacks. In  windows, there is an option in the realtek drivers which I think takes the background sound to the rear speakers by taking off the usuaul voice frequencies.

---

