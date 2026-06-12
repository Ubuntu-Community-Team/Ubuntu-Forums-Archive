---
title: "Problem Using Gyachi and its upgrades"
date: 2009-08-07
forum: Networking &amp; Wireless
---

### Post by Rezwan Mahbub on 2009-08-07
My Gyachi don't support the voice functionality. I know my libasound may not be installed with others which is creating the problem.
When I tried to upgrade gyachi through Synaptic: It says that the following packages have unresolved dependencies and to make sure the required repositories are enabled the message it shows is as follows:
gyachi:
  Depends: libasound2 (>1.0.1:cool: but 1.0.17a-0ubuntu4 is to be installed
  Depends: libdbus-glib-1-2 (>=0.7:cool: but 0.76-1 is to be installed
  Depends: libgpgme11 (>=1.1.:cool: but 1.1.6-2ubuntu1 is to be installed
  Depends: libgtk2.0-0 (>=2.16.0) but 2.14.4-0ubuntu1 is to be installed
  Depends: libltdl7 (>=2.2.6a) but 2.2.4-0ubuntu4 is to be installed
  Depends: libpulse0 (>=0.9.14) but 0.9.10-2ubuntu9.4 is to be installed
  Depends: libxcb-render-util0 (>=0.2.1+git1) but 0.2+git36-1 is to be installed
  Depends: libxcb1 (>=1.1.92) but 1.1-1.1 is to be installed

---

### Post by loell on 2009-08-08
you could be using an older ubuntu version.

---

### Post by Rezwan Mahbub on 2009-08-08
> **loell said:**
> you could be using an older ubuntu version.
I am using this old Ubuntu in my old PC that's why i m seeking a solution for it. Is there anybody for help now?

---

### Post by colau on 2009-08-14
> **Rezwan Mahbub said:**
> I am using this old Ubuntu in my old PC that's why i m seeking a solution for it. Is there anybody for help now?
Can you post the output of the following:
```

dpkg -l | grep gyachi

```

---

