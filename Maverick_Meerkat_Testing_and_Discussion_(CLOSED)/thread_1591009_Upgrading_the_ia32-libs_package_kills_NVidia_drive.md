---
title: "Upgrading the ia32-libs package kills NVidia driver, forcing me to reinstall it."
date: 2010-10-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by DodgeV83 on 2010-10-08
Upgrading the ia32-libs package kills NVidia driver, forcing me to reinstall it.  I installed the Nvidia 64 bit 260.19.06 driver myself (before Ubuntu started packaging the beta driver themselves).  Is anyone experiencing this issue with the automatic NVidia driver install?  I don't want to submit a bug report if it's just affecting the manual install people.

Edit:  BTW, when I say "kills" I mean Wine games don't work and I can't turn on Compiz.

---

### Post by Quackers on 2010-10-08
I have the Nvidia driver installed and have run the update. It hasn't done anything nasty to my system. I don't play games through Wine,but compiz still works fine here.

---

### Post by efflandt on 2010-10-09
I had no problems, possibly because I uninstalled flashplugin-installer, which did not really remove nswrapper and related 32-bit libs.  So at some point when doing something else with apt-get it suggested doing an autoremove which removed nswrapper and the unused ia32-libs.

The 10.2 r85 flashplayer.so from flashplugin-installer was segfaulting causing npviewer.bin related to Firefox 3.6.10 to crash in both Maverick and Lucid.  But I never really noticed it other than /var/log/messages in Lucid and crash reports in Maverick, so it may have just been broken flash ads.

I am using real 64-bit flash 10.2 r161 without any issues from [http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)

To switch from nvidia 256.53 in 10.10 beta to 2.60.19.06 which is now the default in the repos, all I did was deactivate nvidia in Hardware Drivers, reboot, activate nvidia, reboot.

---

### Post by Jim_in_Omaha on 2010-10-09
> **DodgeV83 said:**
> Upgrading the ia32-libs package kills NVidia driver, forcing me to reinstall it.  I installed the Nvidia 64 bit 260.19.06 driver myself (before Ubuntu started packaging the beta driver themselves).  Is anyone experiencing this issue with the automatic NVidia driver install?  I don't want to submit a bug report if it's just affecting the manual install people.

Edit:  BTW, when I say "kills" I mean Wine games don't work and I can't turn on Compiz.

My sound is choppy in Urban Terror running the 32 bit not the 64 bit version. 

Update: I just rebooted and its fixed now.

---

