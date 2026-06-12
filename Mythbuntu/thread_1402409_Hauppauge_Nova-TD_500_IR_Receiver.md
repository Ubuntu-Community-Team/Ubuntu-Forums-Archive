---
title: "Hauppauge Nova-TD 500 IR Receiver"
date: 2010-02-09
forum: Mythbuntu
---

### Post by Macka01 on 2010-02-09
Hi,

I finally got around to making up an IR receiver cable from my Hauppauge Nova-TD 500, however I went to test it and found I had no lirc devices.

I tried: sudo mode2 and received a message warning me that the file or path can not be found. I also tried the following:
```
sudo mode2 -d dev/input
sudo mode2 -d devinput
sudo mode2 -d dev/lirc  - and many other variations of that.
```

I repeated the above after stopping lirc service as recommended on [https://answers.launchpad.net/mythbuntu/+question/54983](https://answers.launchpad.net/mythbuntu/+question/54983)

Using: cat /proc/bus/input/devices
I find that it is event6.

At this stage I'd be happy just to have it listening on the correct device, even if my remote is not compatible (Sony RMT-V408).

From what I've read, the kernel will assign a different event# at every boot, however, I am not worried about that at this stage, that can come later, once it's working.

---

