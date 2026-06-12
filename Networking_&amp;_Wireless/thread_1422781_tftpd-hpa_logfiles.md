---
title: "tftpd-hpa logfiles"
date: 2010-03-05
forum: Networking &amp; Wireless
---

### Post by breezybob on 2010-03-05
Hi all,

I'm trying to create a Mythbuntu diskless client using PXE boot. I got part way through the process and made a bit of a boo-boo. I deleted everything from /var/log
The PXE boot process isn't yet working and now I can't figure out why as I'm not getting feedback in the form of the /var/log/tftpd.log as I was previously.
I've tried re-creating the file, wiping out tftpd-hpa package (including using the purge option to remove config files) and then re-installing and checking that the log file is writable by all users. I'm still not getting anything in the log file and it's making it impossible to get any further with the PXE boot.

Can anyone suggest a way to force tftp to output info to the logfile?

---

