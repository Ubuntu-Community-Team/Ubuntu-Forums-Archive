---
title: "No sound after trying all suggested fixes"
date: 2007-07-15
forum: Multimedia &amp; Video
---

### Post by fedira on 2007-07-15
Hi, 

When I first installed Feisty (about 3 weeks ago), my sound worked fine from the get-go. I installed the codecs I wanted, and still no problems. Then one day, about a week ago, it stopped working. When I went into alsamixer, it turned out the master volume had been muted (somehow); I unmuted and all was well.

Now, after coming back from a hibernate, all sound is gone. I rebooted and nothing, not even a login sound. 

Here's what I've tried so far:

```
aplay -l
```
returns:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Even though sound card seemed to fine, I tried a purge/reinstall anyway:

```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils
```

I rebooted and still nothing. I went into alsamixer, turned everything way up, made sure nothing was muted, and still nothing.

I tried
```
grep 'audio' /etc/group
```
and my username was found.

I also tried: 
```
sudo apt-get update && sudo aptitude dist-upgrade
reboot
```
with no luck.

I tried booting into Windows, and suddenly I have no sound there either, even though this laptop is nearly brand new. 

In case it's relevant:
```
cat /proc/asound/modules
 0 snd_hda_intel
```

I'm only a newbie, all of these steps came from the [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449") or other forum posts, and now I don't know what else to try. I can't stand not having sound, since I listen to music constantly. 

Any ideas? What can I try next? I'd be infinitely grateful for any help. Thank you!

---

### Post by Jeff Sell on 2007-07-15
I have the exact same issue, except that my sound works when I run windows. I posted a thread saying this, and that I've tried everything, only to have 3 different people tell me to unmute my sound. What kind of laptop are you running? I have a Toshiba Satellite P105.
The one thing that almost kind of worked was to turn my acpi off.

---

### Post by Jeff Sell on 2007-07-15
You might have some luck with this fix if you haven't tried it already. It didn't work for me, but it seems that it has for others.
[http://www.linuxforums.org/forum/peripherals-hardware/96259-toshiba-p100-series-sound-fix-ubuntu.html](http://www.linuxforums.org/forum/peripherals-hardware/96259-toshiba-p100-series-sound-fix-ubuntu.html)

---

### Post by fedira on 2007-07-15
Hmm, thanks for replying. I have a Thinkpad X60s though, not a Toshiba. Do you also have an Intel soundcard though?

This is so frustrating...

I also just remembered that I recently installed MPlayer & the Mplayer plugin -- would this have any effect?

Also, what's "turning acpi off"? What does that do & how do I try that? Thanks!

---

### Post by DM was on fire! on 2007-07-15
It wouldn't explain why the sound on your Windows computer isn't working. 
Maybe your speakers or sound card quit, is the only thing I can think of.

---

### Post by fedira on 2007-07-15
> **DM was on fire! said:**
> It wouldn't explain why the sound on your Windows computer isn't working. 
Maybe your speakers or sound card quit, is the only thing I can think of.
Is there any way though that things getting messed around with Ubuntu could have created problems with my soundcard so that it doesn't work in Windows either? This computer is only a MONTH old, and it's a Thinkpad -- I can't imagine that it would be having such serious hardware problems so soon. It's not like I dropped it down a mountain.

Are there any other things I can test to see what's going on here? I'm getting pretty desperate...

---

### Post by fedira on 2007-07-15
Could this bug be related, since I also lost sound after hibernate?
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/104712](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/104712)

---

