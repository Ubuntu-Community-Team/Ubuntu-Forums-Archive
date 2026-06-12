---
title: "Unable to Run 10.10 Installer"
date: 2010-12-04
forum: Mythbuntu
---

### Post by uncle hammy on 2010-12-04
I debated on replying in the other thread recently about this, however this is an entirely different issue.

I had a problem install 10.10 fresh, in that it simply wouldn't get anywhere.  So, I turned off quiet and found that the boot process was getting to "freeing intrd memory" then it would simply sit there.  I tried the nomodeset plan as suggested, with no luck.

Eventually, I gave up, installed 10.04 then immediately upgrade to 10.10....with the same result.  Can't boot.  All I see is a blinking cursor in the upper left corner of the screen.

I finally stumbled (I don't even remember where now) accross setting "acpi=off" in my boot parameters (/etc/default/grub -> GRUB_CMDLINE_LINUX_DEFAULT), and WHAM, I was into 10.10 goodness.

However, there is a downside.  I can no longer shut down my machine.  Well, I can, but it doesn't power down.

Anyone help me out of this one?

---

### Post by kyphos on 2010-12-04
@Uncle,
I can't help you on this, but I can tell you I encountered a very similar problem. Trying to install from a 10.10 LiveCD, the installer hangs when it gets to the 'Configure Hardware' phase.  
According to the logs, the installer is stuck on the process of rebuilding the initramfs  which is one of the last steps for the configure_hardware step.

I only encounter this if I'm trying to install to a SATA drive.  I tried installing to an old small IDE drive, and much to my surprise, the install completed successfully. However, it wouldn't boot reliably, so I gave up and returned to 10.04.

I didn't know about the "acpi=off" option you mentioned, so perhaps I'll try that.

I opened a bug on the installer failure:
[https://bugs.launchpad.net/bugs/670003](https://bugs.launchpad.net/bugs/670003)

---

### Post by Whoop365 on 2010-12-04
This probably wont help, but iv realized that my ubuntu doesnt like to start with disks and flash drives plugged in sometimes...try to eject everything. Sorry if it doesnt help - but mine reacts the same way sometimes though.

---

### Post by uncle hammy on 2010-12-04
Well, fwiw, I do have an external usb drive plugged in all the time (I do backups to it) which has not caused any issues under 10.04.  I did think of unplugging it, but then thought "well, that would be stupid to have to unplug it every time I need to reboot).  Plus, I think I tried to install on this machine earlier and couldn't get X open to do the installation and just quit that day and never went back to it.

The point has become somewhat moot because after a 2nd reboot during my setup of 10.10 with acpi=off, MythWeather and MythWeb stopped working, because somehow the InnoDb engine wasn't loading in MySQL (I suspect the MythWeather tables became corrupt, possibly from hitting the reset button because the machine wasn't powering down during shutdowns).  I ended up deciding 10.10 was worth this crap and throwing up the white flag and went back to 10.04.  No problems booting, no "acpi=off", I know it's actually halted when the power goes out, etc.

---

