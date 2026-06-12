---
title: "Please HELP: after update lost sound"
date: 2007-03-10
forum: Multimedia &amp; Video
---

### Post by Markus72 on 2007-03-10
Hi,

I'm desperate.  On my htpc (ubuntu edgy) I lately made an update and since that time, the sound doesn't work any more. The speaker icon shows a big red cross.
I didn't find errors in the logs but I have to admit that I don't know exactly what to search for.

Opening the settings or the mixer results in error messages about missing gstreamer-plugins or a misconfigured sound device or driver.

The sound card (onboard msi k8t) works fine when using the live cd.
So it must have something to do with the last update (I didn't change the system except to that).

While searching for answers I found out that there are numerous other people out there with the same problem - lost sound after update - but without any solution.

Can someone tell me how to fix my problem or - in the first place - how to find out what the original problem really is?

Thanks a lot
Markus

---

### Post by duckzin on 2007-03-10
The problem is w/ the sound levels. Open the [gmix] on the terminal and set all the sound levels to the max.

Hope it will help.:)

---

### Post by Teunis on 2007-03-10
An other solution I had to use after the upgrade to Feisty was through Alsamixergui; it allowed me to switch on the PCM volume that had apparently been disabled during the upgrade.

---

### Post by Shay Stephens on 2007-03-10
> **Teunis said:**
> An other solution I had to use after the upgrade to Feisty was through Alsamixergui; it allowed me to switch on the PCM volume that had apparently been disabled during the upgrade.

Thank you!  This fixed me up.  I ran
```
alsamixer
```
from the terminal and boosted the PCM volume and got my sound back :-)

Left & right arrow keys switch volume controls, up and down arrow keys change the volume of the selected control.  Control Z to exit the mixer.

---

