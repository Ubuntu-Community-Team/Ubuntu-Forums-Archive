---
title: "Volume Control - noob here"
date: 2007-03-02
forum: Multimedia &amp; Video
---

### Post by detroit/zero on 2007-03-02
I have an issue with volume control. I searched posts for something similar but ran out of steam.

I have a Creatve Sound Blaster Audigy LS. I actually have sound, and it's of a very nice quality. The on-screen volume controls don't work, though. Even when using the volume buttons on my keyboard, a slider pops up and moves according to what I'm trying to do, but the actual volume remains unaffected. The "mute" function works both from the keyboard and from the on-secreen control, however.

I notice that from System > Preferences > Sessions, when I check the startup options, the Gnome Volume Manager has the option --sm-disable, but I don't want to go making changes when  I don't know what they do.

Just wondering if anyone has any ideas.

Thanks

---

### Post by jfinkels on 2007-03-02
in the terminal type
```
gnome-volume-control
```
or just double click on the volume icon in the panel (does the same thing).

click on "Edit > Preferences" and then enable all the tracks. One of them will change your volume hopefully. On my computer, it happens to be the slider for "Master" and "Master Mono".

---

### Post by detroit/zero on 2007-03-02
OK.. I found the right slider. It happens to be he "front" channel, so that's easy enough to remember. I disabled all the sliders except that one, but the volume-control on the taskbar and the buttons on my keyboard still don't effect the volume. 

From the keyboard, a slider still pops up on the screen and moves whichever way I'm pressing, but the volume doesn't change. Same with the taskbar controls  - I can slide it around all I want, but it has no effect.

Keep the ideas coming...

Thanks.

---

### Post by sisco311 on 2007-03-02
right click on volume control icon
select Preferences
select PCM

---

### Post by detroit/zero on 2007-03-02
That's not an option.

I get to choose between ALSA Mixer and OSS mixer. Neither one makes a difference.

---

### Post by sisco311 on 2007-03-02
select the alsa mixer and under that is a list of tracks:
Headphone
**PCM**
Front
Surround
...

---

### Post by detroit/zero on 2007-03-02
My list of tracks under ALSA is:

> Line In
Microphone
IEC958 Center/LFE 
IEC958 Front
IEC958 Rear
IEC958 Unknown
Aux
Analog Center/LFE
Analog Front (this is the one that actually controls the volume)
Analog Rear
Analog Side
CAPTURE feedback

---

### Post by KucingKelabu on 2007-03-12
Choose that one then :) Like mine, it is the "PCM" one, to yours - perhaps the Analog Front ones.

This only affects the slider at the volume icon though. It doesn't change the behaviour of the keyboard buttons :(

---

### Post by detroit/zero on 2007-03-13
Aha!

That worked. Like you said, it gave me volume control but didn't tie in the keyboard buttons.

I knew it was a simple fix.. I'm just still too fresh out of Windows to have seen it myself.

Thanks for the help!

---

### Post by detroit/zero on 2007-03-14
Well, now that I have that problem out of the way...

Anybody have any ideas on how to tie-in the keyboard buttons to the volume control?

---

### Post by mac.ryan on 2007-04-22
> **detroit/zero said:**
> Anybody have any ideas on how to tie-in the keyboard buttons to the volume control?


Sure: System --> Preference --> Sound --> Default Mixer Tracks
Then you select the one(s) you want to bind to your keyboard... :)

---

