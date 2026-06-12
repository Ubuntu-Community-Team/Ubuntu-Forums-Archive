---
title: "Creating a account for backuppc"
date: 2010-02-20
forum: Networking &amp; Wireless
---

### Post by Luc484 on 2010-02-20
Hi! I'm trying to setup backuppc to access using apache. I followed this guide: [https://help.ubuntu.com/community/BackupPC](https://help.ubuntu.com/community/BackupPC). Apache2 is correctly running on my pc. I used this command: htpasswd /etc/backuppc/htpasswd user and, as the guide says, I tried to access [http://localhost/backuppc](http://localhost/backuppc) but I get nothing there. Is anything else I should do to access backuppc?
Thanks!

---

### Post by tx836519 on 2010-03-10
Hi Luc,

I'm having to rebuild my backuppc server due to doing what I do best -- making mistakes!  I'm good at it since I've been practicing for a long time and they say you get good at what you practice!

When you install backuppc using apt-get, it will open a dialog to configure some of the backuppc settings.  The first selection is for the browser.  You need to select the last item, apache2.  If you select apache, it will not present the logon panel for the web interface.

If you selected apache instead of apache2 on the previous install, you need to completely purge the system of backuppc as follows:
sudo apt-get purge backuppc

Next, reinstall backuppc with 'sudo apt-get install backuppc' and be certain to select apache2 at the bottom of the panel by moving down until high-lighted and then press the space bar followed by <enter>.

You can change the backuppc user password using the command you used before if you wish.

[http://hostname/backuppc/](http://hostname/backuppc/) should now present the logon screen. -- ken

---

