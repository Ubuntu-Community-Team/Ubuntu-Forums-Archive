---
title: "Shared printer won't work after reboot"
date: 2011-04-15
forum: Networking &amp; Wireless
---

### Post by jimbo99 on 2011-04-15
After connecting up a printer to my desktop, then installing the driver, and setting up the share, I can print from the local workstation without a problem.  But...

If I try to print to that shared printer from any other workstation, whether it be Windows or Linux, nothing prints.

Checking the shared services/devices from a windows workstation (via network neighborhood), looking at the shares on the Linux desktop, the shared folders are visible and accessible from the Windows workstation, but the printer (shared device) is missing.

It took a while but I uncovered some info about having to kill the samba daemon then restart it.  Until recently I could do a "samba restart" and that worked.  It no longer works because of the way that the samba service is started (the term upstart job comes to mind--I don't remember the exact phrase).

I was for a short time successful at killing the smbd daemon.  After every reboot I would forget.

Shortly thereafter I realized that in the /var/run/samba folder is a file smbd.pid that contains the process ID.  I then created a small script that would kill the job based on the PID in that file automatically for me.

Throughout all of this I couldn't help thinking that though this works it is a real pain to have to remember.  There needs to be a better way.  Actually, this shouldn't exist as a problem.  Canonical (or whomever is in charge of this part of it) needs to resolve this issue.  I can imagine all the small companies that might use a Linux, but don't--and how the resolution I devised had to change within a matter of a couple weeks.

Anyone have any solid ideas on how to resolve this properly once and for all without forcing user intervention to make a shared printer print over the network?

---

### Post by jimbo99 on 2011-04-15
Earlier today I did my daily updates to Ubuntu.  I rebooted.  At that time I decided to try to get my script to run as an autostart in KDE.

I set up the autostart command and then rebooted again.  After coming up I tried to print something from another machine.  No luck.  I then decided to look at a Win7 workstation to see if the printer share was listed.  It was not.  The folder shares were there and accessible, but not the printer.

I then removed the entries from the autostart feature of KDE and rebooted again.  I issued the command manually this time and looked again to see if the printer shares were listed.  They were not.  The folder shares were there, but the printer shares were not.

I then decided to go to /etc/init.d/ and look at the smbd entry.  It's a link "smbd -> /lib/init/upstart-job".

I then issued the "sudo smbd restart" command and this time it worked.  I was able to successfully see the printer shares from the Windows workstation.

That's 3 changes in about as many weeks.  I have to wonder when are they going to get this straightened out.  First it works with smbd restart, then it doesn't and I can kill the job and have it restart, then I can't kill the job and have it restart, instead I have to go back to the "smbd restart" command.

I am still looking for a solution to this.  I would really like to have this resolved once and for all.  Any help would be appreciated.

---

