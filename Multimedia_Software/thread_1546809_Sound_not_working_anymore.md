---
title: "Sound not working anymore"
date: 2010-08-05
forum: Multimedia Software
---

### Post by HolyPhoenix on 2010-08-05
Earlier I was in windows to do school that I had to do in windows.  I shut my monitor to suspend my computer, which disables my sound card.  Later on I went back into ubuntu and forgot about it.  Ubuntu had updates to the system and since then I have not been able to get my sound to work.  Please help me get it working again.  I would greatly appreciate it.

---

### Post by lidex on 2010-08-06
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

### Post by HolyPhoenix on 2010-08-07
Thanks for providing help.  I just installed a new update that I saw yesterday in the version of ubuntu that was previous(since grub lets you boot into ubuntu before your update too).  Then read your post and booted back into ubuntu with unworking sound to grab the info.  It works after the update.

But Kudos to you.  I greatly appreciate it and see no reason to bother you with it anymore.

---

