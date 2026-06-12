---
title: "Won’t Boot after Graphic Driver uninstall"
date: 2018-12-26
forum: Multimedia Software
---

### Post by originterminus on 2018-12-26
I like to game, particularly with Steam. Recently I upgraded my GPU to AMD Radeon RX580 8Gb. Worked straight after installation, but needed to install AMD graphics drivers to get Vulkan capabilities; I manually installed amdgpu and amdgpu-pro drivers. 

With Vulkan enabled I was able to get my game up and running, but I noticed some performance issues while running other games, noticeably if I suspected that the engine was using OpenGL. 

To test for issues, I decided to uninstall AMD Pro drivers and work with the standard AMD drivers. I proceeded to uninstall by running the following in a terminal:

cd /opt

uninstall amdgpu-pro

After the uninstallation was complete I restarted the computer. Now Ubuntu fails to boot. 

Any thoughts on how to proceed? I tested the hardware by connecting with both DVI and HDMI—neither worked.

---

### Post by CatKiller on 2018-12-26
I've not used AMD graphics on Linux, but for those that have it would be worth describing in detail your symptoms, so that they'll have something to work from in helping you.

In the meantime, it is relatively straightforward to boot into a live environment and use that infrastructure to fix a broken system. You'd mount the system's hard drive and then use **chroot** to run commands as if you'd booted into the system.

---

### Post by originterminus on 2018-12-26
Solved! 

I was able to reinstall amdgpu-pro drivers from command line in recovery mode. 

Thanks!

---

### Post by Yellow Pasque on 2018-12-27
Please mark the thread solved (thread tools menu above first post).
FWIW, you shouldn't need to install the "pro" drivers for vulkan support. This should do it for open source drivers and you can check the Vulkan info with a tool named... vulkaninfo:
```
sudo apt install mesa-vulkan-drivers vulkaninfo
vulkaninfo | head -n 20
```

---

