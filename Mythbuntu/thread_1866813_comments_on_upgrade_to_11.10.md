---
title: "comments on upgrade to 11.10"
date: 2011-10-22
forum: Mythbuntu
---

### Post by ZedThou on 2011-10-22
After painful experiences in the past I had vowed not to mess with a system that works, but come April and October I just can't help myself. So I've done the upgrade to Mythbuntu 11.10. No doubt others who have done the same are having a lot of trouble and I can certainly sympathize, but here is my experience.

**gdm configuration**
The first conundrum was encountered after the upgrade downloaded all of the new packages - a gdm configuration dialog asking me which interface to use by default, gdm or lightdm. I chose gdm not knowing which was the correct answer. I had read [http://ubuntuforums.org/showthread.php?t=1860270](http://ubuntuforums.org/showthread.php?t=1860270) where lightdm hadn't configured itself properly on the upgrade, but figured I could straighten this out later regardless.

**lightdm configuration**
From there everything went smoothly up to the reboot dialog. At this point I took the suggestions of superm1 and colin.mcgregor in [http://ubuntuforums.org/showpost.php?p=11358168&postcount=16](http://ubuntuforums.org/showpost.php?p=11358168&postcount=16) and removed unity-greeter (apt-get purge unity-greeter), edited /etc/lightdm/lightdm.conf (changing supermario to my frontend username) and rebooted.

**new lirc configuration**
After the reboot everything seemed to look good. The only problem was that the remote (mceusb, a Harmony One with a generic Vista MCE receiver) wasn't working. I took the advice of beartard at [http://ubuntuforums.org/showpost.php?p=11373685&postcount=6](http://ubuntuforums.org/showpost.php?p=11373685&postcount=6)
and ran mythbuntu-lirc-generator. This created a new ~/.lirc/mythtv and it backed up my modified previous file to ~/.lirc/mythtv.old Many button names have changed and with the old file for consultation and judicious use of irw I was able to reconstruct the modifications in the new file.

**impressions**
My combined FE/BE is an Atom 330 ION with an HDHomeRun. Two things have always bothered me. Viewing photo albums on the frontend has always been incredibly sluggish. This has improved a lot, and I don't know why nor do I care. It's just much nicer. The other is that LiveTV has always been painful with buffer timeouts and such but is more responsive now.

So thanks very much to the Mythbuntu developers, the system is running better than ever at the moment.

---

### Post by 2F4U on 2011-10-22
Thanks for sharing your experience. Its good to hear at least some positive comments besides all the negative experiences.

---

