---
title: "Upgrade from 9.04 to 9.10 stopped s-video out."
date: 2010-01-22
forum: Mythbuntu
---

### Post by Techmanm on 2010-01-22
I have upgraded my mythbuntu system from 9.04 to 9.10 but now my s-video output no longer works.

I'm using a ATI Radeon HD 3650 graphic card.

1. removed all old drivers with the command: "sudo sh ./fglrx-uninstall.sh" (in directory /usr/share/ati).

2. Downloaded driver 9.12 from support.amd.com.

3. installed de AMD driver with the command: "sudo sh ./ati-driver-installer-9.12-x86.x86_64.run", followed the instructions.

4. configured the driver with: "sudo aticonfig --initial".

5. rebooted the system.

I have connected an LCD monitor and my TV with S-video.

I can not get the TV to work.

Please help.

---

### Post by LowSky on 2010-01-22
This might help
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Techmanm on 2010-01-26
i have found out that the systems hangs on start up when i only connect the TV.
When i disconnect the cable the systems starts normal.
I can then plug in the s-video cable and i am having a picture.
Is there a way to get the system start op normaly?

---

