---
title: "Maximum volume not high enough"
date: 2009-08-26
forum: Multimedia Software
---

### Post by gobberpooper on 2009-08-26
When I'm listening to music on my computer or watching a movie, the volume is slightly low. I turn the volume up to the max but it's still not high enough, especially when other people are watching TV. It's not like situations where the sound is almost completely inaudible. I can hear it but it's just not loud enough. On Windows mid-volume was more than enough. I'm using ALSA, if that has to do with anything

---

### Post by inobe on 2009-08-26
click volume and open volume control, raise pcm.

---

### Post by gobberpooper on 2009-08-27
> **inobe said:**
> click volume and open volume control, raise pcm.

it's already at the max

---

### Post by Donalb on 2009-08-28
I have the same issue. I added Intrepid to a friend's 1 yo Dell entry level Inspiron. Sound is perfect in Vista so it's not hardware. Everything is set to max in 'buntu but the volume is still low.

---

### Post by Shibblet on 2009-08-28
> **Donalb said:**
> I have the same issue. I added Intrepid to a friend's 1 yo Dell entry level Inspiron. Sound is perfect in Vista so it's not hardware. Everything is set to max in 'buntu but the volume is still low.

Windows over-gains the signal in order to achieve a higher volume level.

This isn't a problem on desktops, as external speakers usually have a volume control.  But on laptop speakers, you get what you get.

---

### Post by Hogosha on 2009-08-28
yeah, i have the same issue, max volume is audible to me only, anyone beyond the user in front of the computer can't hear a thing. even when the volume is at half i cannot hear it at all.

---

### Post by benerivo on 2009-08-28
You could try changing from alsa to oss4, which i have heard can produce a louder max volume. I know it does on my laptop. Have a look [here...]("https://help.ubuntu.com/community/OpenSound")

---

### Post by gobberpooper on 2009-08-29
Thanks. I'll take a look at that. VLC can raise the volume up to 400% so I'm using that right now. 200% is more than enough though.

---

### Post by fishbulb1022 on 2009-12-14
For anyone dual booting with windows (possibly anything else as well) make sure the volume in windows is not muted (or likely, even low) when you shut down. It sounds dumb, but my brother had problems for months with this before he figured it out.

---

