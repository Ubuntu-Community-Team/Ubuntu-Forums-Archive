---
title: "USB Headset - cannot open device"
date: 2008-12-18
forum: Multimedia Software
---

### Post by dchurch24 on 2008-12-18
Hi all,

I have a Plantronics C50 USB headset - plugged in, can see it fine in lsusb, and when I open "Sounds" from the Preferences menu I can select it from a list etc...

...but when I clidk the 'Test' button I get the following error:

```

audotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosing profile=music: Could not open device for playback

```

I have tried killing PulseAudio, and even tried opening Jack but the device is nowhere to be seen.

I am on 64 bit Intrepid.

As a test, I plugged in the device into a 32bit Intrepid install whilst at work, and after a little trouble it worked fine.

If I open alsa-mixer from the terminal and change the channel from 2ch to 6ch, I can hear an audible change in the hiss - so something is happening in there somewhere ;-)

I have also tried killing anything is ps -A that looks remotely audio based in desperation.

I'm sure I can get this device working, but I am stuck at the moment.

Has anyone got any ideas, or come across this before?

---

