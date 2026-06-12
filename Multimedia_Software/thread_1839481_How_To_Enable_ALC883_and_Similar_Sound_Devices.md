---
title: "How To Enable ALC883 and Similar Sound Devices"
date: 2011-09-05
forum: Multimedia Software
---

### Post by rockney on 2011-09-05
For Ubuntu 11.04 Natty to enable a RealTek ALC883 (ALC-883) sound device/card for Dolby 5.1 surround sound using ALSA.

This procedure may work for other sound devices/cards as well. There is nothing specific to particular hardware here.

By default Ubuntu 11.04 is configured for stereo output. However it already has the drivers and software necessary for a 5.1 setup. All that is needed is to enable the hardware.

 1. In a terminal session run:  [FONT="Fixedsys"]alsamixer -Dhw[/FONT]

 2. Use the left/right arrow keys to go to each output and turn-up it's volume. Do this for at least Front, Surround, LFE (low frequency effects), and Center.

 3. Continue right-arrow keys until you see <Channel>, then use the up-arrow key to select "6ch". This turns-on the 5.1 hardware.

 4. Logout and back in again for the changes to take affect, or reboot.

Other Notes:

 a. To list the recognized hardware:  [FONT="Fixedsys"]aplay -l[/FONT]  and  [FONT="Fixedsys"]aplay -L[/FONT]

 b. To test the speakers:  [FONT="Fixedsys"]speaker-test -Dplug:surround51 -c6 -l1 -twav[/FONT]


*Rock 'n Roll*

:guitar:

---

### Post by rockney on 2011-10-19
Upgrade Note

Just did the distribution upgrade to 11.10 Oneiric and the previous audio setup was carried-over cleanly.  Worked the first time.

Kudos to the 11.10 migration folks.

---

