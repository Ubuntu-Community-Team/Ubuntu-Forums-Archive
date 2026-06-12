---
title: "GPSD reconfigured my GPS"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by geking on 2009-07-20
I have a Bu-353 GPS, and have used it for quite a while in windows.  (Mappoint, Netstumbler... all worked with NMEA and worked well.)  I have been using ubuntu for about 6 months and I decided to give the same thing a shot in Linux.

Loaded GPSD, GPSDrive, and Kismet.  I got all of them working just fine.  When I went to use my gps with windows again, it would not connect.  Looking at the data, it is NOT NMEA and is all garbled.  Turns out, I should have used -b in gpsd as it reconfigured my gps.

SO, the burning question I have is: How can I set my GPS back to the NMEA protocal?

Thank you very much in advance.
Rob

---

### Post by geking on 2009-07-21
So I tried sending some commands to the GPS, $PSRF100,1,4800,8,1,0*0E plus the term, but that does nothing.

I am running out of ideas short of cracking it open and pulling the battery, any help would be great.

Rob

---

