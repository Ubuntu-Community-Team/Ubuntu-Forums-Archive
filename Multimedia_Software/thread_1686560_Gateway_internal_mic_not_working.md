---
title: "Gateway internal mic not working"
date: 2011-02-12
forum: Multimedia Software
---

### Post by jcreneau on 2011-02-12
I've got a Gateway CX2724.  The sound works perfectly out of the speakers and headphones, but I can't get the internal mic to work for the life of me.

I asked around on other threads and tried a few modifications to /etc/modprobe.d/alsa-base.conf and none of these get the mic working when appended:

From the ALSA-Configuration instructions
```
options snd-hda-intel model=ref
```

Ideas taken from [this thread]("http://ubuntuforums.org/showthread.php?t=314383")
```
options snd-hda-intel probe_mask=1
```
```
options snd-hda-intel model=test enable-msi=1 probe-mask=1
```

This also doesn't work (modified from [this thread.]("http://art.ubuntuforums.org/showthread.php?p=9815275"))
```
options snd-hda-intel model=ref probe_mask=1 position_fix=1
```

This also doesn't work (from ["Extra Hints to get sound working."]("https://help.ubuntu.com/community/HdaIntelSoundHowto"))
```
options snd-hda-intel model=laptop position_fix=1 enable=yes
```

When I use alsamixer to turn "mux" all the way up and have my headphones plugged into the microphone jack (don't have an external mic... ) in the front of the computer, I am able to record things but the volume is greatly muted.  Perhaps the external jack is set to default for the microphone instead of using the internal mic?

I also have the [output for alsa-info.sh]("http://www.alsa-project.org/db/?f=e5cd120004c7868cafa7d5dbad3458575d1271cf") if you want it - this was mentioned in the alsa configuration file (/usr/share/doc/alsa-base/driver/ALSA-Configuration.txt).  Info about alsa-info.sh[ here.]("http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh")

---

### Post by brianpeiris on 2011-06-05
Any update on this issue?

I've got Ubuntu 11.04 installed on a Gateway CX2724 as well (two of them actually!) and I can't get the internal microphone working either. The sound output works well.

alsa-info.sh output:
[http://www.alsa-project.org/db/?f=ca34128a4c8e4c275324e35cf9c85958a5ec2e93](http://www.alsa-project.org/db/?f=ca34128a4c8e4c275324e35cf9c85958a5ec2e93)

---

### Post by BagOfMostlyWater on 2011-07-15
The same problem exists on a Gateway LT31 with RealTek ALC272X. Many different options in the alsa-base modprobe config file were tried. natty's alsa exposes multiple capture sliders but turning them up had no effect. pavucontrol recognized Microphone and Line inputs and plugging a mic into the line input did work, but the internal mic didn't.

---

### Post by rickytikki on 2011-07-15
this might seem redundant but have you gone to sound prefrences and made sure your mic isnt muted or under connecter using internal mic??

---

