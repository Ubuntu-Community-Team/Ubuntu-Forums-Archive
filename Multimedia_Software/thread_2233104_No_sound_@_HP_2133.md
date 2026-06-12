---
title: "No sound @ HP 2133"
date: 2014-07-06
forum: Multimedia Software
---

### Post by theo5 on 2014-07-06
Hello.

I recently installed Ubuntu 14.04 LTS to a HP 2133 Netbook, but it couldn't take it (lags as hell). So I installed lubuntu-desktop and now it works.. let's say good enough. But there is no sound at all.
By entering alsamixer i checked that everything is maximized and unmute, but still no sound.

Unfortunately I can't check if "normal" ubuntu has sound (as I said it lags).

Can anyone help me?

EDIT: I installed pavucontrol. So, I open it (using terminal or by clicking at volume control in right corner) and play a music video with firerox. I can see the bar going up and down but still no sound from the speakers.

---

### Post by theo5 on 2014-07-07
After days of searching I finally find out that the problem is with the chip vt8237a/vt8251 which HP 2133 is using. There is a confirmed bug here [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1265611](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1265611)

Any ideas for how to fix that bug?

---

### Post by jarmo2 on 2014-08-25
> **theo5 said:**
> After days of searching I finally find out that the problem is with the chip vt8237a/vt8251 which HP 2133 is using. There is a confirmed bug here [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1265611](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1265611)

Any ideas for how to fix that bug?
-> had the same issues too... first HP2133 is very slow with normal 14.4 (32bit) and with light Lubuntu version I had only sound from head phones, no sound from speakers... I then did one more try and installed 12.4 Ubuntu - all good so far - wireless, sound... everything started working out of box.

---

