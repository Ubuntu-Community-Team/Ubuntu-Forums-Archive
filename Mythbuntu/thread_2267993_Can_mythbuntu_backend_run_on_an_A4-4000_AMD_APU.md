---
title: "Can mythbuntu backend run on an A4-4000 AMD APU"
date: 2015-03-05
forum: Mythbuntu
---

### Post by necb on 2015-03-05
I have some computer parts lying around and I wanted to build a mythtv backend/frontend which will sit in my living room and be connected to my tv.  There will only be one other frontend in my bedroom (openelec on a Aspire Revo), so the entire setup will be one backend/frontend running on a machine and another frontend.  I have the following....

AMD A4-4000 APU (3.0 GHz, 128 core GPU)
Gigabyte Mini-Itx GA-F2A88XN-WIFI
2x2GB DDR3-1333 RAM

I still need to purchase a hard drive, case, tv tuner, and power supply.  Do you guys thing Mythtv would run on this?  I have Comcast so for a tuner I was thinking I'd use the Centon InfiniTV 4 PCIe.  Any suggestions/questions would be appreciated.  Thanks!

---

### Post by uteck on 2015-03-05
I was using an Atom CPU with an Nvidia 8400 years ago to run a front-end and it had no problems.  The main thing is to get the proper video drivers installed and configured for use in video playback.  The AMD drivers have been a bit more of a hassle in the past, not sure if that is still true.

---

### Post by necb on 2015-03-05
Thanks uteck.  You mentioned that it would run frontend; what about backend?  This build will have to run the backend and frontend.

---

### Post by uteck on 2015-03-05
Running as a backend is not that demanding, except for processing commercial skips.  Using a tuner that does the video capture and encoding has almost no use on the CPU or memory of the backend.

---

### Post by necb on 2015-03-05
Thanks uteck.  It looks like that setup may work.  I don't think the ceton card I mentioned in my OP captures and encodes, I think it just captures.  I guess I need a tuner card that captures and encodes as long as it takes CableCARD.

EDIT:
I was reading that digital signal, such as the one I get from Comcast, does not require encoding as they are already MPEG-2.  Is this correct?  Would I need a tuner that can capture and decode?

---

### Post by uteck on 2015-03-06
If the signal is MPEG2, then no encoding is needed.  I may have been thinking of some of my older capture cards were encoding was a problem.  My Silicon Dust and Hauppauge both out put MPEG2 as well.  My backend has been stable for so long I have forgotten most of the work I put into it.  That hardware is over 5 years old now.

---

