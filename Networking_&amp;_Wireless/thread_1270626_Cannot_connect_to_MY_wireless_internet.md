---
title: "Cannot connect to MY wireless internet"
date: 2009-09-19
forum: Networking &amp; Wireless
---

### Post by tyqre on 2009-09-19
I cant connect to my wireless internet. The funny thing is that i can connect to my neighbors wireless internet but not mine. I have no idea why. My signal is a Wireless G and my adapter is a PCIe slot card. Please Help.:KS

---

### Post by marshag63 on 2009-09-19
In a terminal try this command to see all the signals available and what encryption and strength:

sudo iwlist scan

Maybe its just a password issue?

MarshaG.

---

### Post by tyqre on 2009-09-19
it is not a password issue. I know the password and everything. I also know my neibors password and it works when i enter it. Both of our signals are being found its just when i asks for my password i enter it and then about 5 minutes later it asks me for my password again. I AM CERTAIN that i entered my password correctly.

---

### Post by dunkar70 on 2009-09-19
When reviewing the results of the iwlist command, make sure your network is on a unique channel. If one of your neighbors has a network on the same channel, they will interfere with each other. If your network channel is unique, try changing it to a different (but still unique) value.

Another thing to check is that your access point is not too close to other electronic equipment. Make sure you do not have your AP next to a wireless phone, unshielded speakers, wire shelves, florescent lights, running water, or large metal objects like a furnace. All of these can contribute to interference.

---

