---
title: "Smbs/cifs Need some Editing"
date: 2010-06-26
forum: Networking &amp; Wireless
---

### Post by mirzagulraiz on 2010-06-26
I m Using Ubuntu 10.04 desktop.
I want to share some folders for XP.
I have added some shares through GUI.
I click on FOlder and share it, i was asked to install sharing utilities to install.
I click ok, then it starts downloading Samba and smbpass, then automatically install it.
My sharing is running.
But i want to edit that configuration file to change some rules.
I change /etc/samba/smb.conf but nothing happens as it is not associated with shares.
my Shares were not in it.
So tell me how to Find then in Conf file.
tell me the Location of smb.conf which is installed automatically by ubuntu.

---

### Post by Morbius1 on 2010-06-26
Ubuntu uses two completely different ( and sometimes conflicting ) samba methods to share files:

Samba Nautilus-shares, which you use through Nautilus itself, has shares defined in [COLOR=Blue]/var/lib/samba/usershares.[/COLOR] That's why you can't find them in smb.conf. They look different from the traditional share definitions .

Samba Classic-shares which have shares defined in [COLOR=Blue]smb.conf.[/COLOR]

You can't edit Nautilus-shares. The only options are the ones offered through the Nautilus gui itself.

---

