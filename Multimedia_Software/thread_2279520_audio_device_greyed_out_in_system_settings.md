---
title: "audio device greyed out in system settings"
date: 2015-05-23
forum: Multimedia Software
---

### Post by peter.hewett on 2015-05-23
This used to work, but following update today, the Phonon audio option I want in system settings is greyed out.

This is a fresh install of Kubuntu 15.04 on an Intel NUC, used as media PC to drive a TV screen.  It worked fine using HDMI for both video and audio to the TV.  It was necessary to select the HDMI option in system settings / multimedia, but now the HDMI option is greyed out.  The built in analog option is still there.  No hardware changes made, just the Kubuntu updates.

What can I do to restore the HDMI option for audio, or at least investigate this?

TIA

Peter

---

### Post by peter.hewett on 2015-05-24
Some more info; output of alsa-info.txt attached (from the script in the sound troubleshooting procedure). (Split into 2 text files, because the uploader said it was too big for this forum as one file.)

The command aplay -l shows only the analog playback device, not the HDMI device.

After running step 1 of the troubleshooting procedure, the HDMI line has disappeared. It is not even there as greyed out.

When Kubuntu 15.04 was first installed on this hardware, the sound worked fine over HDMI (provided it was selected in system settings).  It is only after the updates today that HDMI audio has stopped working.

---

### Post by SeijiSensei on 2015-05-24
If you have an NVIDIA or ATI adapter, have you installed the proprietary driver?  I found this necessary to support HDMI output from those devices.  Intel adapters work with the drivers contained in the Linux kernel.

---

### Post by johnG43 on 2015-05-24
I have the same issue after updating two days ago. The HDMI profile does not show at all. My MB has only the built-in Intel audio and video.

---

### Post by peter.hewett on 2015-05-24
Hardware info: Intel NUC 
all in one board; D34010WYK
CPU: i3-4010U

The video and audio are all on board, so there are no nvidia or ati drivers.

---

### Post by peter.hewett on 2015-05-25
Someone has raised bug 1458301 on launchpad with very similar symptoms.
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1458301](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1458301)

---

### Post by peter.hewett on 2015-06-11
solved

This bug was fixed with kernel 3.19.0-20.
Refer launchpad bug kernel 3.19.0-18 breaks HDMI audio for snd_hda_intel
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1457369](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1457369)

---

