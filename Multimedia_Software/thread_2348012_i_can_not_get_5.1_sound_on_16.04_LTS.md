---
title: "i can not get 5.1 sound on 16.04 LTS"
date: 2016-12-30
forum: Multimedia Software
---

### Post by KayaE on 2016-12-30
i've just installed ubuntu 16.04 LTS and having a problem to get 5.1 surround sound.
my subwoofer (and i guess right channels too) dont work properly.

i had same issue while i was using 14 LTS.
i fixed it by an edit in my /etc/pulse/daemon.conf
it was changing
; disable-lfe-remixing = yes
to
disable-lfe-remixing = no

but now on 16.04 LTS i have same problem and can not do the same fix.
because that line in my /etc/pulse/daemon.conf look different now.
; enable-lfe-remixing = yes

(i guess i also tried all recommendations i could reach online.. i feel stuck now.)

---

### Post by KayaE on 2017-01-04
i'm still having the same issue. :/ ??

---

