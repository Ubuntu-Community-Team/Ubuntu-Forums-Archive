---
title: "DVD not opening in VLC"
date: 2016-11-02
forum: Multimedia Software
---

### Post by Aiden_Henrie on 2016-11-02
I have looked at many instructions, and installed ubuntu-restricted-extras, lubuntu-restricted-extras, libdvdread4, and libdvdnav4. Whenever I open VLC and click on "open disc", my disc drive spins up and VLC even shows "ARACHNOPHOBIA" at the top, but it won't play no matter what I try to do. I have even tried opening up the specific video file on the DVD, but it just gives me an error. Is there something that I forgot to install, or did I just do it wrong?

---

### Post by deadflowr on 2016-11-02
Which version of Ubuntu? (lubuntu)

---

### Post by Aiden_Henrie on 2016-11-03
I am using Lubuntu 16.04.

---

### Post by deadflowr on 2016-11-03
Install libdvd-pkg
```
sudo apt install libdvd-pkg
```

---

### Post by Aiden_Henrie on 2016-11-03
I installed the file, then restarted my computer, but it still didn't do anything.

---

### Post by Autodave on 2016-11-07
libdvdread4  should have been installed when you installed the package. Make sure it is installed.

---

