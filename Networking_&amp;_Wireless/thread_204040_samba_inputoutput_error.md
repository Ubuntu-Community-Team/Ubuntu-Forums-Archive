---
title: "samba input/output error"
date: 2006-06-26
forum: Networking &amp; Wireless
---

### Post by BryanKeith on 2006-06-26
I have some windows shares mounted on an ubuntu machine.  When I reboot the ubuntu machine, I see and can write to the shares fine.  However, after some time, ubuntu no longer recognizes the shares and I get an input/output error when trying to access files on those shares. The shares are mounted like this (in /etc/fstab):

#windows2000 desktop example:
//bryan2000/c       /home/bryan/windows/bryan2000c  smbfs credentials=/etc/samba/user,rw,uid=bryan   0   0
#windows file server (not sure what OS) example
//gisserver/data    /home/bryan/windows/gisserver   smbfs  defaults,uid=1001,gid=1001,credentials=/etc/samba/user,uid=bryan,umask=777   0   0

Why do I get this input/output error?  I have the shares mounted on a redhat machine, and the shares are always available there (though they're mounted as read-only).  The machines are not rebooted.

How do I get the shares to work again?  The only solution that's worked is to reboot the ubuntu machine.  Then everything's happy again.

Bryan

---

### Post by punky on 2007-08-09
*bump*

I get this error too.

I've tracked down the cause.

Basically, I run an Ubuntu fileserver with samba installed. I have an XP machine with file sharing enabled. The linux box mounts a shared directory on the XP machine. The Linux box is on 24/7, the XP box is shutdown at night and started again in the morning. 

When the XP box is restarted overnight, samba suddenly fails with an input/output error. 

I have other XP and an Mac OSX machine which can both interact just fine with the restarted machine.

The only way to fix is to reboot the linux box. If you force an unmount, it comes up with a device is busy error.

Can another think of a way around this? I can't leave my XP machine on 24/7

---

### Post by BryanKeith on 2007-08-09
I hadn't figured out why this was happening, but I solved the problem by having a cron job that runs every ten minutes.  It checks to see if the mount is ok.  If it's not, it attempts to umount and mount the share again.  This solution seems to have worked for me, though it sounds like that won't work in your case.

---

### Post by punky on 2007-08-10
I just can't see why smbfs needs to maintain a permanant connection, rather than just making a connection as-and-when like every other FS does... The shutdown computer comes back with the same IP, etc, so its nothing daft like that

People have suggested cron jobs and raising the timeout value, but ti won't help because no matter how quickly i restart my shutdown computer after being shutdown, the smbfs connection because borked.

I'm just hoping there's some magical option that I can put in fstab

---

### Post by punky on 2007-08-10
Some follow up....

I have found this page: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/46514](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/46514)

Which is what's happening. Someone mentioned about SMBFS still working through rthymnbox, so I tried access it via the GUI/Konquerer after the machine was shut down for a night, and it works splendidly. Try to do a ls via terminal and keeps coming up with input/ouput errors. Still works via Konquerer either side of getting an input/out error via terminal

There are time out errors in the /var/log/syslog as someone said there would. 

I could try increasing the timeout value, although this is happened after only a couple of mins. 

Still does anyone know where the smbfs timeout is? does it share its config with smb.conf?

---

### Post by matthias_k on 2007-10-19
*bump*

This is so annoying. I can't browse my shares beause of these timeout problems. There must be a solution?! Is this a Ubuntu problem or a problem with my server?

(I have posted my config in the bug report on launchpad)

---

### Post by jogar2 on 2007-12-03
I've been experiencing this sort of failure for *YEARS* now. Several times I've rampaged through the interwebs looking for a possible solution but I always come back to "reboot the Linux box". :(

I have an hourly cron job do a "df", which helps keep the shares fresh, and several of my Samba-hitting scripts do a df > /dev/null >&1 before they start, but if the Windows server goes down or there is any other sort of network interruption, the Samba connection goes dead for good.

---

