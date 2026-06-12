---
title: "Can't get latest NVIDIA  driver to work on Ubuntu 12.04"
date: 2012-05-22
forum: Multimedia Software
---

### Post by mdialogo on 2012-05-22
Hello,
I'm currently using the open source driver NOVEAU and so far Unity 3D is working very good.  However, I want enable the proprietary driver NVIDIA because NOVEAU is slow with games requiring full 3D graphics like Nexuis.  I am told NVIDIA driver can utilize hardware acceleration so I was hoping it could greatly improve my experience with Ubuntu.  

So, when I tried to activate the NVIDIA accelerated graphics driver via the Additional Drivers, after restarting, the screen resolution drops to 640x480.  I can't get any resolution other than that in the Display window.

I executed -> glxinfo | grep rendering, and got this output -> direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose).  Also, the NVIDIA settings tell me "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server".  I also tried installing the latest NVIDIA 295.53 driver via Synaptic package manager but got the same result.

Is this because I didn't removed the NOVEAU driver before activating NVIDIA?  This link doesn't recommend removing NOVEAU driver ->[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia), so I'm afraid it might break things if I do it.  I just deactivated NVIDIA to get back my original resolution to 1366x768.

My video card is GeForce 6150SE nForce 430.

Any help is greatly appreciated.  Thanks,

---

### Post by sycoso on 2012-06-04
Yes, removing nouveau is a bad idea. But you can blacklist it:

1. open /etc/modprobe.d/blacklist.conf as root
2. add > blacklist nouveau to the file
3. reboot

---

### Post by inashdeen on 2012-06-04
Never remove the existing driver! just activate nvidia proprietary if you really need em

---

### Post by sycoso on 2012-06-04
> **inashdeen said:**
> Never remove the existing driver! just activate nvidia proprietary if you really need em
You can't just activate the nvidia drivers, it seems as if you have to blacklist the nouveau drivers...

---

### Post by inashdeen on 2012-06-04
Ok, no problem in blacklisting, but never remove them. it is suicidal

---

### Post by sycoso on 2012-06-04
> **inashdeen said:**
> Ok, no problem in blacklisting, but never remove them. it is suicidal
eeyup

---

