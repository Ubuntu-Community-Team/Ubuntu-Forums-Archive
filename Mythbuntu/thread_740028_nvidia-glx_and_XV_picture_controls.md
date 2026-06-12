---
title: "nvidia-glx and XV picture controls"
date: 2008-03-30
forum: Mythbuntu
---

### Post by sciguy125 on 2008-03-30
I recently upgraded to 8.04 beta and my XV picture controls disappeared.  In the previous version, it was working with nvidia-glx-legacy with my MX440.  However, it seems that I have to use nvidia-glx now.  Before I upgraded, I changed the settings in nvidia-settings.

I really need picture controls because the image is WAY over saturated.  I've tried changing brightness/contrast/gamma, but it's just not the same.

---

### Post by foxbuntu on 2008-04-01
nvidia-settings should still be in the nvdia-glx package...if not:

```
sudo apt-get install nvidia-settings
```

---

### Post by sciguy125 on 2008-04-06
I've narrowed it down to a change in the Nvidia drivers.  There's three versions now: nvidia-glx-new, nvidia-glx, and nvidia-glx-legacy.  My MX440 uses nvidia-glx.  However, until the changes, it used nvidia-glx-legacy.  nvidia-glx doesn't support XV controls.  I'm not sure what prompted this change, but reverting to an old version worked.  Getting an old version of the nvidia driver required me to go back to an old version of mythbuntu though.  I guess I'm stuck until I decide to upgrade my hardware.

---

