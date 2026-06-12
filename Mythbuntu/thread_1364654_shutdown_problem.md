---
title: "shutdown problem"
date: 2009-12-26
forum: Mythbuntu
---

### Post by MickeT on 2009-12-26
Hi
is this myth or ubuntu related? guess both...
[http://swiss.ubuntuforums.org/showthread.php?p=8560435#post8560435](http://swiss.ubuntuforums.org/showthread.php?p=8560435#post8560435)
BR
 
[[COLOR=#000000]seeking upgrade to 9.10 reports, please[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1308421") thread mentions shutdown problems at least 2 times,no solutions though

---

### Post by nickrout on 2009-12-26
why r u opening a new thread. you already posted in the other one!

---

### Post by MickeT on 2009-12-27
wrong threadname, should have been segmentation fault or something
which is a myth problem i guess (this forum ) and my shutdown problem seems to
be a ubuntu problem(the linked one). 
 
 
Dec 25 17:55:03 tvuser-desktop kernel: [ 3266.815713] mythbackend[5158]: segfault at 8c8e01c ip 08427ab3 sp bfd260e0 error 7 in libGL.so.185.18.36[83fc000+81000]
Dec 25 18:01:05 tvuser-desktop kernel: [ 3629.245904] mythshutdown[5499]: segfault at 821501c ip 0318dab3 sp bfacec90 error 7 in libGL.so.185.18.36[3162000+81000]
Dec 25 23:23:03 tvuser-desktop kernel: [22947.091670] mythshutdown[20976]: segfault at 8b9c150 ip 0763cab3 sp bf88f0e0 error 7 in libGL.so.185.18.36[7611000+81000]
26 09:21:58 tvuser-desktop kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
D

---

### Post by MickeT on 2009-12-27
Had some success, tried to disable acpi. Shutdown problem seems to have vanished,
ok now what ? guess I need acpi for my acpi alarm wakeup to work.
Had lot of problems in the beginning booting with acpi and this asus motherboard

---

