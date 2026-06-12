---
title: "Gimp doesn't accept keyboard input"
date: 2015-07-27
forum: Multimedia Software
---

### Post by Bjoern_Sk on 2015-07-27
Hi Folks,

I have some strange behaviour using Gimp.
Suddenly gimp stops, taking keyboard input e.g. when typing in a layer name or file name.
Other applications including KDE are working fine.
The only solution I've found so far, is deleting .gimp folder and start over. But this is very very annoying.
Did someone face this issue and has a solution for it?
Any help / idea is appreciated.

My system:
Kubuntu 14.04.2 LTS
Kernel: 3.13.0-57-generic #95-Ubuntu SMP
Gimp version 2.8.10

Best regards
B.

---

### Post by bapoumba on 2015-07-27
Please see if this workaround works for you :
[https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/1350812](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/1350812)

If it does, you can change the bug report to say it affects you too (log into LP, the is a green line at the top of the report).

---

### Post by Bjoern_Sk on 2015-07-28
Thanks for your help. The workaround works, I've confirmed the bug report.

---

### Post by bapoumba on 2015-07-28
OK, I did experiment a similar bug (with Chrome). Has to be done at each reboot, unfortunately.

---

