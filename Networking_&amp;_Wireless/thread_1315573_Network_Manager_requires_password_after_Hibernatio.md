---
title: "Network Manager requires password after Hibernation"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by ardyer on 2009-11-05
I recently upgraded to Ubuntu 9.10 from 9.04 and have a bizarre issue with the network manager keychain.  I am running 9.10 on a 4 year old Dell Inspiron 6000, and everything worked fine prior to the upgrade.

Whenever my laptop awakes from hibernation after the computer has been shut, I have to reenter my keychain password to connect to my wireless network.  This does not occur if the machine was shutdown/restarted or if I manually choose Hibernate and do not shut the lid of the laptop.

I have tried following the instructions about adding the two instructions to the end of /etc/pam.d/gdm file, but this had no effect.

Does anyone have any ideas about this?

---

### Post by ardyer on 2009-11-07
Solved.  I launched gconf-editor, went to apps->gnome-power-manager->lock and unchecked gnome_keyring_hiberrnate.

---

