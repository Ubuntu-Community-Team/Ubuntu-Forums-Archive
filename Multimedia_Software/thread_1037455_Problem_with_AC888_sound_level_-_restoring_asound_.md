---
title: "Problem with AC888 sound level - restoring asound settings"
date: 2009-01-11
forum: Multimedia Software
---

### Post by dj_tcso on 2009-01-11
Hello.

I've problem with my soundcard (integrated NVidia based on AC888).

Sound level are very low on clear install comparing to my previous Kubuntu installation (also 8.04 but upgraded from 7.10) and Windows.

I've found out that ranges in /var/lib/alsa/asound.state file were setup  on wrong levels by default (as I suppose).
After changing values manually - Master Volume from default 31 to 63 and reloading alsa:
```
sudo alsa force-reload
```
everything was working ok. Sound level was as it should be from beginning.

Problem is that after reboot values from asound.state file are not used and each time I have to reload alsa manually.
Is there any trick that would tell alsa to use values from that file when initializing?

PS. In Kubuntu 8.10 I had same problem with low sound level so I reinstalled 8.04 but sound didn't work as it did previously.

---

