---
title: "Had sound, lost it"
date: 2012-11-17
forum: Multimedia Software
---

### Post by HerixFromParis on 2012-11-17
Xubuntu 12.04 64-bit

Everything was right, sound and all.

Then I did *something* to mute sound during a TV commercial ... and can not go back. I triple-checked the obvious, and some of the less obvious.

Sounds still is fine with the two other Xubuntu accounts on the same computer.

What "hidden" feature could I have triggered ?

-----------------
Edit 5 minutes later

Funny enough, just after posting the above, I gave it one more try, and found the culprit to be
[Apps Menu] -> Multimedia -> PulseAudio Volume Control
On the [Ouput Devices] tab, the "Built-in audio anolog stereo" was muted.
When I unmuted it, I got my sound back. When I muted it again, unsurprisingly computer went ... well ... mute. The Alsa Mixer panel shown muted accordingly.
More surprising, unmuting from the Alsa Mixer Panel did not bring the sound back, although the panel clearly showd unmutted.
Looks like PulseAudio and Alsa still have to learn to work together.

<rant> I am a big fan of Linux, and have been using it as my primary OS at home for eight years, and also a borderline geek software engineer. I can't believe it's still possible to get trapped by this kind of glitch in a distro that is supposed to be the most user-friendly. Why can't I have one, just one, user friendly, first level sound control interface ?</rant>

---

