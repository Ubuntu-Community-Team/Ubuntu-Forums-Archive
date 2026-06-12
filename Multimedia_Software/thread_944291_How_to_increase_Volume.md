---
title: "How to increase Volume?"
date: 2008-10-11
forum: Multimedia Software
---

### Post by vittalp88 on 2008-10-11
Hi guys, I am getting a very low volume output whenever I try playing some videos. This problem is primarily with the default player. The volume increases a little bit when I shift over to VLC media player, but is still not sufficient. 
I have put the volume to max in every place possible.
Made it 100% in the Master Volume,
Made it 100% in the VLC's volume controller. But still I am not getting as high volumes I get in WIN XP. 
Can anyone help me out here? Is there any volume controller that I am missing/dont know of?:confused:

---

### Post by buixuanduong1983 on 2008-10-11
Try righ-click on Volume icon next to the clock, Open volume control, then increase the PCI volume there. Also try this command to see if you have alsa installed:
alsamixer
Hope this help.

---

### Post by vittalp88 on 2008-10-11
I had tried that also. Its been set to maximum. But still no appreciable increase in volume.

---

### Post by buixuanduong1983 on 2008-10-11
Sorry for late, and how about alsamixer? Before in Ubuntu 7.04, I also had the problem with low volume, then I installed alsa and get a very good volume. In 7.10 alsa is automatic installed and till now I don't have that problem anymore.

---

### Post by vittalp88 on 2008-10-12
I am in 8.04
Is aslamixer installed in this also? If so how to use it?

---

### Post by vittalp88 on 2008-10-12
Anyone? please?

---

### Post by buixuanduong1983 on 2008-10-21
Once again sorry for late. 
I'm not sure alsa is the problem, because before in Ubuntu 7.04 I also had low volume, but after install alsa I have good volume.
alsamixer is installed by default in my laptop in 7.10 (Acer Aspire 3650). You can test it by typing in command line:
alsamixer
If you see a colorful graphic screen mean it is installed.
So, maybe it is not what you want, try google more, hope someone have solution for your problem.
Good luck!

---

### Post by 22Ti on 2008-11-29
To vittalp88:

VLC has a "built in" volume booster which will allow the volume output=electrical signal output to your speakers/headphones go up to 200%.
Check Settings->Preferences->Interface->hotkeys settings  to find the default(as I have changed mine :P) hotkey!

A quick fix that might help! :)

---

### Post by Jack Yan on 2012-03-14
> **buixuanduong1983 said:**
> Try righ-click on Volume icon next to the clock, Open volume control, then increase the PCI volume there. Also try this command to see if you have alsa installed:
alsamixer
Hope this help.

This helped me! Thank you!

---

