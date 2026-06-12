---
title: "broadcom no longer works"
date: 2009-05-15
forum: Networking &amp; Wireless
---

### Post by hallve_revera on 2009-05-15
hiii,,
i got a lil problem here
recently, i tried to install the mac80211 driver that was included in compact-wireless from wirelesskernel.org
but after i installed that module, my broadom no longer works,
i also tried to uninstall the module, but it had the same result
anyone could help me
sory for my bad english and thanks for any help

---

### Post by Kevbert on 2009-05-15
Please go to terminal and enter
```
lspci
```
and post back the model and revision of Broadcom wireless adapter.

---

### Post by hallve_revera on 2009-05-23
sory for the late replay
this is the lspci of the broadcom adapter



Broadcom Corporation BCM4312 802.11b/g (rev 01)


and when i install the compact-wireless i have to remove linux-restricted-modules by this command

sudo update-rc.d -f linux-restricted-modules-common remove

thanks for ur replay

---

### Post by hallve_revera on 2009-05-23
sory for the late replay
this is the lspci of the broadcom adapter



Broadcom Corporation BCM4312 802.11b/g (rev 01)


and when i install the compact-wireless i have to remove linux-restricted-modules by this command

sudo update-rc.d -f linux-restricted-modules-common remove

thanks for ur replay

---

### Post by Ayuthia on 2009-05-23
Can you post the results of lspci -nn?  The 4312 rev 01 card has a couple of chipsets.  One of which does not work (14e4:4315) with the mac80211 but the ieee80211* and wl modules.

---

### Post by hallve_revera on 2009-05-23
yeah that's my card
it uses the wl module

so how to make it work again,
i told u that i had uninstall the mac80211 module but thats not solve the problem

---

### Post by Ayuthia on 2009-05-23
It is most likely not working because you removed linux-restricted-modules-common from rc.d.  You will need to add it back.

For the time being, I think you can start it back up manually by doing:
```
sudo /etc/init.d/linux-restricted-modules-common start
```
It has been a while since I have added anything to rc.d so I cannot remember the exact command.  It has something to do with update-rc linux-restricted-modules-common, but I can't remember the numbers that you need to add to the end.

---

### Post by hallve_revera on 2009-05-24
thanks for ur reply

---

### Post by hallve_revera on 2009-05-25
but that doesnt solve my problem
did you get a link or tutorial about update-rc.d

---

