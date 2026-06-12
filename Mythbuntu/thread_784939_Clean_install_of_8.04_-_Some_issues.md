---
title: "Clean install of 8.04 - Some issues"
date: 2008-05-06
forum: Mythbuntu
---

### Post by Dewey_Oxberger on 2008-05-06
Summary: a clean install of 8.04 doesn't work even though 7.10 worked great.

Background:

I have a working 7.10 Mythbuntu system built in December 2007 on an ABIT AN-M2HD, Athlon X2 BE-2400 Dual Core (45W), 2 Gig of ram, 250G HD, HDHomeRun tuner, Samsung TV.  The 7.10 install went fine except for a video driver issue that the Envy script fixed with no hassle.  As I recall I spent a lot of time fixing directory permissions/owners and got just about everything working with no real problem.

What I did:

I got a new hard-drive (640G). Pulled the 250G (yes, it's my escape route). Put the 640G in the system and installed Mythbuntu 8.04 and ran into some problems:

1)  Boot off the install CD, say install, follow all the steps including partitioning the HD.  Things seem to happen like clockwork but once the install looks done I was expecting the system to have to reboot, pull the install CD, and boot off the HD.  It didn't happen.  I was left looking at a screen with two icons- one of them says click here to install.  What?

2)  There is a typo on that desktop screen at the end of the install - look for "to install to permanently install".  Minor deal.

3)  So I reboot manually, pull the boot CD, and now the trouble starts.  The system doesn't have network connectivity and doesn't have the ubuntu desktop running.  I boot to a text mode shell.  I sense some quality time with google in my future. :)

At this point my wife asked "if it ain't broke why are you fixing it?"  (Myth was offline and she was going to miss a show).  So I put the 250G HD back and set the system back to running.

Anyway - can anyone comment on whether the install should have had me pull the CD and reboot automatically.  It seems goofy to get to the end and be staring at the icon that says "click here to install"  Did it do that for you?  What was the expected behavior here?

Any hints or really great web pages on getting networking going on ubuntu?

I figure once I get the networking back a sudo apt-get install envyng will fix the rest.

Thanks

---

### Post by superm1 on 2008-05-07
> **Dewey_Oxberger said:**
> Summary: a clean install of 8.04 doesn't work even though 7.10 worked great.

Background:

I have a working 7.10 Mythbuntu system built in December 2007 on an ABIT AN-M2HD, Athlon X2 BE-2400 Dual Core (45W), 2 Gig of ram, 250G HD, HDHomeRun tuner, Samsung TV.  The 7.10 install went fine except for a video driver issue that the Envy script fixed with no hassle.  As I recall I spent a lot of time fixing directory permissions/owners and got just about everything working with no real problem.

What I did:

I got a new hard-drive (640G). Pulled the 250G (yes, it's my escape route). Put the 640G in the system and installed Mythbuntu 8.04 and ran into some problems:

1)  Boot off the install CD, say install, follow all the steps including partitioning the HD.  Things seem to happen like clockwork but once the install looks done I was expecting the system to have to reboot, pull the install CD, and boot off the HD.  It didn't happen.  I was left looking at a screen with two icons- one of them says click here to install.  What?

2)  There is a typo on that desktop screen at the end of the install - look for "to install to permanently install".  Minor deal.

3)  So I reboot manually, pull the boot CD, and now the trouble starts.  The system doesn't have network connectivity and doesn't have the ubuntu desktop running.  I boot to a text mode shell.  I sense some quality time with google in my future. :)

At this point my wife asked "if it ain't broke why are you fixing it?"  (Myth was offline and she was going to miss a show).  So I put the 250G HD back and set the system back to running.

Anyway - can anyone comment on whether the install should have had me pull the CD and reboot automatically.  It seems goofy to get to the end and be staring at the icon that says "click here to install"  Did it do that for you?  What was the expected behavior here?

Any hints or really great web pages on getting networking going on ubuntu?

I figure once I get the networking back a sudo apt-get install envyng will fix the rest.

Thanks
When the installer failed like that, it's probably from a setting you chose (unfortunately probably a bug).  Could you post /var/log/syslog in a bug after a failed install?

---

### Post by Dewey_Oxberger on 2008-05-08
superm1 - thanks for the help.

Where should I post the log?  Here or to a bug on lauchpad?

