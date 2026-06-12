---
title: "Video card fan to 100% only on shutdown/restart, not bootup"
date: 2011-09-02
forum: Multimedia Software
---

### Post by fpoe1 on 2011-09-02
Hi all. Any help you could provide on the below situation would be greatly appreciated.

It's more of a nuisance than anything but...

Whenever the restart/shutdown splash screen appears, the video card fan kicks into high gear. The odd thing is the same bootup splash screen does not do this.

Ubuntu 10.04.3 LTS / 2.6.32-33-generic / 32-bit
Card: Nvidia GeForce GTX460
- Running in a dual monitor configuration

Trying to locate the driver version but there are a couple packages installed. I set this desktop up so long ago when I had 0 knowledge (still have very little) that I really don't know what I did back then, anyway...

nvidia-current 195.36.24-0ubuntu1~10.04
nvidia-kernel-common 20080825+1ubuntu2

Card is also running at a cool 44C mostly all the time.

Any ideas? Thanks in advance.

---

### Post by fpoe1 on 2011-09-02
I was able to fix this by adding the Nvidia PPA and updating the drivers from there. Posting this in case anyone runs into this in the future.

As of right now, 280.13 is the current driver for 10.04.3 on the Nvidia PPA and it has fixed this issue.

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

sudo apt-get update && sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings
```

---

