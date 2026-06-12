---
title: "Problem using Bluetooth device with ALSA"
date: 2012-03-16
forum: Multimedia Software
---

### Post by BlackWidower on 2012-03-16
Here's what I got: A set of Bluetooth speakers (Creative D100, though I doubt it matters) paired with my system using bluez and managed using ALSA.

I might be getting the terms wrong but I set this up several months ago.

This works fine with VLC, which is what I use most of the time.  But only if I use this command:

```
vlc --aout alsa --alsa-audio-device bluetooth
```

Which is fine because I do almost all of my work on this system through the command line anyway, and setting up aliases is pretty easy.  The problem arises when I try to use an application other than VLC.  Like, for example, Chromium.  If I want to play a video using my favourite web browser, I get no sound.

The problem is: bluetooth isn't listed in...anywhere...  It's not listed in the mixer nor can I call it up manually.  I checked '/proc/asound/cards' and it's not there either.  I don't know what to do!

Now, I know there are a few solutions I could use:  I could switch to wired speakers, but I don't have any that are worth anything.  I also don't have a cable that can make my speakers wired.  I could switch to Pulse Audio, but I don't like Pulse Audio.  Primarily because (if memory serves) ALSA is needed anyway for what I'm trying to do.  I'd rather have the two just interface directly.  Besides, I don't see a reason why this couldn't work.

So I guess in the end my question is this: How can I add bluetooth to the list of ALSA sound devices?  I know it works, so how can I tell ALSA that?

---

### Post by BlackWidower on 2012-03-18
No one can help?  Please, I'm really stuck.

---

