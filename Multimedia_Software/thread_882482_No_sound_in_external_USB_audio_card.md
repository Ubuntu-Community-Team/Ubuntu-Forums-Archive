---
title: "No sound in external USB audio card"
date: 2008-08-07
forum: Multimedia Software
---

### Post by tsphere on 2008-08-07
Hi,
I bought me an Edirol UA-1EX sound card. Connected it through usb, when connected it played that ubuntu startup music through the card.
However, it will not play sound through the card. I tried changing the configuration in Administration-Sound, changed the setting to USB audio, and when pressing "test" I get the following:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample !
gconfaudiosink profile=music: Could not open audio device for playback.
```

I have pulseaudio applet installed, it recognizes the device perfectly, and I also tried using asoundconf which recognized the device, and set it to default but still wouldn't help.

I think it must be a conflict with my other, built in, sound card, but I can't disable it because it's a laptop.

Thanks,  
Eyal

---

### Post by tsphere on 2008-08-09
Nobody's experienced this kind of thing?

---

### Post by lavadisco on 2008-08-09
I have experienced the same thing. I have googled everywhere and can't find a way to fix it. When I select "USB Audio" under the sound preferences, then I try to play an mp3, whatever playback program I'm using (tried multiple) just crashes and disappears.

---

### Post by cult hero on 2008-08-09
Can you disable the onboard sound via your BIOS?

And what does "aplay -l" result in?

---

### Post by tsphere on 2008-08-10
aplay -l recognizes the card.
I modified the modules file to put usb audio in higher priority, and now whenever I play a file it just crashes.

It appears, lavadisco, that we're on the same boat. Surely this can be fixed. Do you have the same soundcard, or a different one?

---

### Post by tsphere on 2008-08-11
well, this is resolved.
What I did was change edit modprobe.d file and indexed the usb sound device ahead of the other devices, so now it is the default and works.

I sometimes have issues when the device isn't connected that my onboard device doesn't get loaded automatically.
Found some guides on ALSA to using multiple cards but they are not very comprehensible to a layman like me. Will dig deeper, maybe post a layman guide if I ever understand it well enough.

---

