---
title: "No sound in Jaunty installed on a home-grown system"
date: 2009-05-14
forum: Multimedia Software
---

### Post by jgmsys on 2009-05-14
Greetings.

Now, I know that this appears to be a rather large issue, as many people seem to be having this problem, and I have looked at a number of postings thus far regarding the issue, but none seem to present the same situation I have, so I am opening a new thread.

I just installed Jaunty on a AMD-powered system (Athlon 64 3500+) with 4G of RAM, a VIA onboard sound system, which is disabled in the BIOS in favor of my SoundBlaster Audigy 2 Value card.  There is absolutely no sound whatsoever coming across, though I do notice a couple of things.

On bootup, the "thump" sound of access to the card by the driver being loaded occurs twice, and I'm guessing the second is an unloading.  Both sound devices appear in the volume control, and I'm honestly confused as to why the installer attempted to configure a device that is disabled in the BIOS.  To me, that's a bug.  If this is a device driver conflict, I have to conclude it's caused by the installer.  I also notice that the PulseAudio volume control, which I believe was available under Hardy Heron (I no longer have it installed, so I can't verify that), and by which I was able to establish that the system use the SoundBlaster card as the default device -- thereby getting the sound working under Hardy -- is no longer present.

Has anyone encountered such a scenario previously, and if so, what was done to address it?

Let me know if there's anything else I need to supply.

Thanks in advance.

---

### Post by jgmsys on 2009-05-15
The PulseAudio volume control was not actually installed in Hardy.  I'm getting confused now with the Fedora installation I also have.

---

