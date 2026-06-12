---
title: "HDMI sound problem with Nvidia GeForce"
date: 2010-01-23
forum: Multimedia Software
---

### Post by David Robinson on 2010-01-23
I can't get HDMI sound reliably when using Ubuntu. The strange thing is, if I repeatedly reboot the computer, eventually the sound will work. This can take anything up to 10 reboots. Once working, it will keep on working as long as the machine is not rebooted or shut down. HDMI sound works fine under Windows.

aplay -l will only list the Intel (analogue and S/PDIF) hardware, not the Nvidia, even when it is working. Selecting between analogue and digital output under Sound Preferences has no effect on the HDMI either way.

All suggestions gratefully received.

_System details_

HP Pavilion laptop
Nvidia GeForce Go 7600
Ubuntu 9.10
Nvidia proprietary driver version 185

---

### Post by David Robinson on 2010-01-29
I have now installed the Nvidia driver 190 from their website. This doesn't cure the problem, but there is some improvement. The sound will now work about 1 boot in 2 i.e. an average of 1 boot plus 1 reboot.

I have a theory about this. I assume the Nvidia driver must hook itself into the main sound driver in order to eavesdrop on the audio. Could it be that there is a race condition between the sound driver and the Nvidia driver during startup? Maybe the Nvidia driver is attempting to call up the sound driver before the latter is ready and hence the hook fails.

The improvement could be simply because the new Nvidia driver, like every update ever written, is slightly more bloated and slower, therefore giving the sound driver longer to initialise.

Does this make sense?

---

### Post by danlherman on 2011-02-03
I am having the exact same issue.  If anyone has any idea on a resolution please let me know.

thanks,
Dan

---

