---
title: "Flash Update -&gt; no sound for flash"
date: 2010-06-26
forum: Multimedia Software
---

### Post by AKADAP on 2010-06-26
Flash was updated two days ago on my system:

flashplugin-installer (10.1.53.64ubuntu0.10.04.1) to 10.1.53.64ubuntu0.10.04.2
flashplugin-nonfree (10.1.53.64ubuntu0.10.04.1) to 10.1.53.64ubuntu0.10.04.2

Since then, I have been unable to get any sound out of flash.
All other sound sources work fine.

Is there any work around?

---

### Post by AKADAP on 2010-06-26
I installed "flash-aid".

Still no sound in videos

---

### Post by AKADAP on 2010-06-27
Ok, it is stranger than I originally thought.

About the same time as this update, I changed from using the SPDIF out to using the analog outputs of my motherboard (SPDIF can't do 7.1).

It turns out that all of my sound is going to the analog outputs except sound from Flash, that is still going to the SPDIF output.

I have been unable to find any switch anywhere to change this.

---

### Post by lovinglinux on 2010-06-27
> **AKADAP said:**
> Ok, it is stranger than I originally thought.

About the same time as this update, I changed from using the SPDIF out to using the analog outputs of my motherboard (SPDIF can't do 7.1).

It turns out that all of my sound is going to the analog outputs except sound from Flash, that is still going to the SPDIF output.

I have been unable to find any switch anywhere to change this.

Perhaps with [padevchooser](apt:padevchooser). I have no idea how to use it, but I have seen reports from users being able to fix flash sound issues after installing it.

---

### Post by AKADAP on 2010-06-27
> **lovinglinux said:**
> Perhaps with [padevchooser](apt:padevchooser). I have no idea how to use it, but I have seen reports from users being able to fix flash sound issues after installing it.

padevchooser did not help. I messed with a bunch of settings, none had any effect.

---

### Post by lovinglinux on 2010-06-27
Try [http://ubuntuforums.org/showpost.php?p=9414072&postcount=5](http://ubuntuforums.org/showpost.php?p=9414072&postcount=5)

---

### Post by AKADAP on 2010-06-27
> **lovinglinux said:**
> Try [http://ubuntuforums.org/showpost.php?p=9414072&postcount=5](http://ubuntuforums.org/showpost.php?p=9414072&postcount=5)

pavucontrol is one of the tools accessible via pavuchooser. The outputs were not muted.

---

### Post by lovinglinux on 2010-06-27
Try [http://ubuntuforums.org/showpost.php?p=9402185&postcount=7](http://ubuntuforums.org/showpost.php?p=9402185&postcount=7)

---

### Post by AKADAP on 2010-06-27
> **lovinglinux said:**
> Try [http://ubuntuforums.org/showpost.php?p=9402185&postcount=7](http://ubuntuforums.org/showpost.php?p=9402185&postcount=7)

That is missing a step. after logout-login I had to go to System->Preferences->Sound and set everything up again, but yes I now have analog sound from Flash. Thanks

---

### Post by lovinglinux on 2010-06-27
> **AKADAP said:**
> That is missing a step. after logout-login I had to go to System->Preferences->Sound and set everything up again, but yes I now have analog sound from Flash. Thanks

Thanks for the missing info. I will add this to my flash troubleshooting tutorial. It might help others in the same situation.

---

