---
title: "AR9285 (ath9k) broken?"
date: 2011-03-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ikt on 2011-03-14
Can anybody who has this wireless confirm against alpha 3 that it is causing lockups and other unhappiness.

thanks

Bug report here: [https://bugs.launchpad.net/ubuntu/+bug/729549](https://bugs.launchpad.net/ubuntu/+bug/729549)

---

### Post by r-senior on 2011-03-14
I had a lot of problems initially with ath5k on Alpha 3. Not quite the same as the bug report (and not quite the same driver) but it would drop out and then keep asking for my WEP key and never reconnect. I did an apt-get dist-upgrade on Friday and that pulled in kernel 2.6.38-6-generic. Wireless has been solid ever since and I have tried to hammer it hard with downloads, large file transfers over NFS and streaming video.

The bug report I was subscribed to suggested that major fixes were coming in 2.6.38-7 but 38-6 seems to have done the trick for me.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/714300]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/714300")

Obviously with ath9k, YMMV.

---

### Post by beew on 2011-03-14
> **r-senior said:**
> I had a lot of problems initially with ath5k on Alpha 3. Not quite the same as the bug report (and not quite the same driver) but it would drop out and then keep asking for my WEP key and never reconnect. I did an apt-get dist-upgrade on Friday and that pulled in kernel 2.6.38-6-generic. Wireless has been solid ever since and I have tried to hammer it hard with downloads, large file transfers over NFS and streaming video.

The bug report I was subscribed to suggested that major fixes were coming in 2.6.38-7 but 38-6 seems to have done the trick for me.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/714300](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/714300)

Obviously with ath9k, YMMV.

ath5k works flawlessly for me.

---

### Post by ikt on 2011-03-15
> **beew said:**
> ath5k works flawlessly for me.

yeah, this is more about ath9k, which seems to be causing system lock ups.

---

