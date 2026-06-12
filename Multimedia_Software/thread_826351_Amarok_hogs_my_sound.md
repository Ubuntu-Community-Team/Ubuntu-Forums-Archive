---
title: "Amarok hogs my sound"
date: 2008-06-11
forum: Multimedia Software
---

### Post by chiefmanyrabbitguteat on 2008-06-11
Hey all
I am running Ubuntu Hardy (Gnome) on a Dell Latitude D820 with the Intel HDA sound card.  When I play a file in Amarok, it disables my sound card for Flash.  For example, I cannot watch videos on youtube if I started Amarok first.  Likewise, I cannot use Amarok, if I opened Firefox first.  

At first, I thought that this was a Flash bug, but it doesn't show up with other sound apps.  I can use Rhythmbox and Flash at the same time.  Flash and Audacity, VLC and any of the above, etc.

---

### Post by Victormd on 2008-06-11
What sound driver are you using?
OSS limits your applications while ALSA will allow several instances (i.e., amarok + flash - someone please correct me if this is wrong...)
Open SYSTEM>PREFERENCES>SOUND and under the DEVICES tab, replace AUTODETECT for ALSA and this should hopefully do the trick... Let us know if it works...

---

### Post by chiefmanyrabbitguteat on 2008-06-11
Worked like a champ.  It was set using xine and esd, I think.  Now, I set it to use ALSA, and everything works peachy!

---

### Post by chiefmanyrabbitguteat on 2008-06-11
In other words, my sound card was already set up to use ALSA.  But I hadn't yet changed Amarok to ALSA.  This was done in Settings->Configure Amarok

---

### Post by Victormd on 2008-06-13
very nice!!! :)

---

### Post by mastermindg on 2008-06-13
I'm not sure if you're problem is completely resolved. :)

In order to get Amarok working effectively on Hardy in Gnome, you have to set it up under pulseaudio. Pulse ports the sound through ALSA. Flash support for Firefox is setup under pulseaudio, so you'll see issues later if you keep Amarok at alsa.

---

