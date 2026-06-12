---
title: "No sound after resuming sleep mode"
date: 2008-09-11
forum: Multimedia Software
---

### Post by Lovok on 2008-09-11
I have checked with Google, and the top most links are all out of date.
When I leave my computer and it goes into sleep mode, I will loose all sound on resume. 
I use Edubuntu 8.04.1, updated, using on board sound with ALSA. Sound works fine on reboot, but doesn't after resuming from sleep.

Doing :
```

sudo mkdir /var/run/alsa
sudo /etc/init.d/alsa force-reload
sudo /etc/init.d/alsa resume

```
doesn't work, nor does restarting alsa-utils.

Also, ```
 cat /proc/asound/modules 
``` gives me my sound card before and after sleep mode, so I know Ubuntu is still detecting it. 

And ```
cat /proc/asound/modules
``` also lists my user account before and after sleep mode.


Any suggestions?

---

