---
title: "Sound From Rosegarden"
date: 2010-11-09
forum: Multimedia Software
---

### Post by cvowen on 2010-11-09
Finally got  sound out of Rosegarden.
While recording midi I could see the bars move but no sound during playback.
I exported Midi file and could play it with Totem.

I went into Rosegarden's Edit/Prefences/Audio tab and checked "Create JACK outputs for individual audio instruments and for submasters"
I don't know if I need both checked.

Also, under the MIDI tab the "Path to "asfxload" or "sfxload command is /usr/bin/asfxload" & the SoundFont path is /usr/share/sounds/sf2/FluidR3_GM.sf2...or whatever .sf2 you'd like.
I had to sudo Nautilus and past the .sf2 because asfxload didn't work for me.

I just wanted to pass this along asap because of the problems users have with creating sound in Linux/Ubuntu.

I'm using the SoudBlaster card with the Emu10k1 chip.
Hope this helps someone!
Thank you Ubuntu.

---

### Post by cvowen on 2010-11-09
For whatever reason I can't edit but I want to add this:
I'm using an old Casio midi capable keyboard connected to the SoundBlaster card via gameport.
JACK - under MIDI Driver enable "seq".

Next is to get Qtractor going, but with Rosegarden up and running I might just forget that.

I havn't rebooted since todays discovery, but I'll report out any other findings.
Cheers.

---

