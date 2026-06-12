---
title: "USB headset not working after hibernation"
date: 2010-07-12
forum: Multimedia Software
---

### Post by Jguy101 on 2010-07-12
I have a Microsoft LX-3000 USB headset that has been working fine for me on all of my Ubuntu machines... until today.  I accidentally clicked on "Hibernate" instead of "Shut Down" on my Lucid laptop this morning, and something seemed a little off about the hibernation process, although I don't remember exactly what happened.  Anyway, since I woke this machine up, I can't get sound out of the headset.  I've plugged it into multiple USB ports and can still use the microphone and the volume controls just fine, but there's no output.  (Yes, I've made sure the device is enabled for output in my sound preferences).  Any ideas on how I can fix this?

---

### Post by lidex on 2010-07-14
Hibernation can cause a variety of issues with your system. Have you tried rebooting? This is from alsa documentation ( I could be wrong but assume it would also apply to hibernation?):
> reloading modules across APM suspend-and-resume
-----------------------------------------------
During suspension many peripherals are switched off; on resuming the
machine these peripherals need to be re-initialized.  Many ALSA
drivers do this properly but some still do not.

If this problem affects you and if your ALSA drivers are built as
loadable modules and your kernel supports module unloading then you
can work around the problem by unloading the driver before suspending
and loading it again after resuming.  This will be done for you
automatically if you add the name of the problematic sound card driver
module to the variable force_unload_modules_before_suspend variable in
/etc/default/alsa.  E.g., if your CS46XX and AZX cards don't work
properly after resuming from APM suspend, add the names of their
driver modules to the list:

    force_unload_modules_before_suspend="snd-cs46xx snd-azx"


restoring sound volumes across APM suspend-and-resume
-----------------------------------------------------
alsa-base provides an APM script in /etc/apm/scripts.d/alsa to
automatically store/restore sound volumes during APM suspension.
Since this option relies on alsactl, please install the recommended
alsa-utils package.

unloading modules
-----------------
If you want to unload ALSA driver modules then you will have to stop
all applications that are using ALSA device files.  You can do both
in one step by running:

    alsa force-unload


---

### Post by Jguy101 on 2010-07-28
> **lidex said:**
> Hibernation can cause a variety of issues with your system. Have you tried rebooting? This is from alsa documentation ( I could be wrong but assume it would also apply to hibernation?):Sorry that it took me a while to get back.  I am always putting this system on sleep, and I've never had any problems because of it.  And since it's been two weeks, I've rebooted quite a bit.

---

