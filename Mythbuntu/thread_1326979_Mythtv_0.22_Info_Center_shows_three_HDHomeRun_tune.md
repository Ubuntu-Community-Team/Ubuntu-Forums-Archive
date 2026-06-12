---
title: "Mythtv 0.22 Info Center shows three HDHomeRun tuners"
date: 2009-11-14
forum: Mythbuntu
---

### Post by Dewey_Oxberger on 2009-11-14
In the backend set up there are only two HDHomeRun tuners on my system.  In the frontend info center it shows three tuners.  Tuner 1 and Tuner 2 point to the same HDHomeRun tuner.  Tuner 3 points to the second HDHomeRun tuner.

So, I have just one HDHomeRun.  It has two tuners.  Mythtv 0.22 (weekly builds) shows three tuners.

Anybody else have this?

---

### Post by kdiebold on 2009-11-15
That's normal - for one of your physical tuners an additional virtual tuner was added. I'd recommend running mythtv-setup and changing the number of virtual tuners to something >1. That's what I did, anyway, and fixes all of the issues that I had with overlapping recordings on the same channel.

See [http://www.mythtv.org/wiki/Multirec]("http://www.mythtv.org/wiki/Multirec")

---

### Post by Dewey_Oxberger on 2009-11-17
Perfect, thanks.

---

### Post by matt06 on 2009-12-20
> **kdiebold said:**
> That's normal - for one of your physical tuners an additional virtual tuner was added. I'd recommend running mythtv-setup and changing the number of virtual tuners to something >1. That's what I did, anyway, and fixes all of the issues that I had with overlapping recordings on the same channel.

See [http://www.mythtv.org/wiki/Multirec]("http://www.mythtv.org/wiki/Multirec")

I have a dual-tuner HDhomerun I will be setting up soon.  What determines the max number of virtual tuners here?

So I take it the HDHR can use "multirec" on both tuners and can theoretically record four shows at once if two of them are on the same "multiplex" as the other two?.  Is that correct?

---

### Post by nickrout on 2009-12-20
yes correct, and the setting for multirec is in the backend setup for the tuner.

It may be able to be more than two virtual tuners per physical tuner. I have my DVB-S tuners set up to be four virtuals each. However the usefulness will depend on how many channels there are per multiplex.

---

