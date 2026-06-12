---
title: "Enable raw1394"
date: 2009-12-26
forum: Multimedia Software
---

### Post by tnasty on 2009-12-26
I am trying to get my firewire working and I have been following the instructions found here:

[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

but these instructions tell me to edit

/etc/udev/rules.d/65-permission-raw.rules

but this file does not exist on my computer. The only files in /etc/udev/rules.d are 

70-persistent-cd.rules  70-persistent-net.rules  README

any ideas? Also, I tried to install the ubuntu studio controls and enable firewire through that, but it didnt work.
Thanks,
David

---

### Post by scotty64 on 2010-03-29
Although the WiKi mentions Karmic it does not take the new UDEV directory structure into account:
Karmic uses two directories for UDEV rules: /lib/udev/rules.d for the default rules and package rules and /etc/udev/rules.d (what is empty by default) for customized rules.
The standard process is to copy the file you want to change from /lib/udev/rules.d to /etc/udev/rules.d and do the modifications there. raw1394 is not defined in any of the default files, so you have to create a new rules file - in my case 98-raw1394.rules containing the line described in the WiKi.

---

