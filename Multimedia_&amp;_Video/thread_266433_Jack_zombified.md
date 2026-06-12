---
title: "Jack zombified?"
date: 2006-09-27
forum: Multimedia &amp; Video
---

### Post by commodore on 2006-09-27
I get that "zombified" error when I'm doing this:
1. Start jack control, vkeybd and zynaddsubfx
2. Start jack
3. Connect the keyboard thingies by the tutorial on the wiki
4. Open up Ardour which makes my computer very slow for a moment and then
5. Ardour says jack is not started and jack shows the zombified error

I didn't compile the real-time kernel (I'm no real musician and I only want to try this so I didn't care :P). Maybe my computer is too old? I have an Athlon 1ghz and 256mb RAM. I can happily use it for anything else (I even did 3d in Blender with it!). My sound card is an integrated VIA 8235 AC'97 :D. I used the settings in the tutorial for jack so maybe that's a problem?

And another question: do Linux musicians make stuff like trance, hardstyle, dance and whatever they are?

---

### Post by dolson on 2006-09-27
As the wiki page says, the settings in the image are for a very specific sound card. You have to try different things on your system, especially WRT the device dropdowns and buffer settings.

Instead of using hw0,1 and hw0,3 or whatever I use, try just setting them both to hw0. And try higher buffer/periods, or a lower sampling rate, etc.

However, you didn't specify if vkeybd and Zyn work fine together or not, so if they do, then JACK settings are maybe not the issue, and I don't know what is.

---

### Post by commodore on 2006-09-27
How do I check if they work together? When I click on the keys in vkeybd the zyn colored bar moves :D.

---

### Post by dolson on 2006-09-27
So MIDI is working, which is handled by ALSA. That's a good first step.

You said you followed the tutorial, and if you did, then you would have connected the audio outputs of ZynAddSubFX to the inputs of ALSA PCM, resulting in you hearing sound in your speakers when you press the Virtual Keyboard's keys. That would mean it's working.

If you get no sound, and the connections are made, something is messed up.

---

### Post by commodore on 2006-09-29
I don't hear the sound :P. And sorry for not replying so long :S

---

