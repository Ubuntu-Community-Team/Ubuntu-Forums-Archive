---
title: "ASUS AT5IONT 5.1 DTS out on HDMI"
date: 2011-05-24
forum: Multimedia Software
---

### Post by linux_good on 2011-05-24
Hi Linux people!

I have an ASUS at5iont mobo with an ION2 GPU. A nice setup with the Visio M420NV and Denon receiver. I have tried many different Linux's and every suggestion from every forum and have not been able to get 5.1 and DTS (6 channel) on HDMI. Hdmi works, but only 2 channels. I have been trying to get this to work for at least a month.

I have a fresh install of 11.04 now.

Does anyone with the AT5IONT board have HDMI 5.1 and DTS working with 11.04? If so, would you post the settings that did the trick? 

Such as the following or any other pertinent config file:
/etc/asound.conf
/etc/modprobe.d/sound.conf
/etc/pulse/default.pa
/etc/modprobe.d/snd-hda-intel.conf
/etc/modprobe.d/alsa-base.conf

Did you remove pulseaudio?

Thanks in advance!

---

### Post by MeduZa on 2011-05-24
I have 5.1 on analog running on a SB audigy 4, you maybe need to set your output to 5.1 digital, I never used digital output or HDMI but I think you need to set that on the pulseaudio's settings.

---

