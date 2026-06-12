---
title: "Laptop built in microphone not working"
date: 2012-08-04
forum: Multimedia Software
---

### Post by stormshot on 2012-08-04
I have installed Ubuntu 10.04 LTS on my toshiba satellite m300d laptop. I have been having trouble getting the built-in microphone to work. I have been looking through the forums but none of their fixes have been working for my problem. Any help would be greatly appreciated.

---

### Post by b12nd0n on 2012-10-03
I'm currently on a Toshiba Satellite too with the same problem.

I'm actually running 12.10 beta 2 though, so I dont know if it's a beta problem or what.

---

### Post by Yellow Pasque on 2012-10-04
> **b12nd0n said:**
> I'm currently on a Toshiba Satellite too with the same problem.

Make sure it's not an inverted mic: > Install the pavucontrol application, start it and go to the “Input Devices” tab. Unlock the channels (click the keylock icon), then mute the right channel while keeping the left channel at the volume you want.
If the internal mic is now working correctly, you have an inverted internal mic, so that your right channel cancels out the left one. (Why the hardware is constructed that way is beyond me.)
This seems to be most common on Acer Aspire laptops, but I’ve seen them on other laptops as well, and fixing these are more of a long term project as they are non-trivial kernel patches. So far I’ve created a patch for Thinkpad U300s. Anyway, I would like to track the remaining ones in bug 1002978, so please add your system there according to the instructions.



---

### Post by mathsgeek on 2012-10-15
Please delete/remove this post...it was a user issue with some software...sorry my bad

---

