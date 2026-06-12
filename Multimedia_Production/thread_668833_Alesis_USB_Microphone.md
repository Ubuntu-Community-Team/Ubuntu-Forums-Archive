---
title: "Alesis USB Microphone?"
date: 2008-01-15
forum: Multimedia Production
---

### Post by BennieBlount on 2008-01-15
Does anyone have any knowledge on how to use an Alesis USB mic on Ubuntu?

It worked great on Windows, but I can't seem to get it to work on Ubuntu. In the Alsa mixer under File>Change Device  it is listed, but I just can't figure out how to record with it. I have been trying to use it with Audacity.

Any help is greatly appreciated.

Thanks,

Bennie

---

### Post by gobuntu on 2008-01-18
Hi BennieBlount,

I believe this should work for you:

No need to go to the Mixer, just at Audacity click:

Edit/Preferences

At Audacity Preferences Screen, set Recording Device to one from the list of choices that has the word USB, likely it'd be something like: ALSA: USB Device etc ...

Then control the volume of the USB mic with Audacity's own sliders.

You can then record, but only the sounds going into the USB microphone, though.

I am still trying to figure out how to record ALL output from the sound mixer where the USB mic would be taking the place of the regular analog mic, though.

If someone knows how to mix the USB mic so as to record in Audacity several sources simultaneously, please help!

---

