---
title: "Diskless Ubuntu and tftp-hpa"
date: 2010-01-15
forum: Networking &amp; Wireless
---

### Post by vasg on 2010-01-15
Hi

I followed [https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)
on a fresh installed Ubuntu Server 9.10 to make some diskless machines boot 
over the network. Although originally it worked and clients booted into the OS,
after rebooting the server, every attemp of the clients to boot was stopping early by *pxelinux.0* file not being found. 
I had  */tftpboot*  as tftp root directory set in  */etc/default/tftpd-hpa file*:

[I]#Defaults for tftpd-hpa
RUN_DAEMON="[COLOR=Red]yes[/COLOR]"
OPTIONS="-l -s [COLOR=Red]/tftpboot[/COLOR][/I]"              

witch originally worked. So i found that after rebooting the server, tftp-hpa was using  */var/lib/tftpboot  *defined in  */etc/inetd.conf*
ignoring  */etc/default/tftpd-hpa *options
I have read about this issue but does it stand in 9.10 too?

---

