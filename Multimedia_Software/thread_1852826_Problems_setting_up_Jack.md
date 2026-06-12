---
title: "Problems setting up Jack"
date: 2011-10-01
forum: Multimedia Software
---

### Post by Tallguitarguy on 2011-10-01
I'm having trouble setting up Jack. I want to record using a USB microphone, which is hw:1 in the inputs, but whenever I select it, JACK has errors while starting. I'm also fairly certain that I want to use ALSA, but whatever helps. Also, does Ardour automatically go by the input from jack? I've attached screenshots of my current settings and the error message. So far I've got the latency down from 67.9ms to 2.something.

---

### Post by JayPeeJay on 2011-10-01
Try unchecking the real time box.  From what I understand the realtime adds higher priority to your soundcard, which in this case may not work since it is not your selected input.

You might also try setting the input to default or your sound card, and seeing if it will let you make the connection from the usb mic to Ardour in the Jack connections or patchbay.

---

### Post by Tallguitarguy on 2011-10-01
I've tried without realtime. The problem is that I don't know what's going on in patchbay or connections, because it doesn't let me select the usb mic anywhere.

---