The log ends with this (and I'm going to try installing without the lirc stuff...):

May  8 14:07:55 ubuntu python: log-output -t ubiquity chroot /target mount -t proc proc /proc
May  8 14:07:55 ubuntu python: log-output -t ubiquity chroot /target mount -t sysfs sysfs /sys
May  8 14:07:55 ubuntu python: log-output -t ubiquity chroot /target dpkg-divert --package ubiquity --rename --quiet --add /sbin/udevd
May  8 14:07:58 ubuntu python: log-output -t ubiquity umount /target/cdrom
May  8 14:07:58 ubuntu finish-install: Disabling CD in sources.list
May  8 14:07:58 ubuntu python: Exception during installation:
May  8 14:07:58 ubuntu python: Traceback (most recent call last):
May  8 14:07:58 ubuntu python:   File "/usr/share/ubiquity/mythbuntu_install.py", line 365, in <module>
May  8 14:07:58 ubuntu python:     install.run()
May  8 14:07:58 ubuntu python:   File "/usr/share/ubiquity/mythbuntu_install.py", line 152, in run
May  8 14:07:58 ubuntu python:     self.configure_ir()
May  8 14:07:58 ubuntu python:   File "/usr/share/ubiquity/mythbuntu_install.py", line 263, in configure_ir
May  8 14:07:58 ubuntu python:     self.lirc.set_device(ir_device,"remote")
May  8 14:07:58 ubuntu python:   File "/var/lib/python-support/python2.5/mythbuntu_common/lirc.py", line 128, in set_device
May  8 14:07:58 ubuntu python:     self.remote_modules=device["remote_modules"]
May  8 14:07:58 ubuntu python: KeyError: 'remote_modules'
May  8 14:07:58 ubuntu python: 
May  8 14:07:58 ubuntu ubiquity[8278]: debconffilter_done: Install (current: None)
May  8 14:07:58 ubuntu ubiquity[8278]: Exception in GTK frontend (invoking crash handler):
May  8 14:07:58 ubuntu ubiquity[8278]: Traceback (most recent call last):
May  8 14:07:58 ubuntu ubiquity[8278]:   File "/usr/lib/ubiquity/bin/ubiquity", line 229, in <module>
May  8 14:07:58 ubuntu ubiquity[8278]:     main()
May  8 14:07:58 ubuntu ubiquity[8278]:   File "/usr/lib/ubiquity/bin/ubiquity", line 226, in main
May  8 14:07:58 ubuntu ubiquity[8278]:     install()
May  8 14:07:58 ubuntu ubiquity[8278]:   File "/usr/lib/ubiquity/bin/ubiquity", line 68, in install
May  8 14:07:58 ubuntu ubiquity[8278]:     ret = wizard.run()
May  8 14:07:58 ubuntu ubiquity[8278]:   File "/usr/lib/ubiquity/ubiquity/frontend/mythbuntu_ui.py", line 259, in run
May  8 14:07:58 ubuntu ubiquity[8278]:     self.progress_loop()
May  8 14:07:58 ubuntu ubiquity[8278]:   File "/usr/lib/ubiquity/ubiquity/frontend/mythbuntu_ui.py", line 337, in progress_loop
May  8 14:07:58 ubuntu ubiquity[8278]:     (ret, realtb))
May  8 14:07:58 ubuntu ubiquity[8278]: RuntimeError: Install failed with exit code 1
May  8 14:07:58 ubuntu ubiquity[8278]: Traceback (most recent call last):
May  8 14:07:58 ubuntu ubiquity[8278]:   File "/usr/share/ubiquity/mythbuntu_install.py", line 365, in <module>
May  8 14:07:58 ubuntu ubiquity[8278]:     install.run()
May  8 14:07:58 ubuntu ubiquity[8278]:   File "/usr/share/ubiquity/mythbuntu_install.py", line 152, in run
May  8 14:07:58 ubuntu ubiquity[8278]:     self.configure_ir()
May  8 14:07:58 ubuntu ubiquity[8278]:   File "/usr/share/ubiquity/mythbuntu_install.py", line 263, in configure_ir
May  8 14:07:58 ubuntu ubiquity[8278]:     self.lirc.set_device(ir_device,"remote")
May  8 14:07:58 ubuntu ubiquity[8278]:   File "/var/lib/python-support/python2.5/mythbuntu_common/lirc.py", line 128, in set_device
May  8 14:07:58 ubuntu ubiquity[8278]:     self.remote_modules=device["remote_modules"]
May  8 14:07:58 ubuntu ubiquity[8278]: KeyError: 'remote_modules'
May  8 14:07:58 ubuntu ubiquity[8278]: 
May  8 14:07:58 ubuntu last message repeated 2 times
May  8 14:08:01 ubuntu gdm[2589]: WARNING: Didn't understand `' (expected true or false) 
May  8 14:08:04 ubuntu /usr/sbin/cron[2665]: (CRON) INFO (pidfile fd = 3)
May  8 14:08:04 ubuntu /usr/sbin/cron[2666]: (CRON) STARTUP (fork ok)
May  8 14:08:04 ubuntu /usr/sbin/cron[2666]: (CRON) INFO (Running @reboot jobs)
May  8 14:08:21 ubuntu NetworkManager: <info>  Updating allowed wireless network lists. 
May  8 14:08:21 ubuntu NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored..

---

### Post by Weidbrewer on 2008-05-09
I had a similar problem with an install last night.  I used the Alternate Install CD, since the machine is older tech and has issues with graphical installation.  When it was done, it *did* kick the cd out and reboot...but then it went to a text login and prompt.

This was at about 2:30 this morning, and I've been having nothing but trouble with this machine, so I didn't have time to trouble-shoot.

---

### Post by Dewey_Oxberger on 2008-05-10
If I'm reading the syslog right about the only thing that seems wrong is I checked the option to configure a remote and that process seems to crash. 

I'll be trying again later today and I'll post back what I get.

---

### Post by Weidbrewer on 2008-05-10
Okay, I'm up and running...I did a fresh install of Ubuntu 8.04, then DL'd Mythbuntu Control Center again and installed that way.  Then, I (by accident) discovered that the restricted Ati driver is what was screwing me up in an earlier problem - By disabling it, everything started to work fine.

---

### Post by Dewey_Oxberger on 2008-05-18
I did a clean install of 8.04 with two changes:

No IR remote

Changed a JFS partition mount point from /media to /htpc because I realised that mount point has special meaning...

It installed fine and almost works but their are two bugs that I need to report.

So - looks like checking the IR remote config and setting a remote to custom is a show-stopper.

---

