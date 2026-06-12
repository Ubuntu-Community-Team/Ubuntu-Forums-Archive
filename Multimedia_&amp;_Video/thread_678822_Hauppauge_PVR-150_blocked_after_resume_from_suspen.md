---
title: "Hauppauge PVR-150 blocked after resume from suspend"
date: 2008-01-26
forum: Multimedia &amp; Video
---

### Post by mclusky on 2008-01-26
I need some advice how to properly resume TV card (Hauppauge PVR-150) from suspend.
I use ivtv drivers under FF 7.04.
To bring PVR-150 back to work after resume I do easy trick before suspend:
```
sudo rmmod ivtv
```

and after resume I do:
```
sudo modprobe ivtv
```

It works for 1-2 suspending in the row, after next suspend I get an error message trying to access TV card. It is important to me to be able to control recording process from script, and suspending PC during the time between recordings - that is why I don't consider restarting PC to establish access to TV Card again (in fact I'm forced to do it very often). 
Also, I don't consider to upgrade my Ubuntu to 7.10, because it don't support 's2ram' suspend method.

---

