---
title: "n00b need help with remote"
date: 2009-03-31
forum: Mythbuntu
---

### Post by DonMegel on 2009-03-31
Yeah. Feel completely lost with linux. Just installed Mythbuntu and am having a slew of issues. However, this thread is about the remote and IR receiver. I have a spare remote and USB IR receiver that came with a windows media center PC. Can I use these with my Mythbuntu box? If so, how?

Thank you in advance.

---

### Post by nickrout on 2009-03-31
type ```
lsusb
``` in a terminal and check if its a Philips or a Microsoft receiver device.

Then go into mythbuntu-control-center and choose infrared devices, then choose one of the Windows Media Centre remotes. Click your way out and it should then work.

---

### Post by DonMegel on 2009-04-01
Well, its a Philips, V2 WMC remote/transmitter.

There are several Windows media center trasmitter options in the control center but that all say things like Pioneer cable box, Dish Reciever, Direct TV reciever, etc.

There is a good profile for the remote though.

---

### Post by DonMegel on 2009-04-01
Ok, I unchecked the IR transmitter part and just enabled the Remote settings and it works like a charm. Heheheh, Im kinda excited.

---

### Post by nickrout on 2009-04-01
transmitter is only useful if you are trying to control another device via infrared. eg contolling a set top box by transmitting an ir signal to change channel.

---

### Post by DonMegel on 2009-04-01
Good to know, thanks

---

### Post by Nobodyspeshul on 2009-04-01
> **DonMegel said:**
> Good to know, thanks

Ditto.

IN BRIGHT YELLOW, DEAR GOD MY EYES!!!

---

