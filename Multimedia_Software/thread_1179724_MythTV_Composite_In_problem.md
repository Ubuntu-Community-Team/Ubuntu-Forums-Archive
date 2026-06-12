---
title: "MythTV Composite In problem"
date: 2009-06-05
forum: Multimedia Software
---

### Post by TheIdiotThatIsMe on 2009-06-05
Hi guys, I recently bought a KWorld TV Terminator card for playing game systems on my computer. I put in the card, and added the driver module to be autoloaded on boot, and then run mythtv-setup.

Under Capture Card, I have it set to Analog, and it detects the card. The VBI and video devices match what it shows in dmesg (video0 and vbi0). The default input is set to composite1. 

Under video sources, I made one and named it KWorld Composite. I changed the listings grabber to no grabber, since I don't have cable or anything hooked up to it. And the Channel frequency table is set to default.

Under Input connections, I have Composite1 -> KWorld Composite. The video source is KWorld Composite, starting channel set to 4, both input groups are set to "generic".

Under Channel Editor, I have on Channel, which is channel 4, set to callsign 100, input source KWorld Composite, tv format default, priority 0, no filters, nothing set to frequency/channel option in the GUI.

When I start the backend and then start the frontend, I turn on the console with it's video composite plugged in, and all I get is a black screen.

Any ideas? :popcorn:

---

### Post by TheIdiotThatIsMe on 2009-06-06
Does anyone know of any other information that may help? ):P

---

