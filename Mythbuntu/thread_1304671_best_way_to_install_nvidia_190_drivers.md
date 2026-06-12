---
title: "best way to install nvidia 190 drivers?"
date: 2009-10-29
forum: Mythbuntu
---

### Post by ZedThou on 2009-10-29
I wanted to try out the latest nvidia drivers, so I added the nvidia vdpau team ppa to my sources, removed nvidia-185 packages and added nvidia-190. This didn't end well as it had the small side effect of removing my mythtv packages - due to their dependence on nvidia-185 I gather.

So, at this point should I just run the nvidia installer instead? Or is there a cleaner way?

---

### Post by Caysho on 2009-10-30
If something is not available via the package manager, there is no clean way :)
I think you will have to use the nvidia installer.

---

### Post by bforbes on 2009-10-31
The way I usually do it is to remove the existing drivers, and also any packages starting with "linux-restricted". I then just do a console login, and run the NVIDIA installer, and it works fine.

I guess you might have to install mythtv manually, i.e. not from the repository.

---

