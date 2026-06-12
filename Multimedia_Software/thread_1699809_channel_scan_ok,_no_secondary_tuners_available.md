---
title: "channel scan ok, no secondary tuners available"
date: 2011-03-04
forum: Multimedia Software
---

### Post by vidtek on 2011-03-04
I have a Backend running Mythbuntu 23 fixes and a kubuntu frontend with the same.

Backend Divico PCI HDTV and Compro U300 USB DTV

Frontend/secondary Hauppauge 2200

For some reason  the frontend secondary scans channels and populates the database, but those tuners are not available to mythtv which only sees the backend tuners.

exerpt from backend log:

2011-03-04 18:29:45.372 mythbackend: MythBackend started as a slave backend 2011-03-04 18:29:45.481 MythBackend, Error: No valid capture cards are defined in the database.

Everything else works ok.

I have tried completely purging Mythtv from the secondary/frontend and re-installing with no effect.
Also resetting video inputs and binding to the capture card until I'm blue in the face.

Anyone got any ideas?
 
Tony.

---

