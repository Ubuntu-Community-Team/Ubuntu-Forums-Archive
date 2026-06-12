---
title: "No sound with snd-hda-intel on D915 GLGV board"
date: 2006-01-14
forum: Multimedia &amp; Video
---

### Post by csrins on 2006-01-14
Hello,

I have installed ubuntu 5.10 on a system with the Intel D915 GLGV board.  From other posts in the forums about problems and solutions with getting the snd-hda-intel driver to work, I configured alsa so now it shows the sound card as "Realtek ALC880" in the devices option.

However, there is still no sound.   The sound mixer shows 4 input channels: mic, line, pcm2 and io/gain.

Of these pcm2 is stuck either at 100 or at 0, and cannot be set to intermediate values.  

Since the suggested solutions in the forum have not worked so far, I have posted this as a new thread.

Here is the sequence of events:

1.  The installation of 5.10 hangs at the "starting hotplug" step.  Disabling the onboard sound finished the installation.
2.  The snd-hda-intel driver which comes with 5.10 was added to /etc/hotplug/blacklist
3.  Alsa 1.10 was configured and the driver entry removed from the blacklist.
4.  The system now boots properly with onboard sound enabled, but not a peep comes out.  All volume levels are unmuted.  

Googling, it becomes apparent that development of these drivers is still in progress, but has anyone got onboard sound working for this configuration?  Any suggestions/directions greatly appreciated.

Thanks in advance,
csrins

---

### Post by csrins on 2006-01-16
Anyone get sound working with the ALC880 in the intel d915 mobos?

Thanks,
csrins

---

