---
title: "usb o2 midi keyboard works in dapper!"
date: 2006-09-10
forum: Multimedia &amp; Video
---

### Post by majutsu on 2006-09-10
i had posted earlier about problems getting my usb o2 m-audio midi to work in dapper.  i had tried firmware etc.  but after updating jack, alsa, and oss.  i got ChucK to recognize my midi perfectly with the ubuntu studio fix:

sudo su
modprobe snd-seq
if grep -q -x snd-seq /etc/modules; \
  then echo && echo "NOTE: snd-seq is already in /etc/modules, no changes needed."; \
  else cp /etc/modules /etc/modules_backup_`date +%Y%m%d%H%M` && echo snd-seq >> /etc/modules; \
fi
exit

just wanted others who may have this issue to know too.

:p

---

