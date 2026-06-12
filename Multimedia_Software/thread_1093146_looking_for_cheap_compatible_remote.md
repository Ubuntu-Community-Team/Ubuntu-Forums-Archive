---
title: "looking for cheap compatible remote"
date: 2009-03-11
forum: Multimedia Software
---

### Post by kadafi69 on 2009-03-11
im looking for a relatively cheap remote that wont take too much configuring to use with mythbuntu. ive been trying to use the one that came with my tv card but to no avail. can anyone recommend a decent remote?

---

### Post by lovinglinux on 2009-03-11
What model of remote you currently have?

---

### Post by kadafi69 on 2009-03-11
its the hauppauge nova-t, but its not the 45 button model its the new 35 button model numbered DSR-0112. Ive tried a couple of guides for lirc but to no luck.

---

### Post by lovinglinux on 2009-03-11
Have you checked if this remote is compatible with lirc?

I had a lot of trouble to install lirc and time to learn how to configure it. So maybe is not your remote, but your lirc configuration. Sometimes the solution is simpler than you think.

What happens if you run the command irw then press some remote buttons?

EDIT: it would also help if you could post the content of your */etc/lirc/hardware.conf* file

---

