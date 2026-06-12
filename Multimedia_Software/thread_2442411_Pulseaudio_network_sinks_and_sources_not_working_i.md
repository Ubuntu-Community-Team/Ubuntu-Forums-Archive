---
title: "Pulseaudio network sinks and sources not working in ubuntu 20.04"
date: 2020-05-03
forum: Multimedia Software
---

### Post by DVoid on 2020-05-03
Hi All,
   I can't seem to get pulseaudio network sinks and sources working in ubuntu 20.04.

All the checkboxes in paprefs are disabled and unclickable in 20.04 (this wasn't the case before I upgraded). I have also tried manually installing the zeroconf pulseaudio module, and uncommenting the following in /etc/pulse/default.pa:
```
load-module module-esound-protocol-tcp
load-module module-native-protocol-tcp
load-module module-zeroconf-publish
```

but still nothing.

Does anyone know what the new process for enabling network sound is? It's really the best thing about pulseaudio and I can't get it to work anymore.

I'm using vanilla ubuntu.

---

### Post by Autodave on 2020-05-04
I am wondering if the upgrade caused the issue: I learned a looooong time ago that upgrades from one LTS to the next LTS seldom work.

Make a bootable DVD or USB stick with 20.04 on it and boot to that and see if it works.  If it does, then you know that something got borked during the update.  Report back.

---

### Post by DVoid on 2020-05-05
Hi Dave - I only updated from 19.10, not LTS. But I just tried as you suggested running a bootable USB, and it has the exact same problem.

Is paprefs working for anybody on 20.04? It's in the universe repository.

---

### Post by DVoid on 2020-05-05
So it turns out paprefs is looking for modules in the wrong place, and this is a bug: [https://bugs.launchpad.net/ubuntu/+source/paprefs/+bug/1871899](https://bugs.launchpad.net/ubuntu/+source/paprefs/+bug/1871899)

A current workaround is to run
```
sudo ln -s /usr/lib/pulse-13.99.1 /usr/lib/pulse-13.99
```

---

### Post by TheFu on 2020-05-05
Please mark the thread "SOLVED" using the thread tools near the top of the page to save time for people seeking help. Thanks.

---

### Post by DVoid on 2020-10-24
Hi, 
just a quick note for anyone looking to say that this bug still exists in 20.10 groovy. To fix in 20.10 please use:

sudo ln -s /usr/lib/pulse-13.99.2 /usr/lib/pulse-13.99

---

