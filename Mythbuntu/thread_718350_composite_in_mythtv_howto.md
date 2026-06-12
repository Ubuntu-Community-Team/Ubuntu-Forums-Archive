---
title: "composite in mythtv howto"
date: 2008-03-08
forum: Mythbuntu
---

### Post by taehC on 2008-03-08
I have a pvr-500 and i am trying to plug my wii into my comp using mythtv and the inputs on the card.  how do i do this? is it possible?

---

### Post by taehC on 2008-03-08
is there a way?

---

### Post by .nedberg on 2008-03-08
If your card has an input that fits, it should be doable. You would probably have to add a source in mythtv-setup.

---

### Post by ian dobson on 2008-03-08
Hi,

If the PVR-500 supports composite in, you need to define a new tuner and set the input to composite 1.

So, go to mythtv-setup, TV cards, Add new capture card, Card Type "MPEG-2 encoder card (PVR-500)", Select Video Device 1, Default Tuner "composite 1".

The go to video sources and add a new source that points to the tuner you've just created. I imagine that you'll need to create a new channel that points to the video source you've just created.

Regards
Ian Dobson

note: This is all just theory, as I can test it here.

---

