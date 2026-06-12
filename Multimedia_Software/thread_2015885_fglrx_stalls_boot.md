---
title: "fglrx stalls boot"
date: 2012-07-03
forum: Multimedia Software
---

### Post by AshenShugar on 2012-07-03
At a certain point in my boot, xorg goes into uninterruptible sleep waiting for the Radeon GPU, which should be disabled as I'm in igpu mode. There is a six-second jump in the X.org log file which corresponds exactly to the sleep and which always occurs between the same two lines in the fglrx calls. This is causing my Linux system to boot SLOWER than windows! THIS CANNOT BE!

Computer: Samsung 700Z5B
OS: Ubuntu 12.04 LTS
Kernel Version: 3.2.0-26
Catalyst Version 12.6, but 12.4 had the same issue
Radeon HD 6400M

---

