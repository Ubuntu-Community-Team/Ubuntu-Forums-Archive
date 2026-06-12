---
title: "Audio problems after update (no bass)"
date: 2007-06-03
forum: Multimedia &amp; Video
---

### Post by acraft on 2007-06-03
Yesterday, my sound was working fine.  Today I updated, and my subwoofer stopped working after the reboot.  I'm using Feisty, and my sound card is SBLive! Value.  I grep'ed the dpkg.log for "upgrade" to see what all was updated:

```

2007-06-03 16:08:14 upgrade firefox-gnome-support 2.0.0.3+1-0ubuntu2 2.0.0.4+1-0ubuntu1
2007-06-03 16:08:15 upgrade libfreetype6 2.2.1-5ubuntu1 2.2.1-5ubuntu1.1
2007-06-03 16:08:15 upgrade libnspr4 2:1.firefox2.0.0.3+1-0ubuntu2 2:1.firefox2.0.0.4+1-0ubuntu1
2007-06-03 16:08:15 upgrade libnss3 2:1.firefox2.0.0.3+1-0ubuntu2 2:1.firefox2.0.0.4+1-0ubuntu1
2007-06-03 16:08:16 upgrade firefox 2.0.0.3+1-0ubuntu2 2.0.0.4+1-0ubuntu1
2007-06-03 16:08:28 upgrade gimp 2.2.13-1ubuntu4 2.2.13-1ubuntu4.1
2007-06-03 16:08:29 upgrade gimp-data 2.2.13-1ubuntu4 2.2.13-1ubuntu4.1
2007-06-03 16:08:34 upgrade libgimp2.0 2.2.13-1ubuntu4 2.2.13-1ubuntu4.1
2007-06-03 16:08:35 upgrade gimp-python 2.2.13-1ubuntu4 2.2.13-1ubuntu4.1
2007-06-03 16:08:47 upgrade linux-image-generic 2.6.20.15.14 2.6.20.16.28.1
2007-06-03 16:08:51 upgrade linux-restricted-modules-generic 2.6.20.15.14 2.6.20.16.28.1
2007-06-03 16:08:52 upgrade linux-generic 2.6.20.15.14 2.6.20.16.28.1
2007-06-03 16:09:02 upgrade linux-headers-generic 2.6.20.15.14 2.6.20.16.28.1

```

And I'm not sure what could have broken the sound, other than the kernel update.  I have checked the volume control; I am on the right card (says "SBLive! Value [CT4670] (Alsa mixer)"), and changing bass volume has no effect.

I don't know enough about kernel modules or Linux audio to figure this out on my own, so can someone give me some direction?  I can post the complete dpkg.log from the update if needed.

Thanks!

---

