---
title: "mp3 codec problems. distorted &quot;midi&quot; sound quality"
date: 2009-02-18
forum: Multimedia Software
---

### Post by trowsey on 2009-02-18
I'm a complete deb newb, and never had to deal with audio codecs before, they've always worked right after install (fedora) or atleast when I've gotten the sound drivers installed. 

Right now my sound quality while playing mp3s are horrible. I was using rhythmbox but now using banshee, but it seems its using the same codecs cause nothing has changed. It's sounding distorted and or like its a midi or on an 8 bit N system. Sounds about as good as a ringback tone from a crappy phone.

Any ideas? Like i said, i'm new with codecs and new with deb style linux's

Thanks for any and all help =)

---

### Post by mcduck on 2009-02-18
Check through all sound devices in the Volume Control dialog and make sure you haven't got master channels on all devices at 100%. That will almost always lead to distorted sound.
 (Most commonly the channels you'd be interested are Master, PCM and Front, on all available  playback devices.)

Off topic: MIDI is as high quality as sound data can possibly be. It's just a question of using high-quality tools to render it to audio.. ;)

---

