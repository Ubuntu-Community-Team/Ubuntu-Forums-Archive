---
title: "[SOLVED] driver trouble with new Kernel"
date: 2008-09-14
forum: Mythbuntu
---

### Post by Crash87ss on 2008-09-14
I installed mythbuntu 8.04 in a new machine, got everything up and running using a pinnacle 800i tuner card.

I then did the the upgrade to 8.04.1 and the 800i card is no longer recognized. I added the firmware to the new kernel directory and tried to 'make' the v4l-dvb driver, however the make command tries to use the old kernel directory, 2.6.24-16 generic/build, which it says does not exist. 

Everything still works if I book into the old kernel. 

Any clue? bug maybe?

---

### Post by covert on 2008-09-16
Try 

make KDIR=/path/to/the/correct/kernel/headers

---

### Post by Crash87ss on 2008-09-18
I got it figuered out.. It was my own laziness at fault. 

The update broke the 800i driver. When i tried to re-install it I used the old files from the trash.. which didn't work.

Everything worked good once I downloaded the v4l drivers (deleting the ones I had) and proper firmaware and installed as-if they were never there. I also had to reomve some devices included with the kernel, there is a post on what to do, but I can't get to it now.

---

