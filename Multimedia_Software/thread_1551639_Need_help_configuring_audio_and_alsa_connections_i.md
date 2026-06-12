---
title: "Need help configuring audio and alsa connections in JACK"
date: 2010-08-12
forum: Multimedia Software
---

### Post by WallaWalla22 on 2010-08-12
Hey all,
So I'm trying to record my digital keyboard through it's line out. The sound now comes out my speakers when I play notes but I am almost positive I don't have the connections in Jack configured properly because I'm not getting anything in the mixer in Ardour when I play notes. If anyone could help clarify what I need to do in the Audio and Alsa tabs in Jack that would be great!!!

---

### Post by Zeike on 2010-08-12
> **WallaWalla22 said:**
> Hey all,
So I'm trying to record my digital keyboard through it's line out. The sound now comes out my speakers when I play notes but I am almost positive I don't have the connections in Jack configured properly because I'm not getting anything in the mixer in Ardour when I play notes. If anyone could help clarify what I need to do in the Audio and Alsa tabs in Jack that would be great!!!

Is this a regular keyboard or MIDI controller?

If it is the former like you say, all you have to do is (in the jack connections dialog) drag the recording-input (should be in the left column) that your keyboard is connected to onto whatever track you want to record into in ardour (should be in the right column).

I don't think you should have to do anything in the alsa tab.

---

### Post by WallaWalla22 on 2010-08-12
Yes, it is a regular keyboard, not a MIDI.
Here is the screenshot of my connections...

---

### Post by WallaWalla22 on 2010-08-16
bump

Can anyone please tell me, based on my screenshot, what I am doing wrong with my JACK connections?
Thank you!

---

