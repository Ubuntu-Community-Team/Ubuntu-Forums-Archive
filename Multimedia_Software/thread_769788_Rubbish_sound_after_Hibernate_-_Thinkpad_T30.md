---
title: "Rubbish sound after Hibernate - Thinkpad T30"
date: 2008-04-26
forum: Multimedia Software
---

### Post by albeano2004 on 2008-04-26
Hi,
I have recently installed Hardy Heron on my IBM Thinkpad T30. With previous releases of Ubuntu, I had a problem where if I hibernated, the sound would disappear when I next booted up. This was easily fixed by changing ```
HIBERNATE_MODE=shutdown
``` to ```
HIBERNATE_MODE=PLATFORM
``` in the ```
/etc/default/acpi-support file
```
However, with Hardy this no longer fixes the issue. If I run the command ```
sudo /etc/init.d/alsa-utils restart
``` the sound restarts, but anything which relies on PulseAudio for its sound (like VLC) sounds like crap. If I restart, it sounds fine. I've tried restarting the Pulseaudio process, but that does not work either.
Can anyone point me in the right direction? I've tried looking around on Google, but no-one seems to have a similar issue.

Thanks,
Albeano2004

---

### Post by richaoj on 2008-04-27
I'm having the same issue.  Help anyone?

---

### Post by albeano2004 on 2008-04-28
Nice to know I'm not alone ;)

---

### Post by crazy ivan on 2011-03-20
Hi guys,
I have the same problem on an Asus EEE pc 1008HA on ubuntu 10.10 (netbook remix). When I get back from hibernate and start some sound right away, the sound plays normal for some seconds, but then it gets scrambled up.

My guess was that it was due to a lot of application memory still being kept on swap after wakeup. So what I did was, write back swap to memory, i.e. enter 

```
sudo swapoff -a && sudo swapon -a
```

into the "Terminal". That did not yet solve the problem. But then I went to "Volume Control" and turned the "Setting for the selected device" to OFF in the "Hardware" tab, then I pressed play in the program again. Then I went back to "Volume Control" and set the "setting .." back to "Analog Stereo Duplex" and everything went fine :)

This filled swap makes the system very slow at the beginning and you get funny stats like "200 mb" RAM, "400 Mb" swap.. I always wonder why they don't write back swap after resume from hibernate. Maybe doing this would prevent this error from occurring at all.

---

### Post by lidex on 2011-03-20
From alsa documentation:
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

getting OSS support
-------------------
If you need old-style OSS devices for legacy applications, you should
install the oss-compat package, which should get in charge of setting up
your system with the required compatibility modules.


---

