---
title: "[SOLVED] sound jumps from mobo out to sound card out"
date: 2008-02-29
forum: Multimedia &amp; Video
---

### Post by uxe1 on 2008-02-29
i have a cheepass sound card in my comp and it works -some times. if i have my speakers plugged in to the sound card when i boot the sound comes out of my mobo outs, if i have them plugged in to my mobo the sound comes out my sound card outs. 
its tre' annoying to have to go behind my computer and switch what plug i have my speakers plugged in to.
im using gutsy6bit. i dont know what to type to get the stats on my sound card.
thanx for any ideas at all on this

---

### Post by happyhamster on 2008-03-01
Hello. If you don't want to use onboard sound, try disabling it in the bios. If that's no option, or if it doesn't help, could you show the output of the following commands:

aplay -l
cat /proc/asound/cards
cat /proc/asound/modules
cat /etc/modprobe.d/alsa-base

They give info about your sound hardware and configuration.

---

### Post by uxe1 on 2008-03-02
doh! never thought of changing the bios, Thanx!

---

### Post by arimaniac on 2008-03-03
Hi there

Complete HOWTO on disabling your on-board card

[http://ubuntuforums.org/showthread.php?t=712908]("http://ubuntuforums.org/showthread.php?t=712908")

Please reply with your
comments to improve the HOW TO...

Hope it helps....

---

