---
title: "Various problems getting started"
date: 2011-04-14
forum: Mythbuntu
---

### Post by doveman on 2011-04-14
I'm trying to get Mythbuntu 10.10 working.

I installed with Wubi and the first problem was that the default screen resolution was too small to see the install screens properly to click on the buttons. This seems to be quite common to Linux in my experience though and I fixed that by using some startup option or other.

Then, when it came to the Test Connection to database screen, I entered a PIN but it said it failed to connect. I continued anyway.

Then, when it rebooted, after choosing the Mythbuntu option from the boot.ini menu, I got a Grub v1.98 menu with only two options, one each for my two XP boot partitions, and no Mythbuntu entry. bcbc helped me with this at [http://ubuntuforums.org/showthread.php?t=1639198&page=36](http://ubuntuforums.org/showthread.php?t=1639198&page=36) and it's been reported as a bug at [https://bugs.launchpad.net/mythbuntu/+bug/759492](https://bugs.launchpad.net/mythbuntu/+bug/759492) .I've actually gotten round that by booting directly from grub4dos now, as reported in that thread, although only by using a vmlinuz and initrd.img extracted from a Virtualbox machine on my other PC, so I should probably copy over those with the ones from inside the Mythbuntu installation.

So Mythbuntu boots and asks me to select a language and then says it can't connect to the backserver (no doubt connected to the error I had during install). I'm also stuck on 640x480 and can't change it and when I tried to install the proprietary ATI/AMD driver, it failed. It told me to look at jockey.log for details, which was rather hard as there wasn't a text editor installed!

I'd upload grub.cfg and jockey.log but apparently they're not permitted formats and I don't know how to zip with Ubuntu yet. I can't see any Myth logs in var/log either, but let me know if there's anything else I can upload and how to zip the files I have got so I can upload them.

Actually, I just found Mythbuntu Log Grabber, but the MythTV Backend and Fronted options are greyed out, so I assume that can't find them either. Logs are here, but these are from booting with the Ubuntu 10.10 vmlinuz and initrd.img, so I'll redo them after booting with the Mythbuntu ones.

---

### Post by doveman on 2011-04-15
OK, I found that the Mythbackend wasn't even installed for some reason, so I fixed that, but it's still not able to connect to the database.

I rebooted after copying the Mythbuntu vmlinuz and initrd files over, and then I was able to install the ATI/AMD graphics driver, which after rebooting gave me something like 1152x768@60hz.

I tried to change it to the resolution I normally use 1280x1024, but the refresh rate wouldn't change from 60hz and when I applied I lost the display and my monitor went into standby. Rebooting didn't help as after the login screen, the display goes off again.

I've checked the Xorg.conf and there's nothing about screen resolution in there, so I need some help getting this fixed please.

---

### Post by doveman on 2011-04-17
Hmm, just noticed that I managed not to post the link to the logs in my first post!

I'll do them again, but first I need someone to help me get the display working again please?

---

