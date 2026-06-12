---
title: "Audio Skipping in Ubuntu 10.10"
date: 2010-10-16
forum: Multimedia Software
---

### Post by Scooter89 on 2010-10-16
I upgraded to Ubuntu 10.10 on my Macbook and now I am noticing that when I'm listening to audio via web browser or banshee, it makes a skip like noise every 10 or 15 seconds. I do not notice this issue when playing games or anything else. Ideas? :confused:

---

### Post by lidex on 2010-10-16
Try removing your old pulse config files:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Logout/in.**

---

### Post by jmatties on 2010-10-19
I am having the same problem on a fresh install.

On another thread:
> **NightwishFan said:**
> Bug Report: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/621430?comments=all](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/621430?comments=all)

Workaround for glitchy (crackling, skipping) audio is to open:
/etc/pulse/default.pa

Find the line that looks like this and add "tsched=0".
```
load-module module-udev-detect
```

It should look like this:
```
load-module module-udev-detect tsched=0
```

Save and reboot (or just log out).


Note this will not fix a problem with that specific chipset in the bug report with a muted speaker/headphone. I have no idea where to go with that one. Lidex and I have been trying to figure it out.

But this made it worse :(.

---

### Post by Larry_Underwood on 2011-03-25
Hello, I am having the same problem it just started this morning. I have no idea what to do i tried /etc/pulse/default.pa and it said i do not have permission to do that. I have tried a couple other things from another thread that said the destination doesn't exist.

I am a complete newb with linux.

---

### Post by haintwru on 2011-03-25
use old verson

---

### Post by Yellow Pasque on 2011-03-25
Try the gstreamer PPA: [https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

---

### Post by Larry_Underwood on 2011-03-26
My audio came back yesterday but now it is gone again today

---

### Post by lidex on 2011-03-31
Try a suspend/resume cycle. What is your kernel:
```
uname -r
```

---

