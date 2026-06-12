---
title: "CIFS woes (again)"
date: 2006-06-22
forum: Networking &amp; Wireless
---

### Post by jferrando on 2006-06-22
Hi,
I have a Debian/etch Samba version 3.0.22 server in my company and are testing a kubuntu/dapper desktop.

I have two important woes:

1) [COLOR="Navy"]**Openoffice 2.02 does not open files properly**[/COLOR]. They open in the modes

[FONT="Courier New"]Pid          DenyMode   Access      R/W        Oplock           SharePath           Name
----------------------------------------------------------------------------------------
17569        DENY_NONE  0x12019f    RDWR       EXCLUSIVE        /datos   mirror/linux/dns_howto.odt   Wed Jun 21 23:20:45 2006[/FONT]

but when saving, a message apperars "No se pudo crear la copia de seguridad" something like "Could not create backup copy". When this message window is accepted, the samba server does no longer keep the file lock. Of course, when saving again, it saves, but file is unlocked meanwhile.

2) **[COLOR="Navy"]Copying files from local ext3 filesystem to CIFS filesystem using konqueror[/COLOR]**
I select a file in my local filesystem ex. /home/jferrando/test.txt and copy it to the cifs filesystem /home/jferrando/server/personal folder. Then konqueror shows an error message box with "No se pudieron cambiar los permisos de
/home/jferrando/csurera/mirror/linux/cifssmb.c", that means "could not change file permissions".
My server has the following options:
[FONT="Courier New"]unix extensions = yes
delete readonly = yes[/FONT]

For me, aspects like this prevents at this moment linux/kubuntu being usable as an desktop alternative, not to mention lack of applications, etc. Maybe 2 to 5 more maturing years?

---

