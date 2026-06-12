---
title: "Problem with VNC enabling in Mythbuntu Control Center"
date: 2008-01-30
forum: Mythbuntu
---

### Post by Kawayanan on 2008-01-30
I Am trying to get my mythbuntu box setup for remote admin, but have hit a few snags.  One is with VNC.

I am trying to enable VNC from the System Services tab of the Mythbuntu Control Center.  I shows up as disabled.  I set it to enabled and added a password.  When I try to hit apply however, Mythbuntu Control Center crashes and I drop back to the mythbuntu frontend.  If I open Mythbuntu Control Center again, VNC is still disabled.  I checked the /var/log/syslog and found these errors from when I tried to enable VNC:

```
Jan 30 18:32:18 mythbox kernel: [  199.535560] python[5858]: segfault at 00000000000000a9 rip 0000000000457c70 rsp 00007ffff034d5d8 error 4

```

```
Jan 30 18:37:20 mythbox kernel: [  535.308243] python[6020]: segfault at 00000000000000a9 rip 0000000000457c70 rsp 00007fff0cd8e018 error 4

```

Any ideas whats going wrong?

Thanks,
Kawayanan

---

### Post by jbrytan on 2008-01-30
Same happened to me.  I realized that Mythbuntu was looking for the VNC package on the CD.

You need to edit your /etc/apt/sources.list file and comment out (#) the first line with deb cdrom...

---

### Post by superm1 on 2008-01-30
FWIW, this is fixed in hardy.

---

