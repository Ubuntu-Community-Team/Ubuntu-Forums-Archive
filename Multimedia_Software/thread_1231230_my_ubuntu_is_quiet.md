---
title: "my ubuntu is quiet"
date: 2009-08-04
forum: Multimedia Software
---

### Post by stanyo on 2009-08-04
I use ubuntu and windows. Windows (xp-7) is much louder than ubuntu (6.06-9.10). In ubuntu i have every volume i found on Max. In windows I can use everything on 50% or less.  Its not a hardware problem.
Okay, is there a way i can fix this?

---

### Post by kpkeerthi on 2009-08-04
Have you checked the volume controls by right-clicking on the speaker icon on your system tray?

---

### Post by stanyo on 2009-08-04
> **kpkeerthi said:**
> Have you checked the volume controls by right-clicking on the speaker icon on your system tray?

Of course. And in every hardware profile is on max.
Is somewhere have config file to change something in it? Something that restrict my sound card.

---

### Post by martinbaselier on 2009-08-04
It's probably a driver issue. There are a couple of ways to solve it. You could keep the alsa driver and use pulse or jack to amplify the sound. For pulse I believe you would need pavucontrol. For jack you would need jackctl and jackrack and a ladspa plugin to amplify the sound. Plus you would need to change the alsa config file to redirect the sound to jack. The third option would be to try oss.

Pulse is high on resources. Jack is not really easy to install.  I'm not sure if oss is much louder, but the sound quality is better than with the alsa driver.

---

### Post by harry2006 on 2009-08-04
sometimes setting all the options in volume managers does the job...open volume control put all to 100% and retry...HTH..

---

### Post by stanyo on 2009-08-05
Something goes wrong. Now I have sound only from alsaplayer. VLC and Songbird - silence. 
How the sound work in debian, or some kind of ubuntu derivative - mint, studio or .... ?
Thank you for advise.

Edit: After some installs, removes and restarts vlc and songbird are ok.

---

