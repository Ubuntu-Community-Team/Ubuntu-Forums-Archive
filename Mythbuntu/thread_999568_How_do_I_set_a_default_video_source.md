---
title: "How do I set a default video source?"
date: 2008-12-02
forum: Mythbuntu
---

### Post by ebike on 2008-12-02
Hi All,

I have two video sources, Freeview Satellite and Freeview Terrestrial.
At the moment when I goto watch LiveTV it defaults to the satellite card, I want to change that to the Terrestrial Card but see no setup option to do that. 

I also want to prefer that card for recordings. I may have that sorted though as I see you can set the channels on that card a higher priority on the record priorities setup menu.

Anyone know how to set it for LiveTV

Thanks.

---

### Post by danbodoh on 2008-12-02
In the backend setup, "Input Connections" (I believe) you can set a priority number for each connection.  The connection with the highest priority number for the requested station is chosen.

Dan Bodoh

---

### Post by ebike on 2008-12-02
Thanks Dan,

Will try that tonight ... cheers :D

---

### Post by ebike on 2008-12-02
Ok, well that made no difference at all. Any other suggestions?

---

### Post by novellahub on 2008-12-03
In mythtv-setup there is a option of making a tuner higher priority than the others.  Another option would be to delete all your tuners and re-add them in the order you like.

---

### Post by ebike on 2008-12-03
Hi,

Well thanks, but your 1st suggestion was covered by danbodoh and it didn't make any difference hence the reason I kept asking ...

Your second suggestion has merit, I just didn't want to go through the work of tuning in both cards again, editing all my channel numbers, setting up icon paths for each channel etc .... if I didn't have to.

So any simple way of doing it?

---

### Post by novellahub on 2008-12-04
> **ebike said:**
> Hi,

Well thanks, but your 1st suggestion was covered by danbodoh and it didn't make any difference hence the reason I kept asking ...

Your second suggestion has merit, I just didn't want to go through the work of tuning in both cards again, editing all my channel numbers, setting up icon paths for each channel etc .... if I didn't have to.

So any simple way of doing it?

If you delete the tuners and not the video sources, you will keep your custom settings.  Just delete all the tuners, add then in the order you like, then assign the video sources in the input connections again.

---

