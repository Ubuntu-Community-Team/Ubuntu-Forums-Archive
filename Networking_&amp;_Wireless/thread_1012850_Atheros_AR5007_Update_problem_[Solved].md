---
title: "Atheros AR5007 Update problem [Solved]"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by K3N8 on 2008-12-16
Hi everybody,

Like a few others here my wireless connection stopped working right after I updated Ubuntu 8.10 Intrepid.

I decided to uninstall the backport kernel modules and to reinstall them after reboot:
```
apt-get remove --purge linux-backports-modules-intrepid-generic
```

After the reboot the wireless connection worked again?!

Gr. Alexander

---

### Post by krisstaar on 2008-12-16
Thanks a lot, dude! Lifesaver =)

---

### Post by stoopid_noob on 2008-12-16
Can you please provide a dummy proof, step by step for what exactly you did?

I am doing a fresh install of Ubuntu right now on my AAO. So right from the start can you provide me with the exact step by step of what you did in order to get this working?

Thanks.

---

### Post by K3N8 on 2008-12-16
> **stoopid_noob said:**
> Can you please provide a dummy proof, step by step for what exactly you did?

My solution was not for a fresh install. But when I did a fresh install I installed the backport kernel modules:```
apt-get install linux-backports-modules-intrepid-generic
```

After rebooting activate the new 5xxx module and deactivate the standaard Atheros module. Restart again and you're set.

Gr. Alexander

---

### Post by K3N8 on 2009-01-06
Hi all,

Today it happened again after an update. My wireless connection isn't working anymore. I tried the same thing I did last time, but now it doesn't work anymore. Does anybody haave the same issues?

Thankx

Alexander

---

### Post by kevdog on 2009-01-06
What driver do you want to use?  The ath5k driver?  Did you add it to /etc/modules to make it load at boot?

---

### Post by K3N8 on 2009-01-07
> **kevdog said:**
> What driver do you want to use?  The ath5k driver?  Did you add it to /etc/modules to make it load at boot?I use th ath5k driver. I did not have it in /etc/modules. I have just added it. I did load it manually through ```
sudo modprobe ath5k
``` and that didn't work.

The stangest thing is, that I started the computer just now and it worked again?! The only thing different is that I had the power cord attached.

Gr. Alexander

---

### Post by kevdog on 2009-01-07
Make sure ath5k is listed in the /etc/modules file (just like ath_pci would be for madwifi) and that it is not listed in the /etc/modprobe.d/blacklist file.

---

