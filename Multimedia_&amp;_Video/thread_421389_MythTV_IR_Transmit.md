---
title: "MythTV IR Transmit"
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by SyvanX on 2007-04-24
I just upgraded to feisty and after rebuilding the lirc modules, my serial ir transmitter no longer makes my cable box change channels.  It just blinks over and over again.

I had this problem before, but I just went back to a kernel version that supports this.  I think my cable box might be the problem if the new lirc is more specific to certain frequencies, is this the case?  I've tried all the frequencies I can find for the box.

If anyone has any advice it would be greatly appreciated.

---

### Post by SyvanX on 2007-04-24
alright...  I fixed it.

Turns out a carrier signal needs to be selected in the configuration.  I might just be the one n00b that screws it up, but I didn't see anything in the lirc-howto on help.ubuntu.com.  It might be a worthwhile addition if this is in fact something that should be selected.

---

