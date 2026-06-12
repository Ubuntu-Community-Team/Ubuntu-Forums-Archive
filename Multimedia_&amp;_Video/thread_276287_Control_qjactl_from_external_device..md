---
title: "Control qjactl from external device."
date: 2006-10-12
forum: Multimedia &amp; Video
---

### Post by CadetD on 2006-10-12
I have an M-audio Keystation 88 midi controller. 

Is there a way to control jack via the external device? For example, instead of clicking the start / pause / rewind on qjackctl, I would press the corresponding buttons on the external midi controller. 

The keyboard is fully customizable to assign any key to any midi control event.

---

### Post by dolson on 2006-10-14
I am not aware of such a feature. You may wish to request it.

However, I think that you could do it with some applications that hook into the JACK transport.

Ardour can bind MIDI events to particular things in the interface, and so you should be able to use your board, if you are using Ardour. If you aren't, then see if whatever apps you are using can do it.

---

