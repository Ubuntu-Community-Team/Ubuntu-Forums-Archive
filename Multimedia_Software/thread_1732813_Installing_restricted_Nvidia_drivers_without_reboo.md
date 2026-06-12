---
title: "Installing restricted Nvidia drivers without reboot?"
date: 2011-04-18
forum: Multimedia Software
---

### Post by c-shadow on 2011-04-18
Is it possible without a reboot?
Yesterday I tried to upgrade nvidia drivers on my lucid installation from 256.35 to 270.29 (from x-updates repo). Added a repo, opened a VT via CTRL+ALT+F1, stopped the GDM, installed the new drivers, removed nvidia module via modprobe, loaded module again and tried to start GDM, but nothing happened. Got this in log:
```

Apr 17 12:52:01 witch kernel: [7031690.407323] NVRM: API mismatch: the client has the version 270.29, but
Apr 17 12:52:01 witch kernel: [7031690.407324] NVRM: this kernel module has the version 256.35.  Please
Apr 17 12:52:01 witch kernel: [7031690.407325] NVRM: make sure that this kernel module and all NVIDIA driver
Apr 17 12:52:01 witch kernel: [7031690.407326] NVRM: components have the same version.

```
Seems to me that the old module was still loading.
After a reboot everything works fine. 
Same thing happened to me a couple of times before but never bothered and just rebooted.
Now i'm curious why it didn't work?

---

