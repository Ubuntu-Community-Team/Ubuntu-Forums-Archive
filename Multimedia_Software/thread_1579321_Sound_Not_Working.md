---
title: "Sound Not Working"
date: 2010-09-21
forum: Multimedia Software
---

### Post by gamehero77 on 2010-09-21
Hi, I've been using Ubuntu for several months now. The sound was working just fine until now. I installed an update I put off that came 9/20/10. I restarted and my sound no longer works. The speakers built into the laptop doesn't work nor do the headphones. I tried going to the preferences to fix it, but my sound card info wasn't there anymore. Dummy Output was in my Output. I've been searching frantically for a solution but found none. I think my driver has been uninstalled some how but I'm not sure. I use the laptop for multimedia purposes, so please respond as soon as possible. I would GREATLY appreciate it. I have Ubuntu 10.04 on my Acer Aspire 5532 laptop.

---

### Post by Herber on 2010-09-21
I am having a similar problem, I tried substituting a known good sound card and still the card is not recognized as installed.  I am using a Dell 8100 desktop.

---

### Post by lkjoel on 2010-09-24
> **gamehero77 said:**
> Hi, I've been using Ubuntu for several months now. The sound was working just fine until now. I installed an update I put off that came 9/20/10. I restarted and my sound no longer works. The speakers built into the laptop doesn't work nor do the headphones. I tried going to the preferences to fix it, but my sound card info wasn't there anymore. Dummy Output was in my Output. I've been searching frantically for a solution but found none. I think my driver has been uninstalled some how but I'm not sure. I use the laptop for multimedia purposes, so please respond as soon as possible. I would GREATLY appreciate it. I have Ubuntu 10.04 on my Acer Aspire 5532 laptop.
Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.

---

### Post by lidex on 2010-09-24
> **gamehero77 said:**
> Hi, I've been using Ubuntu for several months now. The sound was working just fine until now. I installed an update I put off that came 9/20/10. I restarted and my sound no longer works. The speakers built into the laptop doesn't work nor do the headphones. I tried going to the preferences to fix it, but my sound card info wasn't there anymore. Dummy Output was in my Output. I've been searching frantically for a solution but found none. I think my driver has been uninstalled some how but I'm not sure. I use the laptop for multimedia purposes, so please respond as soon as possible. I would GREATLY appreciate it. I have Ubuntu 10.04 on my Acer Aspire 5532 laptop.

Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)
Also these:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```
```
dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```

---

