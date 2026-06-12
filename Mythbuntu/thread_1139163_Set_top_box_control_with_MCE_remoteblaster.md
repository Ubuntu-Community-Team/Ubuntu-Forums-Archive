---
title: "Set top box control with MCE remote/blaster"
date: 2009-04-26
forum: Mythbuntu
---

### Post by Brasil on 2009-04-26
G'day, simple question - having trouble getting the blaster to work with my Pace (optus/foxtel) cable tv box.

I have Mythbuntu 9.04 set up, I have enabled the remote in Mythbuntu control centre - works fine. I have the new MCE remote, plugged into the USB. I have tried the blaster plugged into both ports one and two on the IR receiver. I have enabled the MCE Sky satellite transmitter in mythbuntu control centre. I've got Foxtel feeding in via the S-Video port (no problems there), and I've used the scripts off this page [http://www.ozmyth.com/wiki/Setting+u...nels+in+MythTV](http://www.ozmyth.com/wiki/Setting+u...nels+in+MythTV) to get all the foxtel channels names into Myth. I tried the changefoxtel script suggested on the page, didn't work for me.


I haven't yet configured a grabber (shepherd most likely) but I figure that is neither here nor there. My issue is that when I put in a foxttel channel number, everything looks correct (ie the number and name come up on the screen) but the signal is not being sent to the blaster. My guess is I'm missing something really obvious - how does myth "know" to send certain channels to the blaster? Is there a checkbox or something? Or perhaps the Sky Satellite transmitter is not the same as the Foxtel transmitter (I think both are a PACE box...). I have added /usr/local/bin/change-channel-lirc.sh to "External channel change command" to no avail.

I've read everything I can find that might be relevant, but can't figure this out.

Anyway, thanks in advance!

---

### Post by nickrout on 2009-04-27
edit, srcub that i just read your message properly.

---

### Post by Brasil on 2009-04-27
Guess it wasn't so simple after all!

---

