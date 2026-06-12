---
title: "Strange HDMI problem"
date: 2012-12-10
forum: Multimedia Software
---

### Post by Doctor Devious on 2012-12-10
Hello all

A question please :
I have a strange HDMI problem on Kubuntu 12.04 that popped up recently that i need some help with please.
My mother board is a Asus P5N7A with on board Nvidia graphics(Geforce 9300 series) and Realtek ALC1200 8 channel HD audio.

I have always run audio through my TV via dvi to hdmi and/or hdmi to hdmi with no problems. Had to obviously tweak a few things here and there but it normally works fine.
Just recently it has stopped working via my TV but if I start kubuntu with my AV amp connected it works fine.

The hardware output has been checked with aplay -l and hdmi is running on 0,7. If i run speaker-test i can get an output from hdmi when connected to the amp but not when connect to the TV.
Windows 7 64 bit talks to the TV fine.
I have checked and everything i can see is un-muted with the alsa mixer and pulse audio has been un-installed as it was just getting in the way.

Here&#8217;s the cruncher. I got frustrated trying to resolve the problem so reinstalled my root partition and it did not fix the problem so figure the issue is with my home partition.
I created another login to rule that out but it still does not work.

As said windows works with the hdmi with no problems so it is not a hardware isssue.

Any ideas why it would work with my AV but not my TV. A TV it was previously working fine with?

Grayham

---

### Post by SeijiSensei on 2012-12-10
I'd start by checking to make sure KDE is using the right devices.  Take a look at System Settings > Multimedia > Phonon.

---

