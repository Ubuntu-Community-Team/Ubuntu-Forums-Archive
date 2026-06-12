---
title: "[SOLVED] cron will not start"
date: 2008-06-29
forum: Mythbuntu
---

### Post by Captain_Bodge on 2008-06-29
I've just found out that cron is not running on my system. I'm running mythbuntu 8.04. I've tried a forced reinstall of cron, but to no avail. The relevant symlinks in /etc/rc*.d exist. I can start cron manually once the system has booted by typing 'sudo /etc/init.d/cron start' and then I see cron printing messages to /var/log/syslog:

Jun 29 12:46:29 newboy /usr/sbin/cron[8978]: (CRON) INFO (pidfile fd = 3)
Jun 29 12:46:29 newboy /usr/sbin/cron[8979]: (CRON) STARTUP (fork ok)
Jun 29 12:46:29 newboy /usr/sbin/cron[8979]: (CRON) INFO (Running @reboot jobs)


But from a cold boot, there are no messages from cron in syslog at all. I find it odd that when I start it manually it says 'Running @reboot jobs' - this implies to me that it simply didn't start at boot at all.

Can anybody help me track this down? Anybody seen the same thing?

---

### Post by ian dobson on 2008-06-29
Hi,

Sounds as if a symbolic link in rcx.d to the cron start scripts.

On my frontend I have the following links that point to /etc/init.d/cron.

```

/etc/rc2.d/S89cron
/etc/rc3.d/S89cron
/etc/rc4.d/S89cron
/etc/rc5.d/S89cron

```

and 
```

/etc/rc1.d/K11cron

```

Regards
Ian Dobson

---

### Post by Captain_Bodge on 2008-06-29
Mmm. OK, typing the post gave me an idea. I've solved the issue of why cron won't start but I don't know why.

Looking in /etc/rc5.d the script to start cron is S89cron. I tried moving it to later in the boot process (to S99 using update-rc.d) but that didn't help. Then I moved it earlier in the boot process (to 19) and now it starts.

So it looks as if something earlier in the init process is preventing cron from starting, but wierdly not affecting it once the system has finished booting. The things earlier in the init process are:

S20apache2
S20apmd
S20apport
S20hddtemp
S20hotkey-setup
S20mysql
S20mythtv-backend
S20nfs-common
S20nfs-kernel-server
S20ntp
S20nvidia-kernel
S20powernowd
S20rsync
S20samba
S24dhcdbd
S24hal
S30gdm
S51lirc
S51mythtv-status
S89atd

Anybody have any ideas as to what might be going on?

Edit: Ian, thanks you replied while I was posting the above. I had all those symlinks existing already, and they were recreated when I forced a reinstall of cron. So I'm pretty sure the problem is (was) not due to a missing symlink.

---

### Post by ian dobson on 2008-06-29
Hi,

Try finding out when (at what start level) cron doesn't start. It sounds as if one of the init scripts is dying and killing the process that calls the rest of the list.

Regards
Ian Dobson

---

### Post by Captain_Bodge on 2008-06-29
Hi Ian,

Thanks I think you've found the problem. Looking at my list I just checked which processes are running - lirc is, but atd isn't .. so it must be mythtv-status that is dying I think. Which is odd because again, I can start that from the command line and it starts OK - but it does take several seconds to start even then. I'll do some more digging now that I know what I'm looking for.

Thanks for your help.

---

### Post by Captain_Bodge on 2008-06-29
Hi Ian,

Thanks I think you've found the problem. Looking at my list, I checked which processes are running - lirc is running *but* there is also a process called S51lirc - so it looks as if that script hangs for some reason. Now at least I know what I'm looking for.

Thanks for your help.

Edit. Ah. that was meant to be an edit of the post above..

---

### Post by Captain_Bodge on 2008-06-29
Got it. My lirc arguments in hardware.conf included a '-n', which seems to cause the behaviour I was seeing. No idea what '-n' does, it's something I found in another thread somwehere else... doesn't seem to need it anyway so all is good now.

---

### Post by ian dobson on 2008-06-29
Hi,

Good to hear the problems solved. Maybe change the thread title to [SOLVED] bla bla bla.

Regards
Ian Dobson

---

