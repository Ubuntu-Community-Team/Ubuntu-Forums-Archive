---
title: "Black screen after upgrade from Maverick with Nvidia card"
date: 2011-04-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by elegant55 on 2011-04-13
I did a distribution upgrade from Maverick. After I rebooted and load from GRUB the system greeted me with a black screen with monitor going to power save mode.

The system actually booted up fine. I have to ssh in from another machine (fortunately the system installed sshd for me in the upgrading) and

sudo apt-get install nvidia-current

to fix it. It seems the default open-source driver not work well with my system.

Graphics card: Nvida 9600GT
Motherboard: Gigabyte GA-MA790X-UD4P

The same thing happens with the beta2 live cd. The installer screen not shown up after booting.

---

### Post by Harry33 on 2011-04-13
> **elegant55 said:**
> I did a distribution upgrade from Maverick. After I rebooted and load from GRUB the system greeted me with a black screen with monitor going to power save mode.
The system actually booted up fine. I have to ssh in from another machine (fortunately the system installed sshd for me in the upgrading) and
sudo apt-get install nvidia-current
to fix it. It seems the default open-source driver not work well with my system.
Graphics card: Nvida 9600GT
Motherboard: Gigabyte GA-MA790X-UD4P
The same thing happens with the beta2 live cd. The installer screen not shown up after booting.

The default driver is nouveau and it is very far away from the NVidia proprietary drivers.
You could have installed nvidia-current also with recovery mode and then from console or fail-safe graphics mode (vesa).

---

### Post by elegant55 on 2011-04-13
> **Harry33 said:**
> The default driver is nouveau and it is very far away from the NVidia proprietary drivers.
You could have installed nvidia-current also with recovery mode and then from console or fail-safe graphics mode (vesa).
Forgot to mention the recovery mode goes to black screen as well after upgrading.

Also with the live CD the screen goes black before I have a chance to install the OS at all.

---

### Post by Harry33 on 2011-04-13
> **elegant55 said:**
> Forgot to mention the recovery mode goes to black screen as well after upgrading.

Also with the live CD the screen goes black before I have a chance to install the OS at all.

How can recovery mode go to black screen as it does not even start gdm nor x?
It only uses text mode booting and end up in the whiptail menu, where you can choose "drop to shell", which is the console.

---

