---
title: "How to disable front panel jack detection?"
date: 2011-01-17
forum: Multimedia Software
---

### Post by eekhoorn13 on 2011-01-17
Hi,

My audio front panel is not working properly anymore. That is, the jack detection (which notifies the OS when you plug a headphone in) is defect. For it to work I have to push and twist and bend the jack (so it's a hardware problem). Anyway, this was no problem in Linux (Ubuntu 10.04), until I've had to re-install my system (because I got a new hard drive, now Ubuntu 10.10 is installed).

What happened before is that Linux sent an audio signal to the front panel anyway (and not trying to detect whether or not a headphone was plugged in) and I got sound on my headphone. What happens now is that Linux only sends an audio signal to the read panel and when I plug in a headphone in the front panel (and twist and bend the plug), it mutes my rear panel and sends the signal to the front panel (and thus my headphone).

This is a nice feature which most people are trying to get working on their system. My problem is only that automatic detection doesn't work properly, so the OS won't know there's a headphone plugged in. So while the whole world is trying to get this feature working (as Google results on this topic indicate), I'd rather disable it and let PulseAudio send a signal to both rear and front panel, without trying to see if there's really something plugged in. In Windows I managed this by installing a (probably old?) driver which doesn't support the automatic jack detection, thus sending the signal to both panels. But I hope there is some better way of disabling this functionality in Ubuntu? Any help here would be welcome!

---

