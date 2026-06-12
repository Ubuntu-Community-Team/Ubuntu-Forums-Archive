---
title: "Shared folder requires user/pass"
date: 2009-07-11
forum: Networking &amp; Wireless
---

### Post by xerces8 on 2009-07-11
Hi!

On Ubuntu 9.04 I did this:
 - create a folder in home dir
 - right click it and select "Sharing Options"
 - in the dialog enabled "Share this folder"
 - OK'ed the dialog saying to install sharing components, entered password
 - in a dialog telling me that a restart of session is needed, I clicked "Restart"

Expected result: Being able to access the shared folder from other PC

Actual result: When trying to open the shared folder on other PC (Windows XP Pro SP3) it pops up a dialog asking for username and password. I enter my username and password that I use on the linux box, but it just shows the same dialog again.

The share (also new created ones) appears in the My Network Places, I just can not open it...

Any clue ? Are there any steps I (well, the wizard) forgot ?

Regards,
David

---

### Post by superprash2003 on 2009-07-11
post contents of the following 2 files /etc/samba/smb.conf and /etc/samba/smbusers

---

### Post by xerces8 on 2009-07-12
I attached the smb.conf (gzipped due to forum restrictions).

There is no /etc/samba/smbusers  file.

---

### Post by xerces8 on 2009-07-12
Ah, after a reboot, it works !

I guess a reboot fixes everything ;)

---

