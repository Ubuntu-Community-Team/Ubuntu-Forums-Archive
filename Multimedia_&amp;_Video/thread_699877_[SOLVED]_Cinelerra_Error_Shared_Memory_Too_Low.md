---
title: "[SOLVED] Cinelerra Error: Shared Memory Too Low"
date: 2008-02-17
forum: Multimedia &amp; Video
---

### Post by alsamman on 2008-02-17
For some reason when I load Cinelerra I always get this error:
void MWindow::init_shm0: WARNING:/proc/sys/kernel/shmmax is 0x2000000, which is too low.
Before running Cinelerra do the following as root:
echo "0x7ffffff">/proc/sys/kernel/shmmax

but the weird thing is, I already edited my /etc/sysctl.conf and added kernel/shmmax=0x7fffffff at the bottom yet I still get this error. I had Cinelerra working fine before I reinstalled Gutsy but now it does not seem to recogize the kernel/shmmax=0x7fffffff I added to the /etc/sysctl.conf. Can someone please give me some help?:confused:

---

### Post by alsamman on 2008-02-17
bump

---

### Post by alsamman on 2008-02-18
double bump

---

### Post by alsamman on 2008-02-18
triple bump

---

