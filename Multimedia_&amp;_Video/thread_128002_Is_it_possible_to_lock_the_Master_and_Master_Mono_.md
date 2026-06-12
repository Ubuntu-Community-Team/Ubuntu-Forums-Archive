---
title: "Is it possible to lock the Master and Master Mono levels?"
date: 2006-02-10
forum: Multimedia &amp; Video
---

### Post by K.Mandla on 2006-02-10
I have a Dell XPS M170, and the sound channels between the main speakers and the subwoofer are split between the Master and Master Mono sliders on the Volume Control panel. If I want to change the volume, I have to open the panel and work both sliders individually so the volume doesn't sound distorted.

Is there a way to link those two sliders to move together, so I don't have to wrangle the sound each time I want to turn it up or down? It's not a big deal, so I won't be heartbroken if no one finds a way. :)

---

### Post by tombeharrell on 2006-04-15
[QUOTE=K.Mandla]I have a Dell XPS M170, and the sound channels between the main speakers and the subwoofer are split between the Master and Master Mono sliders on the Volume Control panel. If I want to change the volume, I have to open the panel and work both sliders individually so the volume doesn't sound distorted.[/QUOTE]

Same problem here, I believe it's the same with Inspiron 9300/9400 too. I'm sure I've seen a way of choosing which control becomes the main volume, was it in KDE rather than Gnome?

---

### Post by MDanihy on 2007-05-25
Using Feisty Fawn here.  I set the Master and LFE to a level I like, then I set the volume control buttons to control PCM instead of master, that way I can raise and lower the volume and have the level for all speakers set.

---

### Post by tombeharrell on 2007-05-26
> **MDanihy said:**
> Using Feisty Fawn here.  I set the Master and LFE to a level I like, then I set the volume control buttons to control PCM instead of master, that way I can raise and lower the volume and have the level for all speakers set.

How are you setting the multimedia buttons to control PCM volume? I have made the volume control applet, near the clock, change the PCM, so that works well, but the volume buttons on the front of the laptop still only control master volume (via keyboard shortcuts).

Tom.

---

### Post by Evil Monkey on 2007-05-27
If you right-click on the volume control icon in the system tray and then "Select Master Channel.." and choose PCM.

Jeff

---

### Post by tombeharrell on 2007-05-28
> **Evil Monkey said:**
> If you right-click on the volume control icon in the system tray and then "Select Master Channel.." and choose PCM.

Jeff

Yes that's what I tried, it does affect the volume control's slider, but not the channel the front panel laptop buttons control.

Tom.

---

### Post by voice06 on 2007-06-21
Alright, first post, but I think I may have the solution. I have the same problem, after hours of tinkering I tried going to System -> Preferences -> Sound, then at the bottom where it says ¨Default Mixer Tracks¨  with the Device set to ¨HDA Intel (Alsa mixer)¨ I highlighted ¨PCM¨, somehow that seemed to be the magic fix for me.

---

### Post by tombeharrell on 2007-06-23
> **voice06 said:**
> I have the same problem, after hours of tinkering I tried going to System -> Preferences -> Sound, then at the bottom where it says ¨Default Mixer Tracks¨  with the Device set to ¨HDA Intel (Alsa mixer)¨ I highlighted ¨PCM¨, somehow that seemed to be the magic fix for me.

Ah ha that's the one, it's worked for me - Thanks!

---

### Post by paladin677 on 2007-08-07
Thank you!

---

### Post by tomrob on 2008-01-22
Thank You!!

---

