---
title: "Gnome ignoring some automatic settings"
date: 2009-02-01
forum: Multimedia Software
---

### Post by Montblanc_Kupo on 2009-02-01
I have an Nvidia 6800 XT installed on this machine... been running really well actually (aside from it can't figure out which card it is but it seems to run okay shrug).

The problem I just noticed though is that I have some custom settings in the nvidia-settings. I have changed the "digital vibrance", the "gamma", and the "brightness" through the settings (can't be done through My monitor... no actual controls lol). This works fine... while I'm in session... if I logout or reboot... it remembers My resolution and such... but doesn't apply these tweaks. If I start nvidia-settings... they automatically kick in as soon as it starts and stay where I want them. I am currently using the 180.11 drivers from the repositories. Haven't had any other problems I've seen with them... but I had the same issue with 177 as well.

So I guess two questions.

1. Any ideas how to get these to automatically apply at boot/login?

2. Where does nvidia store its settings? I thought it was all stored in xorg.conf... but even if I save to xorg with the little button in nvidia-settings... the information that is displayed in nvidia-settings doesn't always match xorg... especially if I manually edit xorg.

---

