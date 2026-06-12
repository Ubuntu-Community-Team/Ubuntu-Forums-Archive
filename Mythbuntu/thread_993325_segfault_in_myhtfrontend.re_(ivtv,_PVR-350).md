---
title: "segfault in myhtfrontend.re (ivtv, PVR-350)"
date: 2008-11-25
forum: Mythbuntu
---

### Post by tschoo on 2008-11-25
Hi,

since upgrading from 8.04 to 8.10 I have frequent segfaults in mythfrontend.re:

kernel: [ 8552.584159] mythfrontend.re[8334]: segfault at 1 ip b6033194 sp bf9cc7d0 error 4 in libX11.so.6.2.0[b6004000+eb000]
...
kernel: [ 9100.680813] mythfrontend.re[15604]: segfault at 690065 ip b5f17194 sp bfbaf0e0 error 4 in libX11.so.6.2.0[b5ee8000+eb000]
...
kernel: [ 8277.818952] mythfrontend.re[20620]: segfault at dcf27f13 ip b5fb5194 sp bff4de70 error 5 in libX11.so.6.2.0[b5f86000+eb000]
...
The errors usually occur when doing FF/Rewind.

My configuration:
PVR-350 (also used for Video-out)
Athlon 64 X2
lirc
rather plain Ubuntu 8.10 (kernel 2.6.27-7-generic)

Does anyone have an idea about the cause of the problem?

-tschoo

---

### Post by mike909 on 2009-02-24
I too have these messages in the 'messages' log (/var/log/messages).

---

### Post by karmabreath on 2009-04-24
Anyone develop any more information regarding this segfault issue?

---

### Post by mike909 on 2009-04-24
I'm upgrading to 9.04 and crossing my fingers.

---

### Post by mike909 on 2009-04-26
$mike@mike-desktop:~$ egrep -i segfault /var/log/*.log
$/var/log/kern.log:Apr 25 06:42:19 mike-desktop kernel: [71423.072715] mythfilldatabas[417]: segfault at 34003000 ip 084decbf sp b45e479f error 6

No such luck on 9.04 getting rid of my segfaults...though they are different from the OP's post.

---

