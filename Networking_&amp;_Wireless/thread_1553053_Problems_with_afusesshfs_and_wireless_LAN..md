---
title: "Problems with afuse/sshfs and wireless LAN."
date: 2010-08-14
forum: Networking &amp; Wireless
---

### Post by yaaaaaarghe on 2010-08-14
Hello,

I'm trying to set up my laptop (Ubuntu 10.04) to mount directories of my server (Ubuntu Server 9.04) at boot with SSHFS.

I tried adding the sshfs#... thingy in fstab but the mount won't succesfully work at boot because the wireless adapter has not yet initialized and connected to my LAN.

I also tried using afuse in a boot script which also wouldn't work because it usually takes some time before the wireless adapter will connect to the LAN after I have manually logged on.

Is there some way I can execute a specific script immediately when a successful connection to LAN is established?

Thanks, y'all.

---

