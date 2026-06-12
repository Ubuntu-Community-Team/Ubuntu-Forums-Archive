---
title: "No sound on USB audio device after upgrade to 11.10"
date: 2011-10-18
forum: Multimedia Software
---

### Post by ChrisiPK on 2011-10-18
Hi everyone,

I use a compact sound system as the main speakers for my Ubuntu machine. The device (Philips FW-M567) is connected via USB. So far, Ubuntu automatically detected the device and enabled me to use it as audio output.

After upgrading to Ubuntu 11.10 (64 bit), the device is still recognized in the sound dialogue. However, now it only shows up in the "Hardware" list, but no longer in the "Audio output" list, which is why I can no longer select it for audio output.

Is there anything I can do about this? Any help would be appreciated, as I would really like my sound output back.

Thanks in advance and best regards,

ChrisiPK

---

### Post by ChrisiPK on 2011-10-18
It works now. I installed various updates today (see list below), not sure which one fixed the issue.

libdvbpsi7 (0.2.0-1)
libebml3 (1.2.1-1)
libmatroska4 (1.2.0-1)
libtar0 (1.2.11-8)
libupnp3 (1:1.6.6-5.1)
libxcb-keysyms1 (0.3.8-1)
vlc (1.1.11-2build2)
vlc-nox (1.1.11-2build2)
vlc-plugin-notify (1.1.11-2build2)
vlc-plugin-pulse (1.1.11-2build2)

Thanks and regards,

ChrisiPK

---

### Post by missmoondog on 2011-10-19
same issue here although i never got sound to work in 11.04 either, but that wasn't on this computer for very long either.

i do believe i have all those updates OP installed, already installed here.

i do have sound settings set for usb alsa mixer also.

crap! didn't notice this was marked as solved already.  :(

---

### Post by ChrisiPK on 2011-10-19
It's no longer working. However, I cannot find a way to mark this thread as unsolved again. I don't know, why it's failing again as I didn't change anything on my system. Filed a bug now: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/878028](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/878028)

edit: Found the button. Now unsolved.

---

### Post by missmoondog on 2011-10-26
issue is solved. i uninstalled xubuntu from this crap dell machine. it never has ran any version of x/ubuntu correctly anyway. usually it's the graphics that's messed up on this machine, but that was fine this time. between no sound and usb mouse locks up when coming out of suspend and i have to do a hard shutdown to fix that, xubuntu is history! at least windows 7 runs good on it

---

### Post by ChrisiPK on 2011-10-26
It's been working for me for a week in a row now. I have no idea, what has changed, but marking this as solved for now. Little point in people giving me advice on what to do, when the issue does not persist.

Thanks and regards,

ChrisiPK

---

