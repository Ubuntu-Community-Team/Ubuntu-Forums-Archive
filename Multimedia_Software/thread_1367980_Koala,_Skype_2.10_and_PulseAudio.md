---
title: "Koala, Skype 2.10 and PulseAudio"
date: 2009-12-30
forum: Multimedia Software
---

### Post by Moses_ on 2009-12-30
Hi

I am having this common problem with Skype 2.10 and PulseAudio:

With Ubuntu 8.04 and Skype 2.0, I could select different devices for ringing and for voice. This is for my mom's PC so I like to keep things as simple as possible. She has a logitech USB headset and an onboard sound card with speakers. Before, her default sound device was the sound card which was fine for music, etc. Then in Skype I'd select the USB headset as the device for input and ouput, but I'd keep the ringing set to the sound card, for obvious reasons.

Now, with Ubuntu 9.10, PulseAudio and Skype 2.10, this option seems to have been removed. If the default device is set to the soundcard (as it should be for all sound) then Skype also ouputs the voice out of the speakers, which is not okay.

It seems there is no fix for this, except to either remove PulseAudio, or to downgrade Skype to 2.0. 

As this is my mom's PC, who I only see once a year, everything needs to be setup to work perfectly, until I visit again. 

I have just done a clean install of 9.10, and it seems both the options (downgrading skype or removing pulseaudio) are quite messy, and I don't want to compromise the stability of system for the next year. Especially when it comes to updates and dependencies, etc as there is no one around to fix it.

My question is this. I removed PulseAudio, changed my mind and then reinstalled it. Everything is fine again, except the volume now has to be turned up very loud to hear anything, and there is a loud high pitched sound now coming out of the speakers. Any idea how I can restore the sound systems to how they were after the clean install?

The other advice given is to add a repo with Skype 2.0, install it and then lock that version in synaptic. Will this be stable? Will the old repos interfere when it comes to the daily updates? I think this is the best idea, but I can't find an old repo with SKype 2.0. If I find the deb and install it manually, can I still lock the version? And will updates to other dependencies compromise it?

In summary, how can I fix pulseaudio, and how can I get skype 2.0 installed?

Sorry for the long post. I have less than 24 hours to get this fixed before I hop on a plane!

---

