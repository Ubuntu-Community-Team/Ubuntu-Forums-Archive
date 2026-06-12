---
title: "automatic startup of samba?"
date: 2010-05-19
forum: Networking &amp; Wireless
---

### Post by wkulecz on 2010-05-19
I like the faster boot of 10.04, but how do I get smbd to start automatically on a boot up?

Every thing is fine if I sudo service smbd start but I don't see where I'm supposed to have it run automatically on a reboot.

--wally.

---

### Post by wkulecz on 2010-05-20
bump!

Somebody must know how to add a new startup service or where its documented.

If I get desperate I could run it with @reboot from a root crontab but this is not the Ubuntu way!

--wally.

---

### Post by puppywhacker on 2010-05-20
"service" is a wrapper script which uses the sys-v style startup-scripts in /etc/init.d/ so the old method of starting samba was "/etc/init.d/smb start". The service script is a more intelligent way of stopping and starting these services.

There is probably an cool script or program to start services at boot time but in sys-v the method is to make a softlink in the runlevel directory towards the startup script in the init.d directory.

in a terminal shell you can run "runlevel" and you will see that Ubuntu Desktop usually runs in level "2".

```
sudo ln -s /etc/init.d/smbd /etc/rc2.d/S51smbd
```

This would create a softlink in the directory /etc/rc2.d/ that starts with a capital S and a 2-digit number representing the startup order relative to the other scripts.

This softlink makes the real file /etc/init.d/smbd also accessible from an other directory.

```
ls -la /etc/rc2.d/S51smbd 
lrwxrwxrwx 1 root root 16 2010-05-20 17:16 /etc/rc2.d/S51smbd -> /etc/init.d/smbd

```

To be complete you can switch to runlevel 6 with "sudo init 6" or shutdown with "sudo init 0". To stop a service in a different runlevel use the same style softlink with a capital K in the other runlevel directory.

```
sudo ln -s /etc/init.d/smbd /etc/rc6.d/K51smbd
```

although this last step is pretty much optional as smb would be killed anyway during a restart.

Let me know when this concept is not clear, because I wouldn't know how to explain this more clearly without specific followup questions.

---

### Post by ZeldeR on 2010-05-20
[PHP]update-rc.d YouR-Process defaults 18  [/PHP]



Example:
[PHP]
update-rc.d firewall defaults 18  [/PHP]


[PHP]ostname:~# update-rc.d firewall defaults 18
 Adding system startup for /etc/init.d/firewall ...
   /etc/rc0.d/K18firewall -> ../init.d/firewall
   /etc/rc1.d/K18firewall -> ../init.d/firewall
   /etc/rc6.d/K18firewall -> ../init.d/firewall
   /etc/rc2.d/S18firewall -> ../init.d/firewall
   /etc/rc3.d/S18firewall -> ../init.d/firewall
   /etc/rc4.d/S18firewall -> ../init.d/firewall
   /etc/rc5.d/S18firewall -> ../init.d/firewall[/PHP]

---

### Post by wkulecz on 2010-05-20
The current "Ubuntu way" using upstart  is described briefly in:
[http://ubuntuforums.org/showthread.php?t=1487822](http://ubuntuforums.org/showthread.php?t=1487822)

More detailed info can be found at:
[http://www.linuxplanet.com/linuxplanet/tutorials/7033/1/](http://www.linuxplanet.com/linuxplanet/tutorials/7033/1/)



Basically /etc/init/smbd.conf  (note its not init.d) has to be changed:

start on local-filesystems

to:

start on (local-filesystems and net-device-up IFACE!=lo)




The /etc/init.d and /etc/rc.d are depreciated and likely to introduce bugs eventually if you try to use them for stuff handled in /etc/init.

--wally.

---

### Post by puppywhacker on 2010-05-20
thanks for your analysis. "upstart" indeed replaces init.d sys-v style startup scripts. Although it is still backwards compatible with the init levels and rc scripts, it is indeed deprecated.

The more you know, the slower you accept change :) Time for me to start reading.

---

