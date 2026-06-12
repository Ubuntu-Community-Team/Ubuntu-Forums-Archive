---
title: "CUPS Printer Install Locked out Local Login on Ibex"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by Nausser on 2008-12-22
I am running a fresh install of Ibex and was trying to get a web interface printer install working on a Vista machine.

After trying to install a shared printer on Vista via the CUPS web("http://<ubuntucomp>:631/printers"); it said it installed the printer(which it did not) and then all my local printers on my ubuntu machine were gone.

After restarting my ubuntu machine, everything seems fine until I try to login. 

I type my username, password and hit enter expecting my desktop to show and the screen flickers a few times and returns to the login screen.

This is the second time I've done this to myself thinking there is not way CUPS could have this effect. WRONG!! 

My laster version was UbuntuStudio(went regular the second time around.)

Not really sure where to file this one; however, it is definently caused by the CUPS web interface install printer process from another machine.

Also, if I drop to command line login, I experience the same problem. 
I really do not want to fresh install yet again!! I tweaked everything so perfectly!

Someone please help!!

If you need more info, please let me know.

Thank You,
Nausser

---

### Post by dmizer on 2008-12-24
Try this to regain access to your box: [http://ubuntuforums.org/showthread.php?t=3609](http://ubuntuforums.org/showthread.php?t=3609)

Don't know what to tell you about your CUPS issue though ...

---

### Post by bgiannes on 2009-03-05
i just had the same thing happen to me, 

i was installing a print on a ubnutu laptop, on my home network, the cups install crashed at the enter password.....

next thing i know, my ubnutu server (cups server) will not let me login anymore!?!?

resetting the root password in recovery mod did not fix the problem?

other then the fact i cant login, the server is running as normal? ssh, webmin, local login all are a no go :( 

help please!

---

### Post by bgiannes on 2009-03-05
UPDATE:


okay, for some reason i can now login to webmin.

but i can't login to the commandline, ssh don't....

---

### Post by bgiannes on 2009-03-05
i think to bug is noted here:

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/303458](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/303458)

and

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/260687](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/260687)

fix is...

- Reboot and choose the "recovery mode" from the boot selection menu
- Choose "drop into root shell" from the recovery menu
- Execute the command: dpkg --purge libpam-smbpass

Doing this, I am able to logon again.
Before reinstalling libpam-smbpass, delete or rename /var/lib/samba/secrets.tdb:

sudo mv /var/lib/samba/secrets.tdb /var/lib/samba/secrets.tdb.old
sudo apt-get install libpam-smbpass

disco!

---

