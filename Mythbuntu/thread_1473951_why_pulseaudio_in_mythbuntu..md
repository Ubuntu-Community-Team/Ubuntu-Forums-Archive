---
title: "why pulseaudio in mythbuntu."
date: 2010-05-05
forum: Mythbuntu
---

### Post by agkbill on 2010-05-05
A short question, why is pulseaudio included in mythbuntu when MythTV do not support pulseaudio?


I have never managed to get sourround audio to work OK with mythtv and pulseaudio.

I even tried to change to Gentoo in order to avoid pulseaudio, but unfortunately there were even bigger problems with mythtv there. Guess you need a phD to manage Gentoo;)

well, pulseaudi has never caused anything but troble, so I dont understand why it is included.

to bad with such great software as MythTV.

Best regards,
/Christer

---

### Post by tgm4883 on 2010-05-05
It's not included in Mythbuntu. Did you install other packages that may have pulled it in? Did you install MythTV on top of Ubuntu?

---

### Post by agkbill on 2010-05-06
Hi,

Ok, it should not be installed.

I installed 10.04 from CD that I burned from ISO-file.

But I did installed something that might pulled it in I realize now. That is Ubuntu Desktop.

From "Mythbuntu Control Centre" in system roles I marked Ubuntu Desktop.

Maybe that is the problem?

I will try to reinstall from CD and se.

Thank you for replay!

Best regards,
/Christer

---

### Post by tgm4883 on 2010-05-06
yea, ubuntu desktop pulled it in

---

### Post by agkbill on 2010-05-06
Thank You!

I did not thought of that in the first place.

Time to reinstal.


Do you know if it is possible to install Gnoome desktop without pulseaudio? 

Guess that it is Ubuntu desktop package that inklude pulseaudio and not Gnoome itself.

Best regards,
/Christer

---

### Post by tgm4883 on 2010-05-06
Doubt it. It is probably a dependency of ubuntu-desktop

---

### Post by yonkiman on 2010-05-08
> **agkbill said:**
> Do you know if it is possible to install Gnoome desktop without pulseaudio?

Actually, I'm pretty sure you can uninstall pulseaudio.  Just go into Synaptic and search for anything *pulse* and if it IS related to pulseaudio, uninstall it.  If, as you try to do that, it says it needs to uninstall a zillion non-audio packages, then don't do it.

But I'm pretty sure I (Mythbuntu 9.10) successfully uninstalled it several times while I was troubleshooting my alsa sound problems.  However right now I have Pulse installed, but am basically doing everything through alsa, and all my A/V programs seem to be happy.

-Fred

---

