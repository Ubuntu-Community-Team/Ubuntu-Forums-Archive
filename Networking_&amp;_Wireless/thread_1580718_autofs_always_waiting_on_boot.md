---
title: "autofs always waiting on boot"
date: 2010-09-23
forum: Networking &amp; Wireless
---

### Post by menkelis on 2010-09-23
System: 10.04
I use NIS for logins, and autofs for NFS mounting home directory.
On booting, the status of 'autofs' is waiting, so if I try to login there
is no home directory.
Wha I am currently doing to prevent this is login as a "local" user
and then use "sudo /etc/init.d/autofs start"
When this is done I can then login using with the NIS username/password
and the home directory is now mountable.

Is there a fix so that I do not need to kick autofs each time a boot is done?

---

### Post by haihovu on 2010-11-16
Your problem was probably caused by autofs coming up before NIS (or may be autofs not starting at all). In recent releases of Ubuntu autofs startup was migrated to the newer upstart framework while NIS is started using the old system V init scripts. I'd put the following line in /etc/rc.local to make sure that autofs is started and started after nis:

start autofs

---

