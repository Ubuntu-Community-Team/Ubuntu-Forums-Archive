---
title: "Problem with nvidia drivers."
date: 2014-10-17
forum: Multimedia Software
---

### Post by AADAS on 2014-10-17
Recently I have installed the cuda drivers for using gpu.But then glitches showed up and now I want to rollback the changes .How to do this?

---

### Post by Bucky Ball on 2014-10-17
*Thread moved to **Multimedia**.*

---

### Post by SeijiSensei on 2014-10-17
Did you install the drivers from the Ubuntu repositories (strongly recommended), or did you trying installing them from NVIDIA's site?  If the former, you can remove them with a package manager or "sudo apt-get remove".

---

### Post by AADAS on 2014-10-17
I have tried sudo apt-get remove but i doesn't work.

---

### Post by SeijiSensei on 2014-10-17
Did you try using --purge?

What specifically do you mean by "doesn't work?"  If you reboot after removing them with apt-get and run the "lsmod" command, is the nvidia driver still listed there?

Were the drivers installed for the previous kernel as well?  What if you select the (n-1)th kernel when you get the grub screen?

---

