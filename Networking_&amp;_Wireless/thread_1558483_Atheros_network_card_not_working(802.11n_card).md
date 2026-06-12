---
title: "Atheros network card not working(802.11n card)"
date: 2010-08-22
forum: Networking &amp; Wireless
---

### Post by SonnyKing on 2010-08-22
Hi,
My atheros network card (AR9287) work well with ath9k driver, 
but for some reasons, i need uninstall it, and install madwifi driver.My OS version is 10.04, and kernel 2.6.32-21-generic;

I followed the HowTo Link: 
[http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo)
And downloaded madwifi in [http://madwifi-project.org/](http://madwifi-project.org/), (surely, branch version);
when i "make",there is some some warning, "athstats.c: format not a string literal and no format arguments", and alse "wlanconfig.c: ignoring return value of fgets, declared with attribute warn_unused_result",etc.

but when i "make install", only one warning:"-e needs -E or -F
Then I modprobe ath_pci module, reboot, but lshw -C network returns "AR9287 unclaimed",

Any suggestions? thank you.
One thing more, system>administrator>hardware drivers, only ATI card included, nothing more, even the wireless card integrated with my laptop isn't there, but they can work! what's wrong

---

