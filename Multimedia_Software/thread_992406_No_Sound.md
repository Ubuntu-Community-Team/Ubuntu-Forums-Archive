---
title: "No Sound"
date: 2008-11-24
forum: Multimedia Software
---

### Post by supernova1 on 2008-11-24
I just installed Ubuntu 8.10 64-bit on my AMD 64 3200+.  Let me start off by saying I have searched the forums and have found some things helpful but have not found a solution for my problem.

I have 2 sound cards, 1 onboard and 1 PCI card, it is a ALS-4000 sound card.  The onboard has never worked, even in windows which is why I have the PCI sound card.  if I go to System->Preferences->Sound and select Avance Logic ALS 4000 (OSS) and hit test I can hear the tone coming from my speakers.  However I cannot hear anything else such as audio files played in Rythmbox, flash videos on youtube etc...

Does anyone know what steps I should go through to troubleshoot this issue?

Thanks,

David

---

### Post by psyke83 on 2008-11-24
> **supernova1 said:**
> I just installed Ubuntu 8.10 64-bit on my AMD 64 3200+.  Let me start off by saying I have searched the forums and have found some things helpful but have not found a solution for my problem.

I have 2 sound cards, 1 onboard and 1 PCI card, it is a ALS-4000 sound card.  The onboard has never worked, even in windows which is why I have the PCI sound card.  if I go to System->Preferences->Sound and select Avance Logic ALS 4000 (OSS) and hit test I can hear the tone coming from my speakers.  However I cannot hear anything else such as audio files played in Rythmbox, flash videos on youtube etc...

Does anyone know what steps I should go through to troubleshoot this issue?

Thanks,

David

You need to configure PulseAudio properly (and ensure it chooses the correct card as default). See: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

