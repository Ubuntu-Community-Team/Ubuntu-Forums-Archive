---
title: "sound and slmodem &amp; hard reboot"
date: 2005-10-20
forum: Multimedia &amp; Video
---

### Post by towsonu2003 on 2005-10-20
I was wondering whether anyone would have an idea why slmodem would clash with my sound and force a hard reboot. 

Specifically, I am using the precompiled slmodemd from linmodems, and I believe my sound card is snd-atiixp. this is a laptop (hp pavilion zv5120us). I am not sure what else to include. 

Any help is appreciated so much!

thanks.

---

### Post by towsonu2003 on 2005-10-29
I just found that updatedb was running (and causing this) during my dialup attempts, which occur right after i boot. don't know how to edit that cron, as sudo crontab -e doesn't show updatedb as scheduled process...

---

### Post by towsonu2003 on 2005-11-21
ok I found a way to edit cron (had to change -x updatedb under /etc/cron.daily).

---

