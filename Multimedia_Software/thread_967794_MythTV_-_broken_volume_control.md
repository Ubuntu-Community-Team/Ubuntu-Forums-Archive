---
title: "MythTV - broken volume control"
date: 2008-11-02
forum: Multimedia Software
---

### Post by scweston on 2008-11-02
Hi,

I have recently done a fresh installation of Intrepid Ibex and added MythTV to the system. My system uses a Hauppauge Nova-T 500 card, with a remote control.

Firstly I have to thank the many people who contribute to these forums. Using the various How-Tos and reading the various threads I have managed to set up the system to work almost perfectly. However, I do have a slight issue, which I did not experience when I was using Hardy.

The problem seems to be with the volume control within MythTV. It seems to have absolutely no effect on the actual volume at all. I have tried changing the volume whilst watching live TV and also tested it playing back music in MythMusic plugin. Also switching on 'mute' also has no effect.

I have tried changing the master volume controls and tested the volume controls in other applications (such as mplayer and amarok) and can see no problems there. It's only in MythTv that the problem arises.

I would appreciate any help. If you need more info please just let me know (although if the formula one GP comes on you may not here back from me until after the race...lol).

Stephen

Also, if anyone could help with another problem of the live TV playback becoming jittery when the OSD comes up the I will welcome suggestions (again this wasn't a problem in hardy only in intrepid).

---

### Post by scweston on 2008-11-02
Hi,
Thanks to anyone who read my post and was considering helping. I''ve managed to fix my own problem.

For others who have the same issue, all I had to do was change the 'Mixer' setting in the Utilities/Setup > Setup > General > Audio from PCM to Master.

Works fine now!

Stephen

---

### Post by araidian on 2011-05-01
> **scweston said:**
> Hi,

For others who have the same issue, all I had to do was change the 'Mixer' setting in the Utilities/Setup > Setup > General > Audio from PCM to Master.

Works fine now!

Stephen


I can confirm that indeed it does thanks mate you rock my world :)

 I had this exact issue after upgrading mythbuntu to the 11.4 distro and after reboot i had no sound at all i had to add 
options snd-hda-intel model=auto 
to 
/etc/modprobe.d/alsa-base.conf then changed mixer from pcm to master and works a treat, i hope that this helps someone.

peace.

---

