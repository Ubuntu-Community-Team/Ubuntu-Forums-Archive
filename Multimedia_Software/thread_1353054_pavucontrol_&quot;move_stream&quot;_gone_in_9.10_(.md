---
title: "pavucontrol &quot;move stream&quot; gone in 9.10 (Karmic)"
date: 2009-12-12
forum: Multimedia Software
---

### Post by rknop on 2009-12-12
In 9.04, the great program pavucontrol that let you control the devices and streams of pulseaudio had an option "move stream" for each stream that let you specify to which output device sound went, and from which input device sound came.

In 9.10, I do not see this option.  If you right-click on the stream name, you get "Terminate Stream", but no move stream.  Unfortunately, there's some caching somewhere (does anybody know where that is?) that remembers specific programs.  On a laptop, where sometimes you have a USB device plugged in and sometimes you don't, you don't always want the same program going to the same stream.  However, setting the "fallback" stream isn't good enough, it seems.

This is a huge functionality loss for pavucontrol.  Is there another utility that will let me move pulseaudio streams to different devices?  Or, is there some way to get this back with pavucontrol?

---

### Post by Endolith on 2009-12-12
It's still there, but now it's a button that shows the current device.  You click the button and it gives a drop-down for selecting other devices.  It still changes and mutes completely randomly, though, and the "set as fallback" is more confusing than "set as default".

---

### Post by rknop on 2009-12-12
> **Endolith said:**
> It's still there, but now it's a button that shows the current device.  You click the button and it gives a drop-down for selecting other devices.  It still changes and mutes completely randomly, though, and the "set as fallback" is more confusing than "set as default".

Hmm -- that's what I would have thought, but when I cilck on that button, the other sound card is never listed.

---

### Post by mooreted on 2010-02-25
Same problem here. The buttons don't work. There doesn't seem to be a solution.

---

### Post by Endolith on 2010-02-25
I think it doesn't give you the ability to change it if there's only one option to choose from.  If you have more than one device, the button lets you redirect the streams.

---

### Post by mooreted on 2010-02-25
For me: two streams shows two buttons and clicking them does nothing. If you click really fast over and over you might get the switch stream dialog to open, but usually it wont.

---

