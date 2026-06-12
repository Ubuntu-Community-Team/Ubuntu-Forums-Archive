---
title: "Mythbuntu Control Center Hangs"
date: 2012-11-25
forum: Mythbuntu
---

### Post by mosborne41 on 2012-11-25
Hi All:
I have just installed Mythbuntu on a ASROCk Z77 with an Intel i3.  Mythbuntu is ver 12.04.  I have a FusionHDTV7 and a DVBSKY dual express S2 installed.  Right now I am working on the FusionHDTV7.  I an new at this and learning on the way, but I would like to get some help on a problem I've run into.  During one of my upgrades my Mybuntu Control Center must have been partially disabled.  Some of the buttons are now grayed out and if I used them the MCC just hangs. Can anyone point me in the right direction on how to fix this.  I was in the process of trying to work out two other problems: a) getting the TV card to pickup all OTA channels like my TV (60% success) and getting the remote to work.  Any ideas on the latter two problems is also welcomed.

---

### Post by Bucky Ball on 2012-11-25
*Thread moved to **Mythbuntu***

---

### Post by tgm4883 on 2012-11-26
Open it via terminal 'mythbuntu-control-centre' and post any errors. Also, what buttons are disabled?

---

### Post by mosborne41 on 2012-11-26
> **tgm4883 said:**
> Open it via terminal 'mythbuntu-control-centre' and post any errors. Also, what buttons are disabled?


Hi:
Thanks for the reply.  There is an error which states that the config file is missing so it is using the default.

"mosborne@mosborne-desktop:~$ mythbuntu-control-centre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Error: Config file not found. Setting defaults"

The ones greyed out are:  Plugins, Infared, Bare Console, System Updatess, Startup Behaavior, Backup and Restore, Proprietary Codecs, MythExport, and MySQL.  

The ones that look normal are: Log Grabber and Graphics Drivers.

I looked in the etc/mythtv folder and found a file called config.xml.  Is this the file I need to work with?  If so, where can I find the docs to set it up or is there another way to regenerate the config file?

---

### Post by mosborne41 on 2012-11-28
Hi:
This is an update.
I could not repair the Back-end, so I upgraded to 12.10.  The Back-end is now functional.   I will move on to getting the remote working and then the DVB sat card.  Also doing plenty of backups.

Thanks

---

### Post by mosborne41 on 2013-02-17
Thanks all:
After several installs, I got it working.  However, still working on drivers.  It looks like maybe the drivers are not yet fully developed yet for the DVBSky S2 and Fusionhdtv7.

---

